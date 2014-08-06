## `NSString *const` 와 `const NSString *` 의 차이.

### Issue : 상수값을 선언한 NSString 을 인자값으로 넘기려고 할 때 아래와 같은 warning이 발생했다.

![Sending 'const NSString *__strong' to parameter of type 'NSString *' discards qualifiers](https://raw.githubusercontent.com/kyungkoo/study-note/master/objc/images/const-pointer-warning.png)

### 선언한 상수 형태
```objective-c
const NSString *ConstantValue = @"ConstantValeu";
```

### Solution : `const` 위치를 변경한다.

### 아래와 같이 상수 선언 상태를 변경시키면 warning 을 없앨 수 있다.
```objective-c
NSString *const ConstantValue = @"ConstantValue";
```

### Why?
`const` 를 사용한 목적은 상수값으로 정의해 주고 싶기 때문이다.
`NSString` 같이 pointer 가 변경되지 않도록 하려면, 즉, 상수 포인터를 생성하기 위해서는 `*` 뒤에 `const`를 적용 해 주어야 한다.
`const NSString *` 과 같이 적용했을 경우, 해당 객체의 포인터 가 변경 가능하다.

```objective-c
NSString *const ConstantValue = @"ConstantValue";
ConstantValue = @"AnotherValue";
```
위 경우 아래처럼 변경 불가능 하다는 error 가 발생한다.

![Read-only variable is not assignable](https://raw.githubusercontent.com/kyungkoo/study-note/master/objc/images/const-pointer-error.png)
