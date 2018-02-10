# Breadth-First Search & Depth-First Search

### BFS Java Example

```java
class Node {
    public int value;
    public Node left;
    public Node right;
}
public void bfs(Node root) {
    Queue<Node> queue = new LinkedList<>();
    queue.offer(root);
    while(!queue.isEmpty()) {
        Node node = queue.poll();
        System.out.print(node.value);// visit node
        if(node.left != null) queue.offer(node.left);
        if(node.right != null) queue.offer(node.right);
    }
}
```

### DFS Java Example

```java
class Node {
    public int value;
    public Node left;
    public Node right;
}
public void dfs(Node root) {

}
```

### Usage
#### BFS
* Use Queue for bfs
* Find the shortest path in a graph even contains circle. However, BFS must maintain a queue of nodes to visit, this queue will grow to the size of whole graph.
#### DFS
* Use stack for DFS, or recursion (the call stack)
* DFS is ofen used in simulation of games.
* Compare with BFS, DFS has less space complexity.
* A good summary from Stackoverflow 
#### Ref
* [When is it practical to use Depth-First Search (DFS) vs Breadth-First Search (BFS)?](https://stackoverflow.com/questions/3332947/when-is-it-practical-to-use-depth-first-search-dfs-vs-breadth-first-search-bf)

### Advance
#### iterative deepening search
#### Dijkstra's algorithm for weighted graphs