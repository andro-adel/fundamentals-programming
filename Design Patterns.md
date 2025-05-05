# Design Patterns / أنماط التصميم

## Summary / الملخص

**English:**
Design Patterns are reusable solutions to common software design problems. They offer best practices for organizing code in a scalable, efficient, and maintainable way.

**العربية:**
أنماط التصميم هي حلول قابلة لإعادة الاستخدام لمشاكل شائعة في تصميم البرمجيات. وهي تمثل أفضل الممارسات لتنظيم الشيفرة بطريقة قابلة للتوسّع وسهلة الصيانة وفعالة.

---

## 1. Concept / المفهوم

* **English:** Design patterns abstract common programming problems and provide tested and proven development templates.
* **العربية:** أنماط التصميم تُجرد مشاكل البرمجة الشائعة وتوفر قوالب مجربة ومثبتة للتطوير.

### 1.1 Types of Patterns / أنواع الأنماط:

* **Creational / الإنشائية** – Object creation (e.g., Singleton, Factory)
* **Structural / الهيكلية** – Class and object composition (e.g., Adapter, Decorator)
* **Behavioral / السلوكية** – Communication between objects (e.g., Observer, Strategy)

---

## 2. Code Examples / أمثلة الكود

### Singleton Pattern (C++)

```cpp
class Logger {
private:
    static Logger* instance;
    Logger() {}
public:
    static Logger* getInstance() {
        if (!instance) instance = new Logger();
        return instance;
    }
};
```

### Factory Pattern (PHP)

```php
interface Notification {
    public function notify();
}
class Email implements Notification {
    public function notify() { echo "Email sent"; }
}
class NotificationFactory {
    public static function create($type) {
        if ($type === 'email') return new Email();
    }
}
```

### Observer Pattern (JavaScript)

```js
class Subject {
    constructor() { this.observers = []; }
    subscribe(observer) { this.observers.push(observer); }
    notify(msg) { this.observers.forEach(o => o.update(msg)); }
}
class Observer {
    update(msg) { console.log("Received:", msg); }
}
```

### Strategy Pattern (Python)

```python
class PaymentStrategy:
    def pay(self, amount): pass

class PayPal(PaymentStrategy):
    def pay(self, amount): print(f"Paying {amount} via PayPal")

def process_payment(strategy, amount):
    strategy.pay(amount)
```

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **Factory:** Used in API response parsing or object creation based on config.
* **Observer:** Real-time systems like chat apps or notification systems.
* **Decorator:** Extend UI functionality without modifying existing components.
* **Strategy:** Payment gateways, shipping algorithms, or sorting strategies.

---

## 4. Job Market Relevance / أهمية في سوق العمل

* Shows that the developer writes scalable, maintainable code.
* Many large systems rely on proper pattern usage.
* Patterns are common discussion points in code reviews and system design interviews.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **What are design patterns? / ما هي أنماط التصميم؟**

   * **Answer / الإجابة:** Reusable solutions to common design problems, helping write cleaner and more maintainable code.

2. **What’s the difference between Factory and Singleton? / ما الفرق بين Factory و Singleton؟**

   * **Answer / الإجابة:** Factory creates new objects, Singleton ensures one instance only.

3. **Where is Observer Pattern used? / أين يُستخدم نمط Observer؟**

   * **Answer / الإجابة:** In systems needing real-time updates like notification systems.

4. **How does Strategy Pattern support Open/Closed Principle? / كيف يدعم نمط Strategy مبدأ الانفتاح/الانغلاق؟**

   * **Answer / الإجابة:** Allows extending behaviors without modifying existing code.

---

*Mastering design patterns gives you a strong foundation for building complex, clean, and scalable applications.*
