# 변수
**목차**<br>
[1. ](#1-%EB%B3%80%EC%88%98%EC%99%80-%EC%83%81%EC%88%98)변수와 상수<br>
[2. ](#2-%ED%83%80%EC%9E%85)타입<br>
[3. ](#3-lateinit)lateinit<br>
[4. ](#4-%ED%8F%AC%EB%A7%B7%ED%8C%85)포맷팅<br>
***

## 1. 변수와 상수
- var: 변수
- val: 상수

**비교**
- 자바
```java
String strVar = "";       // 변수
final String strVal = ""; // 상수
```

- 코틀린
```kotlin
var strVar = "" // 변수
val strVal = "" // 상수
```

## 2. 타입
- 파이썬과 같이 타입을 타입을 명시하지 않고 사용가능.
```kotlin
var strVar: String = ""
var number: Int = 0
var condition: Boolean = false
```
아래와 같이 생략 가능
```kotlin
var strVar = ""
var number = 0
var condition = false
```

## 3. lateinit
- 초기화하지 않고 선언하기 위해서 lateinit 사용
```kotlin
lateinit var string: String
```
**주의사항**
- 초기화하지 않으면 에러
- 초기화 전에 사용하면 에러
- 상수에는 사용 불가능

**비교**
- lateinit var와 var?의 비교

|선언 방식| Nullable 가능? | 초기화 필요? | 사용 전 체크 필요? |
|:---:|:---:|:---:|:---:|
| lateinit var | 불가능 | 선언만 가능 | isInitialized 체크 가능 |
| var? | 가능 | 초기값 null 필요 | 그냥 사용 가능 |

## 4. 포맷팅
```kotlin
var myPet : String = "고양이"
println("myPet: $myPet")
/* 출력
myPet: 고양이
*/
```
- 띄어쓰기를 하지 않는 경우는 스코프 사용
```kotlin
var myPet : String = "고양이"
println("나는 ${myPet}가 좋아")
/* 출력
나는 고양이가 좋아
*/
```
