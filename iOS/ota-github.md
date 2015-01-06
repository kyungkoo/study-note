#Github 를 이용한 OTA 배포.

iOS 는 OTA 방식을 이용하여 ipa 설치를 유도 할 수 있습니다.

이를 위해서는 application plist 파일, ipa 파일 그리고 설치를 위한 html 페이지가 필요합니다.

또한, `plist` 는 반드시 `https` 를 통해 전달 되어야 합니다.

Dropbox 를 통해서도 OTA 를 구현할 수 있으나 아래와 같이 불편한 점이 있습니다.

-	파일 공유 시, `https://www.dropbox.com` 를 `https://dl.dropboxusercontent.com` 으로 변경 해 주어야 함.

-	Dropbox 로 공유 시, 다운로드가 전체적으로 느림.

Github 에서는 raw 파일을 https 를 통해 접근이 가능하고, github blog 를 사용하여

간단하게 페이지를 관리할 수 있으며, 버전 관리도 가능한 장점이 있어, Github 를 통한,

OTA 배포가 사용하기 좀 더 용이 하다 생각 됩니다.

-	Github Page 만들기 : [Github Page](https://pages.github.com/) 사이트를 통해 만들 수 있습니다.
-	plist 만들기 : xcode6 부터는 adhoc 빌드에서 plist 를 제공 해 주지 않기 때문에, 이를 만들어 주는 사이트를 만들어 보았습니다. [OTA Plist Maker](http://ota-plist-maker.appspot.com/)

![OTA Plist Maker Site](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/ota-plist-maker.jpg)

위 화면에서 URL 에는 ipa 가 있는 url을 입력하고, 나머지 창에도 앱의 정보를 입력한 후, make 를 선택하면 plist 파일을 생성합니다.

-	download page 만들기 :`<a href="">` 의 `[github plist raw url]` 에 github 에 업로드 한 plist 의 raw 주소를 입려 합니다.

```html
<a href="itms-services://?action=download-manifest&url=[github plist raw url]">Download</a>
```

-	github page 에 배포: 'http://{github-name}.github.io' 에 접속하거나 혹은 상세 url 로 접속하여 download page 에 접속 합니다.

![Github OTA Page](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/ota-page.jpg)

그리고 링크를 선택하면 아래와 같이 ipa 파일을 단말에 설칠 할 수 있습니다.

![OTA Install](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/ota-install.jpg)

##P.S.

[Fabric](https://fabric.io) 이나 [Parse](https://parse.com), [TestFlight](https://www.testflightapp.com) 를 통해서 배포하는편이 더 편하긴 하지만, 부득이하게 이런 방법으로 배포할 수 있기 때문에...
