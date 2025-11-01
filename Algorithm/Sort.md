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

🔹 개념 요약

선택 정렬(Selection Sort)은 전체 데이터 중에서 가장 작은(또는 큰) 값을 선택하여 앞쪽부터 순서대로 정렬하는 알고리즘입니다.

정렬되지 않은 부분에서 최솟값(또는 최댓값)을 찾아서
현재 위치의 값과 교환(Swap)

한 회전마다 하나의 원소가 정렬 위치에 고정됨

단순하지만 비효율적인 O(n²) 정렬

🔹 동작 원리

주어진 리스트 중에서 최솟값을 찾는다.

최솟값을 맨 앞의 값과 교환한다.

맨 앞의 값은 정렬 완료 상태로 고정

나머지 부분 리스트에 대해 위 과정을 반복한다.

```

public class SelectionSort {
    static int[] nums;

    public static void main(String[] args) {
        nums = new int[5];
        for (int i = 0; i < 5; i++) {
            nums[i] = (int) (Math.random() * 10);
        }
        System.out.println("정렬 전 :");
        System.out.println(Arrays.toString(nums));
        System.out.println();

        for(int i = 0; i < nums.length - 1; i++) {
            // 현재 탐색에서 가장 앞의 원소를 초기 값으로 설정해둔다.
            int MinIndex = i;
            // 탐색을 진행하며, 가장 작은 값을 찾는다.
            for(int j = i + 1; j < nums.length; j++) {
                if(nums[MinIndex] > nums[j])
                    MinIndex = j;
            }
            // 탐색이 완료되면 가장 작은 값을 가장 앞의 원소와 가장 작은 원소의 위치를 바꾸어준다.
            int temp = nums[MinIndex];
            nums[MinIndex] = nums[i];
            nums[i] = temp;
            System.out.println(i+"라운드 정렬 후:");
            System.out.println(Arrays.toString(nums));
        }

        System.out.println("정렬 후:");
        System.out.println(Arrays.toString(nums));
    }
}

```
<img width="134" height="296" alt="image" src="https://github.com/user-attachments/assets/1a20904b-2019-4c5d-9695-bf0c5cd57e9a" />

| 구분               | 시간 복잡도 | 설명                                                  |
| ---------------- | ------ | --------------------------------------------------- |
| **최선 (Best)**    | O(n²)  | 이미 정렬된 상태라도 **모든 원소를 비교**해야 하므로 최선이라도 n(n-1)/2 번 비교 |
| **평균 (Average)** | O(n²)  | 임의 배열에서 비교 횟수와 교환 횟수 모두 평균적으로 n² 수준                 |
| **최악 (Worst)**   | O(n²)  | 역순 배열에서도 **모든 원소를 비교**하고 교환해야 함                     |


🧩 선택 정렬의 특징
✅ 장점

구현이 간단하다.

교환 횟수가 적음 → 최대 n−1번

추가 메모리가 거의 필요 없음 (O(1))

❌ 단점

비교 횟수가 많음 → n(n−1)/2번

이미 정렬된 경우에도 모든 비교를 수행함

안정 정렬이 아님 (동일 값의 상대적 순서가 바뀔 수 있음)

🧩 선택 정렬(Selection Sort)의 불안정성 (Unstable)

선택 정렬은 정렬되지 않은 구간에서 최솟값(또는 최댓값)을 선택하여 현재 위치의 원소와 교환(swap) 하는 방식으로 동작한다.
하지만 이 과정에서 같은 값을 가진 원소들의 상대적인 순서가 바뀔 수 있어 불안정한 정렬 알고리즘이다.

⚙️ 불안정이란?

“불안정한 정렬(Unstable Sort)”이란
→ 같은 키(값) 를 가진 원소들이 정렬 후 원래 순서를 유지하지 못하는 정렬을 의미한다.

반대로, 같은 키를 가진 원소들의 입력 순서가 그대로 유지된다면 그 정렬은 안정적(Stable) 이다.

예시:
Array - <B> <b> <a> <c>    ( a < b < c ), (b == B)(숫자로 나타내면 2 2 1 3 이라고 보면 된다.)
선택 정렬 시 위의 결과는 아래와 같다.
Array - <a> <b> <B> <c>    ( a < b < c )b 와 B는 동일한 수였지만 B가 순서로 보자면 b 보다 앞서 있었다.
하지만 선택 정렬 후 B가 b보다 뒤로 배치되면서 순서가 바뀌었다.이렇게 순서가 유지되지 않는 경우를 불안정 정렬이라함으로써 선택 정렬은 불안정 정렬이 되는 것이다.

해결방법
가장 작은 값이 있는 인덱스에서부터 오른쪽으로 쉬프트하고 앞쪽에 가장작은수를 삽입한다.
```
public class StableSelectionSort {
    public static void main(String[] args) {
        int[] arr = {1, 3, 4, 2};
        int n = arr.length;

        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;

            // i 이후 구간에서 최소값 찾기
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }

            // 최소값 저장
            int minVal = arr[minIndex];

            // 최소값 위치 앞에 있는 원소들을 오른쪽으로 한 칸씩 이동
            for (int k = minIndex; k > i; k--) {
                arr[k] = arr[k - 1];
            }

            // 최소값을 i 위치에 삽입
            arr[i] = minVal;
        }

        System.out.println("정렬 후 배열: " + Arrays.toString(arr));
    }
}
```

## 3. 삽입 정렬 (Insertion Sort)

🔹 개념 요약

삽입 정렬(Insertion Sort)은 두 번째 원소부터 시작하여, 해당 원소를 이미 정렬된 앞부분과 비교하여 올바른 위치에 삽입하며 정렬하는 알고리즘입니다.

현재 원소를 정렬된 부분에 끼워 넣는(Insert) 방식

