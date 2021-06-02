- 에러를 던지는 함수나 생성자를 호할때는 try표현식을 사용해야 함
- do 블럭이 아닌 다른 곳에서 try문을 사용할때는 optional try나 forced try를 사용함
- Optional try(try? expression) - 표현식에서 에러가 전달된 경우 nil을 리턴함
- Forced try(try! expression) - 표현식에서 에러가 전달된 경우 실행을 중지함, 런타임 에러가 발생함
- 두 표현식은 에러를 옵서널 값을 변경함 , 그래서 주로 옵셔널 바인딩과 함께 사용함

```
enum DataParsingError: Error{
  case invalidType
  case invalidField
  case missingRequiredField(String)
}

func parsing(data: [String:Any]) throws {
  guard let _ = data["name"] else {
    throw DataParsingError.missingRequiredField("name")
  }
  
  guard let _ = data["age"] as? Int else {
    throw DataParsingError.invalidType
  }
}

if let _ = try? parsing(data: [:]){
  print("success")
} else {
  print("fail")
}
//함수에서 오류가 발생하지 않는다면 if문이 실행됨, 에러가 발생하면 else문이 실행됨
//지금은 빈딕셔너리를 발생하고 있고 코드에서 에러가 나므로 fail을 출력함
```

-위의 if문을 do-catch로 하면 다음과 같이 바뀜
```
do {
  try parsing(data: [:])
  print("success")
} catch {
  print("fail")
}

```
