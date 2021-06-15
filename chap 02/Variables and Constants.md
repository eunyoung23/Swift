```
import UIKit

//var variableName = initialValue

var name = "Swift"
var year = 2018
var valid = false

var x=0.0,y=0.0,z=0.0

name
print(name)

name = "steve"
name = "yoona"

print(name)

var anotherName = name
anotherName = "Tim"
print(name,anotherName)

year = "2018" //오류가 남
```
---------------------------
```
//let constantName = initialValue

//변수와 문법적으로 유사하지만 값을 저장한 다음에 변경할 수 없음

let name = "Yoona"

name
name = "steve"//오류가 남

//변수와 상수는 한번 저장한 다음에 특징을 바꿀 수 없음
//(이름과 저장된 값의 형식을 바꿀 수 없음)
//(변수를 선언한 다음 정수를 저장했는데 문자열을 저장하도록 바꾸거나 상수로 바꿀 수는 없음)
//변수나 상수가 있다면 상수를 선언함 - 실수로 값을 변경하는 경우 없음 ,컴파일러가 별도의 최적하해서 코드가 빠름

