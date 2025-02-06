# null
**목차**<br>
[1. ](#1-%EA%B0%9C%EC%9A%94)개요<br>
[2. ](#2-safe-call-operator-)Safe call operator ?.<br>
[3. ](#3-elvis-operator-)Elvis operator ?:<br>
[4. ](#4-not-null-assertion-operator-)Not-null assertion operator !!<br>
[5. ](#5-let-%ED%95%A8%EC%88%98)let 함수<br>
[6. ](#6-%EC%B0%B8%EA%B3%A0%EB%AC%B8%ED%97%8C)참고문헌<br>

***

## 1. 개요
- 타입 뒤에 ?를 붙여서 널값 허용 가능
- 자바는 변수의 기본값이 null 허용인 반면,<br>
코틀린은 반대로 기본값이 null값 비허용

**비교**
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

## 2. Safe call operator ?.
- 변수?.함수 실행 시 자동으로 null 검사
**비교**
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

**다른 예시**
```kotlin
val a: String? = "Kotlin"
val b: String? = null

println(a?.length) // 6
println(b?.length) // null
```

### 주의사항
- 아래와 같이 변수에 null값이 들어가 있을 때 코드를 작성하면 에러
```kotlin
var strNullable : String? = null
strNullable.split("/") // NPE
```

## 3. Elvis operator ?:
- null값인지 확인하고 값을 대입하는 삼항연산을 간편화
- ?: 앞에 오는 값이 null일 경우 뒤쪽 코드 실행 및 반환

**기존**
```kotlin
val b: String? = null
val l: Int = if (b != null) b.length else 0
println(l) // 0
```
**?: 사용**
```kotlin
val b: String? = null
val l = b?.length ?: 0
println(l) // 0
```

**다른 예시**
```kotlin
fun foo(node: Node): String? {
    val parent = node.getParent() ?: return null
    // node.getParent() 값이 null이면 foo 함수 null로 반환
    // null이 아닐 경우 parent에 대입
    val name = node.getName() ?: throw IllegalArgumentException("name expected")
    // node.getName()이 null일 경우 에러 유발시킴
}
```

## 4. Not-null assertion operator !!
- 명시적 NonNull 선언
- !!를 이용하여 Nullable 값이 null이 아님을 명시적으로 표현
- 만약 null값이 들어갈 경우 에러
```kotlin
val b: String? = null
val l = b!!.length // 에러 발생
// Exception in thread "main" java.lang.NullPointerException
println(l)
```
- 참고로 위에서 l을 var, val 상관없이 String? 타입으로 선언하더라도 에러

## 5. let 함수
- null값이 아닐 경우 뒤의 코드블럭을 실행
```kotlin
var item : String? = "test"
item?.let { println(it) } // it을 통하여 item의 값인 "test" 출력
// 만약 item이 null일 경우 코드블록 실행X
```

## 6. 참고문헌
[코틀린 공식문서](https://kotlinlang.org/docs/null-safety.html)
