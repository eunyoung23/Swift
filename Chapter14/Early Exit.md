```
guard condition else {        //guard블럭에서는 else키워드를 생략할 수 없음
  statements
}
//condition이 true로 평가되면 else블럭이 실행되지 않고 반대로 false로 평가되면 else블럭이 실행됨.
```

```
guard optionalBinding else {
  statements
}                 //guard문을 optionalbinding에서도 사용할 수 있음
```

- guard문의 장점 : if문에서 발생하는 중첩을 피할 수 있고 코드가 좀더 깔끔해짐

------------------------------------------------------------------------
```
func validate(id: String?) -> Bool {  
   guard let id = id else{     //조건이 true가 되면 다음 guard문이 실행이 됨.
      return false
   }
   
   gurad id.count >=6 else{.   //조건이 true가 되면 guard문 이후의 코드가 실행이 됨.
      return false
   }
   
 //  guard let id = id , id.count >= 6 else {
 //      return false
 //  }.   -- 이런식으로 조건을 2개 넣어도 됨
   
   return true
}
```
- guard문은 대부분 local scope에서 사용하고 else문은 해당 local scope의 실행을 중지시키는 것
```
validate(id:nil)   //호출하면 false가 출력이 됨 -- 첫번쨰에서 optional binding이 실패해서 false 출력함
validate(id: "abc").  //호출하면 false가 출력이 됨
validate(id: "swiftlang").  //호출하면 true가 출력이 됨
```
//***** guard문에서 else문은 필수이고 반드시 코드의 실행을 중지해야 함 *******//

-----------------------------------------------------------------------
**********guard문과 if문을 사용했을 때의 차이점*******************
```
//#1
func validateUsingIf(){
    var id:String? = nil
    
    if let str = id {
       if str.count >= 6 {
          print(str)
       }
    }
}
```
```
//#2
func validateUsingGuard(){
    var id:String? = nil
    
    guard let str = id else { return }  //반드시 else문을 통해서 종료해야 함 , 여기서는 return을 통해서 종료함
    //if문과 달리 str을 else 블럭에서 사용할 수 없음
    
    //guard let str = id else { print(id) } 하면 오류가 남
    
    guard str.count >= 6 else { return }
    
    print(str)
}
```
-guard문은 조건의 수가 늘어나더라고 코드의 중첩은 발생하지 않음

