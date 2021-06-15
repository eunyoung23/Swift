1.Global Scope   
2.Local Scope
- 다른 scope에 있다면 같은 이름으로 선언하는 것이 가능함
```
-- #1 - Global
let g1 = 123

func doSomething() {
   // #3  - Local : 4번과 다른 범위
   
   if true {
      // #4 - Local
     let local3 = 123
   }
   
    print(local3)   //오류 남
   // #5 - Local : 3번과 같은 범위
}
```
```
-- #2 - Global

struct Scope {
   // #6
   
   func doSomething() {
      // #7
   }
}

doSomething()
```
