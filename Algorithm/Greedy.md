#  그리디 알고리즘 (Greedy Algorithm)

##  개념
그리디 알고리즘(Greedy Algorithm)은  
**매 순간 최적의 해(즉, 가장 좋아 보이는 선택)** 을 하는 방식으로 전체 문제의 최적해를 구하는 알고리즘이다.  
**"지금 가장 좋은 선택이 전체적으로도 최선이다"** 라는 직관에 기반한다.

---

## ⚙️ 특징
- 각 단계에서 **가장 최적인 선택(local optimum)** 을 반복적으로 수행.
- 전체적으로 **최적해(global optimum)** 을 보장하지 않을 수도 있음.
- 하지만 문제의 구조가 **탐욕 선택 속성(Greedy Choice Property)** 과 **최적 부분 구조(Optimal Substructure)** 를 만족할 경우, 전체 최적해를 구할 수 있다.

---

## ✅ 장점
- 구현이 간단하고 직관적이다.
- 동적 계획법(DP)보다 빠르고 메모리 사용이 적다.
- 실시간 계산에도 적합하다.

## ⚠️ 단점
- 항상 최적해를 보장하지 않는다.
- 탐욕적 선택이 전체적으로 잘못된 방향일 수 있다.
- 증명 과정이 필요하다 (탐욕 선택 속성과 최적 부분 구조 확인).

---

## 💡 대표 예시

### 1️⃣ 동전 거스름돈 문제

#### 🔹 문제
가장 적은 개수의 동전으로 거스름돈을 주는 문제.  
단, 동전 단위가 특정 조건(큰 단위가 작은 단위의 배수)일 때만 그리디로 최적해 가능.

#### 💻 Java 예제 코드
```java
import java.util.*;

public class CoinChange {
    public static void main(String[] args) {
        int[] coins = {500, 100, 50, 10};
        int money = 1260;
        int count = 0;

        for (int coin : coins) {
            count += money / coin;
            money %= coin;
        }

        System.out.println("필요한 동전 개수: " + count);
    }
}
