#Scala / Swift / Python 의 Tuple

###1. 사용법

####1) Scala

```scala
// tuple 선언
val response = (200, "OK")
// response: (Int, String) = (200,OK)
// access
val statusCode = response._1 // 200
val statusMsg = response._2 // "OK"
```

<br />

####2) Swift

```swift
// tuple 선언
let response = (200, "OK")
// access
let statusCode = response.0
let statusMsg = response.1

// tuple 원소에 naming 이 가능
let response = (statusCode: 200, statusMsg: "OK")
let statusCode = response.statusCode
let statusMsg = response.statusMsg
```

<br />

####3) Python

```python
response = (200, "OK")
statusCode = response[0]
statusMsg = response[1]
# 아래 방법을 더 선호한다.
statusCode, statusMsg = response
```
