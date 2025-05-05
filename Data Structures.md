# Data Structures / هياكل البيانات

## Summary / الملخص

**English:**
Data Structures are fundamental components in computer science that allow efficient storage, manipulation, and retrieval of data. This document covers the most important structures—arrays, linked lists, stacks, queues, trees, graphs, hash tables—in four major programming languages (C++, PHP, JavaScript, Python). For each structure, we explain key concepts, language-specific syntax, practical industry use cases with real-world examples, and provide interview questions with detailed, example-driven answers. A concise bilingual comparison table highlights syntax differences. The document concludes with recent industry trends to ensure you're fully prepared for technical interviews and practical development tasks.

**العربية:**
تُعد هياكل البيانات من المكونات الأساسية في علوم الحاسوب التي تتيح تخزين البيانات ومعالجتها واسترجاعها بكفاءة. يغطي هذا الملف أهم الهياكل—المصفوفات، القوائم المرتبطة، الستاك، الكيو، الأشجار، الرسوم البيانية، جداول الهاش—باستخدام أربع لغات برمجة رئيسية (C++، PHP، JavaScript، Python). لكل هيكل نشرح المفاهيم الرئيسية، الصياغة الخاصة بكل لغة، تطبيقات عملية مع أمثلة حقيقية من سوق العمل، وأسئلة مقابلات بإجابات مدعمة بأمثلة عملية. يختتم الملف بجدول مقارنة ثنائي اللغة وأحدث التحديثات في الصناعة.

---

## 1. Arrays / المصفوفات

### 1.1 Concept / المفهوم

* **English:** An array is a collection of elements identified by index. It offers O(1) access time.
* **العربية:** المصفوفة هي مجموعة من العناصر يُحدد كل عنصر فيها بواسطة فهرس. توفر وقت وصول ثابت O(1).

### 1.2 Syntax and Examples / الصياغة والأمثلة

| Language   | Declaration            | Access     | Insert/Delete                     |
| ---------- | ---------------------- | ---------- | --------------------------------- |
| **C++**    | `int arr[5];`          | `arr[i]`   | Manual shift                      |
| **PHP**    | `$arr = array(1,2,3);` | `$arr[$i]` | `array_splice($arr, $i, 0, $val)` |
| **JS**     | `let arr = [1,2,3];`   | `arr[i]`   | `arr.splice(i,0,val)`             |
| **Python** | `arr = [1,2,3]`        | `arr[i]`   | `arr.insert(i, val)`              |

### 1.3 Practical Applications / التطبيقات العملية

* Use arrays for static data, lookup tables, and buffer implementations.
* **Real-world Example / مثال عملي من سوق العمل:**  في تطبيقات البث المباشر للفيديو، تُستخدم المصفوفات كـ circular buffers لتخزين إطارات الفيديو المؤقتة قبل العرض لضمان تدفق سلس دون تأخير.

---

## 2. Linked Lists / القوائم المرتبطة

### 2.1 Concept / المفهوم

* **English:** A linked list is a sequence of nodes where each node points to the next. Allows O(1) insertion/deletion at known positions.
* **العربية:** القائمة المرتبطة هي تسلسل من العقد حيث تشير كل عقدة إلى التالية. تتيح إدخال وحذف بعُمدة ثابتة O(1) في مواضع معروفة.

### 2.2 Syntax and Examples / الصياغة والأمثلة

```cpp
// C++
struct Node { int data; Node* next; };
Node* head = nullptr;
```

```php
// PHP
class Node { public $data; public $next; }
$head = null;
```

```js
// JavaScript
class Node { constructor(data){ this.data = data; this.next = null; } }
let head = null;
```

```python
# Python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
head = None
```

### 2.3 Practical Applications / التطبيقات العملية

* Implement stacks, queues, and adjacency lists in graphs.
* **Real-world Example / مثال عملي من سوق العمل:** في أنظمة الـOS، تُستخدم القوائم المرتبطة في إدارة الـfree lists للذاكرة لتتبع الكتل الفارغة وإعادة تخصيصها بكفاءة.

---

## 3. Stacks & Queues / الستاك و الكيو

### 3.1 Stack / الستاك

* **Concept / المفهوم:** LIFO structure.
* **Syntax / الصياغة:**

  * C++: `stack<int> st;`
  * PHP: `SplStack` class
  * JS: `let st = []; st.push(val); st.pop();`
  * Python: `st = []; st.append(val); st.pop()`

