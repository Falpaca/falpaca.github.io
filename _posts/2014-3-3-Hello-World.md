202101627 이준한 컴퓨터알고리즘 기말과제
=============




<br/><br/>
수학적 모형 가정
-------------

<br/> <br/>
**회귀분석에 대하여** <br/><br/>

회귀분석은 변수 간의 인과관계를 알아보기 위한 분석방법의 하나로, 1개 또는 그 이상의 독립변수와 종속변수 
사이의 관계를 수학적인 함수식을 이용하여 규명하고자 하는 분석법으로, **독립변수의 변화에 따른 종속변수의 변화를 예측하는 데에 사용된다.

<img src="https://www.tibco.com/sites/tibco/files/media_entity/2020-09/regression-analysis-diagram.svg" width="500" height="300"/>
간단히 말하면, 두 변수 관의 상관관계를 기본으로 하여 하나의 1차 선형식으로 두 변인의 관계를 일반화하는 분석법이다. 
용어 설명을 간단히 하자면, <br/>

* 회귀 : 평균으로의 회귀현상. 두 변수의 관계가 어떤 일반화된 선형관계의 평균으로 돌아간다는 의미이다.
* 선형성 : 두 변수의 관계가 하나의 직선의 형태로 설명될 수 있는 관계를 지닌다는 것
* 선형관계의 중심 : 예측치와 관측치의 차이의 제곱((X1 - X2)^2)의 합이 최소가 되는 직선
* 회귀의 개념 : 독립변수의 종속변수 간의 1차 선형적 관계를 도출하여 독립 변수가 종속변수에 미치는 영향, 혹은 예측 정도를 분석하는 방법.
* 독립변수와 회귀변수 : 예시를 들자면 키에 따른 몸무게를 구하는 과정에서, 몸무게 = a + b * 키 이므로, 키에 따라 몸무게가 결정되므로 키는 독립변수, 몸무게는 종속변수라고 할 수 있다.  
<img src="https://t1.daumcdn.net/cfile/tistory/99E4663F5B7918E612" width="450" height="200"/>


**회귀분석의 과정** <br/><br/>
회귀분석의 종류 중에 단순회귀분석에 대해 자세히 알아보도록 하겠다. 
단순회귀분석의 기본적인 회귀모형은<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/2b0e945b562aea6898c39936716ae5b56513a38e" width="170" height="20"/>이다.
여기서 추정 회귀식은<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/32ec6013c4d398481c083f9cdad6fe6614bf6caa" width="170" height="20"/>이 된다. 
다음으로 알아야 할 것은 단순회귀분석의 전제조건이다. 
이는 크게 6가지로 구분할 수 있는데, <br/>
* 독립변수는 연속형이어야한다.<br/>
* 종속변수는 연속형이어야 한다.<br/>
* 오차항은 정규분포를 가진다.<br/>
* 오차항은 등분산을 가진다.<br/>
* 오차항은 독립적이다.<br/>
* 오차항은 특이치가 존재하지 않는다.<br/>

다음으로는 회귀 계수를 추정해야 하는데, 회귀 계수를 추정하는 방법 중 하나인 최소제곱법에 대해 알아보자면, 
<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/d259b4f42e0c48051b95df8c7c7df71cef48a3b9" width="200" height="30"/>을 각각 <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/eeeccd8b585b819e38f9c1fe5e9816a3ea01804c" width="40" height="40"/>
와 <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/40b42f71f244103a8fca3c76885c7580a92831c8" width="40" height="20"/>
로 편미분하여 각각 0과 같다고 놓은 뒤, <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/bd95a14efde69b526482b717c7b4f38ee28c896a" width="170" height="20"/>
 <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/4a346e54a13c06dcb2dcaca30bf3c7c6eb3dc656" width="170" height="20"/>
