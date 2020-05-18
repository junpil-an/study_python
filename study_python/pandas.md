# pandas
```python
import numpy as np
import pandas as pd
```
<br>
## Pandas 자료구조

- 빅 데이터 분석에 있어서 높은 수준의 성능을 보여줌

#### Series

```python
obj = pd.Series([4,7,-5,3])
obj
>>>0 4
>>>1 7
>>>2 -5
>>>3 3


obj = pd.Series([4,7,-5,3])

#1.value 값 확인
obj.values
    #array([ 4,  7, -5,  3])


#2.index 값 확인
obj.index
    #RangeIndex(start=0, stop=4, step=1)


#3.type 확인
obj.dtypes
    #dtype('int64')


#4.index 변경 가능
obj2 = pd.Series([4,7,-5,3],index=["a","b","c","d"])
obj2


#5. python 의 dic type을 series data로 만들 수 있음, key= index
sdata= {"A":1,"B":2,"C":3}
obj3 = pd.Series(sdata) #변환가능 인덱스 새로 설정 가능


#6. 이름 설정 , 인덱스 이름 설정
obj3.name = "alphabet"
obj3.index.name="name"
obj3

#7. index 변경(2)
obj3.index=["D","F","G"]

```

## DataFrame

```python
# dataframe
#python 의 dic or np의 array로 정의할 수 있음

data = {"name":["A","B","C"],
        "age":[14,17,20],
        "year":[2010,2015,2020]}

df = pd.DataFrame(data)
print(df)
#행 방향의 index
df.index
    #RangeIndex(start=0, stop=3, step=1)

df.columns   
    #col 이름 
    #Index(['name', 'age', 'year'], dtype='object')

df.values
'''
    array([['A', 14, 2010],
       ['B', 17, 2015],
       ['C', 20, 2020]], dtype=object)
'''

#index 이름 설정하기
df.index.name='Num'
#col 이름 설정
df.columns.name = 'info'
df

#index 값은 새로 지정  가능
#col 값은 새로운 col값을 넣어주면 없는 값이면 NaN을 출력
df =pd.DataFrame(data,index=["03","04","05"],columns=["name","age","year","panalty"]) 

#descirbe()
df.describe()
    #다양한 값들의 계산 결과값을 보여줌


#df 에서 열을 선택하고 조작하기/ 두개 다 동일한 방법
df['age']
df.age


#두개 이상의 col 값 가져오기
df[["age","name"]]


#원하는 값 대입도 가능
df['penalty'] = [1,2,3]

#새로운 col 값 추가해주기
df['zerozs']=np.arange(3)

#Series도 추가가 가능하다
val=pd.Series([100,200,300],index=["03","04","05"])
df['debt'] =val # index값에 맞춰서 새로 생성 가능하다

#더하기 ,빼기 or boolean type 가능
df["plus"]= df['penalty']+df['debt']
df['pus_bool']= df['plus'] >0
df.index.name= "blabla"
df.name = "test"
```

## loc,iloc

```python

#특정 행 가져오기 -> 사용할 것을 추천
#loc / [":",":"] 특정 row의 특정 col
df.loc["03":"04","debt"] 

df.loc[:,"debt":"pus_bool"]

#새로운 row 삽입하기
df.loc["06",:]=["test",22,2030,"NaN",4,3,400,404,True]


# 특정 row 값을 가져온다
# 특정 row,col 값을 index값으로 불러온다
df.iloc[2:4,[0,1]]
```

## data

```python
# data

df= pd.DataFrame(np.random.randn(6,4))
df.columns=["A","B","C","D"]
df.index=np.arange(6)

#date_range 함수를 사용해서 기간을 정해 줄 수 있음
df.index= pd.date_range("20200505",periods=6)
df["E"]=np.random.randn(6)
#df.loc["2020-05-11",:]=[1,2,3,4,5]


#NaN값 없애기
df.dropna(how="any") #nan이 하나라도 있을경우 행을 날림
df.dropna(how="all") #모든 값이 nan일 경우 그 행을 없앤다
df.fillna(value=0.5) #nan 값에 value값 채우기
df.isnull() #null 값 찾기

df.loc[df.notnull()["E"],:]  #E 에 nan값이 아닌것만 출력

pd.to_datetime("20200202")
    # imestamp('2020-02-02 00:00:00')

#특정 열 삭제하기
df.drop(["E","A"],axis=1) #axis 값 1로 설정해줘야함
```

## pandas 에서 DataFrame 에도 적용되는 함수들

- sum() 함수 이외에도 pandas에서 DataFrame에 적용되는 함수는 다음의 것들이 있다.

- count 전체 성분의 (NaN이 아닌) 값의 갯수를 계산

- min, max 전체 성분의 최솟, 최댓값을 계산

- argmin, argmax 전체 성분의 최솟값, 최댓값이 위치한 (정수)인덱스를 반환

- idxmin, idxmax 전체 인덱스 중 최솟값, 최댓값을 반환

- quantile 전체 성분의 특정 사분위수에 해당하는 값을 반환 (0~1 사이)

- sum 전체 성분의 합을 계산

- mean 전체 성분의 평균을 계산

- median 전체 성분의 중간값을 반환

- mad 전체 성분의 평균값으로부터의 절대 편차(absolute deviation)의 평균을 계산

- std, var 전체 성분의 표준편차, 분산을 계산

- cumsum 맨 첫 번째 성분부터 각 성분까지의 누적합을 계산 (0에서부터 계속 더해짐)

- cumprod 맨 첫번째 성분부터 각 성분까지의 누적곱을 계산 (1에서부터 계속 곱해짐)

## 상관계수

```python
df2["A"].corr(df2["B"])
df2["B"].cov(df2["C"])

dates = df2.index
random_datas = np.random.permutation(dates)
df2 = df2.reindex(index=random_dates,columns=["D","B","C","A"])
df2

df2.sort_index(axis=0) #인덱스가 오름차순이 되도록

df2.sort_index(axis=1) #col로 오름차순이 되도록

df2.sort_index(axis=1,ascending=False) # 내림차순 정렬

df2.sort_values(by="D")

df2.sort_values(by="B",ascending=False) #B를 중심으로 내림차순 정렬

df2.sort_values(by=["A","B"]) #A와 B를 동시에 고려하여 오름차순 정렬

df2["F"].unique() #중복값 제외한 유니크한 값 얻기

df2["F"].value_counts() #지정한 행 or 열에서 값에 따른 개수 얻기

df2["F"].isin(["a","b"]) #안에 "a","b"가 있나 없나 확인해보기

```

#### lambda 함수 사용

```python
func = lambda x: x,max() - x.min()

df3.apply(func,axis=0)
```
