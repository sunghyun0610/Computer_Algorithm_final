💻Computer Algorithm final-term assingment💻
<br> by 201901671 문성현
===========================================

# Topic : 거리에 따른 스테픈 커리의 슛 성공률 변화를 매달 주기로 알아보고 회기식을 통해 오차를 최소화되게 다음달 예측.
/*회귀식이란? Y=f(x)에서 한쪽의 변수에서 다른쪽의 변수 값을 예측하기 위한 방정식을 회귀식이라 하고 Y를 종속변수, X를 독립 변수라고 한다.*/
![Alt text](https://github.com/sunghyun0610/Computer_Algorithm_Final/blob/main/%ED%9A%8C%EA%B7%80%EC%8B%9D%20%EA%B7%B8%EB%9E%98%ED%94%84%20%EC%98%88.png?raw=true)
## List
- **1.최적해(유전)알고리즘 원리 및 설명**
    - *1-1. P&Np(NP-hard)문제 소개*
    - *1-2. 용어 정리(사전지식) 및 유전알고리즘 원리 설명*
    - *1-3. 유전 알고리즘을 이용해 주제(topic)의 최적해 구하기*
- **2.유전(Genetic) 알고리즘으로 주제 구현(C++) 및 동작방식 설명**
- **3.코드 결과 및 성능 분석**
- **4.개선점과 하면서 새로 배우고 느낀 점**

## 1-1 **P&NP(NP-hard)문제 소개**
#### - P 문제는 결정 문제들 중에서 쉽게 풀리는 것을 모아 놓은 집합이다. 어떤 결정 문제가 주어졌을 때, 다항식(Polynomial) 시간 이내에 그 문제의 답을 YES와 NO 중의 하나로 계산해낼 수 있는 알고리즘이 존재하는 문제이다.     

#### -수업시간에 다루었던 **NP**(Non-deterministic Polynomial) 문제는 형식적으로는, 문제를 푸는 각 단계에서 여러가지의 가능성을 동시에 고려할 수 있는 비결정적 알고리즘(non-deterministic algorithm)으로 다항시간내에 문제를 해결할 수 있는 문제라고 정의한다. 즉,어떤 결정 문제의 답이 YES일 때, "그 문제의 답이 YES라는 것을 입증하는 힌트가 주어지면, 그 힌트를 사용해서 그 문제의 답이 정말로 YES라는 것을 다항식 시간 이내에 확인할 수 있는 문제가 바로 NP 문제에 해당된다."</br>
![Alt text](https://upload.wikimedia.org/wikipedia/commons/4/4a/Complexity_classes.png)
#### 사실 많은 컴퓨터공학자들은 절대로 P=NP일리가 없다고 믿고 있다. 왜냐하면, P=NP가 의미하는 바는, 만약 어떤 문제가 주어졌을 때, 그 문제의 답안을 쉽게 검산할 수 있다면, 그 문제 자체도 쉽게 풀 수 있다는, 너무나도 강력한 주장이기 때문이라고 수업시간에 배웠다.</br>


## 1-2. **용어 정리(사전지식) 및 유전알고리즘 원리 설명**
#### 유전 알고리즘은 생물체가 환경에 적응하면서 진화해가는 모습을 모방하여 ~~최적해~~를 찾아내는 검색 방법이다. 유전 알고리즘은 이론적으로 전역 최적점을 찾을 수 있으며, 수학적으로 명확하게 정의되지 않은 문제에도 적용할 수 있기 때문에 매우 유용하게 이용된다. 일반적으로 유전 알고리즘에 대해 알고리즘이라는 표현을 이용하지만, 유전 알고리즘은 특정한 문제를 풀기 위한 알고리즘이라기 보다는 **최적화 문제를 풀기 위한 방법론**에 가깝다. 즉, 모든 문제에 적용 가능한 하나의 알고리즘이나 소스 코드가 있는 것이 아니기 때문에 유전 알고리즘의 원리를 이해하고, 이를 자신이 원하는 문제에 적용할 수 있도록 하는 것이 중요하다고 생각한다.
### 용어정리
- **염색체(chromosome)**: 유전 알고리즘에서 하나의 해 (solution)를 표현한다. 즉 어떠한 문제의 해를 염색체로 치환한 것이다.
- **유전자(gene)**: 염색체를 구성하는 요소로써, 하나의 유전 정보를 나타낸다. 어떠한 염색체가 [A B C]라면, 이 염색체에는 각각 A, B 그리고 C의 값을 갖는 3개의 gene이 존재한다.
- **자손 (offspring)**: 특정 시간 t에 존재했던 염색체들로부터 생성된 염색체를 t에 존재했던 염색체들의 자손이라고 한다. 자손은 이전 세대와 비슷한 유전 정보를 갖는다.
- **적합도 (fitness)**: 어떠한 염색체가 갖고 있는 고유값으로써, 해당 문제에 대해 염색체가 표현하는 해가 얼마나 적합한지를 나타낸다.