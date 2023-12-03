# 1. 데이터 중심의 지표
<br/>

## 1.1. 평균값
## 1.2. 중앙값
## 1.3. 최빈값
---
<br/>
# 2. 데이터의 산포도 지표
<br/>

## 2.1. 분산과 표준편차
### 2.1.1. 편차
### 2.1.2. 표본분산
> 편차 제곱들의 평균<br/>
> $\sum{(편차)^2}$/데이터의 개수
- NumPy 라이브러리 활용
```
import numpy as np
# 방법1
np.mean(deviation**2)
# 방법2
np.var(scores)
```
- Pandas와 NumPy 활용
```
import pandas as pd
import numpy as np
# 방법1
scores_df['square of deviation'] = np.square(deviation)
scores_df.mean()
# 방법2
scores_df.var(ddof=0)  # ddof = 1: 불편분산, ddof = 0: 표본분산
```
### 2.1.3. 표준편차(standard deviation)
> 분산의 제곱근<br/>
> $\sqrt{(표본분산)}$
- NumPy 라이브러리 활용
```
import numpy as np
# 방법1
np.sqrt(np.var(scores, ddof=0))
# 방법2
np.std(scores, ddof=0)
```
## 2.2 범위
  ### 2.2.1. 범위
  > 데이터의 최댓값과 최솟값의 차이<br/>
  > 분산, 표준편차와 달리 데이터 전체를 보지 않음<br/>
  > $Rg = x_{max} - x_{min}$
  - 일반 작성
  ```
  max(scores) - min(scores)
  ```
  - NumPy 라이브러리 활용
  ```
  import numpy as np
  np.max(scores) - np.min(scores)
  ```
  ### 2.2.2. 사분위 범위
  > 데이터 하위 25%, 50%, 75%에 위치하는 값으로 범위 분할<br/>
  > 중앙값에 대해서 정의되는 산포도의 지표<br/>
  > 25% = 제1사분위수 = Q1<br/>
  > 50% = 제2사분위수 = Q2 = 중앙값<br/>
  > 75% = 제3사분위수 = Q3<br/>
  > 사분위 범위(IQR): $IQR = Q3 - Q1$<br/>
  - NumPy 라이브러리 활용
  ```
  import numpy as np
  Q1 = np.percentile(scores, 25)
  Q1 = np.percentile(scores, 25)
  IQR = Q3 - Q1
  ```
---
<br/>
# 3. 데이터의 정규화
<br/>
> 정규화 
## 3.1. 표준화
## 3.2. 편찻값
---
<br/>
# 4. 1차원 데이터 시각화
<br/>

## 4.1. 도수분포표
## 4.2. 히스토그램
## 4.3. 상자그림(box plot)
