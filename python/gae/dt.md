## Google App Engine 에서 Local Time 을 출력하는 방법.

### Issue : ndb 의 `DatetimeProperty` 는 [UTC](http://ko.wikipedia.org/wiki/%ED%98%91%EC%A0%95_%EC%84%B8%EA%B3%84%EC%8B%9C) 로만 저장이 가능하다.
Google App Engine 에서 사용하는 ndb 의 `DatetimeProperty` 는 UTC(Coordinated Universal Time) 만 저장 할 수 있다.
다른 datetime 을 저장하려고 하면 아래와 같은 에러가 발생한다.

```python
NotImplementedError: DatetimeProperty date can only support UTC.
Please derive a new Property to support alternative timezones.
```

### Solution : UTC 로 저장하고, 호출 후 출력 전에 Local Time 으로 변환한다.

#### 1. pytz 를 사용하기.
[pytz](http://pytz.sourceforge.net/) 는 python 의 time 관련 library 이다. standard library 가 아니기 때문에
gae 에서 사용하기 위해서는 Flask 와 마찬가지로 `pip install` 을 사용하여 설치 해여야 한다.

`requirements.txt` 에 아래와 같이 추가한다.

```
pytz==2014.4
```

그리고 pip install 을 사용하여 설치한다.

```shell
pip install -r requirements.txt -t lib/
```

그러면 관련 모듈들이 `lib/` 에 추가 되었음을 확인 할 수 있다.
```shell
Downloading/unpacking pytz==2014.4 (from -r requirements.txt (line 1))
  Downloading pytz-2014.4.tar.bz2 (159kB): 159kB downloaded
  Running setup.py (path:/private/var/folders/6x/c_v0v09n5cs6sgqh3r02f6hh0000gn/T/pip_build_pine84/pytz/setup.py) egg_info for package pytz

Installing collected packages: pytz
  Running setup.py install for pytz

Successfully installed pytz
Cleaning up...
```
![pytz installed tree](https://raw.githubusercontent.com/kyungkoo/study-note/master/python/gae/images/pytz-tree.png)

코드상에서는 아래와 같이, utc datetime 을 불러온 후, local tiemzone 을 생성하여 해당 timezone 으로
변경 하면 된다.

```python
from pytz import timezone
import pytz

utc_dt = datetime.now() # utc 시간을 생성한다.(DatetimeProperty 값을 가져오는 부분.)
local_tz = timezone('Asia/Seoul') # local timezone 을 생성한다.
local_dt = utc_dt.replace(tzinfo=pytz.utc).astimezone(local_tz)
```
