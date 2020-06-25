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
