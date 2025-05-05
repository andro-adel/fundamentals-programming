# Object-Oriented Programming (OOP) / البرمجة الموجهة للكائنات

## Summary / الملخص

**English:**
Object-Oriented Programming (OOP) is a paradigm organizing software around *objects*, which combine data and behaviors. This document covers core OOP principles—classes & objects, encapsulation, inheritance, polymorphism, abstraction—and demonstrates implementation in C++, PHP, JavaScript, and Python. For each concept, we provide syntax, real-world industry use cases, practical code examples, and illustrative interview questions with detailed answers. We conclude with job market insights and latest trends to ensure readiness for technical interviews and professional development.

**العربية:**
البرمجة الموجهة للكائنات هي نمط برمجي ينظم البرامج حول *الكائنات* التي تجمع بين البيانات والسلوكيات. يغطي هذا الملف المبادئ الأساسية—الفئات والكائنات، التغليف، الوراثة، تعدد الأشكال، التجريد—مع تطبيقات عملية في C++، PHP، JavaScript، Python. لكل مبدأ نوفر الصياغة البرمجية، أمثلة من سوق العمل، أمثلة كود تطبيقية، وأسئلة مقابلات بإجاباتها. نختم برؤى سوق العمل وأحدث التوجهات لضمان الجاهزية.

---

## 1. Classes & Objects / الفئات والكائنات

### 1.1 Concept / المفهوم

* **English:** A *class* defines a blueprint for data (attributes) and functions (methods). An *object* is an instance of a class.
* **العربية:** *الفئة* تحدد قالبًا للبيانات (الخصائص) والدوال (الطرق). و*الكائن* هو مثيل لفئة.

### 1.2 Syntax Examples / أمثلة الصياغة

| Language       | Class Definition                                              | Instantiation                                   |
| -------------- | ------------------------------------------------------------- | ----------------------------------------------- |
| **C++**        | `class Person { public: string name; void greet(); };`        | `Person p; p.name="Alice"; p.greet();`          |
| **PHP**        | `class Person { public $name; function greet(){}`             | `$p=new Person(); $p->name="Ali"; $p->greet();` |
| **JavaScript** | `class Person { constructor(name){this.name=name;} greet(){}` | `const p=new Person('Bob'); p.greet();`         |
| **Python**     | \`class Person:                                               |                                                 |

```
def __init__(self,name): self.name=name
def greet(self): ...` | `p=Person('Aya'); p.greet()` |
```

### 1.3 Real-World Example / مثال عملي من السوق

In a web application, a `User` class encapsulates user data and authentication methods; each logged-in visitor is a `User` object handling profile and session behaviors.

---

## 2. Encapsulation / التغليف

### 2.1 Concept / المفهوم

* **English:** Encapsulation restricts direct access to internal state and exposes behavior via methods. Promotes modularity and security.
* **العربية:** التغليف يقيد الوصول المباشر لحالة الكائن الداخلية ويعرض السلوك عبر الطرق. يعزز الوحدة والأمان.

### 2.2 Syntax Examples

```cpp
// C++
class Account { private: double balance; public:
  void deposit(double amt){ balance+=amt;} double getBalance(){ return balance; }};
```

```python
# Python
class Account:
  def __init__(self): self.__balance=0
  def deposit(self,amt): self.__balance+=amt
  def get_balance(self): return self.__balance
```

### 2.3 Industry Use Case / حالة استخدام صناعية

Financial systems enforce encapsulation in `Account` objects to prevent unauthorized balance manipulation and ensure only controlled methods update the state.

---

## 3. Inheritance / الوراثة

### 3.1 Concept / المفهوم

* **English:** Inheritance allows a *child* class to acquire attributes and methods from a *parent* class, enabling code reuse.
* **العربية:** الوراثة تتيح للفئة الفرعية اقتباس الخصائص والطرق من الفئة الأم، مما يعزز إعادة استخدام الكود.

### 3.2 Syntax Examples

```js
// JavaScript
class Animal { speak(){ console.log('...'); }}
class Dog extends Animal { speak(){ console.log('Woof'); }}
```

```php
// PHP
class Animal { function speak(){}}
class Dog extends Animal { function speak(){ echo 'Woof'; }}
```

### 3.3 Practical Example / مثال عملي

In UI frameworks, a base `Component` class defines rendering and state handling; specialized components like `Button` or `Modal` inherit common functionality and override specific methods.

---

## 4. Polymorphism / تعدد الأشكال

### 4.1 Concept / المفهوم

* **English:** Polymorphism allows objects of different classes to be treated through a common interface, with method calls resolved at runtime (dynamic) or compile-time (static).
* **العربية:** يتيح تعدد الأشكال معاملة كائنات من فئات مختلفة عبر واجهة موحدة، مع حل الاستدعاءات في وقت التشغيل أو الترجمة.

### 4.2 Syntax Examples

```cpp
// C++
class Shape { public: virtual void draw()=0; };
class Circle : public Shape { void draw() override { /*...*/ }};
```

```python
# Python
class Shape:
  def draw(self): raise NotImplementedError
class Circle(Shape):
  def draw(self): print('circle')
```

### 4.3 Real-World Use Case

Payment gateways handle different `PaymentMethod` objects (CreditCard, PayPal) via a unified `processPayment()` interface, invoking the correct implementation at runtime.

---

## 5. Abstraction / التجريد

### 5.1 Concept / المفهوم

* **English:** Abstraction hides complexity by exposing only necessary components of an object or system.
* **العربية:** التجريد يخفي التعقيد عن طريق عرض المكونات الضرورية فقط من كائن أو نظام.

### 5.2 Example

Database connectors provide a generic `connect()` and `query()` interface, while underlying drivers (MySQL, PostgreSQL) implement specific protocols.

---

## 6. Job Market Insights / رؤى سوق العمل

* **Design Patterns:** Knowledge of OOP patterns (Factory, Singleton, Observer) is highly valued in enterprise applications.
* **SOLID Principles:** Employers expect familiarity with Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion to maintain scalable codebases.
* **Framework Usage:** Many web frameworks (Laravel, Django, Spring) build heavily on OOP; practical experience is a plus.

---

## 7. Interview Questions & Practical Examples / أسئلة مقابلات وأمثلة عملية

1. **What is the difference between composition and inheritance? / ما الفرق بين التكوين والوراثة؟**

   * **Explanation / شرح:** Composition embeds objects as members, for flexible relationships; inheritance defines an “is-a” relationship.
   * **Example / مثال:** A `Car` **has-a** `Engine` (composition) vs. a `SportsCar` **is-a** `Car` (inheritance).

2. **How do you implement interface in PHP? / كيف تنشئ واجهة Interface في PHP؟**

   ```php
   interface Logger { public function log($msg); }
   class FileLogger implements Logger { function log($msg){ file_put_contents('log.txt',$msg); }}
   ```

3. **Explain method overloading vs overriding. / اشرح التحميل الزائد للطرق مقابل التجاوز.**

   * *Overloading:* Same method name, different parameters (compile-time).
   * *Overriding:* Child class redefines parent method (runtime).

4. **Describe SOLID principles with examples. / صف مبادئ SOLID مع أمثلة.**

   * **Single Responsibility:** Each class does one thing. E.g., `UserService` handles business logic, not DB access.
   * **Open/Closed:** Extend classes via inheritance/plugins without modifying existing code. E.g., payment plugins.

*Prepared to help you master OOP in major languages and ace your technical interviews!*
