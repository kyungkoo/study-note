# Swift Programming Guide 번역본 변경사항

### Swift Programming Guide

**[Korean](http://swift.leantra.kr/#a-swift-tour)**

**[English](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/index.html)**

###1. Simple Value

####Before
```swift
let emptyArray = String[]()
let emptyDictionary = Dictionary<String, Float>()
```
####After
```swift
let emptyArray = [String]()
let emptyDictionary = [String, Float]()
```
<br />

###2. Control Flow

####Before
```swift
var firstForLoop = 0
for i in 0..3 {
  firstForLoop += i
}
```
####After
```swift
var firstForLoop = 0
for i in 0..<3 {
  firstForLoop += i
}
```
<br />

###3. Functions and Closures

####Before
```swift
func hasAnyMatches(list: Int[], condition: Int -> Bool) -> Bool {
  // same code
}
```
####After
```swift
func hasAnyMatches(list: [Int], condition: Int -> Bool) -> Bool {
  // same code
}
```
