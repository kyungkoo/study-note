#readlines 을 다시 생각해보자.

파일을 읽어 한줄씩 출력하고자 할때, 다음과 같이 코드를 짜게 된다.

```python
file = open('readline.md')

for line in file.readlines():
  print line

file.close()  
```

여기서 `file.close` 는 `with as` 를 사용하여 아래와 같이 바꿀 수 있다.

```python
with open('readline.md') as file:
  for line in file.readlines():
    print line
```

그런데 사실 for loop 를 통해 file 을 읽을 경우, `readlines()` 를 사용하지 않아도
python 은 해당 라인별로 출력한다.

```python
with open('readline.md') as file:
  for line in file:
    print line
```

위 코드를 실제로 구동시켜보면 `file.readlines()` 를 사용했을때와 정확하게 동일한 결과를 얻을 수 있다.
