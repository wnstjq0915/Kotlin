# 함수
**목차**<br>
[1. ]()선언<br>
[2. ]()가변인자<br>
[3. ]()인라인 함수<br>
[1. ]()선언<br>

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

### Unit과 Nothing
**Unit**
- Unit: 흔히 함수의 반환 구문이 없다는 것을 표현하기 위해 사용<br>
자바의 void와 유사하나 Unit은 void와 다르게 클래스로 존재
- 아래의 코드에서 위와 아래의 함수가 같음<br>
(반환값이 없음)
```kotlin
fun myFun1() { }
fun myFun2(): Unit { }
```
**Nothing**
- Nothing: 의미 있는 데이터가 없다는 것을 명시적으로 선언하기 위해 사용하는 타입
1. 종료되지 않는 함수
2. 예외를 던지는 함수
3. null을 리턴하는 함수(반환타입 Nothing?)
- **Nothing은 모든 클래스의 자식클래스**
```kotlin
val nullableValue: String? = null
val value = nullableString ?: throw IllegalStateException()
```
- 위 코드에서 nullableValue가 null값을 가질 때<br>
변수에 Nothing을 대입하게 되는데<br>
이때 Nothing은 String의 자식클래스이므로 에러X

#### 차이점
- Unit: '아무런 값도 리턴을 하지 않는다'의 의미<br>
즉 리턴의 대상이 없을 뿐이지 리턴이라는 행위 자체를 하지 않는다는 의미는 아님

- Nothing은 리턴이라는 행위 자체를 하지 않음을 의미

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

## 익명함수
- 이름만 없는 구조의 함수
- 람다식 문법의 제약을 무시하고 사용하기 위해
```kotlin
val testFunc:(Int, Int) -> Int = fun(a, b) = a + b
}
```
- 매개변수와 반환값의 타입을 기재할 시에<br>
아래와 같이 변수타입을 지정하지 않아도 됨.
```kotlin
val testFunc = fun(a:Int,b:Int):Int{
    return a + b
}
```

## 고차함수
### 반환값으로 사용
- 반환값에서 함수를 호출하여 반환하는 형식
```kotlin
fun TestFunc(): Int{
    return sum(2, 4)
}

fun sum(a:Int, b:Int) = a + b
```

### 인자에 사용
```kotlin
fun TestFunc(vabs:(Int)->Int, value:Int){
    /*
        vabs: 함수이름
        (Int): 함수의 매개변수타입
        ->Int: 함수의 반환타입

        value: 매개변수
    */
    println("vabs(${value}) = ${vabs(value)}")
}

fun main(args:Array<String>){
    TestFunc(::abs, -4)
    // :: -> 함수 참조를 위해
}
- :: -> 함수 참조 기호<br>
TestFunc가 시작된 뒤에 함수가 실행될 수 있도록 사용<br>
소괄호를 넣게 되면 TestFunc가 실행되기 전에 abs 함수가 실행됨


fun abs(v:Int): Int = if(0 < v) v else -v
```

## 람다식
**기본구조**
```kotlin
{v1, v2 -> expression}
```
**매개변수와 반환타입**
```kotlin
() -> Int     // 매개변수는 없으나 반환값이 Int 타입인 람다식의 자료형
(Int) -> Int  // Int 타입의 매개변수가 하나 있고 반환값이 Int 타입인 람다식의 자료형
(Int) -> Unit // Int 타입의 매개변수가 하나 있고 반환값은 없는 람다식의 자료형
() -> Unit    // 매개변수도 반환할 값도 존재하지 않는 람다식의 자료형
```
**사용예시**
```kotlin
fun TestLambda(test:(Int, Int) -> Int){
    // 람다식 함수를 인자로 받아 그대로 이용
    println("3 + 5 = ${test(3, 5)}") // 3 + 5 = 8 출력
}

fun main(args:Array<String>){
    TestLambda({a, b -> a + b}) // 람다식 함수 자체를 넘김
}
```
- 변수에도 람다식 할당 가능
```kotlin
val plus:(Int, Int) -> Int = {a, b -> a + b}
```
```kotlin
// plus 사용
fun TestLambda(lambda:(Int, Int) -> Int){
    println("3 + 5 = ${lambda(3, 5)}")
}

fun main(args:Array<String>){
    val plus:(Int, Int) -> Int = {a, b -> a + b}
    TestLambda(plus)
}
```
**다른 변수에 재할당**
```kotlin
val printHelloA:()->Unit = {println("Hello world!")}
val printHelloB:()->Unit = printHelloA
// val printHelloB = printHelloA
// printHelloB 변수는 printHelloA의 타입을 추론하기 때문에 굳이 자료형을 작성하지 않아도 됩니다.
printHelloA()
printHelloB()
/* 출력
Hello world!
Hello world!
*/
```

**인자를 하나만 활용**
```kotlin
fun ignoreFunc(func:(String, String)->String){
    println(func("Hello", "World!"))
}

fun main(args:Array<String>){
    ignoreFunc({_, b->"${b}"})
}
```

## 참고문헌
[블로그](https://pang2h.tistory.com/315)<br>
