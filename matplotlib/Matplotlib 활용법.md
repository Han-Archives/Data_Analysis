## Matplotlib

### 소개

Matplotlib는 Python 프로그래밍 언어 및 수학적 확장 NumPy 라이브러리를 활용한 플로팅 라이브러리로 데이터를 시각적으로 표현하는데 주로 사용되는 라이브러리.

![basic.PNG](attachment:basic.PNG)
![2.PNG](attachment:2.PNG)
 출처:https://matplotlib.org/stable/plot_types/index.html

### 활용 예시 (삼성 주가 변화)


```python
## import modules
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
```


```python
# 한글 폰트 사용하기
from matplotlib import font_manager,rc
import matplotlib

font_path = 'C:\\Windows\\Fonts\\gulim.ttc'
#폰트 이름 얻어오기
font_name = font_manager.FontProperties(fname=font_path).get_name()
#font 설정
matplotlib.rc('font',family=font_name)
```


```python
# upload data
s_stock = pd.read_csv("C:\\Users\\USER\\Desktop\\Analysis\\Proceed\\Matplotlib\\example\\samsung_stock.csv")
```


```python
s_stock
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-06-30</td>
      <td>81100</td>
      <td>81400</td>
      <td>80700</td>
      <td>80700</td>
      <td>79545.93750</td>
      <td>13288643</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-07-01</td>
      <td>80500</td>
      <td>80600</td>
      <td>80000</td>
      <td>80100</td>
      <td>78954.50781</td>
      <td>13382882</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021-07-02</td>
      <td>80000</td>
      <td>80400</td>
      <td>79900</td>
      <td>80000</td>
      <td>78855.94531</td>
      <td>8753097</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-07-05</td>
      <td>80100</td>
      <td>80800</td>
      <td>80000</td>
      <td>80400</td>
      <td>79250.21875</td>
      <td>8330969</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-07-06</td>
      <td>80600</td>
      <td>81200</td>
      <td>80500</td>
      <td>81200</td>
      <td>80038.77344</td>
      <td>12131651</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>240</th>
      <td>2022-06-24</td>
      <td>57900</td>
      <td>59100</td>
      <td>57700</td>
      <td>58400</td>
      <td>58400.00000</td>
      <td>23256103</td>
    </tr>
    <tr>
      <th>241</th>
      <td>2022-06-27</td>
      <td>59000</td>
      <td>59900</td>
      <td>58300</td>
      <td>58800</td>
      <td>58800.00000</td>
      <td>18122236</td>
    </tr>
    <tr>
      <th>242</th>
      <td>2022-06-28</td>
      <td>59200</td>
      <td>59500</td>
      <td>58700</td>
      <td>59400</td>
      <td>59400.00000</td>
      <td>13540538</td>
    </tr>
    <tr>
      <th>243</th>
      <td>2022-06-29</td>
      <td>58500</td>
      <td>58800</td>
      <td>58000</td>
      <td>58000</td>
      <td>58000.00000</td>
      <td>14677138</td>
    </tr>
    <tr>
      <th>244</th>
      <td>2022-06-30</td>
      <td>57200</td>
      <td>57600</td>
      <td>57000</td>
      <td>57000</td>
      <td>57000.00000</td>
      <td>18499814</td>
    </tr>
  </tbody>
</table>
<p>245 rows × 7 columns</p>
</div>




```python
date = s_stock['Date']
high = s_stock['High']
low = s_stock['Low']
```

### plot

Plot 그래프를 필요한 것은 x,y 값으로 위의 예시의 경우 x값은 Date, y값은 주가(high)로 표현


```python
plt.plot(date, high) # x축 (date), y축 (high 값)
```




    [<matplotlib.lines.Line2D at 0x1f8d42cb748>]




    
![png](output_9_1.png)
    


### subplot
![subplot.PNG](attachment:subplot.PNG)

subplot이란 위의 그릇의 경우 한 그릇안에 2가지 메뉴를 포함할 수 있듯이 2개 이상의 그래프(ax)를 한 그릇(fig)에 담는 기능을 말한다.
하나의 Figure 안에 여러 ax를 담을 수 있다.
![fig.PNG](attachment:fig.PNG)
출처: https://realpython.com/python-matplotlib-guide/



```python
# 2개의 그래프를 그리기 (가로)
fig = plt.figure()
ax1 = fig.add_subplot(2, 1, 1)
ax2 = fig.add_subplot(2, 1, 2)

