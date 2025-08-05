# 🚀 Ultimate Coding + DSA Cheat Sheet

## 📋 Table of Contents
1. [Programming Languages Syntax](#programming-languages-syntax)
2. [I/O Operations](#io-operations)
3. [Data Structures](#data-structures)
4. [Algorithms](#algorithms)
5. [Coding Patterns](#coding-patterns)
6. [Problem Solving Templates](#problem-solving-templates)
7. [Time & Space Complexities](#time-space-complexities)
8. [Must-Know Questions](#must-know-questions)
9. [Interview Tips & Tricks](#interview-tips-tricks)
10. [Bonus Sections](#bonus-sections)

---

## Programming Languages Syntax

### Basic Syntax Comparison

| **Concept** | **C** | **C++** | **Java** | **Python** |
|-------------|-------|---------|----------|------------|
| **Variable Declaration** | `int x = 5;` | `int x = 5;` | `int x = 5;` | `x = 5` |
| **Array Declaration** | `int arr[10];` | `int arr[10];` | `int[] arr = new int[10];` | `arr = [0] * 10` |
| **Dynamic Array** | `int* arr = malloc(n*sizeof(int));` | `vector<int> arr(10);` | `List<Integer> arr = new ArrayList<>();` | `arr = []` |
| **String** | `char str[100];` | `string str = "hello";` | `String str = "hello";` | `str = "hello"` |
| **For Loop** | `for(int i=0; i<n; i++)` | `for(int i=0; i<n; i++)` | `for(int i=0; i<n; i++)` | `for i in range(n):` |
| **While Loop** | `while(condition)` | `while(condition)` | `while(condition)` | `while condition:` |
| **If Statement** | `if(x > 5) { }` | `if(x > 5) { }` | `if(x > 5) { }` | `if x > 5:` |
| **Function** | `int func(int x) { return x*2; }` | `int func(int x) { return x*2; }` | `public int func(int x) { return x*2; }` | `def func(x): return x*2` |

### Standard Libraries & Collections

| **Data Structure** | **C++** | **Java** | **Python** | **Use Case** |
|-------------------|---------|----------|------------|--------------|
| **Dynamic Array** | `vector<int> v` | `ArrayList<Integer> list` | `list = []` | Resizable arrays |
| **Stack** | `stack<int> st` | `Stack<Integer> stack` | `stack = []` | LIFO operations |
| **Queue** | `queue<int> q` | `Queue<Integer> queue` | `from collections import deque; q = deque()` | FIFO operations |
| **Priority Queue** | `priority_queue<int> pq` | `PriorityQueue<Integer> pq` | `import heapq; pq = []` | Heap operations |
| **Set** | `set<int> s` | `Set<Integer> set = new HashSet<>()` | `s = set()` | Unique elements |
| **Map** | `map<int,int> mp` | `Map<Integer,Integer> map = new HashMap<>()` | `d = {}` | Key-value pairs |
| **Unordered Map** | `unordered_map<int,int> ump` | `HashMap<Integer,Integer> map` | `d = {}` | Fast lookups |

---

## I/O Operations

### Fast I/O for Competitive Programming

| **Language** | **Fast Input** | **Fast Output** | **📝 Notes** |
|--------------|----------------|-----------------|--------------|
| **C++** | `ios_base::sync_with_stdio(false); cin.tie(NULL);` | `cout << result << "\n";` | Use `\n` instead of `endl` |
| **Java** | `BufferedReader br = new BufferedReader(new InputStreamReader(System.in));` | `System.out.print(result);` | StringBuilder for multiple outputs |
| **Python** | `import sys; input = sys.stdin.readline` | `print(result, end='')` | Consider PyPy for speed |
| **C** | `scanf("%d", &n);` | `printf("%d\n", result);` | Fastest for simple I/O |

### File I/O

| **Language** | **Read File** | **Write File** |
|--------------|---------------|----------------|
| **C++** | `ifstream file("input.txt"); file >> data;` | `ofstream file("output.txt"); file << data;` |
| **Java** | `Scanner sc = new Scanner(new File("input.txt"));` | `PrintWriter pw = new PrintWriter("output.txt");` |
| **Python** | `with open("input.txt", "r") as f: data = f.read()` | `with open("output.txt", "w") as f: f.write(data)` |

---

## Data Structures

### Arrays & Strings

| **Operation** | **C++** | **Java** | **Python** | **Time Complexity** |
|---------------|---------|----------|------------|-------------------|
| **Access** | `arr[i]` | `arr[i]` | `arr[i]` | O(1) |
| **Search** | `find(arr.begin(), arr.end(), val)` | `Arrays.binarySearch(arr, val)` | `val in arr` | O(n) linear, O(log n) binary |
| **Sort** | `sort(arr.begin(), arr.end())` | `Arrays.sort(arr)` | `arr.sort()` | O(n log n) |
| **Reverse** | `reverse(arr.begin(), arr.end())` | `Collections.reverse(Arrays.asList(arr))` | `arr[::-1]` | O(n) |
| **String Length** | `str.length()` | `str.length()` | `len(str)` | O(1) |
| **Substring** | `str.substr(start, len)` | `str.substring(start, end)` | `str[start:end]` | O(k) where k is length |

### Linked Lists

| **🧠 Concept** | **Implementation** | **⚡ Use Case** | **🧩 Interview Tip** |
|---------------|-------------------|----------------|---------------------|
| **Singly Linked List** | `struct Node { int data; Node* next; };` | Sequential access, dynamic size | Practice reversing in-place |
| **Doubly Linked List** | `struct Node { int data; Node* next; Node* prev; };` | Bidirectional traversal | Good for LRU cache implementation |
| **Circular Linked List** | Last node points to first | Josephus problem, round-robin | Detect cycle using Floyd's algorithm |

### Stacks & Queues

| **🧠 Data Structure** | **🧪 Implementation** | **⚡ Common Operations** | **🧩 Applications** |
|---------------------|----------------------|------------------------|-------------------|
| **Stack** | `stack<int> st; st.push(x); st.pop(); st.top();` | Push, Pop, Top, Empty | Expression evaluation, DFS, parentheses matching |
| **Queue** | `queue<int> q; q.push(x); q.pop(); q.front();` | Enqueue, Dequeue, Front, Empty | BFS, level order traversal |
| **Deque** | `deque<int> dq; dq.push_back(x); dq.push_front(x);` | Push/Pop from both ends | Sliding window maximum |
| **Priority Queue** | `priority_queue<int> pq; pq.push(x); pq.pop(); pq.top();` | Insert, Extract-Max/Min | Dijkstra's, heap sort, median finding |

### Trees

| **🧠 Tree Type** | **🧪 Properties** | **⚡ Operations** | **🧩 Time Complexity** |
|----------------|------------------|------------------|----------------------|
| **Binary Tree** | Each node has ≤ 2 children | Insert, Delete, Search | O(n) worst case |
| **BST** | Left < Root < Right | Insert, Delete, Search | O(log n) average, O(n) worst |
| **AVL Tree** | Self-balancing BST | Rotations maintain balance | O(log n) guaranteed |
| **Heap** | Complete binary tree | Insert, Extract-Min/Max | O(log n) |
| **Trie** | Prefix tree for strings | Insert, Search, StartsWith | O(m) where m is string length |

### Graphs

| **🧠 Representation** | **🧪 Implementation** | **⚡ Space** | **🧩 Best For** |
|---------------------|----------------------|-------------|----------------|
| **Adjacency Matrix** | `int adj[V][V]` | O(V²) | Dense graphs, quick edge lookup |
| **Adjacency List** | `vector<vector<int>> adj(V)` | O(V + E) | Sparse graphs, traversal |
| **Edge List** | `vector<pair<int,int>> edges` | O(E) | Kruskal's algorithm, simple storage |

---

## Algorithms

### Searching Algorithms

| **🧠 Algorithm** | **🧪 Implementation Hint** | **⚡ Time Complexity** | **🧩 Use Case** |
|----------------|---------------------------|----------------------|----------------|
| **Linear Search** | `for(int i=0; i<n; i++) if(arr[i] == target) return i;` | O(n) | Unsorted arrays |
| **Binary Search** | `while(left <= right) { mid = (left+right)/2; ... }` | O(log n) | Sorted arrays |
| **Ternary Search** | Divide into 3 parts instead of 2 | O(log₃ n) | Unimodal functions |

### Sorting Algorithms

| **🧠 Algorithm** | **⚡ Time** | **Space** | **🧩 Stability** | **Best For** |
|----------------|-----------|-----------|------------------|-------------|
| **Bubble Sort** | O(n²) | O(1) | Stable | Teaching purposes |
| **Selection Sort** | O(n²) | O(1) | Unstable | Small datasets |
| **Insertion Sort** | O(n²) | O(1) | Stable | Nearly sorted data |
| **Merge Sort** | O(n log n) | O(n) | Stable | Large datasets, linked lists |
| **Quick Sort** | O(n log n) avg | O(log n) | Unstable | General purpose |
| **Heap Sort** | O(n log n) | O(1) | Unstable | Memory-constrained |
| **Counting Sort** | O(n + k) | O(k) | Stable | Small range integers |
| **Radix Sort** | O(d × n) | O(n + k) | Stable | Large integers |

### Graph Algorithms

| **🧠 Algorithm** | **🧪 Template** | **⚡ Time** | **🧩 Use Case** |
|----------------|----------------|-----------|----------------|
| **DFS** | `void dfs(int v) { visited[v] = true; for(int u : adj[v]) if(!visited[u]) dfs(u); }` | O(V + E) | Cycle detection, topological sort |
| **BFS** | `queue<int> q; q.push(start); while(!q.empty()) { ... }` | O(V + E) | Shortest path (unweighted) |
| **Dijkstra** | `priority_queue<pair<int,int>> pq; // {distance, vertex}` | O((V + E) log V) | Shortest path (weighted) |
| **Floyd-Warshall** | `for(k=0; k<n; k++) for(i=0; i<n; i++) for(j=0; j<n; j++)` | O(V³) | All pairs shortest path |
| **Kruskal's MST** | Sort edges + Union-Find | O(E log E) | Minimum spanning tree |
| **Prim's MST** | Priority queue from any vertex | O((V + E) log V) | Minimum spanning tree |

### Dynamic Programming

| **🧠 DP Type** | **🧪 Pattern** | **⚡ Example Problems** | **🧩 Template** |
|--------------|---------------|------------------------|----------------|
| **Linear DP** | `dp[i] = f(dp[i-1], dp[i-2], ...)` | Fibonacci, House Robber | 1D array |
| **2D DP** | `dp[i][j] = f(dp[i-1][j], dp[i][j-1], ...)` | Unique Paths, Edit Distance | 2D matrix |
| **Knapsack** | `dp[i][w] = max(dp[i-1][w], dp[i-1][w-weight[i]] + value[i])` | 0/1 Knapsack, Subset Sum | 2D optimization |
| **LIS** | `dp[i] = max(dp[j] + 1)` for all j < i where arr[j] < arr[i] | Longest Increasing Subsequence | O(n²) or O(n log n) |
| **LCS** | `dp[i][j] = (s1[i] == s2[j]) ? dp[i-1][j-1] + 1 : max(dp[i-1][j], dp[i][j-1])` | Longest Common Subsequence | String matching |

---

## Coding Patterns

### Two Pointers

| **🧠 Pattern** | **🧪 Template** | **⚡ Problems** | **🧩 Tip** |
|--------------|----------------|----------------|-----------|
| **Opposite Ends** | `left = 0, right = n-1; while(left < right)` | Two Sum (sorted), Palindrome check | Move pointers based on condition |
| **Same Direction** | `slow = 0, fast = 0; while(fast < n)` | Remove duplicates, sliding window | Fast pointer explores, slow maintains result |
| **Fast & Slow** | `slow = head, fast = head; while(fast && fast.next)` | Cycle detection, middle of linked list | Floyd's tortoise and hare |

### Sliding Window

| **🧠 Window Type** | **🧪 Template** | **⚡ Problems** | **🧩 Key Insight** |
|------------------|----------------|----------------|-------------------|
| **Fixed Size** | `for(i=0; i<k; i++) sum += arr[i]; for(i=k; i<n; i++) { sum += arr[i] - arr[i-k]; }` | Max sum subarray of size k | Maintain window sum/properties |
| **Variable Size** | `left=0; for(right=0; right<n; right++) { while(condition) left++; }` | Longest substring without repeating chars | Expand right, contract left |
| **Shrinkable** | `left=0, minLen=INT_MAX; for(right=0; right<n; right++) { while(valid) { minLen = min(minLen, right-left+1); left++; } }` | Minimum window substring | Find minimum valid window |

### Backtracking

| **🧠 Problem Type** | **🧪 Template** | **⚡ Examples** |
|-------------------|----------------|----------------|
| **Permutations** | `void backtrack(vector<int>& nums, vector<bool>& used, vector<int>& current)` | All permutations of array |
| **Combinations** | `void backtrack(int start, int target, vector<int>& current)` | Combination sum, subset sum |
| **Subsets** | `void backtrack(int index, vector<int>& current)` | All subsets, power set |
| **N-Queens** | `void backtrack(int row, vector<string>& board)` | N-Queens, Sudoku solver |

---

## Problem Solving Templates

### Binary Search Template

```cpp
// Template for "find minimum x such that condition(x) is true"
int left = 0, right = n;
while (left < right) {
    int mid = left + (right - left) / 2;
    if (condition(mid)) {
        right = mid;
    } else {
        left = mid + 1;
    }
}
return left;
```

### DFS Template

```cpp
void dfs(int node, vector<vector<int>>& adj, vector<bool>& visited) {
    visited[node] = true;
    // Process current node
    
    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            dfs(neighbor, adj, visited);
        }
    }
}
```

### BFS Template

```cpp
void bfs(int start, vector<vector<int>>& adj) {
    vector<bool> visited(n, false);
    queue<int> q;
    
    q.push(start);
    visited[start] = true;
    
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        
        // Process current node
        
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}
```

### DP Template

```cpp
// Bottom-up approach
vector<int> dp(n + 1, 0);
dp[0] = base_case;

for (int i = 1; i <= n; i++) {
    for (int j = 0; j < i; j++) {
        dp[i] = max(dp[i], dp[j] + transition(i, j));
    }
}

return dp[n];
```

---

## Time & Space Complexities

### Data Structure Operations

| **Data Structure** | **Access** | **Search** | **Insertion** | **Deletion** | **Space** |
|-------------------|-----------|-----------|---------------|-------------|-----------|
| **Array** | O(1) | O(n) | O(n) | O(n) | O(n) |
| **Dynamic Array** | O(1) | O(n) | O(1) amortized | O(n) | O(n) |
| **Linked List** | O(n) | O(n) | O(1) | O(1) | O(n) |
| **Stack** | O(n) | O(n) | O(1) | O(1) | O(n) |
| **Queue** | O(n) | O(n) | O(1) | O(1) | O(n) |
| **Hash Table** | N/A | O(1) avg | O(1) avg | O(1) avg | O(n) |
| **BST** | O(log n) avg | O(log n) avg | O(log n) avg | O(log n) avg | O(n) |
| **AVL Tree** | O(log n) | O(log n) | O(log n) | O(log n) | O(n) |
| **B-Tree** | O(log n) | O(log n) | O(log n) | O(log n) | O(n) |
| **Heap** | N/A | O(n) | O(log n) | O(log n) | O(n) |
| **Trie** | N/A | O(m) | O(m) | O(m) | O(ALPHABET_SIZE × N × M) |

### Algorithm Complexities

| **Algorithm** | **Best** | **Average** | **Worst** | **Space** |
|---------------|----------|-------------|-----------|-----------|
| **Quick Sort** | O(n log n) | O(n log n) | O(n²) | O(log n) |
| **Merge Sort** | O(n log n) | O(n log n) | O(n log n) | O(n) |
| **Heap Sort** | O(n log n) | O(n log n) | O(n log n) | O(1) |
| **Bubble Sort** | O(n) | O(n²) | O(n²) | O(1) |
| **Insertion Sort** | O(n) | O(n²) | O(n²) | O(1) |
| **Selection Sort** | O(n²) | O(n²) | O(n²) | O(1) |
| **Binary Search** | O(1) | O(log n) | O(log n) | O(1) |
| **DFS** | O(V + E) | O(V + E) | O(V + E) | O(V) |
| **BFS** | O(V + E) | O(V + E) | O(V + E) | O(V) |
| **Dijkstra** | O((V + E) log V) | O((V + E) log V) | O((V + E) log V) | O(V) |

---

## Must-Know Questions

### Easy Level (Foundation Building)

| **Problem** | **Pattern** | **Key Insight** |
|-------------|-------------|-----------------|
| Two Sum | Hash Map | Store complements |
| Valid Parentheses | Stack | LIFO matching |
| Merge Two Sorted Lists | Two Pointers | Compare and advance |
| Maximum Subarray | Kadane's Algorithm | Reset on negative sum |
| Climbing Stairs | DP | Fibonacci pattern |
| Best Time to Buy/Sell Stock | One Pass | Track minimum price |
| Valid Palindrome | Two Pointers | Ignore non-alphanumeric |
| Reverse Linked List | Iterative/Recursive | Change next pointers |
| Binary Tree Inorder Traversal | DFS | Left-Root-Right |
| Symmetric Tree | Recursion | Mirror comparison |

### Medium Level (Interview Favorites)

| **Problem** | **Pattern** | **Key Insight** |
|-------------|-------------|-----------------|
| Add Two Numbers | Linked List | Handle carry |
| Longest Substring Without Repeating | Sliding Window | Use hash set |
| 3Sum | Two Pointers | Fix one, find two |
| Container With Most Water | Two Pointers | Move shorter line |
| Group Anagrams | Hash Map | Sort as key |
| Spiral Matrix | Simulation | Layer by layer |
| Rotate Image | Matrix | Transpose + reverse |
| Unique Paths | DP | Combinatorics |
| Coin Change | DP | Minimum coins |
| Product of Array Except Self | Prefix/Suffix | Two passes |
| Top K Frequent Elements | Heap | Min/Max heap |
| Kth Largest Element | Quick Select | Partition |
| Course Schedule | Topological Sort | Detect cycle |
| Number of Islands | DFS/BFS | Mark visited |
| Binary Tree Level Order | BFS | Queue traversal |

### Hard Level (Advanced Concepts)

| **Problem** | **Pattern** | **Key Insight** |
|-------------|-------------|-----------------|
| Median of Two Sorted Arrays | Binary Search | Partition optimization |
| Trapping Rain Water | Two Pointers/Stack | Track max heights |
| Regular Expression Matching | DP | State transitions |
| Merge k Sorted Lists | Divide & Conquer | Priority queue |
| Largest Rectangle in Histogram | Stack | Monotonic stack |
| Word Ladder | BFS | Shortest transformation |
| Edit Distance | DP | Levenshtein distance |
| Sliding Window Maximum | Deque | Monotonic deque |
| Serialize/Deserialize Binary Tree | DFS | Preorder with nulls |
| LRU Cache | Hash Map + Doubly Linked List | O(1) operations |

---

## Interview Tips & Tricks

### Language-Specific Optimization Tricks

| **Language** | **Trick** | **Example** | **Benefit** |
|--------------|-----------|-------------|-------------|
| **C++** | `lower_bound/upper_bound` | `lower_bound(v.begin(), v.end(), x)` | O(log n) search in sorted array |
| **C++** | `__builtin_popcount` | `__builtin_popcount(n)` | Count set bits |
| **C++** | Reserve vector capacity | `v.reserve(n)` | Avoid reallocations |
| **Python** | List comprehension | `[x*2 for x in range(10)]` | Faster than loops |
| **Python** | `collections.Counter` | `Counter(arr)` | Frequency counting |
| **Python** | `collections.defaultdict` | `defaultdict(int)` | Auto-initialize |
| **Java** | StringBuilder | `StringBuilder sb = new StringBuilder()` | Efficient string building |
| **Java** | Arrays.asList | `Arrays.asList(1,2,3)` | Quick list creation |

### Common Edge Cases

| **Scenario** | **Edge Cases to Consider** | **Testing Strategy** |
|--------------|---------------------------|---------------------|
| **Arrays** | Empty array, single element, duplicates | Test with [], [1], [1,1,1] |
| **Strings** | Empty string, single char, all same chars | Test with "", "a", "aaaa" |
| **Linked Lists** | NULL head, single node, cycle | Test with null, single, cycle |
| **Trees** | Empty tree, single node, skewed tree | Test with null, single, linear |
| **Graphs** | Disconnected, self-loops, no edges | Test various topologies |
| **Numbers** | Negative, zero, overflow | Test with -1, 0, INT_MAX |

### Debugging Strategies

| **Issue Type** | **Common Causes** | **Quick Fixes** |
|----------------|------------------|----------------|
| **Infinite Loop** | Wrong loop condition, not updating variables | Add print statements, check bounds |
| **Array Out of Bounds** | Off-by-one errors, wrong indexing | Check array size, use size() - 1 |
| **Stack Overflow** | Infinite recursion, deep recursion | Add base case, consider iterative |
| **Wrong Answer** | Logic error, edge cases | Dry run with simple examples |
| **Time Limit Exceeded** | Inefficient algorithm, nested loops | Analyze complexity, optimize |

### Problem-Solving Framework

1. **📝 Understand**: Read problem twice, identify inputs/outputs, ask clarifying questions
2. **🎯 Approach**: Start with brute force, think of optimizations, consider data structures
3. **⚡ Implement**: Write clean code, handle edge cases, use descriptive variables
4. **🧪 Test**: Test with given examples, edge cases, stress test if time permits
5. **📊 Optimize**: Analyze time/space complexity, discuss trade-offs

---

## Bonus Sections

### Object-Oriented Programming

| **Concept** | **C++** | **Java** | **Python** | **Key Points** |
|-------------|---------|----------|------------|----------------|
| **Class** | `class MyClass { };` | `class MyClass { }` | `class MyClass:` | Blueprint for objects |
| **Inheritance** | `class Child : public Parent` | `class Child extends Parent` | `class Child(Parent):` | IS-A relationship |
| **Polymorphism** | Virtual functions | Method overriding | Duck typing | One interface, multiple implementations |
| **Encapsulation** | Private/Protected/Public | Private/Protected/Public | Name mangling with `_` | Data hiding |
| **Abstraction** | Pure virtual functions | Abstract classes/interfaces | ABC module | Hide implementation details |

### System Design Basics

| **Component** | **Purpose** | **Examples** | **Considerations** |
|---------------|-------------|--------------|-------------------|
| **Load Balancer** | Distribute traffic | nginx, HAProxy | Round-robin, weighted, geographic |
| **Cache** | Fast data access | Redis, Memcached | TTL, eviction policies, consistency |
| **Database** | Data persistence | MySQL, PostgreSQL, MongoDB | ACID, CAP theorem, sharding |
| **Message Queue** | Async communication | RabbitMQ, Apache Kafka | Ordering, durability, scalability |
| **CDN** | Content delivery | CloudFlare, AWS CloudFront | Geographic distribution, caching |

### Bit Manipulation

| **Operation** | **Formula** | **Use Case** | **Example** |
|---------------|-------------|--------------|-------------|
| **Check if power of 2** | `n & (n-1) == 0` | Optimization checks | `8 & 7 = 0` |
| **Toggle kth bit** | `n ^= (1 << k)` | Bit manipulation | Toggle bit at position k |
| **Clear kth bit** | `n &= ~(1 << k)` | Reset specific bit | Clear bit at position k |
| **Set kth bit** | `n \|= (1 << k)` | Set specific bit | Set bit at position k |
| **Get kth bit** | `(n >> k) & 1` | Extract bit value | Check if bit is set |

### Memory Management

| **Language** | **Memory Model** | **Key Points** | **Best Practices** |
|--------------|-----------------|----------------|-------------------|
| **C** | Manual management | malloc/free, no garbage collection | Always free allocated memory |
| **C++** | RAII, smart pointers | Stack/heap, destructors | Use smart pointers, avoid raw pointers |
| **Java** | Garbage collection | Heap management, generational GC | Avoid memory leaks, use profilers |
| **Python** | Reference counting + GC | Automatic memory management | Be aware of circular references |

### Big O Notation Rules

| **Rule** | **Explanation** | **Example** |
|----------|----------------|-------------|
| **Drop Constants** | O(2n) → O(n) | `for(int i=0; i<2*n; i++)` is O(n) |
| **Drop Non-Dominant Terms** | O(n² + n) → O(n²) | Quadratic dominates linear |
| **Different Inputs** | O(a + b) not O(n) | Two separate inputs |
| **Nested Loops** | Multiply complexities | `for(i) for(j)` is O(n²) |
| **Recursive Relations** | Use Master Theorem | T(n) = 2T(n/2) + O(n) = O(n log n) |

---

## 🎯 Quick Reference Commands

### Git Commands for Coding Interviews
```bash
git init                    # Initialize repository
git add .                   # Stage all changes
git commit -m "message"     # Commit with message
git push origin main        # Push to remote
```

### Essential Linux Commands
```bash
ls -la                      # List files with details
grep "pattern" file         # Search in file
sort file                   # Sort file contents
wc -l file                  # Count lines
chmod +x script.sh          # Make executable
```

### Database Queries (SQL)
```sql
SELECT * FROM table WHERE condition;
INSERT INTO table VALUES (val1, val2);
UPDATE table SET col = val WHERE condition;
DELETE FROM table WHERE condition;
```

---

**🚀 Remember**: Practice consistently, understand patterns, and focus on problem-solving approach rather than memorizing solutions. Good luck with your interviews!