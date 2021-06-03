-NonEscaping closure: 함수의 실행흐름을 탈출하지 않음
```
func performNonEscaping(closure: () -> ()) {
  print("start")
  closure() //파라미터로 전달한 클로저를 호출함
  print("end")
}

performNonEscaping {
  print("closure")
}
//start
//closure
//end순서로 출력이 됨
```

-Escaping closure: 함수의 정상적인 흐름을 탈출함 , 함수 실행이 종료된 다음에 실행되는 경우도 있는 클로저임, 함수 실행이 끝나기 전에 끝날 수도 있고, 함수 실행이 완료된 후에도 끝날 수도 있음
```
func performNonEscaping(closure: () -> ()) {  
  print("start")
  
  DispatchQueue.main.asyncAfter(deadline: .now() + 3){. //에러가 발생함 - 클로저 파라미터는 기본적으로 non-escaping클로저임
    closure()    //그래서 함수의 실행이 끝나기전에 클로저 실행이 끝나야 함
  }
  
  print("end")
}
//함수의 실행이 완료된 후에 클로저가 실행이 되므로 오류가 남
```

-함수의 실행과 관련없이 클로저가 실행됨.
```
func performNonEscaping(closure: @escaping () -> ()) {  //함수의 실행과 관련없이 클로저 실행이 가능함
  print("start")
  
  DispatchQueue.main.asyncAfter(deadline: .now() + 3){.
    closure()    
  }
  print("end")
}
//오류가 해결이 됨

performEscaping{
  print("closure"). //start,end가 출력되고 3초 뒤에 closure호출됨
}
```

-escaping closure가 왜 필요할까?
파라미터는 함수가 실행되면 생성 되었다가 함수의 실행이 끝나면 자동으로 제거가 됨 
non-escaping 클로저를 실행하면 함수의 종료와 함께 클로저도 함꼐 종료가 됨
