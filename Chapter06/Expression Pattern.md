```
let a = 1

switch a {
case 0...10:
  print("0 ~ 10")
default:
  break
}
```

- Pattern Matching Operator
a ~= b

```
struct Size{
  var width = 0.0
  var height = 0.0
  
  static func ~=(left: Range<Int>, right: Size) -> Bool
  {
    return left.contains(Int(right.width))
  }
}

let s = Size(width: 10, height: 20)

switch s {
  case 1..<9:
     print("1~9")
  case 10..<99:
     print("10 ~ 99")
   default:
      break
}
```