### 3.2 Queue / الكيو

* **Concept / المفهوم:** FIFO structure.
* **Syntax / الصياغة:**

  * C++: `queue<int> q;`
  * PHP: `SplQueue` class
  * JS: `let q = []; q.push(val); q.shift();`
  * Python: `from collections import deque; q = deque(); q.append(val); q.popleft()`

### 3.3 Applications / التطبيقات العملية

* Call stacks, undo mechanisms, task scheduling.
* **Real-world Example / مثال عملي من سوق العمل:** في تطبيقات معالجة الدُفعات (batch processing) و messaging brokers مثل RabbitMQ، تُستخدم قوائم الانتظار (queues) لتنظيم المهام ومعالجتها بالتتابع.

---

## 4. Trees / الأشجار

### 4.1 Binary Tree / الشجرة الثنائية

* **Concept / المفهوم:** Each node has up to two children.
* **Syntax examples:**

```cpp
struct Node { int data; Node* left; Node* right; };
```

```python
class Node:
    def __init__(self,data):
        self.data=data
        self.left=None
        self.right=None
```

### 4.2 Binary Search Tree / شجرة البحث الثنائية

* **Concept:** Ordered tree for fast lookup, insert, delete (O(log n) average).

### 4.3 Applications / التطبيقات العملية

* Databases indexes, file systems, in-memory search.
* **Real-world Example / مثال عملي من سوق العمل:** قواعد البيانات العلائقية مثل MySQL وPostgreSQL تستخدم B-Trees (نوع من الأشجار متعددة الفروع) لإدارة الفهارس (indexes) وتحسين سرعة الاستعلامات.

---

## 5. Graphs / الرسوم البيانية

### 5.1 Concept / المفهوم

Graph consists of vertices and edges; models networks.

### 5.2 Representations / التمثيلات

* Adjacency matrix
* Adjacency list

### 5.3 Applications / التطبيقات العملية

* Social networks, routing algorithms, dependency graphs.
* **Real-world Example / مثال عملي من سوق العمل:** في منصات التواصل الاجتماعي مثل Facebook، تُستخدم الرسوم البيانية لتمثيل العلاقات بين المستخدمين وحساب درجات القرابة واقتراح الصداقات.

---

## 6. Hash Tables / جداول الهاش

### 6.1 Concept / المفهوم

Key-value store with average O(1) access.

### 6.2 Syntax / الصياغة

* C++: `unordered_map<Key,Value>`
* PHP: associative arrays
* JS: `let map = new Map(); map.set(key,val);`
* Python: `dict`

### 6.3 Applications / التطبيقات العملية

* Caches, session stores, lookups.
* **Real-world Example / مثال عملي من سوق العمل:** أنظمة التخزين المؤقت (caching) في تطبيقات الويب مثل Redis أو Memcached تعتمد على جداول الهاش لتخزين واسترجاع البيانات بسرعة.

---

## Summary Table / جدول الملخص

| Structure   | C++                   | PHP               | JavaScript   | Python        |
| ----------- | --------------------- | ----------------- | ------------ | ------------- |
| Array       | `int arr[n]`          | `array()`         | `[]`         | `[]`          |
| Linked List | custom class/struct   | `class Node`      | `class Node` | `class Node`  |
| Stack       | `stack<T>`            | `SplStack`        | `push/pop`   | `append/pop`  |
| Queue       | `queue<T>`            | `SplQueue`        | `push/shift` | `deque`       |
| Tree        | custom struct         | custom class      | custom class | custom class  |
| Graph       | `vector<vector<int>>` | arrays of arrays  | objects/Map  | dict of lists |
| Hash Table  | `unordered_map`       | associative array | `Map`        | `dict`        |

---

## Interview Questions & Answers / أسئلة المقابلات وإجوبتها

