# Algorithms / الخوارزميات

## Summary / الملخص

**English:**
Algorithms are step-by-step procedures for solving computational problems efficiently. This document covers fundamental algorithmic paradigms—sorting, searching, divide and conquer, dynamic programming, greedy algorithms, graph algorithms, and complexity analysis—in four major programming languages (C++, PHP, JavaScript, Python). For each paradigm, we explain key concepts, provide code syntax, illustrate real-world industry use cases, and include practical interview questions with example-driven answers. Recent trends and job market insights ensure readiness for development and interviews.

**العربية:**
الخوارزميات هي إجراءات مرتبة لحل المشكلات الحسابية بكفاءة. يغطي هذا الملف النماذج الأساسية للخوارزميات—الترتيب والبحث والتقسيم والتغلب، البرمجة الديناميكية، الخوارزميات الجشعة، خوارزميات الرسوم البيانية، وتحليل التعقيد—باستخدام أربع لغات رئيسية (C++، PHP، JavaScript، Python). نشرح لكل نموذج المفهوم الرئيسي، الصياغة البرمجية، أمثلة عملية من سوق العمل، وأسئلة مقابلات مع إجابات مدعمة بأمثلة عملية. يتضمن الملف أحدث التوجهات ورؤى سوق العمل لضمان الجاهزية.

---

## 1. Sorting Algorithms / خوارزميات الترتيب

### 1.1 Bubble Sort / الفرز الفقاعي

* **Concept / المفهوم:** Repeatedly swap adjacent elements if out of order, O(n²).
* **Syntax Examples / أمثلة الصياغة:**

  ```cpp
  // C++
  void bubbleSort(vector<int>& a) {
    for(int i=0;i<a.size();i++)
      for(int j=0;j<a.size()-i-1;j++)
        if(a[j]>a[j+1]) swap(a[j],a[j+1]);
  }
  ```
* **Practical Use / تطبيق عملي:** Simple datasets small scale; often used in teaching and built-in library tests.

### 1.2 Quick Sort / الترتيب السريع

* **Concept / المفهوم:** Divide and conquer: pick pivot, partition, sort subarrays, O(n log n) average.
* **Syntax Examples / أمثلة الصياغة:**

  ```python
  # Python
  def quick_sort(a):
      if len(a)<2: return a
      pivot = a[len(a)//2]
      left = [x for x in a if x<pivot]
      mid = [x for x in a if x==pivot]
      right = [x for x in a if x>pivot]
      return quick_sort(left)+mid+quick_sort(right)
  ```
* **Real-world Example / مثال صناعي:** Used in standard libraries (C++ `std::sort`, JS `Array.prototype.sort`) for average cases.

---

## 2. Searching Algorithms / خوارزميات البحث

### 2.1 Linear Search / البحث الخطي

* **Concept / المفهوم:** Scan each element until match, O(n).
* **Example / مثال:** `for x in arr: if x==key: return True`
* **Use Case / حالة استخدام:** Small or unsorted data.

### 2.2 Binary Search / البحث الثنائي

* **Concept / المفهوم:** On sorted arrays, compare middle, eliminate half, O(log n).
* **Syntax Examples:**

  ```js
  // JavaScript
  function binarySearch(a, key) {
    let lo=0, hi=a.length-1;
    while(lo<=hi) {
      let mid=Math.floor((lo+hi)/2);
      if(a[mid]===key) return mid;
      if(a[mid]<key) lo=mid+1; else hi=mid-1;
    }
    return -1;
  }
  ```
* **Industry Context:** Database index lookups, search engines.

---

## 3. Divide and Conquer / التقسيم والتغلب

* **Concept / المفهوم:** Break problem into subproblems, solve recursively, combine results.
* **Example / مثال عملي:** Merge Sort in C++:

  ```cpp
  void merge(vector<int>& a,int l,int m,int r){ /* merge two halves */ }
  void mergeSort(vector<int>& a,int l,int r){ if(l<r){ int m=(l+r)/2; mergeSort(a,l,m); mergeSort(a,m+1,r); merge(a,l,m,r);} }
  ```
* **Real-world Use:** Parallel processing tasks, large-scale data sorting in distributed systems.

---

## 4. Dynamic Programming / البرمجة الديناميكية

* **Concept / المفهوم:** Store results of overlapping subproblems, avoid recomputation.
* **Example / مثال:** Fibonacci with memoization in PHP:

  ```php
  function fib($n,&$memo){ if(isset($memo[$n])) return $memo[$n]; if($n<2) return $n; $memo[$n]=fib($n-1,$memo)+fib($n-2,$memo); return $memo[$n]; }
  $memo=[]; echo fib(10,$memo);
  ```
