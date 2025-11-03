# Backtracking (백트래킹)

📘 개념

**백트래킹(Backtracking)**은 모든 가능한 경우의 수를 탐색하면서, 해가 될 수 없는 경우를 조기에 가지치기(pruning) 하여 탐색 범위를 줄이는 알고리즘 기법이다.
DFS(깊이 우선 탐색)를 기반으로 하며, 주로 조합(combination), 순열(permutation), 부분집합(subset), N-Queen, Sudoku, 경로 탐색 등에서 사용된다.

⚙️ 동작 원리

결정(선택) – 현재 단계에서 가능한 선택지를 하나 고른다.

검사(유망성 판단) – 현재 선택이 조건에 맞는지 검사한다.

가지치기(Pruning) – 조건을 만족하지 않으면 탐색을 중단하고 이전 단계로 되돌아간다.

반복(백트래킹) – 다음 선택으로 넘어가며 탐색을 반복한다.

⚡️ 백트래킹 vs 완전탐색
구분	완전탐색 (Brute Force)	백트래킹 (Backtracking)
탐색 방식	모든 경우의 수 탐색	유망하지 않은 경로는 조기 종료
효율성	비효율적 (모든 경우 탐색)	가지치기로 시간 절약
구현	단순 반복 또는 재귀	DFS + 조건 검사
대표 문제	순열, 조합, 완전탐색	N-Queen, Sudoku, 경로 탐색


💡 핵심 포인트 요약

DFS 기반의 재귀 탐색 + 조건 검사 + 가지치기

모든 경우의 수를 고려하되 불필요한 경로는 빠르게 배제

시간 복잡도는 문제마다 다르지만, Pruning 유무에 따라 큰 차이 발생

백트래킹 예시 문제(양궁)
https://school.programmers.co.kr/learn/courses/30/lessons/92342#

예시 코드
```
import java.util.*;
class Solution {
    static int max = 0;
    static int[] res = new int[11];
    
    public int[] solution(int n, int[] info) {
        dfs(0,n,info,new int[11]);
        if(max == 0) return new int[]{-1};
        return res;
    }
    
    void dfs(int dep ,int arrow, int[] appeach, int[] ryan){
        if(dep == 11){
            // 0점까지 계산해서 활을 쏜이후에도  라이언의 화살이 남은경우 (4번 예시)
            ryan[10] += arrow;
            int gap = getScore(ryan,appeach);
            if(max<gap){
                max= gap;
                res = ryan.clone();
            }else if(max == gap){
                choiceArr(ryan);
            }
            // 남은 화살 추가했던것 빼주기
            ryan[10] -= arrow;
            
        }else{
            // 백트래킹
            // 활을 쏘는경우
            if(arrow>=appeach[dep]+1){
                ryan[dep] = appeach[dep]+1;
                dfs(dep+1,arrow-(appeach[dep]+1),appeach,ryan);
                ryan[dep] = 0;
            }
            // 활을 안쏘는 경우
            dfs(dep+1,arrow,appeach,ryan);
        }
    }
    // 라이언 어피치 점수 차이 구하는 메서드
    int getScore(int[] ryan, int[] appeach){
        int score = 0;
        for(int i=0; i<11; i++){
            if(ryan[i]>appeach[i]) score+= (10-i);
            else{
                if(appeach[i]!=0) score-=(10-i);
            }
        }
        return score;
    }
    // 점수가 같을때 큰점수 구하는 메서드
    void choiceArr(int[] ryan){
        for(int i=10; i>=0; i--){
            if(ryan[i]> res[i]) {
                res = ryan.clone();
                break;
            }else if(res[i]> ryan[i]) break;
        }
    }
}

```
🧩 알고리즘 설명
단계	동작

1️⃣	DFS로 각 과녁(0~10점)을 탐색

2️⃣	각 단계에서 “쏘는 경우”와 “쏘지 않는 경우”를 모두 시도

3️⃣	화살이 남았으면 마지막(0점)에 몰아줌

4️⃣	모든 경우의 수 탐색 후, 어피치와의 점수 차이 계산

5️⃣	최대 점수 차이가 갱신되면 결과 저장

6️⃣	점수 차이가 같을 경우 낮은 점수를 더 많이 맞춘 경우를 선택


🌱 핵심 아이디어

“활을 쏠 수 있는 경우만 탐색하고,

쏘지 못하는 경우엔 화살 수를 그대로 유지하며

마지막에 가능한 정답인지를 판단한다.”

arrow >= appeach[dep] + 1 → 해당 과녁에서 이길 수 있을 때만 “쏘는 경우” 탐색

각 분기마다 ryan[dep] = 0 으로 원상복구 → 백트래킹 핵심

모든 경우를 DFS로 탐색하되, 유효하지 않은 경로는 자연스럽게 제외


⚡️ 특징 요약
항목	내용

알고리즘 유형	DFS + 백트래킹

탐색 구조	완전탐색 기반, 모든 과녁(11개)에 대해 선택/비선택

핵심 로직	활을 쏠 수 있는 상황만 탐색 → 비효율 경로 제거

시간 복잡도	O(2¹¹) (모든 경우의 수 탐색)

가지치기	화살 부족 시 자동 배제

사용 기법	재귀, 배열 복제(clone()), 상태 복원(백트래킹)

출처

https://hongjw1938.tistory.com/88