필요한 경우에만 원소를 뒤로 밀어내어(Shift) 빈 공간을 확보하고 삽입

데이터가 거의 정렬되어 있을수록 효율적인 O(n) 정렬


🔹 동작 원리

주어진 리스트의 **두 번째 원소(index 1)**부터 시작하여 마지막 원소까지 순회한다.

현재 순회 중인 원소를 **'삽입할 값(key)'**으로 지정한다.

key를 정렬된 앞쪽 부분의 원소들과 역순으로 비교한다.

key보다 큰 원소는 key가 들어갈 자리를 만들기 위해 한 칸씩 오른쪽으로 밀어낸다(Shift).

key보다 작거나 같은 원소를 만나거나 배열의 맨 앞에 도달하면 비교를 멈춘다.

비교가 멈춘 위치에 key를 삽입한다.

```
public class InsertionSort {
    public static void main(String[] args) {
        int [] arr = new int[]{4,2,5,1};
        System.out.println("변경 전");
        System.out.println(Arrays.toString(arr));

        for(int i=1; i<arr.length;i++){
            int key = arr[i];
            int j= i-1;
            while(j>=0&& arr[j]>key){
                arr[j+1] = arr[j];
                j--;
            }
            arr[j+1]= key;
            System.out.println(i+"라운드 후 결과");
            System.out.println(Arrays.toString(arr));

        }
        System.out.println("정렬 후");
        System.out.println(Arrays.toString(arr));
    }
}

```
<img width="137" height="225" alt="image" src="https://github.com/user-attachments/assets/db65691b-c8c8-4585-bb04-45c27c95e512" />


| 구분 (Case) | 시간 복잡도 (Time Complexity) | 설명 (Explanation) |
|-------------|------------------------------|------------------|
| 최선 (Best) | O(n)                         | 이미 정렬된 상태인 경우, 비교만 n-1번 수행하고 교환(shift)은 거의 없어 선형 시간에 가까움. |
| 평균 (Average) | O(n²)                        | 무작위 배열에서 비교 및 이동(shift) 횟수가 평균적으로 n²/4에 가까움. |
| 최악 (Worst) | O(n²)                        | 역순으로 정렬된 상태인 경우, 매번 최대 n번의 비교 및 이동이 필요함. |



🧩 삽입 정렬의 특징

✅ 장점데이터가 거의 정렬되어 있을 경우 가장 빠르다 (O(n)).

안정 정렬(Stable Sort)이다. (동일 값의 상대적 순서 유지)구현이 비교적 간단하다.

추가 메모리가 거의 필요 없음 (제자리 정렬, O(1)).

❌ 단점

데이터의 크기가 클 경우 비효율적이다 (O(n²)).

원소들을 밀어내는(shift) 과정 때문에 이동(move) 횟수가 많다.

## 4. 병합 정렬 (Merge Sort)

> **Divide and Conquer (분할 정복)** 알고리즘의 대표적인 예시로,  
> 배열을 반으로 계속 나누고, 각각을 정렬한 후 병합(merge)하는 방식의 정렬 알고리즘입니다.

---

### 📘 알고리즘 개념

1. **분할 (Divide)**  
   배열을 절반으로 계속 나눈다.
2. **정복 (Conquer)**  
   나눈 부분 배열들을 재귀적으로 정렬한다.
3. **병합 (Combine)**  
   정렬된 두 배열을 하나의 정렬된 배열로 합친다.

예시  
[5, 2, 8, 4, 1]
→ [5, 2, 8] + [4, 1]
→ [5] + [2, 8] + [4] + [1]
→ [5] + [2, 8] + [4] + [1]
→ [2, 5, 8] + [1, 4]
→ [1, 2, 4, 5, 8]

```
public class MergeSort {
    public static void mergeSort(int[] arr) {
        if (arr.length <= 1) return; // base case

        int mid = arr.length / 2;
        int[] left = new int[mid];
        int[] right = new int[arr.length - mid];

        // 배열 분할
        for (int i = 0; i < mid; i++) left[i] = arr[i];
        for (int i = mid; i < arr.length; i++) right[i - mid] = arr[i];

        // 재귀 호출로 각각 정렬
        mergeSort(left);
        mergeSort(right);

        // 병합
        merge(arr, left, right);
    }

    private static void merge(int[] arr, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;

        // 두 배열 비교하며 정렬된 상태로 병합
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) arr[k++] = left[i++];
            else arr[k++] = right[j++];
        }

        // 남은 원소들 복사
        while (i < left.length) arr[k++] = left[i++];
        while (j < right.length) arr[k++] = right[j++];
    }

    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 4, 1};
        mergeSort(arr);
        for (int n : arr) System.out.print(n + " ");
    }
}
```



 ⏱️ 시간 복잡도

 | 구분               | 시간 복잡도     | 설명                    |
| ---------------- | ---------- | --------------------- |
| **최선 (Best)**    | O(n log n) | 항상 반씩 나누기 때문          |
| **평균 (Average)** | O(n log n) | 모든 경우 동일한 구조          |
| **최악 (Worst)**   | O(n log n) | 항상 일정한 재귀 깊이          |
| **공간 복잡도**       | O(n)       | 보조 배열(left, right) 사용 |


## 🧩 병합 정렬 (Merge Sort) 특징

| 장점                  | 단점                  |
| ------------------- | ------------------- |
| 항상 O(n log n) 성능    | 추가 메모리 공간 필요 (O(n)) |
| 안정 정렬 (Stable Sort) | 작은 데이터에서는 비효율적      |
| 외부 정렬에 적합 (대용량 데이터) | 구현이 다소 복잡           |




## 5. 퀵 정렬 (Quick Sort)
## 6. 힙 정렬 (Heap Sort)
