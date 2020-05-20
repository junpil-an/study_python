## class __init__ 와 __call__의 차이

__init__ 인스턴스 초기화 할 때 불러와짐, __call__은 인스턴스가 호출됐을 때 실행

```python
class A:
	def __init__(self):
		print('init')
	def __call__(self):
		print('call')

# 객체 생성할 때
a= A()
>>> init

# 인스턴스 호출될 때
a()
>>> init
>>> call
```
