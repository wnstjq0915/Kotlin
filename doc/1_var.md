# 변수
**목차**<br>
[1. ](https://github.com/wnstjq0915/Kotlin/edit/main/doc/1_var.md#1-%EB%B3%80%EC%88%98%EC%99%80-%EC%83%81%EC%88%98)변수와 상수<br>
[2. ](https://github.com/wnstjq0915/Kotlin/edit/main/doc/1_var.md#2-%ED%83%80%EC%9E%85)타입<br>
[3. ](https://github.com/wnstjq0915/Kotlin/edit/main/doc/1_var.md#3-null)null<br>
[4. ](https://github.com/wnstjq0915/Kotlin/edit/main/doc/1_var.md#4-lateinit)lateinit<br>
[5. ](https://github.com/wnstjq0915/Kotlin/edit/main/doc/1_var.md#5-%ED%8F%AC%EB%A7%B7%ED%8C%85)포맷팅<br>

## 1. 변수와 상수
- var: 변수
- val: 상수

### 비교
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

## 3. null
- 타입 뒤에 ?를 붙여서 널값 허용 가능
- 자바는 변수의 기본값이 null 허용인 반면,<br>
코틀린은 반대로 기본값이 null값 비허용

### 비교
- 자바
- 자바는 Annotation을 사용하여 Nullable과 NonNull 구분 가능
```java
@Nullable String strNullable = null;
@NonNull String strNonNull = "";
```
- 코틀린
```kotlin
var strNullable: String? = null
var strNonNull: String = ""
```

### null값 확인
- 변수?.함수 실행 시 자동으로 null 검사
#### 비교
- 자바
```java
if (strNullable != null) {
    strNullable.split("/");
}
```
- 코틀린
```kotlin
strNullable?.split("/")
```
##### 주의사항
- 변수에 null값이 들어가 있을 때 아래와 같이 코드를 작성하면 에러
```kotlin
strNullable.split("/") // NPE
```

## 4. lateinit
- 초기화하지 않고 선언하기 위해서 lateinit 사용
```kotlin
lateinit var string: String
```
### 주의사항
- 초기화하지 않으면 에러
- 초기화 전에 사용하면 에러
- 상수에는 사용 불가능

### 비교
- lateinit var와 var?의 비교

|선언 방식| Nullable 가능? | 초기화 필요? | 사용 전 체크 필요? |
|:---:|:---:|:---:|:---:|
| lateinit var | 불가능 | 선언만 가능 | isInitialized 체크 가능 |
| var? | 가능 | 초기값 null 필요 | 그냥 사용 가능 |

## 5. 포맷팅
```kotlin
var myPet : String = "고양이"
println("myPet: $myPet")
```
```출력
myPet: 고양이
```