의 식이 나오는데, 이를 정리하면  <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/3a75b576068fab475b860cc25230c92d9a642d52" width="170" height="20"/>
<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/bdd97e1c0d105944dcd89b17958c58450e3e54fa" width="200" height="40"/>
이 된다. 이를 그림으로 조금 더 쉽게 표현하자면<br/>
<img src="https://thebook.io/img/080263/084.jpg" width="400" height="250"/>
<img src="https://blog.kakaocdn.net/dn/b8qv2o/btq08vUhOj1/rOshLzbACnd6OYvEbdAkEK/img.png" width="400" height="250"/> <br/>
이 된다. 
이때 구한 회귀계수들은 선형성을 가지고, 불편추정량이며, 최소 분산성을 가진다. <br/><br/><br/>

**C++을 이용한 1차 선형 회귀 구현** <br/><br/>

1차 선형 회귀는 두 개의 변수에 대해 최대한 일치하는, 근접하는 y = ax + b를 찾는 과정이라고 볼 수 있다. 
c++로 구현할 때에 경사하강법을 사용하여 구현하도록 하겠다. 
경사 하강법은 1차 근삿값 발견용 최적화 알고리즘으로, 함수의 기울기를 구하고 경사의 반대 방향으로 계속 이동시켜 극값에 이를 때까지 반복시키는 것이다.
각 변수의 데이터 값을 점으로 생각한다면, 점과 점 사이 직선의 길이를 구하므로서 점 사이의 거리를 구할 수 있는데, 이때 거리가 최소가 되는 
직선의 a, b값을 도출한다면 1차 선형회귀를 얻을 수 있다. 이는
```c++
float dis(float x, float y, float a, float b) {
   return abs(a * x - y + b) / sqrt(a * a + 1);
}
```
와 같이 표현 가능하고, 경사 하강법을 이용해야 하므로 
```c++
float  f(float a, float b) {
   sum = 0.0;
   for (int i = 0; i < N; i++) {
      sum += dis(datax[i], datay[i], a, b) / N;
   }
   return sum;
}
```
N은 데이터의 개수, datax, datay는 각각 x, y좌표, a, b는 y=ax+b에서의 해당 값이다.
경사하강법에는 미분이 필요하므로 a, b에 대한 미분 함수가 필요하다. 
```c++
float dfabda(float a, float b, float da) {
   return (f(a + da, b) - f(a, b)) / da;
}
float dfabdb(float a, float b, float db) {
   return (f(a, b + db) - f(a, b)) / db;
}
```
미분 함수가 만들어졌으므로 이제 코드를 완성시키면, 
```c++
int main() {
   ifstream out("simple.txt");
   out >> N;
   cout << N << endl;
   datax = new float[N];
   datay = new float[N];
   for (int i = 0; i < N; i++) {
      out >> datax[i] >> datay[i];
      cout << datax[i] << "   " << datay[i] << endl;
   }
   float a0 = 0, b0 = 0;
   int iteration = 0;
   float eta = 0.0001;
   float psi = 0.005;
   float da = 0.01;
   float db = 0.01;
   float a1 = 3, b1 = 10;
   while (EE(a0, b0, a1, b1) > eta && iteration < 1000000) {
      a0 = a1;
      b0 = b1;
      a1 -=   psi * dfabda(a0, b0, da);
      b1 -=   psi * dfabdb(a0, b0, db);
      iteration++;
   }
   cout << " y  = " << a1 << "x + " << b1 << endl;
   cout << iteration << "-th  E = " << EE(a0, b0, a1, b1) << endl;
   return 0;
}
```
이 코드를 실행시킬 때 사용할, 회귀시킬 데이터는 <br/>

