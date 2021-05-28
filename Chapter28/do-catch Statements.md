```
do {
  try expression.    //try문에서 에러가 발생하면 다음의 문장은 실행되지 않고 아래쪽의 catch문이 실행이 됨
  statements
} catch pattern {    //catch블럭은 do블럭에서 발생한 에러를 처리함
  statements
} catch pattern where condition {  //where절을 추가해서 매칭시킬 조건에 condition을 추가할 수도 있음
  statements
}

```
-----------------------------------------
