- Closure
- 비교적 짧고 독립적인 코드 조각 : self-contained code blocks
1. Function, Nested Function (Named Closures)
2. Anonymous Function (Unnamed Closures)
- 함수와 클로저는 서로 호환됨(함수를 전달하는 곳에 클로저를 전달하고, 그 반대도 가능함)
- 클로저 형식은 global scope에서 단독으로 사용할 수 없음
```
{ (parameters) -> ReturnType in
    statements
}
```
```
{ statements } : 가장 단순한 형식의 클로저
```
```
let c = { print(“Hello, Swift”)  } //문자열을 출력하는 클로저 , 파라미터와 리턴형이 생략된 클로저
c() //Hello swift가 출력됨  //파라미터가 없고 리턴형이 없는 클로저( ()->() )
//클로저는 global scope에서 단독으로 사용할 수 없으므로 "let c = "을 붙여줘야 함
```
```
let c2 = { (str: String) -> String in
	return “Hello, \(str)”
-함수와 클로저 차이점 : 클로저를 호출할때는 argument레이블을 사용하지 않음
```
```
let result = c2("Closure")
print(result)
//클로저를 사용할때는 argument레이블을 사용하지 않음
```

```
typealias SimpleStringClosure = (String) -> String

func perform(closure: SimpleStringClosure) {
	print(closure("iOS"))
}
perform(closure: c2) //Hello, iOS가 출력됨
//상수에 저장된 클로저를 argument에 전달함
```

```
//클로저 자체를 직접 argument로 전달함
perform(closure: { (str: String) -> String in
	return "Hi, \(str)"
})
//Hi, iOS가 출력됨
```
-----------------------------------------
```
let products = [
   "MacBook Air","MacBook Pro",
   "iMac","iMac Pro","Mac Pro","Mac mini",
   "iPad Pro","iPad","iPad mini",
   "iPhone Xs","iPhone Xr","iPhone 8","iPhone 7",
   "AirPods",
   "Apple Watch Series 4","Apple Watch Nike+"
]

var proModels = products.filter({ (name: String) -> Bool
   in
   return name.contains("Pro")
})

print(proModels)

proModels.sort(by: { 1hs: String, rhs: String) ->
  Bool in
  return 1hs.caseInsensitiveCompare(rhs)
  == .orderedAscending
})

print(proModels)
```
-----------------------------------------
```
print("Start")

DispatchQueue.main.asyncAfter(deadline: .now() + 5, execute: {
   print("End")
})

DispatchQueue.main.asyncAfter(deadline: .now() + 5) {
   print("End")
})
//위의 두코드는 완전히 같음

})
```