**20   <br/>0  0 <br/>1  1 <br/>2  2 <br/>3  3 <br/>4  4 <br/>5  5 <br/>6  6 <br/>7  7 <br/>8  8 <br/>
9  9 <br/>10 10<br/>11 11 <br/>12 12 <br/>13 13 <br/>14 14 <br/>15 15 <br/>16 16 <br/>17 17 <br/>18 18 <br/>19 19 <br/>**
로 한다. 위의 데이터로 본다면 코드 실행의 결과는 x=y에 가깝게 나와야 만족스럽다고 할 수 있는데, 
실행시킨다면 <br/>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb1xlRn%2FbtqKyknGzXR%2FKzoYHNo7nZo2EaZgmHyY41%2Fimg.png" width="600" height="300"/> <br/>
y = 0.989152x -0.00591446으로 x = y에 근사하게 도출되었으므로 만족스럽다고 할 수 있다. <br/>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FBiomA%2FbtqKYmRfxCU%2Farbci2QvkgvVjLufHa83Yk%2Fimg.png" width="400" height="400"/> <br/>
그래프에서도 두 선이 거의 일치하는 것을 볼 수 있다. <br/> <br/> <br/>


유전 알고리즘(최적화 알고리즘)
-------------
<br/>
유전 알고리즘은 미국 최초의 컴퓨터 과학 박사학위 취득자이자 심리학자이자 전기공학자이자 컴퓨터과학자인 John Holland가 1975년, 본인의 저서인
"Adaption on Natural and Artificial Systems"서 소개한 최적화 기법이자, 
생물의 진화과정인 자연 선택과 유전법칙을 모방한 확률적 탐색기법이다. <br/>
진화에서 모티브를 따왔으므로 문제에 대한 가능한 해들은 유전자, 이를 세대가 지날수록 변형, 발전시켜 더 만족스러운 해를 만드는 행위는
진화라고 볼 수 있다. 
그 말은 아까 위에서 했었던 1차 선형 회귀와 비슷하게 어떤 함수 y = f(x)에 대해 가장 만족스러운 x값을 찾기 위한 알고리즘이라고도 설명할 수 있다. 
유전 알고리즘의 순서와 구성을 간단하게 알아보자면, <br/>

* 초기화(시작) <br/>
<img src="https://miro.medium.com/max/1400/1*BUKcLRQEt0hPfYQP2AqBAw.png" width="450" height="200"/><br/>
유전 알고리즘은 각 개체들이 모인 집단에서부터 시작하는데, 각 개체는 노드로 표현하였다.
<br/>

* 적합도 계산 <br/>
<img src="https://miro.medium.com/max/1400/1*PxtWfpKXI9XoGbM3M2EO_w.png" width="450" height="200"/> <br/>
적합도 계산, 측 fitness계산에서는 각각의 개체(노드)들이 주어진 환경에 적응하는 정도를 나타낸다. 
<br/>

* 선택 <br/>
<img src="https://miro.medium.com/max/1400/1*lfLF4d_Xx4SpX23m4BXzng.png" width="450" height="200"/> <br/>
계산한 적합도에 따라 개체들 중 상위 n%를 선별한다. 선별은 자연 선택의 논리로 적사생존으로 하여 n%에 들지 못한 개체들은 제거한다. 
<br/>

* 유전 <br/>
<img src="https://miro.medium.com/max/1400/1*zu5qatttFEKdLvXrLVT_EA.png" width="450" height="200"/> <br/>
선택되어 살아남은 개체들은 서로 유전 연산을 통해 후손을 생성한다. 이 유전 연산은 크게 두 종류가 있는데, 교배와 돌연변이이다. <br/>

* 교배 <br/>
<img src="https://miro.medium.com/max/1400/1*QANM6p076ETglfWEVgO-8g.png" width="450" height="200"/> <br/>
자연에서는 어머니의 DNA 염색체와 아버지의 DNA 염색체가 한 가닥씩 꼬여 자식의 염색체가 생성되는데, 유전 알고리즘도 이와 유사하게 <br/>
<img src="https://miro.medium.com/max/1400/1*6ON769JvXouNAUcN-H6Fkw.png" width="450" height="200"/> <br/>
이런 식으로 0과 1을 교차하여 자식 노드를 생성한다. <br/>

