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

두개의 `Int`형 매개변수와 반환값이 `Int`형 인 함수:
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

모듈 밖으로 노출되는 함수는 반환형을 명시적으로 선언해야 합니다:

```Kotlin
public fun sum(a: Int, b: Int): Int = a + b
```
Function returning no meaningful value:

의미없는 값을 반환하는 함수:

```Kotlin
fun printSum(a: Int, b: Int): Unit {
  print(a + b)
}
```
`Unit` return type can be omitted:

`Unit` 형은 생략할 수 있습니다.

```Kotlin
public fun printSum(a: Int, b: Int) {
  print(a + b)
}
```
