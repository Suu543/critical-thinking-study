## Linear Regression - Algorithm History

회귀분석 (Regression Analysis): 인과관계를 수학적으로 분석하는 것! 

- 어떤 변수들이 한 변수의 원인이 되는지 분석하는 방법. 원인(X) ==> 결과(Y)
- 인과 관계를 수학적으로 분석하는 것. X(독립변수) ==> Y(종속변수 - 독립변수에 영향을 받는다는 의미에서)

독립변수의 수

- 1개: 단순회귀분석
- 2개 이상: 다중회귀분석

독립변수의 척도

- 등간 + 비율 척도: 일반회귀분석
- 명목 + 서열 척도: 더미변수를 이용한 회귀분석

독립변수와 종속변수의 관계

- 선형: 선형회귀분석
- 비선형: 비선형회귀분석

선형은 수학에서 직선 - 두 변수의 관계는 이러한 직선 관계를 이룬다.

#### 이러한 직선 중에서 두 변수의 관계를 가장 잘 설명해 줄 수 있는 직선을 찾자 = 선형회귀분석 (Linear Regression Analysis)

![Fitting the Multiple Linear Regression Model | Introduction to Statistics |  JMP](https://www.jmp.com/en_hk/statistics-knowledge-portal/what-is-multiple-regression/fitting-multiple-regression-model/_jcr_content/par/styledcontainer_2069/par/lightbox_4130/lightboxImage.img.png/1548704005203.png)

#### 직선이 아닌 그래프로 두 변수의 관계를 분석하는 것 = 비선형회귀분석 (Non-Linear Regression Analysis)

![Nonlinear regression with python - what's a simple method to fit this data  better? - Stack Overflow](https://i.stack.imgur.com/G8UoW.png)

#### 회귀분석 예시

자동차가 한 대 있고,

이 차가 달리다가 브레이크를 밟았을 때, 

- 그 시점의 순간 속도를 `x` - 독립변수

- 브레이크를 밟은 후 멈출 때까지 자동차가 이동한 거리를 `y` - 종속변수

직관적으로, `x` and `y`가 인과관계가 있다는 것을 알 수 있다. 이 인과관계를 수학적으로 분석하는 것이 바로 `회귀분석`이다.

50번의 실험을 통해 자동차의 `x, y`를 구한 후, `(x, y)` 점을 찍은 그래프

![img](https://cdn-images-1.medium.com/max/1000/1*4XeS1JwEWK14SF8GTh4E7A.png)



 당연히 이 점들을 동시에 지나는 직선은 존재하지 않지만, 그나마 이 관계를 가장 잘 설명해 줄 수 있는 직선을 구해보자라는 게 바로 선형회귀 분석이라 할 수 있다. 즉, 이 점들을 동시에 지나는 직선이 없으므로, 두 변수의 관계를 가장 잘 나타내줄 수 있는 직선을 구한다.

**두 변수의 관계를 가장 잘 나타낼 수 있다 = 잔차의 제곱의 합이 최소임을 의미한다???**

![img](https://cdn-images-1.medium.com/max/1000/1*0gCoSBWSpOyiSH-lZ_lIvQ.png)

위 그래프의 빨간 직선이 `f(x) = ax + b`라고 생각해보자.

한 점이 (10, 39) 라고 생각해보자.

이 직선에 10을 대입 했을때 함수 값과 `f(10)`과 `39`의 차이가 작을수록 좋음을 알 수 있다.

![img](https://cdn-images-1.medium.com/max/1000/1*Z8hU0qTQD5uFii4U_bCjQA.png)

`f(x) = ax + b`라고 가정 했을때, 밑에 있는 점은 `(10, f(10))` 이라는 것을 알 수 있다.

이때 `f(10)`과 `39`의 차이가 별로 나지 않아야, 이 점들을 최대한 가깝게 표현할 수 있는 직선이 된다는 것을 알 수 있다.

`39 - f(10) = 잔차` 일반적으로 무엇이 더 큰지 알 수 없기 때문이 절댓값을 씌운 값이 작으면 작을 수록 이 변수들의 관계를 잘 표현해주는 직선이라 표현할 수 있다. 수학자들은 아래 그래프와 같이 발생하는 잔차들의 합이 가장 작은 직선을 찾으면 되겠다라고 생각을 했다.

![img](https://cdn-images-1.medium.com/max/1000/1*MbVAlqLqSZWoZw-TjFbn3g.png)

이때 최소값, 최대값할 때 생가나는 개념이 바로 미분이다. 하지만 위와 같이 절대값이 씌워져있으면 미분을 적용하기가 어렵다. 정확히는 편미분을 적용하기가 어렵다. 그래서 잔차의 합의 최소인 것을 구하는 것이 아닌, 잔차의 제곱의 합이 최소인 직선을 구하는 것이 편리하다는 것을 알 수 있다. 수학적인 내용은 조금 건너띄고, **우리가 구해야 하는 것은 잔차의 제곱의 합이 최소인 직선을 구하는 것이다**.

이러한 직선을 구할 수 있다면, 두 변수 사이의 인과관계를 잘 표현해 줄 수 있을 것이라는 생각을 했고, 이것이 바로 단순선형회귀분석이라 할 수 있다.

우리의 목적은 어떻게 잔차의 제곱의 합이 최소가 되는 직선을 찾을 수 있는가를 알아내는 것이다.

이때 사용하는 방식이 바로 `최소제곱법 (Least Square)`이라 칭한다.

1. 편미분을 이용하는 방법 - 잔차의 제곱의 합을 식으로 쓰면 아래와 같은 식이 도출된다.

- 아래 식에서 우리가 모르는 변수는 두개다: **a, b** 
- 고로 잔차의 제곱의 합은 **a, b**에 대한 다변수함수 **E(a, b)**이고, 이 함수의 다변수함수의 최소값을 구하는 문제다.

![img](https://cdn-images-1.medium.com/max/1000/1*OIVwXAyu4uIkfohO5tbS4w.png)

2. 행렬 - 실제로 여러 개의 점들을 동시에 지나는 직선은 없다 (특별한 경우를 제외하고).

- 아래 사진과 같이 연립일차방정식을 행렬로 표현한 것이다.
- 잔차의 제곱의 합이 최소인 **a, b**를 찾는 것은 선형대수학에서의 용어에 따르면 최소제곱해를 찾는 것이다.

![img](https://cdn-images-1.medium.com/max/1000/1*FNxYA4xWv40B-bTWVUgwxw.png)

이렇게 `최소제곱법`을 이용해서 직선을 찾으면 = (**y = 4.13x - 17.8**)

1. 인과관계를 수학적으로 설명할 수 있다는 장점이 있다.

2. 예측 - 제동시 속도가 23km/h 일 때, 이 직선에 대입해서, 브레이크를 밟고 완전히 멈출 때 까지 이동한 거리를 측정할 수 있다. 물론 이 값이 정확하지 않을 수는 있지만, 대략 이 정도는 이동 후에 멈췄을 것이다를 타당하게 예측할 수 있다.

- `y = 4.13 * 23 - 17.8`

  

Before we do any coding, we will have a deep dive into building out an intuition of the theory and motivation behind Linear Regression.

- Brief History
- Linear Relationships
- Ordinary Least Squares
- Cost Functions
- Gradient Descent
- Vectorization

## Brief History

- The history of the "Invention" of linear regression is a bit muddled. 
- The linear regression methods based on least squares grew out of a need for mathematically improving navigation methods based on astronomy during the Age of Exploration in the 1700s.
- 1722 - Roger Cotes discovers combining different observations yields better estimates of the true value.
- 1750 - Tobias Mayer explores averaging different results under similar conditions in studying liberations of the moon.
- 1757 - Roger Joseph Boscovich further develops combining observations studying the shape of the Earth.
- 1788 - Pierre-Simon La-place develops similar averaging theories in explaining the differences of motion between Jupiter and Saturn.
- 1805 - First public exposition in Linear Regression with least squares method published by Adrien-Marie Legendre
  - Nouvelles Methodes pour la Determination des Orbites des Cometes
- 2005 - Side portrait of Adrien-Marie Legendre is actually discovered to be Louis Legendre!
- Only one known sketch of Adrien-Marie Legendre...
- Only one known watercolor caricature sketch of Adrien-Marie Legendre
- 1809 - Carl Friedrich Gauss publishes his methods of calculating orbits of celestial bodies.
- Claiming to have invented least-squares back in 1795!
- Carl Friedrich Gauss was born in 1777, which would make him 18 years old at his proclaimed time of discovery.

- 1808 - Robert Adrain published his formulation of least squares (a year before publication by Gauss).

#### Whatever the case of invention may be, let's build an intuitive understanding of linear regression!

- Put simply, a linear relationship implies some constants straight line relationship.
- The simplest possible being y= x

![img](https://cdn-images-1.medium.com/max/1000/1*vYHnZ9Z4bcXJo5rlao9ObA.png)

- Fundamentally, we understand we want to minimize the overall distance from the points to the line

![img](https://cdn-images-1.medium.com/max/1000/1*2iDrBknwvURTT2mq2t8-1Q.png)

We also know we can measure this error from the real data points to the line, known as the `residual error`

![img](https://cdn-images-1.medium.com/max/1000/1*z9cspZhNZrY6kKpCmIvEtg.png)

Clearly, we want to minimize the level of this `residual error`. We can also see the `residuals` can be both positive and negative.

![img](https://cdn-images-1.medium.com/max/1000/1*BHNLW-aGLpNYV7Gv8JyKaA.png)



Ordinary Least Squares works by minimizing the sum of the squares of the differences between the observed dependent variable (values of the variable being observed) in the given dataset and those predicted by the linear function.

We can visualize squared error to minimize:

![img](https://cdn-images-1.medium.com/max/1000/1*CRZewy_IVkNevS3tb8tmFQ.png)

Having a squared error will help us simplify our calculations later on when setting up a derivative.

## Understanding Ordinary Least Squares

Linear Regression OLS Theory

- We know the equation of a simple straight line
  - y = mx + b
  - m is slope
  - b is intercept with y - axis 

- We can see for y = mx + b there is only room for one possible feature x.
- OLS will allow us to directly solve for the slope m and intercept b.
- We will later see we'll need tools like gradient descent to scale this to multiple features.
- Linear Regression allows us to build a relationship between multiple features to estimate a target output

![img](https://cdn-images-1.medium.com/max/1000/1*kd9L3AtD4EQFm1SYpekI0w.png)

We can translate this data into generalized mathematical notation

![img](https://cdn-images-1.medium.com/max/1000/1*c1-JedSJmIKBSleYpoKUwA.png)

![img](https://cdn-images-1.medium.com/max/1000/1*Cbx1nP8q3LyUBpBMIJVAGg.png)

![img](https://cdn-images-1.medium.com/max/1000/1*RBU7K4_rAqX8EBycAXTslQ.png)

![img](https://cdn-images-1.medium.com/max/1000/1*J8Kj543wHzGCyaQEDR4W3w.png)

Now let's build out a linear relationship between the features X and label y

![img](https://cdn-images-1.medium.com/max/1000/1*GF7pD3NcwZfl1YMiCNALpg.png )

Reformat for y = x equation

![img](https://cdn-images-1.medium.com/max/1000/1*xbBfyv2f0jsdzZW2EM8aCA.png)

Each feature should have some Beta Coefficient associated with it = y = mx + b

This is stating there is some Beta Coefficient for each feature to minimize error

![img](https://cdn-images-1.medium.com/max/1000/1*M4qq0dHSJ6dEUdITZEhX_Q.png)

We can also express this equation as a sum:

![img](https://cdn-images-1.medium.com/max/1000/1*K29FWklHC7vh-Qd8SqaGMQ.png)

Note the y hat symbol displays a prediction. There is usually no set of Betas to create a perfect fit to y!

![img](https://cdn-images-1.medium.com/max/1000/1*9GksZPid0KYev81Ka4mwIw.png)

Line Equation

![img](https://cdn-images-1.medium.com/max/1000/1*qfI6j3CkZV4U_bED80x-tg.png)



For simple problem with one X feature we can easily solve for Betas values with an analytical solution.

### Recall

Recall that the equation of a line follows the form `y = mx + b` where

- `m` is the slope of the line, and
- `b` is where the line crosses the `y-axis` when `x = 0` ( `b` is the `y-intercept`)

![img](https://cdn-images-1.medium.com/max/1000/1*-pV-XD7PqHpzvigXY59frA.png)

- In a linear regression, where we try to formulate the relationship between variables, `y = mx + b` becomes

  ![img](https://cdn-images-1.medium.com/max/1000/1*jb78Y7C_7EWDELmha7TCBA.png)

- Our goal is to predict the value of a `dependent variable (y)` based on that of an `independent variable (x).`

How to derive `b1` and `b0`:

두 개의 변수가 있을때, 두 개의 변수가 서로 상관있는지 없는지를 확인하는 방법

https://en.wikipedia.org/wiki/Pearson_correlation_coefficient

| ![r](https://www.gstatic.com/education/formulas2/355397047/en/correlation_coefficient_formula_correlation_coefficient_formula_var_1.svg) | =    | correlation coefficient              |
| ------------------------------------------------------------ | ---- | ------------------------------------ |
| ![x_{i}](https://www.gstatic.com/education/formulas2/355397047/en/correlation_coefficient_formula_correlation_coefficient_formula_var_2.svg) | =    | values of the x-variable in a sample |
| ![\bar{x}](https://www.gstatic.com/education/formulas2/355397047/en/correlation_coefficient_formula_correlation_coefficient_formula_var_3.svg) | =    | mean of the values of the x-variable |
| ![y_{i}](https://www.gstatic.com/education/formulas2/355397047/en/correlation_coefficient_formula_correlation_coefficient_formula_var_4.svg) | =    | values of the y-variable in a sample |
| ![\bar{y}](https://www.gstatic.com/education/formulas2/355397047/en/correlation_coefficient_formula_correlation_coefficient_formula_var_5.svg) | =    | mean of the values of the y-variable |

![img](https://cdn-images-1.medium.com/max/1000/1*JpPRKHdslZyaVf3Fa_QaIw.png)

![img](https://cdn-images-1.medium.com/max/1000/1*kBsDtOn1cTVCvLprPkgjJQ.png)

![img](https://cdn-images-1.medium.com/max/1000/1*ioWOuKyUWb9elD_gqiG4uQ.png)

## Limitations of Linear Regression

- Anscombe's Quartet illustrates the pitfalls of relying on pure calculation.

- Each graph results in the same calculated regression line.

![img](https://cdn-images-1.medium.com/max/1000/1*8nHJYWVcXk58rASN3o6ltA.png)

- A manager wants to find the relationship between the number of hours that a plant is operational in a week and weekly production.
- Here is the `independent variable x` is `hours of operation`
- `dependent variable y` is `production volume`

The manager develops the following table - Plot the data - Is there a linear patter?

![img](https://cdn-images-1.medium.com/max/1000/1*3qMdfbLdCoxNax61EEF00w.png)

![img](https://cdn-images-1.medium.com/max/1000/1*c8SUL7gd88C9npICIRd2mA.png)



![img](https://cdn-images-1.medium.com/max/1000/1*YWd19AIGx1iVTh_xTFFO2A.png)

![img](https://cdn-images-1.medium.com/max/1000/1*DGbn6xhqRJOSJBcHWaUtzw.png)



![img](https://cdn-images-1.medium.com/max/1000/1*gD4SLK4cZGiQNFdiJU1ipg.png)

Based on the formula, if the manager want to produce 125 unites per week, the plant should run for:

![img](https://cdn-images-1.medium.com/max/1000/1*VXnfOBzfn9ExWdk2uE6dfw.png)

As we expand to more than a single feature, however, an analytical solution quickly becomes unscable.

Instead we shift focus on minizing a cost function with gradient descent.

We can use gradient descent to solve a cost function to calculate Beta values!

![img](https://cdn-images-1.medium.com/max/1000/1*YJexlv9MLevZpVsdUODPDA.png)



























