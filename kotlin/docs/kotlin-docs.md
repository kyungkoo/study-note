#Getting Started
####Basic Syntax
#####Defining packages
패키지 명세는 소스 파일의 맨 처음에 명시 되어야 합니다.
```Kotlin
package my.demo

import java.util.*

// ...
```
디렉토리 와 패키지를 일치 할 필요는 없습니다. 소스파일은 파일 시스템 내 어디든 위치할 수 있습니다.

#####Defining functions
Function having two `Int` parameters with `Int` return type:
두개의 `Int`형 매개변수와 반환형이 `Int`를 가진 함수:
```Kotlin
fun sum(a: Int, b: Int): Int {
  return a + b
}
```
Function with an expression body and inferred return type:
구현 몸체와 추론타입을 가진 함수:
```Kotlin
fun sum(a: Int, b: Int) = a + b
```
Function visible from outside of a module should have return type explicitly
specified:
```Kotlin
public fun sum(a: Int, b: Int): Int = a + b
```
Function returning no meaningful value:
```Kotlin
fun printSum(a: Int, b: Int): Unit {
  print(a + b)
}
```
`Unit` return type can be omitted:
```Kotlin
public fun printSum(a: Int, b: Int) {
  print(a + b)
}
```
