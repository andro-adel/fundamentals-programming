# DRY (“Don’t Repeat Yourself”) Principle / مبدأ لا تكرر نفسك

## Summary / الملخص

**English:**
The DRY principle (Don’t Repeat Yourself) promotes reducing code duplication to improve maintainability, readability, and scalability. This document explains DRY with definitions, code examples in C++, PHP, JavaScript, and Python, showcases real-world use cases, provides job-market relevance, and lists common interview questions with example-driven answers.

**العربية:**
يشجع مبدأ DRY (لا تكرر نفسك) على تقليل تكرار الشيفرة لتحسين سهولة الصيانة، والقراءة، وقابلية التوسع. يشرح هذا الملف المبدأ بالتعريفات، وأمثلة كود في C++، PHP، JavaScript، Python، ويعرض أمثلة عملية من سوق العمل، وأهم الأسئلة في المقابلات مع إجابات تدعمها أمثلة عملية.

---

## 1. Concept / المفهوم

* **English:** DRY means every piece of knowledge or logic should have a single, unambiguous representation in the codebase.
* **العربية:** يعني DRY أن كل جزء من المعرفة أو المنطق يجب أن يكون له تمثيل وحيد وغير غامض في الشيفرة.

### 1.1 Benefits / الفوائد

* Reduces bugs by centralizing logic.
* Simplifies maintenance: updates in one place propagate everywhere.
* Increases readability and consistency.

---

## 2. Code Examples / أمثلة الكود

### 2.1 C++

**Before DRY:**

```cpp
int add(int a, int b) { return a + b; }
int sub(int a, int b) { return a - b; }
int mul(int a, int b) { return a * b; }
```

**After DRY (template + function pointer):**

```cpp
template<typename Func>
int operate(int a, int b, Func f) { return f(a, b); }

int main() {
    auto sum = operate(5, 3, [](int x, int y){ return x + y; });
    auto diff = operate(5, 3, [](int x, int y){ return x - y; });
}
```

### 2.2 PHP

**Before DRY:**

```php
function getUserById($id) { /* database lookup */ }
function getOrderById($id) { /* database lookup */ }
```

**After DRY (single function with type parameter):**

```php
function fetchById($table, $id) {
    // SELECT * FROM `$table` WHERE id = :id
}
// Usage:
$user = fetchById('users', 5);
$order = fetchById('orders', 10);
```

### 2.3 JavaScript

**Before DRY:**

```js
function logInfo(msg) { console.log('INFO: ' + msg); }
function logError(msg) { console.log('ERROR: ' + msg); }
```

**After DRY (higher-order function):**

```js
function createLogger(level) {
  return function(msg) { console.log(level + ': ' + msg); };
}
const info = createLogger('INFO');
const error = createLogger('ERROR');
```

### 2.4 Python

**Before DRY:**

````python
def connect_mysql(): pass
def connect_postgres(): pass\```
**After DRY (factory pattern):**
```python
def get_connection(db_type):
    if db_type == 'mysql': return MySQLConnection()
    if db_type == 'postgres': return PostgresConnection()
````

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **API Endpoints:** Use common controllers or services instead of duplicating request handling logic across routes.
* **Configuration Management:** Centralize config in environment files or centralized service (e.g., Consul).
* **UI Components:** In React/Vue, create reusable components rather than copying structure and styling.

---

## 4. Job Market Relevance / أهمية في سوق العمل

* **Frameworks & Libraries:** Modern frameworks (Laravel, Django, React) emphasize DRY via conventions and utilities.
* **Microservices:** Shared libraries for common tasks (logging, auth) ensure consistency across services.
* **DevOps:** Infrastructure as Code (Terraform modules) prevents duplication of resource definitions.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **What is the DRY principle and why is it important? / ما هو مبدأ DRY ولماذا هو مهم؟**

   * **Answer / الإجابة:** DRY prevents code duplication by centralizing logic. It reduces bugs and eases maintenance.

2. **Give an example of violating DRY and how to fix it. / أعطِ مثالاً على انتهاك DRY وكيف تصلحه؟**

   * **Example / مثال:** Duplicated validation code in multiple services; fix by extracting to a shared utility function or module.

3. **How does DRY relate to design patterns? / كيف يرتبط DRY بنماذج التصميم؟**

   * **Answer / الإجابة:** Many patterns (Factory, Strategy, Decorator) promote DRY by abstracting common behavior into reusable structures.

4. **Can DRY be overused? / هل يمكن الإفراط في استخدام DRY؟**

   * **Answer / الإجابة:** Yes. Over-abstraction may lead to complex code and tight coupling; balance with YAGNI (You Aren't Gonna Need It).

---

*Prepared to help you apply DRY Principle in major languages and excel in technical interviews!*
