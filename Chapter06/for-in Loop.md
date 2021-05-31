- 범위 연산자로 지정한 범위 반복하기
```
for loopConStant in Range {
  statements
}
```
```
for index in 1 ... 100 {
  print("hello")
}
```
```
for index in 1 ... 5 {
  print(index)
}
```
- _사용하기
```
for _ in 1 ... 5 {
  print(index)
}
//for-in 반복문 내부에서 반복상수를 사용하지 않는다면 _로 바꿔줌(Wildcard Pattern)
```

```
let power = 10
var result = 1

for _ in 1 ... power {
  result *= 2
}
result //1024 출력됨
```

- 짝수만 곱하고 싶다면 : 핵심은 stride함수
```
for num in stride(from: 0, to: 10, by: 2){
  print(num)
}
//0 2 4 6 8이 출력됨
```
