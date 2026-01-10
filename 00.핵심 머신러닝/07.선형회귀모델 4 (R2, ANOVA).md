## 1. 변동의 분해 (Sum of Squares)
회귀 분석에서 전체 변동은 세 가지 요소의 관계로 설명됩니다.

<img width="1440" height="1046" alt="image" src="https://github.com/user-attachments/assets/12634569-d5ec-42be-bfe5-2dfa2286a339" />

* **SST (Total Sum of Squares)**: 실제값과 평균값의 차이 (전체 변동)
    $$SST = \sum (y_i - \bar{y})^2$$
* **SSR (Regression Sum of Squares)**: 예측값과 평균값의 차이 (모델이 설명하는 변동)
    $$SSR = \sum (\hat{y}_i - \bar{y})^2$$
* **SSE (Error Sum of Squares)**: 실제값과 예측값의 차이 (모델이 설명하지 못한 잔차 변동)
    $$SSE = \sum (y_i - \hat{y}_i)^2$$

> **공식**: $$SST = SSR + SSE$$

---

## 2. 결정계수 ($R^2$)

### (1) 정의 및 특징
<img width="1484" height="1040" alt="image" src="https://github.com/user-attachments/assets/bb24ae74-b36c-47fe-91a9-634d273f14d3" />
회귀 모델이 종속 변수의 전체 변동 중 얼마만큼을 설명하는지를 나타내는 지표입니다.

$$R^2 = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}$$

* **$R^2 = 1$**: 모든 관측치가 회귀 직선 위에 있음 (100% 설명).
* **$R^2 = 0$**: 모델이 평균값으로 예측하는 것보다 나을 것이 없음 (설명력 없음).

### (2) 수정 결정계수 (Adjusted $R^2$)
<img width="1326" height="1013" alt="image" src="https://github.com/user-attachments/assets/0d803a00-791d-4559-8c93-073db5102543" />
독립 변수의 개수가 늘어나면 $R^2$는 항상 증가하는 단점이 있습니다. 이를 보정하기 위해 샘플 수($n$)와 변수 개수($p$)를 고려한 자유도로 나눈 값입니다.

$$Adjusted\ R^2 = 1 - \left[ \frac{SSE / (n - p - 1)}{SST / (n - 1)} \right]$$

---

## 3. 분산분석 (ANOVA: Analysis of Variance)

<img width="1397" height="902" alt="image" src="https://github.com/user-attachments/assets/a337e0ab-5bed-49d8-8bf6-6b4fc0f99b54" />
<img width="1487" height="908" alt="image" src="https://github.com/user-attachments/assets/5a62a506-188e-443c-9d2c-6f6b28622833" />
<img width="1394" height="821" alt="image" src="https://github.com/user-attachments/assets/ca97cea4-af0e-4d08-8e7f-fb75a6b24117" />

### (1) 가설 설정
* **귀무가설 ($H_0$)**: 모든 회귀 계수는 0이다. ($\beta_1 = \beta_2 = \dots = 0$)
* **대립가설 ($H_1$)**: 적어도 하나의 회귀 계수는 0이 아니다.

### (2) 분산분석표 (ANOVA Table)
| 요인 | 제곱합 (SS) | 자유도 (df) | 평균 제곱 (MS) | F-통계량 |
| :--- | :---: | :---: | :---: | :---: |
| **회귀 (Model)** | $SSR$ | $p$ | $MSR = SSR/p$ | $F = MSR/MSE$ |
| **오차 (Error)** | $SSE$ | $n-p-1$ | $MSE = SSE/(n-p-1)$ | |
| **합계 (Total)** | $SST$ | $n-1$ | | |

* **F-검정**: $F$ 값이 커지고 p-value가 유의수준(예: 0.05)보다 작으면 모델이 통계적으로 유의미하다고 판단합니다.

---

## 4. Top 0.1% 엔지니어의 통찰
1. **$R^2$의 한계**: $R^2$가 높다고 해서 반드시 '인과관계'가 증명된 것은 아닙니다. 단순히 '상관성'과 '설명력'이 높을 뿐임을 명심해야 합니다.
2. **단순함의 미학**: 무조건 변수를 많이 넣어 $R^2$를 높이는 것보다, 꼭 필요한 변수만으로 높은 $Adjusted\ R^2$를 유지하는 모델이 더 강건(Robust)한 모델입니다.
3. **분산의 본질**: ANOVA는 단순한 표가 아니라, 우리가 제어할 수 있는 변동($SSR$)과 제어할 수 없는 변동($SSE$)의 비율을 통해 모델의 가치를 평가하는 도구입니다.