* 돌연변이 <br/>
생물이 진화할 수 있는 이유는 바로 돌연변이 때문이다. 돌연변이 형질이 항상 개체의 생존에 긍정적인 영향을 주지는 않지만, 돌연변이 현상이
발생하고 돌연변이로 인해 나타난 형질이 본래 형질보다 생존애 유리하다면, 돌연변이 개체들은 자연 선택을 당해 주어진 환경에 적응하고 진화하면서 살아남았다. 자연에서는 <br/>
<img src="https://knun.net/data/photos/20121145/art_1352544000.jpg" width="450" height="200"/> <br/>
이런 식으로 염색체에 구조 이상이 발생하여 돌연변이가 일어나게 되는데, <br/>
코드로 구현하기에는 <br/>
<img src="https://miro.medium.com/max/1400/1*A8pQfkeJ_-vuLwvXc_gLUA.png" width="450" height="200"/> <br/>
가 가장 용이하다고 볼 수 있다. <br/>


**코드 구현(파이썬)**
<br/>

자료 조사 결과 유전 알고리즘을 구현하는 것은 C언어나 JAVA보다 Python이나 perl같은 동적 언어가 더 우수하다는 사실을 알아냈으므로, 
그나마 익숙한 python을 이용하여 알고리즘을 짜도록 하겠다. <br/>
Python 은 동적 타입(dynamic type)언어이므로 절차형 프로그래밍과 함수형 프로그래밍, 객체지향 프로그래밍이 모두 가능하다. 
지금 할 유전 알고리즘의 경우 리스트 처리가 많기 때문에 python이 적합하다고 볼 수 있다. <br/>

알고리즘을 어떻게 표현할지 정해보자면, <br/>
위에 설명했던 것 그래도 작동되는 코드를 작성하기에는 다소 무리가 있다고 느껴져, 적자생존이 아닌 우성 유전자가 우선적으로 교배되게 코드를 작성하도록 하겠다. 
우선 하나의 염색체에 0~9사이의 값을 가진 유전자 10개를 배정하고, 그 중 가장 유리한 우성 유전자를 1로 두고 진화하도록 하게 한다.<br/>

```
if gene > dominant:
   approximate_vlaue += gene - dominant
else:
    approximate_vlaue += dominant - gene
```
<br/>
우성 유전자와의 크기 차이가 가장 작은 염색체에게 가장 높은 점수를 주고, 높은 점수를 받은 염색체 두개가 각각 부모가 되어 자손을 만들었다. <br/>
<br/> 
완성된 코드를 보자면
<br/>
```python
import random
import numpy
import copy

def approximate(chromosome):
    approximate_value = [0 for __ in range(5)]
    
    dominant = 1 #우성 유전자의 값을 1로 선언

    for i in range(5):
        m_sum = 0
        for j in range(10):
            if chromosome[i][j] > dominant:
                m_sum += chromosome[i][j] - dominant
            else:
                m_sum += dominant - chromosome[i][j]
        approximate_value[i] = m_sum
    
    return approximate_value

if __name__ == '__main__':
    chromosome     = [[0 for __ in range(10)] for __ in range(5)]
    new_chromosome = copy.deepcopy(chromosome)

    mutation = 0.01 #돌연변이가 발생할 확률을 0.01로 선언
    
    parent_chromosome_index = [0, 0]
    generation = 0

    #첫번째 세대 지정
    for i in range(5):
        for j in range(10):
            chromosome[i][j] = random.randint(0, 9)

    generation += 1

    while True:
        if generation > 500: #실험의 최대 횟수를 제한
            break

        approximate_value = approximate(chromosome)
        
        for i in range(2):
            parent_chromosome_index[i] = numpy.argsort(approximate_value)[i]

        done = False
        for i in range(5):
            if approximate_value[i] == 0:
                done = True
                break
        if done == True:
            break

        #돌연변이 발생 및 유전자 교차 
        for i in range(5):
            for j in range(10):
                if random.random() < mutation:
                    new_chromosome[i][j] = random.randint(0, 9)
                else:
                    new_chromosome[i][j] = chromosome[parent_chromosome_index[random.randint(0, 1)]][j]

        chromosome = copy.deepcopy(new_chromosome)

        #결과 출력
        print("=============================")
        print(generation, "Gen | ", chromosome)
        print('approximate value |', approximate_value)
        print('selected parent |', parent_chromosome_index)

        generation += 1 
        
    print("simulation complete")
```




