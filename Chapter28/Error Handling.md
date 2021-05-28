- Error프로토콜을 사용하면 error형식으로 선언이 됨
```
enum DataParsingError: Error {
  case invalidType
  case invalidField
  case missingRequired(String)
}
```
```
/*throw expression*/

func name(parameters) throws -> ReturnType { //Throwing Function/Method
  statements
}

init(parameters) throws {  //Throwing Initializer
  statements
}

{ (parameters) throws -> ReturnType in   //Throwing Closure
  statements
}
```
- Error를 전달하는 것을 Error를 던진다고 표현함
```
func parsing(data: [String: Any]) throws {
  guard let _ = data["name"] else{
    throw DataParsingError.missingRequired("name")
  }
  
  guard let _ = data["age"] as? Intt else{
    throw DataParsingError.invalidType
  }
}
//parameter로 전달된 딕셔너리에 name키가 추가되어 있고 age에 저장된 값을 Int로 캐스팅할 수 있다면 throw문은 호출되지 않음.
//throw문은 에러가 발생한 경우에만 호출됨.
```
- Throwing Function을 호출할때는 try Statements를 사용함
```
try expression
try? expression
try! expression
//표현식 부분에는 주로 Throwing Function/Method,Throwing Initializer,Throwing Closure가 
```
