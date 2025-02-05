# 함수
## 1. 선언
- fun 함수명(매개변수) : returnType { 로직 }
```kotlin
fun add(num1: Int, num2: Int) : Int {
    return num1 + num2
}
```
- 변수와 마찬가지로 매개변수나 리턴타입에 ?를 이용하여 null 허용 가능

## 가변인자
- Java와 똑같이 배열 형태로 사용
```kotlin
fun sum(vararg arrNum: Int) : Int {
    var sum = 0
    for (num in arrNum) {
        sum += num
    }
    return sum
}
```
