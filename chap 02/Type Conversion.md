//****Type Conversion*****/
```
//Type(value)

let a = 123
let b = 4.56

Double(a) + b //127.56 출력
a + Int(b)    //127 출력

let c = Int8(a)

let d = Int.max
let e = Int8(d)  //값을 저장할 공간이 충분하지 않다면 에러가 발생함 - 큰 자료형에서 작은 자료형으로 conversion할때는 이런 문제가 발생하지 않도록 조심해야 함

let str = "123" //"123"
let num = Int(str) //123

let str = "number" //"number"
let num = Int(str) //nil
```
/************type conversion이 실패했을때 nil이 리턴될 수 있음***********/