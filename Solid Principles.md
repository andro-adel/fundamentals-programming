# SOLID Principles / مبادئ SOLID

## Summary / الملخص

**English:**
SOLID is an acronym for five design principles that improve object-oriented software maintainability, flexibility, and scalability. These principles are:

1. **Single Responsibility Principle (SRP)**
2. **Open/Closed Principle (OCP)**
3. **Liskov Substitution Principle (LSP)**
4. **Interface Segregation Principle (ISP)**
5. **Dependency Inversion Principle (DIP)**

This document explains each principle with clear definitions, code examples in C++, PHP, JavaScript, and Python, real-world industry applications, and common interview questions with practical answers.

**العربية:**
SOLID عبارة عن اختصار لخمس مبادئ تصميمية تساعد على جعل البرمجيات الموجهة للكائنات أكثر قابلية للصيانة والمرونة والتوسع. هذه المبادئ هي:

1. **مبدأ المسؤولية الواحدة (SRP)**
2. **مبدأ المفتوح/المغلق (OCP)**
3. **مبدأ بديلة ليسكوف (LSP)**
4. **مبدأ تقسيم الواجهات (ISP)**
5. **مبدأ عكس التبعيات (DIP)**

هذا الملف يشرح كل مبدأ بتعريفات واضحة، وأمثلة كود بـ C++ وPHP وJavaScript وPython، وتطبيقات في سوق العمل، وأسئلة مقابلات متكررة مع إجابات عملية.

---

## 1. Single Responsibility Principle (SRP) / مبدأ المسؤولية الواحدة

### 1.1 Concept / المفهوم

* **English:** A class should have only one reason to change, meaning it handles only one responsibility.
* **العربية:** يجب أن تتحمل الفئة مسؤولية واحدة فقط، أي أن يكون سبب تغييرها واحدًا.

### 1.2 Code Examples / أمثلة الصياغة

```cpp
// C++: bad - one class does logging and data processing
enum LogLevel { INFO, ERROR };
class Worker {
  void processData();
  void log(LogLevel lvl, const string& msg);
};

// C++: good - separate Logger and Processor
class Logger { public: void log(const string& msg); };
class Processor { public: void process(); };
```

```php
// PHP: bad
class Report {
  public function generate() { /* ... */ }
  public function saveToFile() { /* ... */ }
}

// PHP: good
class ReportGenerator { function generate(){} }
class ReportSaver { function save($report){} }
```

```js
// JavaScript: bad
class User {
  constructor(data){ this.data=data; }
  saveToDatabase(){}
  renderProfile(){ }
}

// JS: good
class UserData { constructor(data){ this.data=data; }}
class UserRenderer { render(userData){} }
class UserRepository { save(userData){} }
```

```python
# Python: bad
class Order:
    def __init__(self, items): self.items=items
    def calculate_total(self): pass
    def save_to_db(self): pass

# Python: good
class OrderCalculator:
    def calculate(self, items): pass
class OrderRepository:
    def save(self, order): pass
```

### 1.3 Real-World Example / مثال عملي

In e-commerce platforms, separate services handle payment processing, order validation, and notification—each with its own class/module.

---

## 2. Open/Closed Principle (OCP) / مبدأ المفتوح/المغلق

### 2.1 Concept / المفهوم

* **English:** Software entities (classes, modules) should be open for extension but closed for modification.
* **العربية:** يجب أن تكون الكيانات البرمجية قابلة للإضافة دون تعديل الكود الأصلي.

### 2.2 Code Examples

```cpp
// C++: using virtual methods to extend behavior
class Shape { public: virtual double area()=0; };
class Circle : public Shape { /*...*/ double area() override; };
class Rectangle : public Shape { /*...*/ double area() override; };
```

```php
// PHP: using interfaces
interface PaymentMethod { function pay($amount); }
class CreditCard implements PaymentMethod { function pay($a){} }
class PayPal implements PaymentMethod { function pay($a){} }
```

```js
// JS: strategy pattern
class Formatter { format(data){} }
class JsonFormatter extends Formatter { format(d){ return JSON.stringify(d); } }
class XmlFormatter extends Formatter { format(d){ /* xml */ } }
```

```python
# Python: using duck typing
class Notifier:
    def send(self, msg): pass
class EmailNotifier(Notifier):
    def send(self,msg): pass
class SMSNotifier(Notifier):
    def send(self,msg): pass
```

