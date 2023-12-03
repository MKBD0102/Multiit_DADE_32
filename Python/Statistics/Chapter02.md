# 1. 데이터 중심의 지표
<br/>

## 1.1. 평균값
> 데이터의 합 / 데이터의 개수
- 일반 작성
```
scores = [69, 56, 41, 57, 48, 65, 49]
sum(scores)/len(scores)
```
- NumPy 라이브러리 활용
```
import numpy as np
np.mean(scores)
```
- Pandas 라이브러리 활용
```
import pandas as pd
scores_df = pd.DataFrame(scores)
scores_df.mean()
```
## 1.2. 중앙값
> 데이터가 크기 순으로 정렬되었을 때 중앙에 위치한 값
- 정렬
```
# 방법1
import numpy as np
sorted_scores = np.sort(scores)
# 방법2
sorted_scores = sorted(scores)
# 방법3
scores.sort()  # 리스트 요소 자체를 정렬 후 원본에 반영
sorted_scores = scores
```
- 일반 작성
```
n = len(sorted_scores)
if n % 2 == 0:
    m0 = sorted_scores[n//2 - 1]
    m1 = sorted_scores[n//2]
    median = (m0 + m1) / 2
else:
    median = sorted_scores[(n+1)//2 - 1]
```
- NumPy 라이브러리 활용
```
import numpy as np
np.median(scores)
```
- Pandas 라이브러리 활용
```
import pandas as pd
scores_df.median()
```
## 1.3. 최빈값
> 데이터에서 가장 많이 나타나는 값
- Pandas 라이브러리 활용
```
import pandas as pd
pd.Series([1,2,3,3,3,4,5,5,5]).mode()
# 최빈값이 여러 개인 경우 해당되는 빈도수를 가진 데이터 모두 반환
```
---
<br/>

# 2. 데이터의 산포도 지표
<br/>

## 2.1. 분산과 표준편차
  ### 2.1.1. 편차
  > 데이터가 평균으로부터 떨어져 있는 정도<br/>
  > 편차의 평균 = 0<br/>
  > 데이터의 값 - 데이터의 평균
  ### 2.1.2. 표본분산
  > 편차 제곱들의 평균<br/>
  > 평균에 대해서 정의되는 산포도의지표<br/>
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
# * `pd.DataFrame.describe()`
> 위의 여러 지표 한 번에 구할 수 있는 메서드
---
<br/>

# 3. 데이터의 정규화
<br/>
> 정규화(normalization): 데이터를 통일된 지표로 변환

## 3.1. 표준화
> 데이터에서 평균을 빼고 표준편차로 나누는 것<br/>
> 표준화 변량 = Z 점수(z-score) = (데이터의 값 - 데이터의 평균)/데이터의 표준편차<br/>
> 표준화된 데이터의 평균 = 0, 표준편차 = 1<br/>
```
import numpy as np
z = (scores - np.mean(scores)) / np.std(scores)
```
## 3.2. 편찻값
> 데이터의 평균 = 50, 표준편차 = 10이 되도록 정규화한 값<br/>
> 편찻값 = 50 + 10 * z-score = 50 + 10 * (데이터의 값 - 데이터의 평균)/데이터의 표준편차
```
import numpy as np
z = 50 + 10 * (scores - np.mean(scores)) / np.std(scores)
```
---
<br/>
# 4. 1차원 데이터 시각화
<br/>

## 4.1. 도수분포표
## 4.2. 히스토그램
## 4.3. 상자그림(box plot)
