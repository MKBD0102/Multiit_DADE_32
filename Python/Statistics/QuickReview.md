# 데이터 통계량
- 위치: 데이터 중심 위치, ex. 평균, 중위수, 절사평균, 최빈값, 사분위수 등
- 변이: 데이터 산포, ex. 표준편차, 분산, 사분위간 범위 등
- 모양: 왜도(비대칭), 첨도(뾰족한 정도)
## 1차원 데이터
### 중심 지표
- 평균
  - 평균값(산술평균) `mean()`
  - 기하평균: n개 양수들의 곱의 n 제곱
  - 조화평균: 역수들의 산술평균의 역수
  - 절사평균 `trim_mean(x,proportiontocnt)`, proportiontocnt: 절사율
- 중앙값 `median()`
- 최빈값 `mode()`
### 산포도 지표
- 편차 `x - mean()`
- 분산 `var()`
- 표준편차 `std()`
### 범위
- 범위 `max(X) - min(X)`
- 사분위수 `np.percentile(X,p)`, p = 0.25,0.5,0.75
- 백분위수 `np.percentile(X,p)`
### 데이터 정규화
- 표준화
  - `z = (x-mean())/std()`
  - `z = scipy.stats.zscore(x)`
  - `z = sklearn.preprocessing.StandardScaler.fit_transform(x)`
- 정규화
  - `z = (x - min()) / (max() - min())`
  - `z = sklearn.preprocessing.MinMaxScaler.fit_transform(x)`
  - MinMaxScaler는 최솟값과 최댓값이 균일하게 나올 때 사용 가능함
### 시각화
- 히스토그램(histogram)
  - `matplotlib.pyplot.hist(x,bins)`
  - `seaborn.histplot(x,bins)`
- 상자그림(boxplot)
  - `matplotlib.pyplot.boxplot(x)`
  - `seaborn.boxplot(x)`
## 2차원 데이터
### 두 데이터 사이 관계 지표
- 공분산 `numpy.cov(x,y)`
- 상관계수 `pandas.DataFrame.corr`
### 시각화
- 산점도
  - `matplotlib.pyplot.scatter(x,y)`
  - `seaborn.scatterplot(data,x,y)`
