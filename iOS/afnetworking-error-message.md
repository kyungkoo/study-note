#AFNetworking 에서 Error 상황시 Response Body를 확인하는 방법.

AFNetworking 에서 statusCode 가 4xx, 5xx 일 경우, fail block 코드가 동작하게 되는데 paramter 에 responseObject 가 존재하지 않는다.

만일 4xx,5xx body 에 json object는 아래와 같이 확인할 수 있다.

```objective-c
NSError *jsonError = nil;
NSData *data = error.userInfo[AFNetworkingOperationFailingURLResponseDataErrorKey];
//NSData *data = error.userInfo[@"com.alamofire.serialization.response.error.data"];
id responseObject = [NSJSONSerialization JSONObjectWithData:data options:kNilOptions error:&jsonError];
```

`NSDictionary` 의 키 값인 `com.alamofire.serialization.response.error.data` 는`AFURLResponseSerialization.h` 에 `AFNetworkingOperationFailingURLResponseDataErrorKey` 로 정의되어 있다.
