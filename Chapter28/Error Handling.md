- Error프로토콜을 사용하면 error형식으로 선언이 됨
```
enum DataParsingError: Error {
  case invalidType
  case invalidField
  case missingRequired(String)
}
```
-----------------------------------------------------------------------------------
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
try expression //주로 do catch문과 함께 사용함
try? expression  //옵셔널 try라고 부르고 표현식에서 error가 발생할 경우 nil을 리턴함
try! expression  //에러가 발생할 경우 runtime 에러가 발생함, 가능하면 사용하지 않는 것이 좋음
//표현식 부분에는 주로 Throwing Function/Method,Throwing Initializer,Throwing Closure가 
```
```
try? parsing(data: [:]).    //nil을 리턴함
```
-에러를 처리하는 방법은 주로 3가지로 분류함
- 1. do-catch statements
- 2. try expression + optional Binding
- 3. 전달받은 에러를 다른 코드 블럭으로 다시 전달함
