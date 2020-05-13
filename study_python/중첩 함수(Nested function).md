## 중첩 함수(Nested function)

- 함수 내부에 정의된 또 다른 함수
- 중첩함수는 해당 함수가 정의된 함수 내에서 호출 & 반환 가능
- 함수 안에 선언된 변수는 함수 안에서만 사용 가능한 원리와 동일(local variable)

```python
def outer_func():
	print('call outer_func function')

	def inner_func():
		return 'call inner_func function'

	print(inner_func())

outer_func()
>>> call outer_func function
# 중첩함수는 함수 밖에서는 호출 X

```

```python
def outer_func(num):
	def inner_func():
		print(num)
		return 'complex'

	return inner_func

fn =outer_func(10)  ->10
print(fn()) 	    ->complex
```