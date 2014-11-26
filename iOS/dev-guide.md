# iOS Project 개발 가이드.

## 1. 목적
iOS App 개발 시, 프로젝트 생성, 배포, 테스트 등에 도움이 될 만한 팁을 제공하기 위함.

## 2. xcproj
xcode 의 Project File, 프로젝트의 각종 설정 및 파일 링크 정보를 가지고 있다.<br />
프로젝트에 새로운 .h, .m 파일을 추가할 경우, SVN 에 .xcproj 도 같이 commit 해야 한다.

## 3. App Destribution
검증용 앱 배포 시, AdHoc 인증서로 빌드 후, 검증 부서에 전달 해 주어야 한다.  
그러나 검증부서에서 해당 앱을 설치하기 어려운 점이 있기 때문에 다음과 같은 방법을 사용할 수 있다.

### 1) [TestFlight](https://www.testflightapp.com)
Apple 에서 제공하는 베타 서비스.
테스트 할 이메일을 지정하여 특정 사용자에게 앱을 설치하도록 할수 있다.

### 2) [Fabric](https://www.testflightapp.com)
Twitter 에서 제공하는 서비스.  
Crashlytics, Beta, Answer, Twitter, MoPob 서비스를 제공.  
Crashlytics, Beta 서비스를 이용하면 앱 배포 및 크래쉬 리포팅을 받기 편리.

## 4. [Cocoapods](http://cocoapods.org/)
iOS, OSX Library Dependency Manager.
java 의 Maven,Gradle 과 유사한 역할을 함.

### 1) [AFNetworking](http://afnetworking.com)
HTTP/HTTPS/Multipart/Networking 기반의 ImageLoading 을 지원하는 라이브러리.<br />
RESTful 을 지원하며 Networking 모듈을 별도로 구현하는 수고를 덜 수 있음. <br />
Block, ARC 기술을 지원.<br />
Android 의 [Volley](http://developer.android.com/training/volley/index.html) 나 [Square](http://square.github.io) 사의  [Okhttp](http://square.github.io/okhttp/),[Retrofit](http://square.github.io/retrofit/),[Picasso](http://square.github.io/picasso/) 와 유사한 기능을 제공.

### 2) [FMDB](https://github.com/ccgus/fmdb)
Objective-C 에서 제공하는 CoreData SQLite 의 Wrapper Library.<br />
기본적으로 제공하는 SQLite 보다 사용하기 편하고, Block, ARC 지원.

## 5. Utilities
### 1) [iExplore](http://www.macroplant.com/iexplorer/)
단말 탐색기 기능.
앱에 저장된 db 파일이나 기타 raw 파일을 가져올 수 있음.

### 2) [SQLite Professional](https://itunes.apple.com/kr/app/sqlite-professional-read-only/id635299994?mt=12)
단말에 저장된 SQLite db 를 열 수 있음.
App Store 에서 무료 다운로드 가능.

### 3) [Parse](https://www.parse.com)
서버 구현없이 iOS 의 Push Notification 서비스 가능.

### 4) [Resizer](https://itunes.apple.com/kr/app/resizer/id411277085?mt=12)
@2x 사이즈의 이미지를 @1x 이미지로 변경해 주는 유틸.
