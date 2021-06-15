```
//***** String *****//

"Have a nice day"

let str = "1"
type(of: str)     //String.Type
```
```
//***** Character *****//
let ch: Character = "1"
type(of: ch)     //Character.Type

let doubleCh: Character = "AA"   //오류남

//swift에서 큰따옴표에서 문자가 1개가 있다면 string이나 character가 될 수도 있음
//문자가 2개 이상이면 항상 string임 - 이 경우 character가 될 수는 없음

let emptyCh: Character= "" //오류가 남
let emptyCh: Character= " "
```