* **Industry Example:** Resource allocation, route optimization in logistics.

---

## 5. Greedy Algorithms / الخوارزميات الجشعة

* **Concept / المفهوم:** Make locally optimal choice at each step.
* **Example / مثال:** Coin change (min coins) in JavaScript:

  ```js
  function coinChange(coins,amount){
    coins.sort((a,b)=>b-a);
    let count=0;
    for(let c of coins){ count+=Math.floor(amount/c); amount%=c; }
    return amount? -1: count;
  }
  ```
* **Use Case / حالة استخدام:** Activity scheduling, Huffman coding in compression.

---

## 6. Graph Algorithms / خوارزميات الرسوم البيانية

### 6.1 BFS & DFS / البحث بالعرض والعمق

* **Concept / المفهوم:** BFS uses queue for shortest path in unweighted graph; DFS uses stack/recursion for connectivity.
* **Syntax Example / مثال بايثون:**

  ```python
  from collections import deque
  def bfs(graph, start):
    visited=[]; q=deque([start]); visited.append(start)
    while q:
      v=q.popleft();
      for n in graph[v]:
        if n not in visited: visited.append(n); q.append(n)
    return visited
  ```

### 6.2 Dijkstra / ديكسترا

* **Concept / المفهوم:** Shortest paths from source in weighted graph, O((V+E) log V).
* **Example / مثال C++:**

  ```cpp
  vector<int> dijkstra(int s){ /* use priority_queue */ }
  ```
* **Real-world Use:** GPS navigation, network routing.

---

## 7. Complexity Analysis / تحليل التعقيد

* **Big O Notation / الترميز الكبير O:** Describes worst-case time.
* **Examples / أمثلة:**

  * O(1): hash lookup
  * O(log n): binary search
  * O(n): linear scan
  * O(n log n): merge sort
  * O(n²): bubble sort
* **Advice / نصيحة:** Optimize hotspots, choose algorithms matching data size.

---

## 8. Job Market Insights / رؤى سوق العمل

* **Performance Tuning:** Familiarity with profiling (gprof, Chrome DevTools) to detect bottlenecks.
* **Algorithmic Libraries:** Employers use optimized libraries (`numpy`, `C++ STL`, `numpy.sort`, `scipy.sparse`).
* **Scalable Systems:** Knowledge of distributed algorithms (MapReduce, Spark) for big data processing.

---

## 9. Interview Questions & Practical Examples / أسئلة مقابلات وأمثلة عملية

1. **Implement Merge Sort and explain its complexity. / نفّذ Merge Sort وشرح تعقيده.**

   * **Explanation / شرح:** O(n log n) divide and conquer.
   * **JavaScript Example / مثال جافاسكربت:**

     ```js
     function mergeSort(a){
       if(a.length<2) return a;
       const mid = Math.floor(a.length/2);
       const left=mergeSort(a.slice(0,mid));
       const right=mergeSort(a.slice(mid));
       const res=[];
       while(left.length&&right.length) res.push(left[0]<right[0]? left.shift() : right.shift());
       return res.concat(left, right);
     }
     ```

2. **How to detect and handle negative cycles in graphs? / كيفية اكتشاف ومعالجة الحلقات السالبة في الرسوم البيانية؟**

   * **Explanation / شرح:** Use Bellman-Ford algorithm.
   * **Python Snippet / مثال بايثون:**

     ```python
     def bellman_ford(graph, source):
         dist={v:float('inf') for v in graph}; dist[source]=0
         for _ in range(len(graph)-1):
             for u in graph:
                 for v,w in graph[u]:
                     dist[v]=min(dist[v], dist[u]+w)
         # detect negative cycle
         for u in graph:
             for v,w in graph[u]:
                 if dist[u]+w<dist[v]: return True
         return False
     ```

3. **Explain Time vs Space trade-offs with an example. / اشرح المقايضة بين الزمن والذاكرة مع مثال.**

   * **Example / مثال:** Memoization trades space for faster time in Fibonacci.

4. **Given a large dataset that cannot fit in memory, what algorithmic approach would you use? / إذا كان لديك مجموعة بيانات كبيرة لا تتسع في الذاكرة، ما الخوارزمية المناسبة؟**

   * **Answer / الإجابة:** External sorting (e.g., k-way merge sort) and streaming algorithms (approximate counts with HyperLogLog).

---

*Prepared to help you master Algorithms in major languages and ace your technical interviews!*
