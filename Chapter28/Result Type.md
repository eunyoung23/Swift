-Result 형식을 사용해서 Error 처리하기
-Result 형식을 사용하면 에러 형식이 명확하게 선언됨(throwing function은 정확하게 어떤 형식을 에러를 던지는지 파악하지 어려움)
```
enum NumberError: Error{
  case negativeNumber
  case evenNumber
}

enum AnotherNumberError: Error{
  case tooLarge
}

fun process(oddNumber: Int) throws -> Int {
  guard oddNumber >=0 else {
    throw NumberError.negativeNumber
  }
  
  guard !oddNumber.isMultiple(of: 2) else {
    throw NumberError.evenNumber
  }
  
  return oddNumber * 2
}

let result = Result { try process(oddNumber: 1) }
switch result {
case .successs(let data):
  print(data)
case .failure(let error):
  print(error.localizedDescription)
}
//함수가 정상적으로 호출되면 success케이스가 호출되고 에러가 나면 failure케이스가 호출됨
```
-DelayedErrorHandling
```
fun processResult(oddNumber: Int) throws -> Result<Int, NumberError> {
  guard oddNumber >=0 else {
    return .failure(.negativeNumber)
  }
  
  guard !oddNumber.isMultiple(of: 2) else {
    return .failure(.evenNumber)
  }
  
  return .success(oddNumber * 2)
}

let result2 = processResult(oddNumber: 1)
switch result2 {
case .success(let data):
  print(data)
case .failure(let error):
  print(error.localizedDescription)
}

if let result = try? result2.get(){
  print(result)
}
```

