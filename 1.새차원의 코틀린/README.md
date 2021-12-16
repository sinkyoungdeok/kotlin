
# 출처 
- url: https://www.inflearn.com/course/%EC%BD%94%ED%8B%80%EB%A6%B0-%EA%B0%95%EC%A2%8C-%EC%83%88%EC%B0%A8%EC%9B%90/dashboard
- 강사님: 새차원

## Install

<details><summary>자세히 보기</summary>

### 코틀린 설치 (Mac OS)
- brew install adoptopenjdk8
- brew install kotlin

</details>

## Basic Syntax

<details><summary>자세히 보기</summary>

### 패키지 정의
- 패키지 정의는 파일 최상단에 위치
- 디렉터리와 패키지를 일치시키지 않아도 됨 
```kotlin
package my.demo

import java.util.*

//..
```

### 함수 정의
- 함수는 fun 키워드로 정의
```kotlin
fun sum(a: Int, b: Int): Int {
    return a+b
}
```

- 함수 몸체가 식(Expression)인 경우 return 생략 가능
- 이런 경우 return type이 추론됨
```kotlin
fun sum(a: Int, b: Int) = a+b
```

- 리턴 할 값이 없는 경우 Unit(Object)으로 리턴 함 
- Unit는 Java에서 void 리턴 역할
```kotlin
fun printKotlin(): Unit {
    println("hello Kotlin")
}
``` 
- Unit은 생략 가능
```kotlin
fun printKotlin() {
    println("hello Kotlin")
}
```

### 지역 변수 정의 
- val: 읽기 전용 변수
- 값의 할당이 1회만 가능, Java의 final과 유사
```kotlin
val a: Int = 1 // 즉시 할당
val b = 2 // `int` type 추론
val c: Int // 컴파일 오류, 초기화가 필요함
c = 3 // 컴파일 오류, 읽기 전용
```

- var: Mutable 변수
```kotlin
var x = 5
x += 1 
```

### 주석
- Java와 Javascript와 동일함
- //: 한 줄 주석
- /* */.: 여러 줄 주석 (block comment)
- block comment가 Java와 다르게 중첩 허용됨 
```kotlin
// 한줄 주석
/* 여러 줄 
주석 */
 
/* block comment가 
    /* 중첩도 가능 */
 */
```

### 문자열 템플릿
- String Interpolation (문자열 보간법) 
```kotlin
var a = 1
// simple name in template:
val s1 = "a is $a"

a = 2
// arbitrary expression in template:
val s2 = "${s1.replace("is", "was")}, but now is $a"
```

### 조건문 
```kotlin
fun maxOf(a: Int, b: Int): Int {
    if (a>b) {
        return a
    } else {
        return b
    }
}
```
- 조건식으로 사용가능
```kotlin
fun maxOf(a: Int, b: Int) = if(a>b) a else b
```

### nullable
- 값이 null일 수 있는 경우 타입에 nullable 마크를 명시 해야 함 
```kotlin
fun parseInt(str: String): Int? {
    //정수가 아닌 경우 null을 리턴
}
```
- nullable 타입의 변수를 접근 할 때는 반드시 null 체크를 해야 함
- 그렇지 않으면 컴파일 오류가 발생 됨
```kotlin
fun printProduct(arg1: String, arg2: String) {
    val x: Int? = parseInt(arg1)
    val y: Int? = parseInt(arg2)
    
    if ( x != null && y != null) {
        println(x * y)
    } else {
        println("either '$arg1' or '$arg2' is not a number")
    }
}
```

### 자동 타입 변환
- 타입 체크만 해도 자동으로 타입 변환이 됨
```kotlin
fun getStringLength(obj: Any): Int? {
    if (obj is String) {
        return obj.length
    }
    
    return null
}
```

### while loop
```kotlin
val items = listOf("apple", "banana", "kiwi")
var index = 0
while (index < items.size) {
    println("item at $index is ${items[index]}")
    index++
}
```

### when expression
```kotlin
fun describe(obj: Any): String = 
    when (obj) {
        1 -> "One"
        "Hello" -> "Greeting"
        is Long -> "Long"
        !is String -> "Not a String"
        else -> "Unknown"
    }
```

### ranges
- In 연산자를 이용해서 숫자 범위를 체크 가능
```kotlin
val x = 3
if (x in 1..10) {
    println("fits in range")
}
```
- range를 이용한 for loop
```kotlin
for (x in 1..5) {
    print(x)
}
```

### collections
- 컬렉션도 in으로 loop 가능
```kotlin
val items = listOf("apple", "banana", "kiwi")
for (item in items) {
    println(item)
}
```
- in으로 해당 값이 collection에 포함되는지 체크 가능
```kotlin
val items = setOf("apple", "banana", "kiwi")
when {
    "orance" in items -> println("juicy")
    "apple" in items -> println("apple is fine too")
}
```

- 람다식을 이용해서 컬렉션에 filter, map 등의 연산 가능
```kotlin
val fruits = listOf("banana", "avocade", "apple", "kiwi")
fruits
    .filter{ it.startsWith("a")}
    .sortedBy{ it }
    .map {it.toUpperCase() }
    .forEach { println(it) }
```


