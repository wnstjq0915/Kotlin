# 함수
**목차**<br>
[1. }()선언<br>
[2. }()가변인자<br>
[3. }()인라인 함수<br>
[1. }()선언<br>

***

## 1. 선언
- fun 함수명(매개변수) : returnType { 로직 }
```kotlin
fun add(num1: Int, num2: Int) : Int {
    return num1 + num2
}
```
- 변수와 마찬가지로 매개변수나 리턴타입에 ?를 이용하여 null 허용 가능
- 아래와 같이도 선언 가능
```kotlin
fun sum(a:Int, b:Int) = a + b
```

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

## 인라인 함수
- 반복문 같은 곳에서 함수를 자주 호출하게 되면  
호출하는 리소스로 인해 느려지게 됨
- 위와 같은 단점을 보완하는 함수
- 인라인 함수가 호출된 곳에 함수의 내용을 붙여넣은 뒤에 컴파일 진행
- 단점은 그만큼 프로그램의 용량이 늘어남
```kotlin
inline fun sum(a:Int, b:Int) = a + b
```

## 익명함수부터

## 참고문헌
[블로그](https://pang2h.tistory.com/315)<br>
