## 쓰레드 
  - 파이썬은 기본적으로 하나의 쓰레드에서 실행,메인 쓰레드가 파이썬 코드를 순차적으로 실행

  - 코드를 병렬로 실행하기 위해, 별도의 쓰레드를 생성 -> threading 모듈을 사용 할 수 있음
 
#### threading
 -  threading 모듈의 threading.Thread() 함수를 호출하여 Thread 객체를 얻은 후 Thread 객체의 start() 메서드를 호출하면 됨

```python
import threading

def sum(low,high):
 total = 0
 for i in range(low,high):
    total += i

t = treading.Tread(target=sum,args=(1,100000))
t.start()
print("Main Tread")

```

```python
import time

#총 25초의 시간이 걸림

#5초의 시간이 걸리는 함수
def long_task():
    #1초간 대기
    time.sleep(1)
    print(f"working:{i+1}")
    

print("start")

#long_task를 5회 수행
for i in range(5):
    long_task()

print("end")


import time
import threading

def long_task():
    #1초간 대기
    time.sleep(1)
    print(f"working:{i+1}")
    
print("start")
threads=[]

for i in range(5):
    t = threading.Thread(target=long_task)
    threads.append(t)

for t in threads:
    t.start()

for t in threads:
    t.join()

print("end")
'''
threading.Thread를 사용하여 만든 스레드 객체가 동시작업을 가능하게 해줌


'''

```
