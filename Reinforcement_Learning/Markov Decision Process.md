# Markov Decision Process (작성듕..)

*의사결정 과정을 모델링하는 수학적인 틀*
*이산 시간확률 제어 과정(discrete time stochastic control process)*

- 시간에 따라 action 을 선택함에 따라 상태가 천이되고, 그 결과로 얻는 reward 를 최대화 하는 의사결정 최적화 과정.

- MDP 는 환경을 완벽히 기술할 수 있는 환경에서 적용하는 강화학습에 속하는 모델이다.

- 모든 강화학습 문제를 MDP 형태로 표현 가능하다.

- MP 모델과 DP 모델의 융합이라고 볼 수 있다. 확률적인 프로세스를 최적화하는 모델이다.

- bellman equation 을 쓰는 방식과 쓰지 않는 방식, 융합 방식으로 RL 을 풀 수 있다.

## 마르코프 과정의 확장

마르코프 과정에서는 상태천이는 미리 정해진 천이 행렬에 의해 진행되는데, MDP 에서는 action 이 동반된다.

**Action** : 각 상태간 천이 시 발생하는 작업 단위

MP		: $p(s'|s)$
MDP	: $p(s'|s,a)$

MDP 는 현재 상태 s 와 액션 a 에 의해 s' 으로 상태 천이가 이루어진다.

---
그리고 MDP 는 액션을 취할 때 마다 실수값 보상을 얻는다.
상태와 액션에 맵핑되어있는 보상을 아래와 같이 나타낸다.

**Reward** : $X×A(X)→R$

---
**Policy (π)** : 각 시간마다 상태에 맵핑되어 있는 액션의 집합
$π=[{π_t|π_t;X→A(X),t={0,1,...,H−1}}]$

[key (상태), value (액션)] 의 딕셔너리 형태.
MDP 에선 최적의 Policy 를 구하는 것이 목적이다.
즉 최적의 액션을 선택하도록 학습하는 것.

---
### Deterministic Policy

policy 가 결정적인 모델.

$π(x)=a$ 로 정의한다.

---
### Stochastic Policy
policy 가 확률적인 모델.

$π(a|x)=p(A=a|X=x)$ 로 정의한다.
확률적이기 때문에 policy 함수의 출력은 확률함수가 된다.

---
## Dynamic Programming

동적 계획법이라고도 하는데 RL 에서는 확률적 동적계획법 기법이 사용된다. 
재귀적인 계산을 통해 최적화 작업을 수행한다. 
완전탐색 방식과 다르게 최적의 값을 찾는데 시간복잡도를 줄이는데 대신 정보를 저장해놔야해서 공간복잡도는 증가한다.


---
## MDP 의 정의

$\sum_{t=0}^{H-1} \gamma^t R(X_t^{\pi}, \pi_t(X_t^{\pi}))$

위 식은 어떠한 Policy 를 따르는 프로세스에서 각 단계의 상태에서 액션을 수행하며 얻어진 보상의 총합을 계산한다. 
이 보상의 합이 최대가 되는 최적의 policy, 즉 최적화 작업을 하는 것이다.


## Value Function

가치함수는 어떠한 policy 선택해 프로세스를 진행한 후 얻어진 총 보상이다.
가치함수는 각 상태에 대한 보상의 정보를 저장하는 역할을 한다. 즉 상태가 인자인 함수다.
policy 가 정의되었다고 해도 프로세스마다 결과는 다를 수 있는데 이는 상태전이가 확률형태로 되어있는 확률 프로세스이기 때문이다. 
중요한 건 확률 프로세스이므로 매번 결과가 달라질 수 있다. 이를 잘 정의되지 않은 문제 라고 한다. 가치함수가 매번 달라지면 최적화하는데 어려움이 따르므로 해결책이 필요한데, **ELAU**  _(Expected Linear Additive Utility) 방식을 채택한다. 이는 최선의 방법은 아니지만 적절히 좋은 policy 를 구할 수 있다고 한다. 

$utilty(R_1, R_2,...) = E[R_1 + \gamma R_2 + \gamma^2 R_3 + ...]$

감가율을 적용한 기댓값의 형태로 가치함수를 정의하면 적절히 좋은 policy 를 얻을 수있다.

보통 매 순간의 보상을 가장 중요하게 여기므로 감가율은 0 - 1 사이 값을 가지는데, 감가율이 1 이면 시간에 대해 독립적이라고 볼 수 있다.


$V_{H}^{\pi}(x) = E\left[\left(\sum_{t=0}^{H-1} \gamma^t R(X_t^{\pi}, \pi_t(X_t^{\pi}))\right)\;\left|\right.\;X_0^{\pi}=x\right]$

가치함수는 위와 같이 표현할 수 있다. 중요한 건 이 함수도 잘 정의된 함수는 아니라서 수렴하는데 어느정도 불안정성이 있다.

## Optimal Principal
$V_{H}^{\pi}(x) = \bar{R}(X_0^{\pi}, \pi_0(X_0^{\pi})) + \gamma \sum_y p_{xy}^{\pi_0(x)} V_{H-1}^{\pi}(y)$

이 식은 재귀적으로 나타낸 가치함수이다. 이를 DP 처럼 반복적으로 수행하면 수렴할 수 있다. 

## Infinite Horizon Discounted  Reward MDP
- 스텝의 수가 정해져있지 않은 MDP 를 의미한다. 즉 무한대의 스텝이라고 할 수 있지만 적절히 수렴하면 종료한다. 
- 스텝의 수가 정해진 것과 종료 조건이 정해진 것은 엄연히 다른 것이다.



## Value Iteration
bellman optimal equation
$V^*(x) = \max_{a\in A(x)}\left(\bar{R}(x, a) + \gamma\sum_{y\in X}p_{xy}^a V^*(y)\right)$
을 사용해 수렴 후 최적의 액션을 선택하는 방법. 

## Policy Iteration
stationary policy 에서 사용.

1. 임의의 policy 를 정하고 기존의 가치함수를 수렴할 때 까지 반복
2. 일부 액션을 변경하여 가치함수가 더 커지면 업데이트.

## Q - function
action - value function
가치함수가 상태에 종속적인 함수라면 q 함수는 상태와 액션에 종속적인 함수이다.

위의 deterministic, stochastic policy 에서 액션은 확률적으로 선택한다고 했다.

$V^{\pi}(s) = \sum_{a \in A} \pi(a|s)Q^{\pi}(s, a)$

확률적 policy 에서 액션이 확률함수로 주어지기 때문에 위 식처럼 가치함수는 기댓값을 의미하게 된다.

$V^{\pi}(s) = \sum_{a \in A}\pi(a|s)\left(R^a_s + \gamma\sum_{s' \in S} p_{ss'}^{a} V^{\pi}(s')\right)$

가치함수를 다시 쓰면 중요한것이 액션을 확률적으로 선택한다는 것이다.
