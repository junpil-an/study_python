## args, kargs

#### *args 
- *arguments의 줄임말
- 여러개의 인자를 함수로 받고자 할 때 쓰임

```python

def lastName_and_FirstName(*Names):
	for name in Names:
		print("%{0} %{1}" .format (name[0],name[1:3],end=' '))
	print("\n")
	print(type(Names),Names)
```
튜플형태로 출력

#### **krgs 

- (키워드 = 특정 값) 형태로 함수를 호출할 수 있음
 

```python

def introduceEnglishName(**kwargs):
	for key,value in kwargs.items():
		print("{0} is {1}".format(key,value))

introduceEnglishName(MyName='Chris!!')

>>> MyName is Chris!!


def name2(**dd):
  for k,v in dd.items():
    print(f"{k}+{v}")

name2(asdasd = "asdsad")

>>> asdasd+asdsad
```
