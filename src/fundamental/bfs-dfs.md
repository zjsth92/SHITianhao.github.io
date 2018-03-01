# Breadth-First Search & Depth-First Search

### BFS Java Example

```java
class Node {
    public int value;
    public Node left;
    public Node right;
}
public void bfs(Node root) {
    if(root == null) return;
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
public void dfsRecursion(Node node) {
    if(node == null) return;
    System.out.print(node.value);// visit node
    // visit left
    dfsRecursion(node.left);
    // visit right
    dfsRecursion(node.right);
}

public void dfsStack(Node root) {
    if(node == null) return;
    Stack<Node> stack = new Stack<>();
    stack.push(root); 
    while (!stack.empty()) {
        Node node = stack.pop();
        System.out.println(node.value);// visit node
        // visit left node's path until end, same as the recursion version
        if(node.left != null) stack.push(node.left); 
        if(node.right != null) stack.push(node.right); 
    }  
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
* A good summary from Stackoverflow [When is it practical to use Depth-First Search (DFS) vs Breadth-First Search (BFS)?](https://stackoverflow.com/questions/3332947/when-is-it-practical-to-use-depth-first-search-dfs-vs-breadth-first-search-bf)

### Advance
* Iterative deepening search
* Dijkstra's algorithm for weighted graphs

### Topological Sort