1. **What is the difference between an array and a linked list? / ما الفرق بين المصفوفة والقائمة المرتبطة؟**

   * **Explanation / شرح:**

     * An array stores elements contiguously in memory, so accessing any element by index is O(1). Inserting or deleting elements in the middle requires shifting and is O(n).
     * A linked list stores elements in nodes connected by pointers. Accessing the k-th node requires traversing from the head (O(k)), but inserting/deleting at a known node is O(1).
   * **C++ Example / مثال C++:**

     ```cpp
     // Array access vs Linked List insertion
     int arr[] = {1,2,3,4};
     // To insert 5 at index 2 in array:
     // Shift items right: arr[4]=arr[3]; arr[3]=arr[2]; arr[2]=5;

     // Linked list insertion:
     struct Node { int data; Node* next; };
     Node* head = new Node{1, nullptr};
     head->next = new Node{2, nullptr};
     // Insert 5 after head:
     Node* newNode = new Node{5, head->next};
     head->next = newNode;
     ```
   * **Arabic Summary / ملخص بالعربية:** تستطيع الوصول للمصفوفة مباشرة عبر الفهرس بسرعة، لكن تعديل وسطها مكلف، بينما القائمة المرتبطة تُعالج التعديل بسهولة على حساب سرعة الوصول.

2. **How do you implement a queue in Python? / كيف تنشئ كيو في بايثون؟**

   * **Explanation / شرح:**

     * Use `collections.deque` for efficient O(1) append and pop from both ends.
   * **Python Example / مثال بايثون:**

     ```python
     from collections import deque

     q = deque()
     # Enqueue
     q.append('task1')
     q.append('task2')
     print(q)  # deque(['task1', 'task2'])

     # Dequeue
     first = q.popleft()
     print(first)  # 'task1'
     ```
   * **Arabic Summary / ملخص بالعربية:** نستخدم deque لإضافة وإزالة العناصر بسرعة من البداية والنهاية دون تكلفة كبيرة.

3. **Explain collision handling in hash tables. / اشرح طرق معالجة التصادم في جداول الهاش.**

   * **Explanation / شرح:**

     * **Chaining:** Each bucket holds a list of entries. On collision, append to list. Worst-case lookup O(n) if many in one bucket.
     * **Open Addressing (Probing):** On collision, find next free slot based on probe sequence (linear, quadratic). Lookup stops when empty slot or key found.
   * **JavaScript Example / مثال جافاسكربت (Chaining):**

     ```js
     class HashTable {
       constructor(size=5) { this.buckets = Array(size).fill().map(() => []); }
       hash(key) { return key.length % this.buckets.length; }
       set(key, val) {
         const idx = this.hash(key);
         this.buckets[idx].push([key,val]);
       }
       get(key) {
         const idx = this.hash(key);
         for (let [k,v] of this.buckets[idx]) if (k===key) return v;
         return null;
       }
     }
     ```
   * **Arabic Summary / ملخص بالعربية:** في تقنية السلسلة نحتفظ بقائمة في كل خانة، أما في المعالجة المفتوحة نبحث عن خانة أخرى شاغرة.

4. **Describe tree traversal methods. / صف طرق اجتياز الأشجار.**

   * **Explanation / شرح:**

     * **Depth-First (DFS):** In-order, Pre-order, Post-order. Uses recursion or stack.
     * **Breadth-First (BFS):** Level-order using a queue.
   * **Python Examples / أمثلة بايثون:**

     ```python
     class Node:
         def __init__(self, val):
             self.val = val
             self.left = None
             self.right = None

     def inorder(node):
         if not node: return
         inorder(node.left)
         print(node.val)
         inorder(node.right)

     def level_order(root):
         from collections import deque
         q = deque([root])
         while q:
             n = q.popleft()
             print(n.val)
             if n.left: q.append(n.left)
             if n.right: q.append(n.right)
     ```
   * **Arabic Summary / ملخص بالعربية:** اجتياز الأشجار يمكن أن يكون عمقياً بأنواعه الثلاث أو عرضياً مستوى بمستوى باستخدام صف.

---

## Recent Trends & Updates / التحديثات الحديثة

* **English:** Many modern languages provide built-in modules (e.g., Python's `collections`, JS's `Map`) to simplify data structure usage. Newer C++ standards (C++17/20) enhance containers and performance. Functional programming paradigms influence immutable data structures (e.g., persistent trees).
* **العربية:** توفر معظم اللغات الحديثة وحدات مضمنة مثل `collections` في بايثون و `Map` في جافاسكربت لتبسيط استخدام هياكل البيانات. معايير ++C الحديثة (C++17/20) حسّنت الحاويات والأداء. تؤثر البرمجة الوظيفية على ظهور هياكل بيانات غير قابلة للتغيير (مثل الأشجار الدائمة).

*Prepared to help you master Data Structures in major languages and ace your technical interviews!*

