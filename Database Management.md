# Database Management & SQL && NoSQL / إدارة قواعد البيانات و SQL و NoSQL

## Summary / الملخص

**English:**
Database Management is the practice of storing, organizing, and retrieving data efficiently. SQL is used for relational databases, while NoSQL is designed for scalability and flexible data models.

**العربية:**
إدارة قواعد البيانات هي عملية تخزين وتنظيم واسترجاع البيانات بكفاءة. SQL تُستخدم مع قواعد البيانات العلائقية، بينما NoSQL تُصمم للتوسّع والنماذج المرنة للبيانات.

---

## 1. Concept / المفهوم

### 1.1 SQL (Structured Query Language) / لغة الاستعلام البنيوية

* **English:** Used to interact with relational databases (e.g., MySQL, PostgreSQL).
* **العربية:** تُستخدم للتعامل مع قواعد البيانات العلائقية مثل MySQL و PostgreSQL.

### 1.2 NoSQL (Not Only SQL) / قواعد البيانات غير العلائقية

* **English:** Designed for unstructured, scalable, and distributed data (e.g., MongoDB, Redis).
* **العربية:** مصممة للتعامل مع البيانات غير المهيكلة وقابلة للتوسع والتوزيع مثل MongoDB و Redis.

---

## 2. Code Examples / أمثلة الكود

### SQL (MySQL)

```sql
-- Create table
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100)
);

-- Insert data
INSERT INTO users (name, email) VALUES ('Ali', 'ali@example.com');

-- Query data
SELECT * FROM users;
```

### NoSQL (MongoDB)

```js
// Insert document
 db.users.insertOne({ name: "Ali", email: "ali@example.com" });

// Find documents
 db.users.find({});
```

### NoSQL (Redis)

```bash
SET user:1 "Ali"
GET user:1
```

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **SQL:** Inventory management, banking systems, ERP tools.
* **NoSQL:** Real-time analytics, caching (Redis), social media feeds (MongoDB).
* **Hybrid Systems:** Some apps use both SQL (for structured data) and NoSQL (for performance & flexibility).

---

## 4. Job Market Relevance / أهمية في سوق العمل

* Almost all software systems rely on some database.
* SQL is essential for data querying, reporting, and migrations.
* NoSQL is highly in demand for microservices, big data, and cloud-native apps.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **What is the difference between SQL and NoSQL? / ما الفرق بين SQL و NoSQL؟**

   * **Answer / الإجابة:** SQL uses structured schema and tables; NoSQL uses flexible document or key-value models.

2. **When would you use NoSQL over SQL? / متى تستخدم NoSQL بدلاً من SQL؟**

   * **Answer / الإجابة:** When dealing with unstructured data, high write/read speeds, or scalability needs.

3. **What is normalization? / ما هو التطبيع؟**

   * **Answer / الإجابة:** A process in SQL to reduce data redundancy and improve integrity.

4. **How does MongoDB differ from Redis? / كيف يختلف MongoDB عن Redis؟**

   * **Answer / الإجابة:** MongoDB stores JSON-like documents; Redis stores key-value pairs in memory for speed.

---

*Mastering databases is key to building fast, scalable, and secure applications.*
