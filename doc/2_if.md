# 조건문 if

**목차**

## 기본사용
- 자바와 같이 사용 가능
```kotlin
val isDarkModeOn = true
if (isDarkModeOn){
  println("다크모드 입니다. $isDarkModeOn")
} else {
  println("다크모드가 아닙니다. $isDarkModeOn")
}
```

## 삼항연산
```kotlin
var isDarkModeOn : Boolean = true
val result : String = if (isDarkModeOn == true) "다크모임" else "라이트모드"
println("현재는 $result 모드입니다.")
```

## when
- 자바의 switch와 유사
- break 사용하지 않음
- finally 대신 else 사용
```kotlin
when(isDarkModeOn){
  true -> println("다크모드 ON")
  false -> println("다크모드 OFF")
}
```
- 아래와 같이 한 줄 이상은 코드블럭 사용
```kotlin
val i: Int = Random.nextInt(10)
when (i) {
  0 -> { }
  1 -> { }
  2 -> { }
  3 -> { }
  4 -> { }
  else -> { }
}
```
