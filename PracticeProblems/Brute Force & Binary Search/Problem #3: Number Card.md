### 문제

숫자 카드는 정수 하나가 적혀져 있는 카드이다. 상근이는 숫자 카드 N개를 가지고 있다. 정수 M개가 주어졌을 때, 이 수가 적혀있는 숫자 카드를 상근이가 몇 개 가지고 있는지 구하는 프로그램을 작성하시오.

### 입력

첫째 줄에 상근이가 가지고 있는 숫자 카드의 개수 N(1 ≤ N ≤ 500,000)이 주어진다. 둘째 줄에는 숫자 카드에 적혀있는 정수가 주어진다. 숫자 카드에 적혀있는 수는 -10,000,000보다 크거나 같고, 10,000,000보다 작거나 같다.

셋째 줄에는 M(1 ≤ M ≤ 500,000)이 주어진다. 넷째 줄에는 상근이가 몇 개 가지고 있는 숫자 카드인지 구해야 할 M개의 정수가 주어지며, 이 수는 공백으로 구분되어져 있다. 이 수도 -10,000,000보다 크거나 같고, 10,000,000보다 작거나 같다.

### 출력

첫째 줄에 입력으로 주어진 M개의 수에 대해서, 각 수가 적힌 숫자 카드를 상근이가 몇 개 가지고 있는지를 공백으로 구분해 출력한다.

#### 예제 입력 1 
10

6 3 2 10 10 10 -10 -10 7 3

8

10 9 -5 2 3 4 5 -10

#### 예제 출력 1 
3 0 0 1 2 0 0 2

### Solution
```java
import java.util.*;
import java.io.*;

public class Main{

     public static int binarySearch(int num, int[] arr){
         int left = 0;
         int right = arr.length-1;
         int cnt = 0;
         boolean flag = false;
         
         while(right>=left){
             int mid = (left+right) / 2;
             
             if(arr[mid] == num){
                 flag = true;
             }
             
             if(num>arr[mid]){
                 left = mid + 1;
                 
             }else if(num<arr[mid]){
                 right = mid - 1;
             }
         }
         
         if(flag == true){
             for(int i=0; i<arr.length; i++){
                 if(arr[i]==num){
                     cnt++;
                 }
             }
         }
         
         return cnt;
     }
     
     public static void main(String []args) throws Exception {
         
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		ArrayList<String> list = new ArrayList<>();
		String line = null;
		while((line=br.readLine())!=null){
		    list.add(line);
		}
		int m = Integer.parseInt(list.get(0));
		int[] mArr = new int[m];
		String[] mStr = (list.get(1)).split(" ");
		for(int i=0; i<m; i++){
		    mArr[i] = Integer.parseInt(mStr[i]);
		}
		
		Arrays.sort(mArr);
		
		int n = Integer.parseInt(list.get(2));
		int[] nArr = new int[n];
		String[] nStr = (list.get(3)).split(" ");
		for(int i=0; i<n; i++){
		    nArr[i] = Integer.parseInt(nStr[i]);
		}
		
		int[] answer = new int[n];
		for(int i=0; i<n; i++){
		    answer[i] = binarySearch(nArr[i], mArr);
		    bw.append(answer[i]+" ");
		}
		
		bw.flush();
		bw.close();
		br.close();
     }
}
```
*Timeout Error*

#### Reference Link: https://www.acmicpc.net/problem/10816
