#App Icon 에 나오는 Display Name 변경.

info.plist 에서 `Add Row` -> `Bundle display name` 을 추가 한 다음, 해당 부분에 원하는 이름을 추가 해 주면 된다.

![Bundle display name = $(PRODUCT_NAME)](https://raw.githubusercontent.com/kyungkoo/study-note/master/iOS/images/change-display-name-1.png)

추가적으로 Localize 를 하기 위해서는 `InfoPlist.strings` 파일을 추가하고 Localize 별로 아래와 같이 추가해 주면 된다.

```
"CFBundleDisplayName" = "App Name You want";
```