자연에서 돌연변이의 발생 확률은 대략 천만분의 1 ~ 1억분의 1이라고 한다. 
이를 그대로 이 코드에 mutation = 0.00000001로 두고 실행한다면 1000세대까지 시뮬레이션을 돌려도 <br/>
```
1000 Gen |  [[5, 2, 2, 3, 1, 1, 4, 1, 0, 7], [5, 2, 2, 3, 1, 1, 4, 1, 0, 7], [5, 2, 2, 3, 1, 1, 4, 1, 0, 7], [5, 2, 2, 3, 1, 1, 4, 1, 0, 7], [5, 2, 2, 3, 1, 1, 4, 1, 0, 7]] <br/>
evalution value | [18, 18, 18, 18, 18] 
selected parent | [0, 1]
simulation complete 
```
<br/>
이런 식으로 목표 우성인자인 1 값에 한참 벗어나는 평균치를 가지게 된다. 따라서 원활한 진행을 위해 mutation = 0.01로 두고 진행한다면, <br/>

```
500 Gen |  [[0, 1, 1, 1, 1, 1, 1, 1, 1, 1], [0, 1, 1, 1, 1, 1, 1, 1, 1, 1], [0, 1, 1, 1, 1, 1, 1, 1, 1, 5], [0, 1, 1, 1, 1, 1, 1, 1, 1, 1], [0, 1, 1, 1, 1, 1, 1, 1, 1, 1]]
evalution value | [1, 1, 1, 1, 1]
selected parent | [0, 1]
simulation complete
```
1000세대의 절반인 500세대까지밖에 진행하지 않았음에도 목표치에 많이 근접해 있는 모습을 볼 수 있다. <br/>

<br/>
이제 반대로 확률이 너무 높으면 어떻게 될까? <br/>
```
500 Gen |  [[0, 2, 1, 0, 1, 3, 0, 0, 1, 1], [0, 2, 1, 0, 1, 4, 0, 4, 1, 1], [0, 2, 1, 0, 1, 3, 0, 2, 7, 1], [0, 2, 1, 0, 1, 3, 0, 0, 1, 1], [0, 2, 1, 0, 1, 3, 0, 0, 1, 1]]
approximate value | [7, 11, 14, 7, 9]
selected parent | [0, 3]
simulation complete
```
<br/>
신기하게도 돌연변이 확률을 매우 낮게 설정했던 것과 유사하게 오히려 우성인자에서 많이 멀어져 있는 모습을 확인할 수 있었다. <br/>

여기서 좀 더 재미있게 생각해보면, 한 세대를 100년이라 가정하고 인류 역사가 20만년이므로 200000 / 100 = 2000세대라고 하고 mutation = 0.00000001 
로 하고 진행해 보면 어떨까? <br/>

```
2000 Gen |  [[3, 1, 0, 4, 3, 4, 2, 5, 4, 4], [3, 1, 0, 4, 3, 4, 2, 5, 4, 4], [3, 1, 0, 4, 3, 4, 2, 5, 4, 4], [3, 1, 0, 4, 3, 4, 2, 5, 4, 4], [3, 1, 0, 4, 3, 4, 2, 5, 4, 4]]
evalution value | [22, 22, 22, 22, 22]
selected parent | [0, 1]
simulation complete
```
<br/>...아직 인류는 진화가 덜 된 것으로 보인다!! <br/>