</details>

## Basic Types

<details><summary>자세히 보기</summary>

### 기본 타입 
- 코틀린에서 모든 것은 객체임
- 모든 것에 멤버 함수나 프로퍼티를 호출 가능하다는 의미이다. 

### 숫자 (Numbers)
- Java의 숫자형과 거의 비슷하게 처리
- Kotlin에서 Number는 클래스임, java의 primitive type에 직접 접근 할 수 없음
- Java에서 숫자형이던 char가 kotlin에서는 숫자 형이 아님 

### 리터럴 (Literal)
- 10진수: 123 (Int, Short)
- Long: 123L
- Double: 123.5, 123.5e10
- Float: 123.5f
- 2진수: 0b00001011
- 8진수: 미지원 ( Java: int I = 017; )
- 16진수: 0x0F

### Underscores in numeric literal (since 1.1)
```kotlin
val oneMilion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val socialSecurityNumber = 999_99_9999L
val hexBytes = 0xFF_EC_DE_5E
val bytes = 0b11010010_01101001_10010100_10010010
```

### Representation
- Java 플랫폼에서 숫자형은 JVM primitive type으로 저장됨
- Nullable이나 제네릭의 경우에는 박싱됨
- 박싱된 경우 identity를 유지 하지 않음
```kotlin
// JVM primitive
val a: Int = 100
print(a === a) // Prints 'true'

// Boxed
val boxedA: Int? = a
val anotherBoxedA: Int? = a
println("==: ${boxedA == anotherBoxedA}") // Prints 'true'
println("===: ${boxedA === anotherBoxedA}") // Prints 'true'
```

### Explicit Conversions
- 작은 타입은 큰 타입의 하위 타입이 아님, 즉 작은 타입에서 큰 타입으로의 대입이 안됨 
```kotlin
val a: Int = 1 // A boxed Int
// val b: Long = a // 오류 
val b: Long = a.toLong()
// println(a == b) // 오류
```

- 명시적으로 변환을 해주어야 함 
```kotlin
val i: Int = b.toInt() // OK 
```
```
toByte(): Byte
toShort(): Short
toInt(): Int
toLong(): Long
toFloat(): Float
toDouble(): Double
toChar(): Char
```

### 문자 (Characters)
- Char는 숫자로 취급 되지 않음
```kotlin
fun check(c: Char) {
    if ( c == 1) { /* ... */ } // ERROR
}

fun check(c: Char) {
    if (c == 'a') { /* ... */ } // OK
}

print('0'.toInt()) // print 48
```

### 배열 
- 배열은 Array 클래스로 표현됨
- get, set ([] 연산자 오버로딩됨)
- size 등 유용한 멤버 함수 포함 
```kotlin
var array: Array<String> = arrayOf("코틀린", "강좌")
println(array.get(0))
println(array[0])
println(array.size)
``` 

### 배열 생성 
- Array의 팩토리 함수를 이용
- arrayOf() 등의 라이브러리 함수 이용 
```kotlin
val b = Array(5, {i -> i.toString() })

val a = arrayOf("0", "1", "2", "3", "4")
```

### 특별한 Array 클래스 
- Primitive 타입의 박싱 오버헤드를 없애기 위한 배열
- IntArray, ShortArray, IntArray
- Array를 상속한 클래스들은 아니지만, Array와 같은 메소드와 프로퍼티를 가짐
- size등 유용한 맴버 함수 포함 
```kotlin
val x: IntArray = intArrayOf(1, 2, 3)
x[0] = 7
println(x.get(0))
println(x[0])
println(x.size)
```

### 문자열
- 문자열은 String 클래스로 표현
- String은 characters로 구성됨
- s[i] 와 같은 방식으로 접근 가능 (immutable이므로 변경 불가)
```kotlin
var x: String = "Kotlin"
println(x.get(0))
println(x[0])
println(x.length)

for (c in x) {
    println(c)
}
```

### 문자열 리터럴
- escaped string ("Kotlin")
  - 전통적인 방식으로 Java String과 거의 비슷
  - Backslash를 사용하여 escaping 처리