ax1.plot(date, high)
ax2.plot(date, low)

plt.show()
```


    
![png](output_11_0.png)
    



```python
# 세로
fig = plt.figure()

ax1 = fig.add_subplot(1, 2, 1)
ax2 = fig.add_subplot(1, 2, 2)

ax1.plot(date, high)
ax2.plot(date, low)

plt.show()
```


    
![png](output_12_0.png)
    



```python
### figsize
fig = plt.figure(figsize=(10,5)) # x축 size y축 size

ax1 = fig.add_subplot(2, 1, 1)
ax2 = fig.add_subplot(2, 1, 2)

ax1.plot(date, high)
ax2.plot(date, low)

plt.show()
```


    
![png](output_13_0.png)
    


### plot 부가 요소

- 그래프 너비 설정하기 : figsize()
figsize를 통해 너비, 높이 설정

- figure의 title 설정하기 : suptitle()
2개 이상의 axes가 있는 경우 메인 이름 설정

- ax별 title 설정하기 : set_title()
ax별로 title 설정

- ax별 label 설정하기 : set_xlabel(), set_ylabel()
x, y축 이름 설정하는 방법

- ax별 axis 설정하기 : xaxis.set_tick_params(), yaxis.set_tick_params()
x, y의 항목의 색깔, 폰트 크기 설정


```python
fig = plt.figure(figsize=(10,5)) # x축 size y축 size
plt.suptitle('삼성 주식', fontsize = 15, y=0.95)

ax1 = fig.add_subplot(1, 2, 1)
ax2 = fig.add_subplot(1, 2, 2)

ax1.plot(date, high)
ax2.plot(date, low)

# ax1 x,y 축 이름 설정
ax1.set_title("삼성 주식(상한가)")
ax1.set_xlabel("날짜") # x축 이름 설정
ax1.set_ylabel("주가(상한가)") # y축 이름 설정
ax1.yaxis.set_tick_params(labelcolor='r') # axis 색 설정


ax2.set_title("삼성 주식(하한가)")
l = ax2.set_xlabel("날짜") # x label 값 설정 (색상, 크기)
l.set_color('g')
l.set_fontsize(20)
ax2.set_ylabel("주가(하한가)")

plt.show()
```


    
![png](output_15_0.png)
    


### 서브플롯 간의 간격 조정

- 직접 조정
plt.subplots_adjust(left, right, bottom, top, wspace, hspace)

- 자동 조정
plt.subplots(constrained_layout=True)


```python
fig, (ax1, ax2) = plt.subplots(nrows=2, ncols=1, figsize=(10, 5))
plt.suptitle('삼성 주식', fontsize = 15, y=1)

ax1.plot(date, high)
ax2.plot(date, low)

# ax1 x,y 축 이름 설정
ax1.set_title("삼성 주식(상한가)")
ax1.set_xlabel("날짜") # x축 이름 설정
ax1.set_ylabel("주가(상한가)") # y축 이름 설정

ax2.set_title("삼성 주식(하한가)")
l = ax2.set_xlabel("날짜") # x label 값 설정 (색상, 크기)
l.set_color('g')
l.set_fontsize(20)
ax2.set_ylabel("주가(하한가)")
plt.subplots_adjust(left=0.125, bottom=0.1, right=0.9, top=0.9, wspace=1, hspace=0.5)

plt.show()
```


    
![png](output_17_0.png)
    


### x,y 구간 정하기

- 특정 x 구간 설정하기 : xlim()
- 특정 y 구간 설정하기 : ylim()


```python
fig, ax = plt.subplots(nrows=1, ncols=1, figsize=(16, 5))
plt.suptitle('삼성 주식', fontsize = 15, y=1)

ax.plot(date, high)