---

## 7. Job Market Insights / رؤى سوق العمل

### 7.1 In-Demand Skills / المهارات المطلوبة

* **Scalability & Performance:** Employers expect you to choose data structures that handle large datasets efficiently. E.g., using **hash tables** for constant-time lookups in high-traffic web services.
* **Memory Management:** In languages like C++, understanding **pointer manipulation** and **custom allocators** for linked lists and trees is crucial in systems programming roles.
* **Concurrency:** Data structures such as **thread-safe queues** (`ConcurrentLinkedQueue` in Java, `std::mutex`-protected queues in C++) are vital for multi-threaded backend services.

### 7.2 Real-World Practices / ممارسات حقيقية

* **LRU Cache Implementation:** Common in web caching layers (e.g., CDNs). Combines a **hash table** for O(1) access with a **doubly linked list** to track usage order.
* **Batch Processing Queues:** As in ETL pipelines, implement **persistent queues** with disk-backed storage (e.g., Kafka topics) rather than in-memory `deque` when data sizes exceed RAM.

---

## 8. Additional Interview Questions & Practical Examples

1. **Implement an LRU Cache. / تنفيذ ذاكرة مخبئية LRU**

   * **Explanation / شرح:** Use a hash map for O(1) key lookup and a doubly linked list to maintain usage order.
   * **Python Example / مثال بايثون:**

     ```python
     from collections import OrderedDict

     class LRUCache:
         def __init__(self, capacity):
             self.cache = OrderedDict()
             self.capacity = capacity

         def get(self, key):
             if key not in self.cache: return -1
             self.cache.move_to_end(key)
             return self.cache[key]

         def put(self, key, value):
             if key in self.cache:
                 self.cache.move_to_end(key)
             self.cache[key] = value
             if len(self.cache) > self.capacity:
                 self.cache.popitem(last=False)
     ```
   * **Industrial Context / سياق صناعي:** تستخدم شبكات CDN مثل **Cloudflare** بنية LRU لضغط التخزين المؤقت للتقليل من زمن الاستجابة.

2. **Explain differences between arrays and vectors in C++. / اشرح الفروقات بين المصفوفات وvectors في ++C**

   * **Explanation / شرح:**

     * `std::vector` يدير الذاكرة تلقائيًا ويزيد السعة ديناميكيًا، بينما المصفوفة ثابتة الحجم.
     * استخدام `vector.reserve()` يقلل من عمليات إعادة تخصيص الذاكرة.
   * **C++ Example / مثال C++:**

     ```cpp
     #include <vector>

     std::vector<int> v;
     v.reserve(100); // allocate ahead
     for(int i=0;i<100;i++) v.push_back(i);

     int arr[100]; // fixed-size
     ```
   * **Arabic Summary / ملخص بالعربية:** يفضِّل المتخصصون استخدام `vector` للمرونة، مع حجز السعة مسبقًا لتحسين الأداء.

3. **How would you detect a cycle in a linked list? / كيف تكتشف حلقة في القائمة المرتبطة؟**

   * **Explanation / شرح:** استخدم خوارزمية **Floyd’s Tortoise and Hare** للحركة بسرعات مختلفة.
   * **JavaScript Example / مثال جافاسكربت:**

     ```js
     function hasCycle(head) {
       let slow = head, fast = head;
       while(fast && fast.next) {
         slow = slow.next;
         fast = fast.next.next;
         if (slow === fast) return true;
       }
       return false;
     }
     ```
   * **Industrial Context / سياق صناعي:** في خدمات المعالجة المتسلسلة للبيانات (stream processing)، تؤدي الحلقات إلى تسرب ذاكرة وأخطاء في البيانات.

4. **Describe how you would choose a data structure for a given problem. / كيف تختار هيكل البيانات لمشكلة معينة؟**

   * **Guidelines / إرشادات:**

     1. Analyze **access patterns** (random vs sequential).
     2. Estimate **size** and **growth** of data.
     3. Consider **operation costs** (insert, delete, search).
     4. Account for **concurrency** and **persistence** requirements.
   * **Example Scenario / مثال سيناريو:**

     * Problem: Real-time analytics on streaming sensor data.
     * Choice: Use a **circular buffer** for fixed-size window computations and a **min-heap** to find top-k readings efficiently.

*Prepared to help you master Data Structures in major languages and ace your technical interviews!*