- raw string ("""Kotlin"")
  - escaping 처리 필요 없음
  - 개행 이나 어떠한 문자 포함 가능
```kotlin
val s = "Hello, world!\n"

val s = """
"'이것은 코틀린의
 raw String
입니다.'"
"""
```

</details>

## Control Flow

<details><summary>자세히 보기</summary>

### if else 문
- Java와 거의 유사함
```kotlin
//Traditional usage
var max = a
if (a < b) max = b
```
```kotlin
var max: Int
if (a > b) {
    max = a
} else {
    max = b
}
```

- If문이 식으로 사용되는 경우 값을 반환함
- If식의 경우 반드시 else를 동반해야 함
```kotlin
val max = if (a > b) a else b 
```

- If식의 branches들이 블록을 가질 수 있음 {...}
- 블록의 마지막 구문이 반환 값이 됨 
```kotlin
val max = if (a>b) {
    print("Choose a")
    a
} else {
    print("Choose b")
    b
}
```

- 삼항연산자(ternary)가 없음
  - If문이 삼항연산자 역할을 잘 해내기 때문에 

### when
- when 문은 C 계열 언어의 switch문을 대체함
- when 문은 각각의 branches의 조건문이 만족 할 때 까지 위에서 부터 순차적으로 인자를 비교함 
```kotlin
when (x) {
  1 -> print("x == 1")
  2 -> print("x == 2")
  else -> { // Note the block
      print("x is neither 1 nor 2")
  }
}
``` 
- when문이 식으로 사용된 경우에는 조건을 만족하는 branch의 값이 전체 식의 결과 값이 됨
- else의 경우 다른 branch들의 조건이 만족되지 않을 때 수행 됨
- when이 식으로 사용된 경우 else문이 필수임
- when이 식으로 사용된 경우 컴파일러가 else문이 없어도 된다는 것을 입증할 수 있는 경우에는 else를 생략가능
```kotlin
var res = when (x) {
  100 -> "A"
  90 -> "B"
  80 -> "C"
  else -> "F"
}
```
```kotlin
var res = when (x) { // boolean인 경우 true or false이므로 else가 없어도 됨 
  true -> "맞다"
  false -> "틀리다"
}
```
- 여러 조건들이 같은 방식으로 처리될 수 있는 경우, branch의 조건문에 콤마를 (,) 사용하여 표기하면 됨
```kotlin
when (x) {
  0,1 -> print("x==0 or x==1")
  else -> print("otherwise")
}
```
- Branch의 조건문에 함수나 식을 사용할 수 있음 
```kotlin
when (x) {
  parseInt(x) -> print("s encodes x")
  1 + 3 -> print("4")
  else -> print("s does not encode x")
}
```

- range나 collection에 in이나 !in으로 범위 등을 검사 할 수 있음 
```kotlin
val validNumbers = listOf(3,6,9)
when (x) {
  in validNumbers -> print("x is valid")
  in 1..10 -> print("x is in the range")
  !in 10..20 -> print("x is outside the range")
  else -> print("none of the above")
}
```

- is나 !is를 이용하여 타입도 검사 할 수 있음
  - 이 때 스마트 캐스트가 적용됨
```kotlin
fun hasPrefix(x: Any) = when(x) {
  is String -> x.startsWith("prefix")
  else -> false
}
```

- when은 if-else if 체인을 대체할 수 있음
- when에 인자를 입력하지 않으면, 논리연산 으로 처리됨 
```kotlin
when {
  x.isOdd() -> print("x is odd")
  x.isEven() -> print("x is even")
  else -> print("x is funny")
}
```


### For Loops
- for문은 iterator을 제공하는 모든 것을 반복할 수 있음
```kotlin
for (item in collection)
    print(item)
```

- for문의 Body가 블록이 올 수도 있음
```kotlin
for (item in collection) {
  print(item.id)
  print(item.name)
}
```

- For문을 지원하는 iterator의 조건
  - 멤버함수나 확장 함수 중에
    - iterator()를 반환 하는 것이 있는 경우
    - next()를 가지는 경우
    - hasNext(): Bollean를 가지는 경우
    - 함수는 위의 3개를 operator로 표기 되어야 For문을 지원한다. 
```kotlin
val myData = MyData()
for (item in myData) {
    print(item)
}
```
```kotlin
class MyData {
    operator fun iterator(): MyIterator {
        return MyIterator()
    }
}
```
```kotlin
class MyIterator {
  val data = listOf(1,2,3,4,5)
  val idx = 0
  operator fun hasNext(): Boolean {
      return data.size > idx
  }
  
  operator fun next(): Int {
      return data[idx++]
  }
}
```

- 배열이나 리스트를 반복할 때, index를 이용하고 싶다면 indices를 이용하면 됨
```kotlin
val array = arrayOf("가","나","다")
for (i in array.indices) {
    println("$i: ${array[i]}")
}
```
- Index를 이용하고 싶을 때, withIndex()를 이용할 수도 있음
```kotlin
val array = arrayOf("가","나","다")
for ((index, value) in array.withIndex()) {
    println("$index: ${value}")
}
```

### While Loops
- while, do-while문은 java와 거의 같음
- do-while문에서 body의 지역변수를 do-while문의 조건문이 참조 할 수 있음
```kotlin
while (x>) {
    x--
}
```
```kotlin
do {
    val y = retrieveData()
} while ( y != null) // y is visible here!
```




</details>

## Packages, Return and Jumps

<details><summary>자세히 보기</summary>

</details>

## Class

<details><summary>자세히 보기</summary>

</details>

## Inheritance

<details><summary>자세히 보기</summary>

</details>

## Properties and Fields

<details><summary>자세히 보기</summary>

</details>

## Data, Nested classes

<details><summary>자세히 보기</summary>

</details>

## Object Expressions and Declarations

<details><summary>자세히 보기</summary>

</details>