- int() <- 정수부분만 추출
- import math / math.ceil() 올림 / math.floor() 버림
- 날짜 객체 생
```
import datetime
day1 = datetime.date(2019, 12, 14)
day1.weekday() # 요일 판
```
- 두 날짜의 차이
```
>>> diff = day2 - day1
>>> diff
datetime.timedelta(days=539)
>>> diff.days
539
```

- 특정 기준으로 리스트 정렬
```
1. 리스트의 각 원소를 기준으로 사전순 정렬
arr = ['abc', 'bac', 'bca']
sorted(arr, key=lambda x : x)

2. 리스트 각 글자의 첫글자를 기준으로 정렬
arr = ['abc', 'bac', 'bca']
sorted(arr, key=lambda x : x[0])

3. 리스트 내 요소의 인덱스를 요소의 크기순으로 정렬
b = [12, 14, 23, 24, 16]
b_idx = sorted(range(len(b)), key = lambda k: b[k])

4. x[0]를 기준으로 정렬하고 같을경우 x[1]를 기준으로 정렬하기
arr = ['abb', 'acc', 'bcd']
sorted(arr, key=lambda x : (x[0], x[1]))

5. x[0]는 내림차순, x[1]는 오름차순을 기준으로 정렬하 
arr = ['abb', 'acc', 'bcd']
sorted(arr, key=lambda x : (-x[0], x[1]))

* 열 기준 정렬
arr.sort(key=lambda x:x[1])

* 두 번째 값이 같을 경우에는 첫 번째 값을 기준으로 오름차순 정렬
arr.sort(key=lambda x: (x[1], x[0]))
```
