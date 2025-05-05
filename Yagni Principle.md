# YAGNI ("You Aren’t Gonna Need It") Principle / مبدأ "لن تحتاجه"

## Summary / الملخص

**English:**
YAGNI stands for "You Aren’t Gonna Need It." It’s a principle of extreme programming that advises developers to avoid adding functionality until it is actually needed.

**العربية:**
YAGNI هو اختصار لـ "You Aren’t Gonna Need It" ويعني "أنت لن تحتاجه". هو مبدأ من مبادئ البرمجة المتطرفة ينصح بعدم إضافة أي وظائف أو مميزات إلا إذا كانت مطلوبة فعلاً.

---

## 1. Concept / المفهوم

* **English:** Don’t build features "just in case"; implement only what is required now.
* **العربية:** لا تنفّذ وظائف أو مميزات من باب الاحتياط؛ نفّذ فقط ما هو مطلوب حالياً.

### 1.1 Goals / الأهداف

* Reduce wasted development time.
* Avoid unused, untested, and buggy code.
* Focus on immediate business needs.

---

## 2. Code Examples / أمثلة الكود

### 2.1 C++

**Before YAGNI (feature not needed yet):**

```cpp
class ReportGenerator {
    void exportToPDF(); // Not needed yet
    void exportToExcel(); // Also unused
};
```

**After YAGNI:**

```cpp
class ReportGenerator {
    void generateSummary(); // Implement what's required only
};
```

### 2.2 PHP

**Before YAGNI:**

```php
class Payment {
    public function payWithBitcoin() {}
    public function payWithStripe() {}
    public function payWithPayPal() {}
}
```

**After YAGNI:**

```php
class Payment {
    public function payWithStripe() {}
}
// Only Stripe is needed now
```

### 2.3 JavaScript

**Before YAGNI:**

```js
function renderChart(type) {
  if (type === 'pie') {/* ... */}
  else if (type === 'bar') {/* ... */}
  else if (type === 'line') {/* ... */}
}
```

**After YAGNI (only bar chart needed):**

```js
function renderBarChart(data) {
  // Render bar chart only
}
```

### 2.4 Python

**Before YAGNI:**

```python
class User:
    def send_email(self): pass
    def send_sms(self): pass
    def send_push(self): pass
```

**After YAGNI:**

```python
class User:
    def send_email(self): pass  # Only email is required for now
```

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **Startups:** Avoid building future modules unless user stories or client feedback require them.
* **APIs:** Don’t expose unused endpoints or support multiple formats unless required.
* **UI Components:** Don’t prepare for all screen sizes/devices unless the product is live across them.

---

## 4. Job Market Relevance / أهمية في سوق العمل

* Saves time and keeps development focused on business priorities.
* Makes teams more agile and responsive to real user needs.
* Avoids maintenance overhead from unused code.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **What is the YAGNI principle? / ما هو مبدأ YAGNI؟**

   * **Answer / الإجابة:** It advises developers not to implement a feature unless it's currently needed.

2. **Why is YAGNI important in agile development? / لماذا YAGNI مهم في التطوير الرشيق؟**

   * **Answer / الإجابة:** Agile encourages rapid, incremental development based on actual needs; YAGNI supports this by reducing unnecessary work.

3. **Can YAGNI conflict with scalability planning? / هل YAGNI يتعارض مع التخطيط للتوسع؟**

   * **Answer / الإجابة:** Not necessarily. Plan for scalability, but implement features only when they’re required.

4. **How can overengineering hurt a project? / كيف يمكن للمبالغة في بناء المميزات أن تضر المشروع؟**

   * **Answer / الإجابة:** It wastes time, complicates code, introduces unused bugs, and slows down delivery.

---

*Stick to what’s required. YAGNI helps you stay focused, agile, and efficient in real-world projects.*
