Quick Sort
==========
* 분할 정복 알고리즘의 하나. 평균적으로 매우 빠른 시간 복잡도를 갖는다.
* 합병 정렬과 달리, 리스트를 비균등하게 분할한다.
* 과정
* 1) 리스트의 한 요소를 선택한다. 이 요소를 Pivot으로 지정한다.
* 2) Pivot을 기준으로 Pivot보다 작은 요소들을 왼쪽, 큰 요소들을 오른쪽에 정렬한다.
* 3) Pivot을 기준으로 왼쪽 / 오른쪽 요소들을 다시 정렬한다.(재귀를 통하여 정렬한다.)

분할 정복의 과정
============
1) 가장 첫 원소를 Pivot으로 지정한다.
2) 두번째 원소와 마지막 원소를 각각 low / high로 지정한다.
3) low의 index는 +1 / high의 index는 -1씩 증가하며, 두 값을 Pivot과 비교한다.
4) low > Pivot 이고 high < Pivot이면 low와 high를 Swap한다.
5) low와 high의 index가 서로 교차된다면 분할이 끝난다.
6) low와 Pivot의 index를 서로 교환한다.
7) 1~6 과정을 반복한다.

```java
public class QuickSort {
    public static int[] data = {1, 10, 5, 8, 7, 6, 4, 3, 2, 9};
    public static int number = data.length;

    public static void show(){
        for(int i = 0; i < data.length; i++){
            System.out.println(data[i]);
        }
    }

    public static void quickSort(int start, int end){
        if(start >= end) return;

        int key = start;
        int i = start + 1, j = end, tmp;
        while(i <= j){
            while(i <= end && data[i] <= data[key]){
                i++;
            }
            while(j > start && data[j] >= data[key]){
                j--;
            }
            if(i > j){
                tmp = data[j];
                data[j] = data[key];
                data[key] = tmp;
            } else {
                tmp = data[i];
                data[i] = data[j];
                data[j] = tmp;
            }
        }
        quickSort(start, j - 1);
        quickSort(j + 1, end);
    }

    public static void main(String[] args) {
        quickSort(0, number - 1);
        show();
    }
}

```