# ax1 x,y 축 이름 설정
ax1.set_title("삼성 주식(상한가)")
ax1.set_xlabel("날짜") # x축 이름 설정
ax1.set_ylabel("주가(상한가)") # y축 이름 설정

plt.xlim(date[184],date[244])
plt.ylim(55000,75000)

plt.show()
```


    
![png](output_19_0.png)
    


### 주석 및 이미지 저장

- 주석 달기 :anonatate(text, xy, xytext, **kw)
- 이미지 저장 : savefig('파일경로 및 이름', 포맷, dpi)


```python
def annot_max(x,y, ax=None):
    xmax = x[np.argmax(y)]
    ymax = y.max()
    text= "%s, %d"%(xmax, ymax)
    if not ax:
        ax=plt.gca()
    bbox_props = dict(boxstyle="square,pad=0.3", fc="w", ec="k", lw=0.72)
    arrowprops=dict(arrowstyle="->",connectionstyle="angle,angleA=0,angleB=60")
    kw = dict(xycoords='data',textcoords="axes fraction",
              arrowprops=arrowprops, bbox=bbox_props, ha="right", va="top")
    # text, 값, 위치
    ax.annotate(text, xy=(xmax, ymax), xytext=(0.2,0.3), **kw)

def annot_min(x,y, ax=None):
    xmin = x[np.argmin(y)]
    ymin = y.min()
    text= "%s, %d"%(xmin, ymin)
    if not ax:
        ax=plt.gca()
    bbox_props = dict(boxstyle="square,pad=0.3", fc="w", ec="k", lw=0.72)
    arrowprops=dict(arrowstyle="->",connectionstyle="angle,angleA=0,angleB=60")
    kw = dict(xycoords='data',textcoords="axes fraction",
              arrowprops=arrowprops, bbox=bbox_props, ha="right", va="top")
    # text, 값, 위치
    ax.annotate(text, xy=(xmin, ymin), xytext=(0.8,0.3), **kw)    
```


```python
fig, ax = plt.subplots(nrows=1, ncols=1, figsize=(16, 5))
plt.suptitle('삼성 주식', fontsize = 15, y=1)

xmax = date[np.argmax(high)]
ymax = high.max()

xmin = date[np.argmin(high)]
ymin = high.min()

ax.plot(date, high)
plt.plot(xmax, ymax, 'o')
plt.plot(xmin, ymin, 'o')
annot_max(date,high)
annot_min(date,high)

# ax1 x,y 축 이름 설정
ax1.set_title("삼성 주식(상한가)")
ax1.set_xlabel("날짜") # x축 이름 설정
ax1.set_ylabel("주가(상한가)") # y축 이름 설정

plt.savefig('samsung.png', format='png', dpi=300)  # 아래 이미지 저장
plt.show()
```


    
![png](output_22_0.png)
    


### 하나의 ax에 2개 그래프 그리기


```python
plt.plot(date, high) # x축 (date), y축 (high 값)
plt.plot(date, low)

plt.show()
```


    
![png](output_24_0.png)
    


### 그래프 유형 및 Legend 나타내기

그래프별로 색상 및 그래프 유형 표현
![3.PNG](attachment:3.PNG)
출처: https://codetorial.net/matplotlib/set_marker.html


```python
plt.figure(figsize=(15,6)) # 표 크기 설정
plt.plot(date, high, 'r-') # x축 (date), y축 (high 값)
plt.plot(date, low)

# 주가 최고점, 최저점 확인
xmax = date[np.argmax(high)]
ymax = high.max()

xmin = date[np.argmin(low)]
ymin = low.min()

plt.plot(xmax, ymax, 'o')
plt.plot(xmin, ymin, 'o')
annot_max(date,high)
annot_min(date,low)

plt.legend(['상한가', '하한가'],loc='center left', bbox_to_anchor=(0, 0.5))
plt.xlabel('일자')
plt.ylabel('주가')
plt.title('21/6/30~22/06/30 삼성 주가', fontsize=15)
plt.show()
```


    
![png](output_26_0.png)
    


### Reference

https://matplotlib.org/stable/plot_types/index.html

https://codetorial.net/matplotlib/heatmap.html
