
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

</details>

## Control Flow

<details><summary>자세히 보기</summary>

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