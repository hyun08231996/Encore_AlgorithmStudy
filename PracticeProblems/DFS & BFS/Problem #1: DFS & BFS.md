### 문제

그래프를 DFS로 탐색한 결과와 BFS로 탐색한 결과를 출력하는 프로그램을 작성하시오. 단, 방문할 수 있는 정점이 여러 개인 경우에는 정점 번호가 작은 것을 먼저 방문하고, 더 이상 방문할 수 있는 점이 없는 경우 종료한다. 정점 번호는 1번부터 N번까지이다.

### 입력

첫째 줄에 정점의 개수 N(1 ≤ N ≤ 1,000), 간선의 개수 M(1 ≤ M ≤ 10,000), 탐색을 시작할 정점의 번호 V가 주어진다. 다음 M개의 줄에는 간선이 연결하는 두 정점의 번호가 주어진다. 어떤 두 정점 사이에 여러 개의 간선이 있을 수 있다. 입력으로 주어지는 간선은 양방향이다.

### 출력

첫째 줄에 DFS를 수행한 결과를, 그 다음 줄에는 BFS를 수행한 결과를 출력한다. V부터 방문된 점을 순서대로 출력하면 된다.

##### 예제 입력 1 
4 5 1 <br/>
1 2 <br/>
1 3 <br/>
1 4 <br/>
2 4 <br/>
3 4
##### 예제 출력 1 
1 2 4 3 <br/>
1 2 3 4

##### 예제 입력 2 
5 5 3 <br/>
5 4 <br/>
5 2 <br/>
1 2 <br/>
3 4 <br/>
3 1
##### 예제 출력 2 
3 1 2 5 4 <br/>
3 1 4 2 5

##### 예제 입력 3 
1000 1 1000 <br/>
999 1000
##### 예제 출력 3 
1000 999 <br/>
1000 999

### Solution
```java
import java.util.*;

public class Solution {
	public static int[][] arr;
	public static boolean[] visited;

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
        
		int vertex = sc.nextInt();
		int edge = sc.nextInt();
		int start = sc.nextInt();
		
		arr = new int[vertex+1][vertex+1];
		
		for(int i=1;i<=edge;i++) {
			int a = sc.nextInt();
			int b = sc.nextInt();
			arr[a][b] = 1;
			arr[b][a] = 1;
		}
		
		visited = new boolean[vertex+1];
		dfs(start); 

		visited = new boolean[vertex+1];
		bfs(start); 

		
	}
	
	public static void dfs(int start) {
		visited[start] = true;
		System.out.print(start+ " ");
		
		if(start == arr.length) {
			return;
		}

		for(int a=1;a<arr.length;a++) {
			if(arr[start][a] == 1 && visited[a] == false) {
				dfs(a);
			}
		}
			
	}
	
	public static void bfs(int start) {
		Queue<Integer> que = new LinkedList<Integer>(); 
		
		que.add(start);
		visited[start] = true;
 		System.out.print(start+ " ");
		
		while(!que.isEmpty()) {
			
			int temp = que.peek();
			que.poll();
			for(int i=1; i<arr.length;i++) {
				if(arr[temp][i] ==1 && visited[i] == false) {
					que.add(i);
					visited[i] = true;
					System.out.print(i+ " ");
				}
			}
		}
	}

}
```

#### Reference Link: https://www.acmicpc.net/problem/1260
