<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

# Markov Process
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
