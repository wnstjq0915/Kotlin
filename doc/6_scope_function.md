# 스코프 함수
**목차**
[1. ](#1-%EA%B0%9C%EC%9A%94)개요<br>
[2. ](#2-apply)apply<br>
[3. ](#3-run)run<br>
[4. ](#4-with)with<br>
[5. ](#5-also)also<br>
[6. ](#6-let)let<br>
[7. ](#7-%EC%B0%B8%EA%B3%A0%EB%AC%B8%ED%97%8C)참고문헌<br>
***
## 1. 개요
- 특정 객체의 컨텍스트 내에서 특정 동작(프로퍼티 초기화, 활용 등)<br>
을 실행하기 위한 목적만을 가진 함수이다
- 함수 뒤에 중괄호{}를 사용하여 스코프를 형성하기 때문에 스코프 함수이다

## 2. apply
- 인스턴스를 새로 생성하고 특정 변수에 할당하기 전에<br>
초기화 및 기타동작을 할 수 있도록 한다
- apply 함수 내의 작업이 모두 끝나면 새로 생성된 인스턴스를 반환한다

```kotlin
fun main(){
  var a = Book("해로의 모험", 10000).apply{
    name = "[폭탄세일중] " + name
    discount()
  }
  println("상품명: ${a.name}, 가격: ${a.price}")
}

class Book(var name: String, var price: Int){
  fun discount(){
    price -= 2000
  }
}
/* 출력
상품명: [폭탄세일중] 해로의 모험, 가격: 8000
*/
```

## 3. run
- apply와 유사하나 반환값은 스코프 내 명령 실행 결과값
```kotlin
fun main(){
  var a = Book("해로의 모험", 10000).apply{
    name = "[폭탄세일중] " + name
    discount()
  }

  var bookCost = a.run{
    println("상품명: ${a.name}, 가격: ${a.price}")
    price + 2000
  } // price+2000을 실행한 10000 반환하여
    // bookCost에 대입
    // a.price는 8000원 그대로
    println("원가는 $bookCost 입니다")
}

class Book(var name: String, var price: Int){
  fun discount(){
    price -= 2000
  }
}
/* 출력
상품명: [폭탄세일중] 해로의 모험, 가격: 8000
원가는 10000 입니다
*/
```

## 4. with
- run과 사용이 동일함
**run**
```kotlin
var bookCost = a.run{
  println("상품명: ${a.name}, 가격: ${a.price}")
  price + 2000
}
```
**with**
```kotlin
var bookCost = with(a){
  println("상품명: ${a.name}, 가격: ${a.price}")
  price + 2000
}
```

## 5. also
- apply와 같은 동작을 하나 it을 사용할 수 있음
- 인스턴스 프로퍼티와 이름이 같은 변수가 있을 경우<br>
it을 쓰기 위해 사용
**apply**
```kotlin
var a = Book("해로의 모험", 10000).apply{
  name = "[폭탄세일중] " + name
  price -= 2000
}
```
**also**
```kotlin
var a = Book("해로의 모험", 10000).also{
  name = "[폭탄세일중] " + name
  it -= 2000
}
```

## 6. let
- run과 같은 동작을 하나 it을 사용할 수 있음
- 인스턴스 프로퍼티와 이름이 같은 변수가 있을 경우<br>
it을 쓰기 위해 사용

**run**
```kotlin
var bookCost = a.run{
  println("상품명: ${a.name}, 가격: ${a.price}")
  price + 2000
}
```
**let**
```kotlin
var bookCost = a.let{
  println("상품명: ${a.name}, 가격: ${a.price}")
  it + 2000
}
```
## 7. 참고문헌
- [haero_tstory](https://haero.tistory.com/21)
- [colabear754_tstory](https://colabear754.tistory.com/80)
