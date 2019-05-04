# Markov Process


Introduction
-----
Markov process is a stochastic process named after famous mathematicians Andrei Markov, who greatly contributed to the field of random process.
\
Markov Process is a general name for a stochastic process with the Markov Property, which means one should be able to predict the future state solely based on its present state.

Some application of Markov process
- Markov decision process
.
.
.


Deterministic vs Stochastic
-----
**Deterministic process** is a process where the present state ```s``` completely determines the future meaning it has only one possible successor state ``s'`` as no randomness is involved during the process.
\
e.g I drop a bomb in the city, a lot of people die due to the explosion.

**Non-deterministic process** is a process where the present state ```s``` can not completely determine the future state, thus, has a set of possible successive states ```{s1, s2, s3..}```.

**Stochastic process** ,also known as random process, is a process of random variables in which the outcome at any stage depends on some probability due to the involvement of some randomness or uncertainty during hte process.
\
(e.g Bernoulli process, Random walk, Wiener process, Markov process etc)
\
e.g If i buy one Bitcoin at the price of 2,000$ today, we are unsure how worthwhile it would be after 1 year, 2 years.


Markov chain vs Markov process
-----
One method of classification of stochastic process is based on
- Time parameter : Discrete or continuous
- State space : Discrete of continuous 

If the **state space** of stochastic process is **discrete**, whether the time parameter is discrete or continuous, the process is **Markov chains**
\
If the **state space** of stochastic process is **continuous**, whether the time parameter is discrete or continuous, the process is **Markov process**

(Note that there is no definitive agreement in the literature on the use of Markov process and Markov chain)

**Continuous-time Markov chains(CTMC)**
\
**Discrete-time Markov chains(DTMC)**

Each independent increment is a markov process
- Poisson process having the independent increment property is a markov process with time parameter continuous and state space discrete
- Brownian motion process having the independent increment property is a markov process with continuous and continuous state space process


Discrete-Time Markov Chains
-----

Special Discrete-Time Chains
-----

Continuous-Time Markov Chains
-----

Special Continuous-Time Chains
-----





Reference
-----
(TU/e)[https://www.win.tue.nl/~iadan/que/h3.pdf]
(Random Service)[http://www.randomservices.org/random/markov/index.html]















`마르코프 과정은 확률 과정이다`
- 계통 : 수학 - 통계학 - 확률과정 - 마르코프 과정

## 확률 과정
확률론에서,  **확률 과정** (또는 랜덤과정, stochastic process)은 시간의 진행에 대해  **확률**적인 변화를 가지는 구조. 또는 그러한 모델

## 마르코프 과정
어떤 상태로 전이될 확률이 이전 상태에만 의존하는 **확률 과정**

## 마르코프 연쇄
###  정의
마르코프 과정에서 **이산적인 경우**를 고려한 것을 마르코프 연쇄 (markov chain) 라고 한다.

* 특징
	* 각 시행의 결과가 미리 정해진 여러 결과 중 하나가 됨.
	* 각 시행의 결과는 직전의 상태에만 영향을 받음.

### 표현
$MP(X, P)$
$X$ : 유한 상태공간 집합
$P$ : 모든 X 사이의 천이확률

일정 시간간격 마다 반복천이되며 천이확률이 항상 동일하다.
이러한 연쇄를 기술하는 행렬을 **천이확률 행렬** 이라고한다.
![enter image description here](http://www.ktword.co.kr/img_data/4312_1.JPG)
초기 상태벡터와 천이확률에 의해 임의 시각의 상태가 완전히 결정됨.

## 천이확률
`상태 간 천이되는 확률`

각 상태간 천이 확률을 조건부 확률로 나타낼 수 있다.
$P_{ij} = P(X_{n+1}=i | X_n=j)$
j 상태에서 i 상태로 천이될 확률

![enter image description here](https://norman3.github.io/rl/images/ch01_f01.png)
