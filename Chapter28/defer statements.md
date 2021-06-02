-defer문을 호출하면 블럭에 실행된 코드가 바로 실행되지는 않음
-defer문이 실행된 scope의 실행이 종료될떄까지 연기됨
```
defer {
  statements
}
```
```
func processFile(path: String){
  print("1")
  let file = FileHandle(forReadingAtPath: path)

  defer {
    print("2")
    file?.closeFile()
  }
  
  if path.hasSuffix(".jpg"){
    print("3")
    return
  }
  print("4")
}
//1,4,2가 출력됨
```
