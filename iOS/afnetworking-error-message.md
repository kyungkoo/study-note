#AFNetworking 에서 Error 상황시 Response Body를 확인하는 방법.

AFNetworking 에서 statusCode 가 4xx, 5xx 일 경우, block 안에 responseObject parameter 가 존재하지 않는다.

따라서 4xx,5xx Error 시, response body data 를 확인하기 위해서는 `NSError` 의 `UserInfo` 값을 체크해야 한다.

예를들어, Error Response 시, json object는 아래와 같이 확인할 수 있다.

```objective-c
NSError *jsonError = nil;
NSData *data = error.userInfo[AFNetworkingOperationFailingURLResponseDataErrorKey];
//NSData *data = error.userInfo[@"com.alamofire.serialization.response.error.data"];
id responseObject = [NSJSONSerialization JSONObjectWithData:data options:kNilOptions error:&jsonError];
```

`NSDictionary` 의 키 값인 `com.alamofire.serialization.response.error.data` 는`AFURLResponseSerialization.h` 에 `AFNetworkingOperationFailingURLResponseDataErrorKey` 로 정의되어 있다.