**모수 값 추정** 
<br/>
모수라느 모집단의 특성(모평균, 모분산, 모분산 등등등), 즉 데이터를 나타내는 값으로, '사전적 정의는 모집단의 특성치' 라고 한다. 모수를 알려면 모집단을 전수조사 해야 한다. 
모수는 미지의 상수 취급을 하며, 모집단에서 추출한 표본 특성을 분석해 모수에 대해 추측을 하는 것이다. <br/>
이 추론엔 크게 두게의 방법이 있는데, 통계적 추론 방식과 가설 검정이 그 방법이다. <br/>
위에서 실행한 python 유전 알고리즘의 경우 초반 세대에서는 각각의 데이터가 원하는 목표치에서 많이 벗어나 있으므로 모수가 1과는 멀지만, 세대가 거듭할수록 모수는 1에 가까워질 것이다.   
<br/>

**최적화 과정에 대한 분석**
<br/>
처음에 구상한 값들이 문제가 다소 있어 여러번의 개선을 거듭했고 세대를 거듭하면 할수록 데이터는 만족스러운 방향으로 최적화되고 범주에서 벗어나지 않게 획일화되었다. 







<br/><br/><br/><br/>
**출처**
* http://contents.kocw.net/KOCW/document/2014/hanyang/maengseungjin/4.pdf
* https://namu.wiki/w/%EB%AA%A8%EC%88%98
* https://namu.wiki/w/%EC%9C%A0%EC%A0%84%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98
* https://www.koreascience.or.kr/article/CFKO200533239321725.pdf
* https://support.minitab.com/ko-kr/minitab/19/help-and-how-to/statistics/basic-statistics/supporting-topics/data-concepts/what-are-parameters-parameter-estimates-and-sampling-distributions/
* https://twinw.tistory.com/1
* https://sourceforge.net/projects/jenes/
* http://jenes.intelligentia.it/
* https://ezerror.com/ko/java%EC%9D%98-%EC%9C%A0%EC%A0%84-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%EC%97%90-%EB%8C%80%ED%95%9C-%EC%97%AC%ED%96%89-%EC%84%B8%EC%9D%BC%EC%A6%88%EB%A7%A8-%EB%AC%B8%EC%A0%9C
* http://www.aistudy.com/pioneer/Holland.J.htm
* https://ko.wikipedia.org/wiki/%EC%9C%A0%EC%A0%84_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98
* https://hongku.tistory.com/384
* https://koreapy.tistory.com/663
* https://blex.me/@baealex/%ED%8C%8C%EC%9D%B4%EC%8D%ACpython-%EC%9C%A0%EC%A0%84-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B8%B0%EB%B3%B8
* https://jenetics.io/
* https://github.com/namsong/GA/wiki/%EC%9C%A0%EC%A0%84%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%86%8C%EA%B0%9C
* http://www.aistudy.co.kr/biology/genetic/represent_moon.htm
* https://naldo627.github.io/2019/05/05/genetic-algorithm/
* https://www.acmicpc.net/
* https://www.youtube.com/watch?v=c-qePE1GCQY
* https://www.knun.net/news/article.html?no=16114
* https://intrepidgeeks.com/tutorial/c-language-genetic-algorithm-ga
* https://medium.com/%EC%8A%AC%EA%B8%B0%EB%A1%9C%EC%9A%B4-%EA%B0%9C%EB%B0%9C%EC%83%9D%ED%99%9C/basic-genetic-algorithm-%EC%9C%A0%EC%A0%84-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%9E%85%EB%AC%B8-%EC%98%88%EC%A0%9C-332863a6edf9
* https://ko.wikipedia.org/wiki/%EA%B2%BD%EC%82%AC_%ED%95%98%EA%B0%95%EB%B2%95
* https://hsm-edu.tistory.com/1224
* https://m.blog.naver.com/aporia25/221159322718
* https://thebook.io/080263/ch03/01/04-01/
* https://math100.tistory.com/116
* https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=lchry&logNo=220511983820&view=img_10
* https://himbopsa.tistory.com/6
* https://modoocode.com/129


