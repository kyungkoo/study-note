#Scala 와 Swift 의 변수/상수/함수 선언 비교.

최근에 Scala 와 Swift 를 공부하면서 각각의 변수/상수/함수 선언 방식을 비교.<br />
일반적으로 Scala 의 선언 방식이 좀더 일관성이 있어보인다.

###1. 변수 선언
####1) Scala
```scala
var myValue: Int = 10
val myValue = 10
```
####2) Swift
```swift
var myValue: Int = 10
var myValue = 10
```
<br />
###2. 상수 선언
####1) Scala
```scala
val myConstant: Int = 10
val myConstant = 10
```
####2) Swift
```swift
let myConstant: Int = 10
let myConstant = 10
```
<br />
###3. 함수 선언
####1) Scala
```scala
// 인자값을 가질때
def myFunction1(x: Int): Int = {
  return 1
}

// 인자값이 없을때
def myFunction2(): Int = {
  return 1
}

// 리턴값이 없을때
def myFunction3() = {
  // no return
}
```
####2) Swift
```swift
// 인자값을 가질때
func myFunction1(x: Int) -> Int {
  return 1
}

// 인자값이 없을때
func myFunction2() -> Int {
  return 1
}

// 리턴값이 없을때
func myFunction3() {
  // no return
}
```