### 2.3 Real-World Example

Frameworks like logging libraries allow new log formatters/handlers to be added without modifying core code.

---

## 3. Liskov Substitution Principle (LSP) / مبدأ بديلة ليسكوف

### 3.1 Concept / المفهوم

* **English:** Subtypes must be substitutable for their base types without altering program correctness.
* **العربية:** يجب أن تحل الأصناف الفرعية محل الأصناف الأساسية دون تغيير سلوك البرنامج.

### 3.2 Code Examples

```cpp
// C++: violate LSP
class Bird { virtual void fly(){} };
class Ostrich : public Bird { void fly() override { /* can't fly */ } };

// design: separate interfaces
class Flyer { virtual void fly()=0; };
class Bird { /* common */ };
class Sparrow : public Bird, public Flyer { void fly(){} };
```

```php
// PHP: LSP violation example omitted for brevity
```

```js
// JS: correct subtype
class Rectangle { setWidth(w){ } setHeight(h){} }
class Square extends Rectangle {
  setWidth(w){ super.setWidth(w); super.setHeight(w); }
  setHeight(h){ super.setWidth(h); super.setHeight(h); }
}
```

```python
# Python: LSP-safe
class FileReader:
    def read(self): pass
class TextFileReader(FileReader):
    def read(self): return 'text'
```

### 3.3 Real-World Example

Payment gateway classes implement a common interface; replacing one provider with another does not break transaction handling.

---

## 4. Interface Segregation Principle (ISP) / مبدأ تقسيم الواجهات

### 4.1 Concept / المفهوم

* **English:** Clients should not be forced to depend on interfaces they do not use.
* **العربية:** يجب ألا تُجبر الفئات على الاعتماد على واجهات لا تحتاج إليها.

### 4.2 Code Examples

```cpp
// C++: split large interface
class IPrinter { virtual void print(); virtual void scan(); };
class SimplePrinter : public IPrinter { void print(){} void scan(){ throw; } };

// better
class IPrint { virtual void print()=0; };
class IScan { virtual void scan()=0; };
class Printer : public IPrint { void print(){} };
```

```php
// PHP: use small interfaces
interface Reader { function read(); }
interface Writer { function write($data); }
```

```js
// JS:
class IReadable { read(){} }
class IWritable { write(d){} }
```

```python
# Python: ABCs
def read_interface(obj): obj.read()
```

### 4.3 Real-World Example

Microservices expose narrow APIs (REST endpoints) focused on specific actions rather than one monolithic interface.

---

## 5. Dependency Inversion Principle (DIP) / مبدأ عكس التبعيات

### 5.1 Concept / المفهوم

* **English:** High-level modules should not depend on low-level modules; both should depend on abstractions.
* **العربية:** يجب أن تعتمد الوحدات العليا والدنيا على التجريدات، وليس على بعضها البعض مباشرة.

### 5.2 Code Examples

```cpp
// C++: depending on interface
class IRepository { public: virtual void save(); };
class UserRepository : public IRepository { void save(){} };
class UserService {
  IRepository& repo;
  UserService(IRepository& r): repo(r){}
};
```

```php
// PHP: constructor injection
declare(strict_types=1);
class UserService {
  public function __construct(Logger $logger) { $this->logger = $logger; }
}
```

```js
// JS: dependency injection
tclass EmailService {}
class UserController {
  constructor(emailService) { this.emailService = emailService; }
}
```

```python
# Python: use protocols/typing
from typing import Protocol
class Notifier(Protocol):
    def send(self,msg): ...
class AlertService:
    def __init__(self, notifier: Notifier): self.notifier=notifier
```

### 5.3 Real-World Example

In large apps, services receive database or messaging clients via dependency injection frameworks (Spring, Symfony) to decouple modules.

---

## Interview Questions & Practical Examples / أسئلة مقابلات وأمثلة عملية

1. **Explain SOLID principles in your own words. / اشرح مبادئ SOLID بكلماتك.**
2. **How does DIP improve testability? / كيف يحسن DIP قابلية الاختبار؟**
3. **Provide an example of SRP violation and refactor. / أعط مثالًا لانتهاك SRP وقم بإعادة الهيكلة.**
4. **Why is ISP important in API design? / لماذا يعد ISP مهمًا في تصميم الواجهات؟**

---

*Prepared to help you apply SOLID Principles in major languages and excel in interviews!*
