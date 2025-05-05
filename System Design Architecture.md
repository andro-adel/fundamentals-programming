# System Design & Architecture / تصميم الأنظمة والمعمارية البرمجية

## Summary / الملخص

**English:**
System Design is the process of defining the architecture, components, modules, and data flow of a system. It ensures scalability, maintainability, and efficiency of applications.

**العربية:**
تصميم الأنظمة هو عملية تحديد بنية النظام والمكونات والوحدات وتدفق البيانات، مما يضمن قابلية التوسع والصيانة والكفاءة للتطبيقات.

---

## 1. Concept / المفهوم

### 1.1 System Design Levels / مستويات التصميم

* **High-Level Design (HLD):** Overview of system modules and their interaction.
* **Low-Level Design (LLD):** Detailed logic of components and internal workflows.

### 1.2 Architecture Styles / أنماط المعمارية

* **Monolithic:** All components in one unit.
* **Microservices:** Decomposed services communicating via APIs.
* **Serverless:** Logic handled by cloud providers on demand.
* **Event-driven:** Based on emitting and reacting to events.

### 1.3 Key Concepts / مفاهيم رئيسية

* **Scalability (التوسع):** Ability to handle growth.
* **Availability (التوفر):** Ensuring the system stays online.
* **Latency (الكمون):** Delay in processing requests.
* **Throughput (الإنتاجية):** Number of requests served per unit time.
* **Caching (التخزين المؤقت):** Speeding up data access.

---

## 2. Code Examples & Patterns / أمثلة كود وأنماط

### C++ – Load Balancer Simulation

```cpp
class Server {
public:
    void handleRequest(int id) {
        cout << "Handling request " << id << endl;
    }
};

int main() {
    vector<Server> servers(3);
    for (int i = 0; i < 10; ++i)
        servers[i % 3].handleRequest(i);
}
```

### PHP – Service Layer Architecture

```php
class UserService {
    public function register($userData) {
        // validate and save user
    }
}

$userService = new UserService();
$userService->register($_POST);
```

### JavaScript – Microservice Communication (Node.js)

```js
// Service A
app.get('/api/data', (req, res) => {
  res.send({ value: 123 });
});

// Service B
fetch('http://localhost:3000/api/data')
  .then(res => res.json())
  .then(data => console.log(data));
```

### Python – Caching Example

```python
from functools import lru_cache

@lru_cache(maxsize=128)
def get_data(id):
    return database_query(id)
```

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **Social Media:** Uses microservices for posts, notifications, search.
* **E-Commerce:** Combines caching, load balancing, and service-oriented architecture.
* **Streaming Services:** Event-driven models with high availability and low latency.

---

## 4. Job Market Relevance / أهمية في سوق العمل

* Critical for senior roles and technical interviews.
* Demonstrates ability to build scalable, fault-tolerant systems.
* Required for designing backend systems, cloud architecture, and distributed services.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **How would you design a URL shortening service? / كيف تصمم خدمة اختصار الروابط؟**

   * **Answer / الإجابة:** Use hash functions, database for mapping, caching layer, and load balancer.

2. **What is the difference between vertical and horizontal scaling? / ما الفرق بين التوسع الرأسي والأفقي؟**

   * **Answer / الإجابة:** Vertical adds more power to one server, horizontal adds more servers.

3. **What is CAP theorem? / ما هو مبدأ CAP؟**

   * **Answer / الإجابة:** A system can have at most two of Consistency, Availability, and Partition Tolerance.

4. **What is a load balancer? / ما هو موازن التحميل؟**

   * **Answer / الإجابة:** A component that distributes incoming traffic across multiple servers to ensure reliability.

---

*System Design is the foundation of reliable, performant, and scalable software.*
