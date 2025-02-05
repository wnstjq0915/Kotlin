# 변수
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
```kotlin
var strVar: String? = null
var number: Int? = null
var condition: Boolean? = null
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

