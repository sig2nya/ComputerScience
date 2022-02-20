1.깊이 우선 탐색 - Depth First Search(DFS)
======================================
* 스택 혹은 재귀 호출을 이용하여 구현한다.
```java
class DFS{
    private int V;
    private int[][] dfsGraph;
    private boolean[] visitArr;
    
    public void dfs(int idx) {
        this.visitArr[idx] = true;
        System.out.print(idx + " "); 
        
        for(int i=1; i <= this.V; i++) {
            if(dfsGraph[idx][i] == 1 && visitArr[i] == false) { // 방문하지 않았으며, 정점이 연결되어 있는 경우.
                dfs(i);
            }
        }
    }
}
```
2.너비 우선 탐색 - Breath First Search(BFS)
======================================
* 큐로 구현합니다. 재귀로 구현하지 않습니다.
```java
class BFS(int V){ // 재귀로 구현하지 않는다.
	private int V;
    	private int[][] dfsGraph;
    	private boolean[] visitArr;
	
	Queue<Integer> queue = new LinkedList<Integer>();
	queue.offer(V); // 큐에 값 넣기.
	check[V] = true;
	while(!queue.isEmpty()){
		int tmp = queue.poll(); // 큐에 담긴 값 꺼내기.
		System.out.print(tmp + " ");
		for(int i = 1; i < arr[V].length; i++){
			if(arr[tmp][i] == 1 && !check[i]){
				queue.offer(i);
				check[i] = true;
			}
		}
	}
}
```
