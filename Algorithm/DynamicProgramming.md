# Dynamic Programming (DP)

## 개념

동적 계획법(DP, Dynamic Programming)은 큰 문제를 작은 부분 문제로 나누어,
중복되는 부분 문제의 결과를 저장(메모이제이션)하면서 효율적으로 해결하는 알고리즘 설계 기법이다.
즉, 부분 문제의 중복과 최적 부분 구조를 만족할 때 사용 가능하다.

 DP 사용 조건

- Overlapping Subproblems (부분 문제의 중복)
동일한 부분 문제가 여러 번 반복되어 나타남

- Optimal Substructure (최적 부분 구조)
큰 문제의 최적해가 작은 문제의 최적해로부터 구해질 수 있음

## 접근 방법
|    접근법    | 설명                                 | 구현 방식              |
| :-------: | :--------------------------------- | :----------------- |
|  Top-Down | 큰 문제를 작은 문제로 나눠가며 푼다 (재귀 + 메모이제이션) | 재귀 함수 사용, dp[]에 저장 |
| Bottom-Up | 작은 문제부터 차근차근 쌓아 올린다 (반복문 + 테이블)    | 반복문으로 dp[] 채움      |

🔹 Top-Down (재귀 + 메모이제이션)

```
int[] dp = new int[50];

int fib(int n) {
    if (n <= 1) return n;
    if (dp[n] != 0) return dp[n];
    return dp[n] = fib(n - 1) + fib(n - 2);
}

```

🔹 Bottom-Up (반복문 + 테이블)

```
int fib(int n) {
    int[] dp = new int[n + 1];
    dp[0] = 0;
    dp[1] = 1;

    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

```

## DP 문제 접근 순서

1. 문제를 부분 문제로 나눌 수 있는지 확인한다.

2. 점화식을 세운다 (이전 상태 → 현재 상태).

3. 메모이제이션 or 테이블을 이용해 중복 계산을 방지한다.

4. Top-Down(재귀) 또는 Bottom-Up(반복) 방식을 선택한다.

