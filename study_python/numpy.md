## numpy

```python


import numpy as np


x=np.array(((11,12,13),(21,22,23),(31,32,33)))

#ndim -> 차원의 수

ax = np.array([1,2,3])
ay=np.array([3,4,5])

np.cos(ax)   #cos 형태 출력
np.where(ax<2,ax,10)

m=np.matrix([ax,ay,ax])
'''
matrix([[1, 2, 3],
        [3, 4, 5],
        [1, 2, 3]]
        '''
m.T
#m.T 행열 transaction

grid1 =np.zeros(shape=(10,10),dtype=float)
grid2 =np.ones(shape=(10,10),dtype=float)
print(grid1) # row 10 col 10 value 0
print(grid2) # row 10 col 10 value 1
print(grid1[1]+10) # row 1 각각 + 10
print(grid2[:,2]*2) 

import numpy as np 
import time  #시간비교시 time 라이브러리 사용

def trad_version():
  t1 = time.time()
  X = range(1000000)
  Y= range(1000000)
  Z=[]
  for i in range(len(X)):
    Z.append(X[i]+Y[i])
  return time.time() - t1

def numpy_version():
  t1 = time.time()
  X = np.arange(1000000)
  Y= np.arange(1000000)
  Z=X+Y
  return time.time() -t1
  
print(trad_version())
print(numpy_version())  #numpy 속도가 현저히 빠름을 알 수 있음
```