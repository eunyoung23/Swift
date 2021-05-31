```
case let name:
case var name:
```
Value Binding Pattern : 매칭시킬 대상을 상수나 변수로 바인딩한 다음에 case block에서 활용하는 패턴임
```
//일반적인 case문
let a = 1

switch a {
case 1:
}
```

```
//value binding case문
let a = 1

switch a {
case let x:
  print(x)
}
//a 상수를 x 상수로 바인딩함
//바인딩한 상수는 case block내에서만 사용할 수 있음 - 스위치문 다음에서는 x라는 상수를 사용할 수 없음
```
-switch에서 value binding을 단독으로 사용하는 경우는 드물고 주로 where절과 함께 사용함
```
let a = 1

switch a {
case let x where x > 100 :
  print(x)
}
//where절에 실행되는 경우에만 case블록이 실행됨
//이렇게 하면 에러가 남

//이렇게 고쳐야 함
let a = 1

switch a {
case let x where x > 100 :
  x=200 //이것은 오류가 남
  print(x)
default:
  break
}

//변수로 바인딩하면 오류가 사라짐
let a = 1

switch a {
case var x where x > 100 :
  x=200 
  print(x)
default:
  break
}
```

- value binding은 튜플 매칭에서도 자주 사용됨
```
let pt = (1,2)

switch pt {
case let(x,y):
    print(x,y)
case (let x, let y):
    print(x,y)
case (let x, var y):
    print(x,y)
case let(x,_):
    print(x) //필요없는 대상을 바인딩 대상에서 제외시킴 
}
```