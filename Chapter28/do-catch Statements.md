- do-catch문
----------------------------------------
- do블럭과 catch블럭으로 구분되어 있음
- do블럭은 필수 블럭, try 표현식을 사용해서 에러가 발생할 수 있는 코드를 실행함
- do블럭에서 발생가능한 모든 에러는 catch블럭에서 모두 처리되어야 함
- catch블럭을 생략한 경우에는 에러가 다른 코드로 전파될 수 있도록 구현해야 함
```
do {
  try expression.    //try문에서 에러가 발생하면 다음의 문장(try밑에 이어지는 문장)은 실행되지 않고 아래쪽의 catch문이 실행이 됨
  statements
} catch pattern {    //catch블럭은 do블럭에서 발생한 에러를 처리함
  statements
} catch pattern where condition {  //where절을 추가해서 매칭시킬 에러 패턴에 condition(조건)을 추가할 수도 있음
  statements
}
```
--------------------------------------------
- parsing 데이터 함수를 호출하면서 빈 딕셔너리를 전달하고 있음
```
enum DataParsingError: Error {
  case invalidType
  case invalidField
  case missingRequiredField(String)
}

func parsing(data: [String: Any]) throws {
  guard let _ = data["name"] else {
    throw DataParsingError.missingRequiredField("name")  //이것을 던지게 됨
  }
  
  guard let _ = data["age"] as? Int else {
    throw DataParsingError.invalidType
  }
}

//위에서 던진 것이 do-catch문으로 전달됨
do {  
  try parsing(data: [:])
} catch DataParsingError.invalidType{ //첫번째 블럭에서는 에러 패턴이 들어감
  print("invalid type error")
} catch {  //두번째 블럭에서는 에러 패턴을 생략함
  print("handle error")
}

//두번쨰 블럭과 매칭되어서 "handle error"을 출력함
```
