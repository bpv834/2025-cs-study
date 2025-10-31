# Sort (정렬 알고리즘)

## 1. 버블 정렬 (Bubble Sort)

🔹 개념 요약

버블 정렬(Bubble Sort) 은 서로 인접한 두 원소를 비교하여 정렬하는 가장 기본적인 정렬 알고리즘입니다.

인접한 2개의 원소를 비교하여 순서가 잘못된 경우 교환(Swap)

한 번의 패스를 수행할 때마다 가장 큰 원소가 뒤로 이동

정렬이 1회전 끝날 때마다 비교 대상이 하나씩 줄어듦

```

public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = new int[]{4,2,3,1};

        System.out.println("초기 상태");
        System.out.println(Arrays.toString(arr));
        System.out.println();

        for(int i=1; i<4;i++){
            for(int j=0; j<3; j++){
                if(arr[j]> arr[j+1]){
                    int tmp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = tmp;
                }
                System.out.println(Arrays.toString(arr));
            }
            System.out.println(i+"라운드 종료 후" +Arrays.toString(arr));
        }
    }

}

```

<img width="206" height="332" alt="image" src="https://github.com/user-attachments/assets/1271cd27-ec7f-442d-b228-94a9fcf7a0cb" />


 버블 정렬의 특징
✅ 장점

구현이 매우 간단하다.

직관적으로 이해하기 쉽다.

❌ 단점

**불필요한 교환(Swap)**이 많음
→ 이미 정렬된 상태에서도 계속 비교가 일어남

하나의 요소가 맨 끝까지 가기 위해 모든 요소와 비교 및 교환 필요

교환(Swap) 연산이 많아 비효율적

💬 실제 사용은 거의 없고, 정렬 원리 학습용으로 주로 사용됨.

비교 횟수
최상, 평균, 최악 모두 일정
n-1, n-2, … , 2, 1 번 = n(n-1)/2
교환 횟수
입력 자료가 역순으로 정렬되어 있는 최악의 경우, 한 번 교환하기 위하여 3번의 이동(SWAP 함수의 작업)이 필요하므로 (비교 횟수 * 3) 번 = 3n(n-1)/2
입력 자료가 이미 정렬되어 있는 최상의 경우, 자료의 이동이 발생하지 않는다.
T(n) = O(n^2)

예외:
이미 정렬돼있는 상태에서 정렬할 경우 1라운드 1회만에 정렬을 종료시킨다면 최상 비교가 n번만에 가능하도록 할수도 있다.
```
 int[] arr = new int[]{1,2,3,4,5,6,7,8,9,10};
        boolean isSort = true;

        int circleCnt=1;

        for(int i=1; i<10;i++){

            for(int j=0; j<9; j++){
                circleCnt++;
                if(arr[j]> arr[j+1]){
                    int tmp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = tmp;
                    isSort = false;
                }
                System.out.println(Arrays.toString(arr));
            }
            if(isSort) break;
            System.out.println(i+"라운드 종료 후" +Arrays.toString(arr));
        }
        System.out.println("회전수 = "+circleCnt);

출력 :
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
회전수 = 10
```


## 2. 선택 정렬 (Selection Sort)
## 3. 삽입 정렬 (Insertion Sort)
## 4. 병합 정렬 (Merge Sort)
## 5. 퀵 정렬 (Quick Sort)
## 6. 힙 정렬 (Heap Sort)
