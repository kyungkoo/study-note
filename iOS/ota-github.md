#Github 를 이용한 OTA 배포.

iOS 앱의 바이너리 파일인 `*.ipa` 은 Android 의 `*.apk` 처럼 단말에 저장 하여 설치가 불가능 합니다.

이를 설치하기 위해서는 `Xocde` 를 이용하거나, `Windows` 환경에서는 별도의 설치 프로그램을 사용해야 합니다.

이러한 불편을 해결하고자, Apple 에서는 `OTA(Over The Air)` 방식의 앱 배포 방법을 제공 하고 있습니다.

OTA 방식으로 앱을 배포하기 위해서는 아래 파일이 필요합니다.

-	배포하고자 하는 `*.ipa`.(adhoc version)
-	`*.ipa` 설치를 유도 할 `*.plist`.
-	설치를 위한 안내 웹 페이지.(`*.html`\)

OTA 방식을 사용하게 되면, 설치를 위한 안내 페이지나, `*.ipa` 파일은 `http` 로 접근이 가능하지만,

`*.plist` 는 반드시 `https` 방식으로 그것도 **공인으로 등록 된 인증서** 만 접근이 가능합니다.

이러한 문제를 해결하고자 OTA 방식을 사용할 때, `https` 접근이 가능한 `Dropbox` 를 많이 이용하고 있습니다.

[Dropbox를 이용한 AdHoc 배포](http://blog.hibrainapps.net/168) 방식은 매우 유용하지만, 다음과 같은 불편함 이 있습니다.

-	업로드 한 파일 공유 시, `www.dropbox.com` 을 `dl.dropboxusercontent.com` 로 변경 해야 합니다.
-	`*.ipa` 를 `Dropbox` 에 업로드 시, 다운로드가 비교적 느린 편 입니다.
-	바이너리 버전 관리가 어렵습니다.

다운로드가 느린 문제는 실제 설치 파일을 다른 서버에 두면 해결이 가능하지만, `URL` 을 변경하거나, 바이너리 버전 관리 문제는

초기 세팅시 불편한 부분이 많습니다.

[Github](https://github.com) 은 [Github Page](https://pages.github.com) 를 통해 `Blog` 형태의 webpage 를 제공하고 있고,`Tag` 를 이용한 버전 관리가 용이하며, `https` 도 제공하고 있습니다.

####1. Github Page

[Github Page](https://pages.github.com/) 사이트를 통해 만들 수 있습니다.

####2. plist Make

`xcode6` 부터는 `archive` -> `export` 시, `*.plist` 파일을 추가로 생성해 주지 않습니다.

[OTA Plist Maker](http://ota-plist-maker.appspot.com) 에서는 간단한 정보 입력을 통해 `*.plist` 를 생성 해 줍니다.

| [OTA Plist Maker](http://ota-plist-maker.appspot.com)                                                                |
|----------------------------------------------------------------------------------------------------------------------|
| ![OTA Plist Maker Site](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/ota-plist-maker.jpg) |

####3. OTA Link

OTA Link 를 위해서는 `<a href="">` 의 `[github plist raw url]` 에 github 에 업로드 한 plist 의 raw 주소를 입려 합니다.

```html
<a href="itms-services://?action=download-manifest&url=[github plist raw url]">Download</a>
```

####4. Access WebPage

`http://<github-name>.github.io` 에 접속하거나 혹은 상세 url 로 접속하여 download page 에 접속 합니다.

| OTA Sample Page                                                                                          |
|----------------------------------------------------------------------------------------------------------|
| ![Github OTA Page](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/ota-page.jpg) |

그리고 링크를 선택하면 아래와 같이 ipa 파일을 단말에 설칠 할 수 있습니다.

| Install Popup                                                                                           |
|---------------------------------------------------------------------------------------------------------|
| ![OTA Install](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/ota-install.jpg) |

#P.S.

OTA 는 물론, Issue Tracking 까지 해주는 서비스도 있습니다.

-	[Fabric](https://fabric.io)
-	[Parse](https://parse.com)
-	[TestFlight](https://www.testflightapp.com)

위 와 같은 서비스를 사용하면 훨씬 더 편리하게 배포가 가능합니다.
