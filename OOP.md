// ===============================
// Object-Oriented Programming: مبادئ، مشاكل وحلول (2025)
// Examples in C++, JavaScript & PHP
// ===============================

/*
Summary / ملخص:
This document covers OOP principles, common problems (like multiple inheritance, access conflicts), and solutions with bilingual comments and examples in C++, JS, PHP.
هذه الوثيقة تغطي مبادئ البرمجة الكائنية، المشاكل الشائعة (مثل الوراثة المتعددة، تعارض صلاحيات الوصول)، والحلول مع تعليقات بالإنجليزية والعربية وأمثلة في C++، JavaScript، وPHP.
*/

// ===============================
// 1. PRINCIPLES / المبادئ
// ===============================

// 1.1 Encapsulation / التغليف
// EN: Hides internal state; exposes methods only. Improves data integrity.
// AR: يخفي الحالة الداخلية للكائن ويعرض الدوال فقط. يحسن سلامة البيانات.

// C++
class Account {
private:
    double balance;          // AR: رصيد الحساب
public:
    void deposit(double amt) { if (amt>0) balance+=amt; } // EN: add money
    double getBalance() const { return balance; }         // AR: الحصول على الرصيد
};

// JavaScript
class AccountJS {
    #balance = 0;            // AR: رصيد
    deposit(amt) { if (amt>0) this.#balance+=amt; } // EN: add money
    getBalance() { return this.#balance; }         // AR: احصل على الرصيد
}

// PHP
class AccountPHP {
    private float $balance = 0;                     // AR: رصيد
    public function deposit(float $amt): void { if($amt>0) $this->balance+=$amt; } // EN: add
    public function getBalance(): float { return $this->balance; }               // AR: احصل
}


// 1.2 Inheritance / الوراثة
// EN: "is-a" relationship; reuse code.
// AR: علاقة "هو-نوع-من" لإعادة استخدام الكود.

// C++
class Vehicle {
public:
    void start() { std::cout<<"Vehicle starts\n"; } // AR: تشغيل المركبة
};
class Car : public Vehicle { /* inherits start() */ };

// JavaScript
class VehicleJS {
    start() { console.log("Vehicle starts"); }   // AR: تشغيل المركبة
}
class CarJS extends VehicleJS {}                    // يرث start()

// PHP
class VehiclePHP {
    public function start(): void { echo "Vehicle starts\n"; } // AR: تشغيل
}
class CarPHP extends VehiclePHP {}                    // يرث start()


// 1.3 Polymorphism / تعدد الأشكال
// EN: Same interface, different implementations at runtime.
// AR: نفس الواجهة، تنفيذات مختلفة أثناء التشغيل.

// C++
class Shape {
public:
    virtual void draw() { std::cout<<"Drawing shape\n"; }
};
class Circle : public Shape {
    void draw() override { std::cout<<"Drawing circle\n"; }
};

// JavaScript
class ShapeJS {
    draw() { console.log("Drawing shape"); }
}
class CircleJS extends ShapeJS {
    draw() { console.log("Drawing circle"); }
}

// PHP
class ShapePHP {
    public function draw(): void { echo "Drawing shape\n"; }
}
class CirclePHP extends ShapePHP {
    public function draw(): void { echo "Drawing circle\n"; }
}


// 1.4 Abstraction / التجريد
// EN: Expose only essential features, hide details.
// AR: اعرض الميزات الأساسية فقط، اخفِ التفاصيل.

// C++
class IDataSource {
public:
    virtual std::string read() = 0;              // AR: دالة تجريدية للقراءة
};
class FileSource : public IDataSource {
    std::string read() override { return "File data"; } // AR: قراءة من ملف
};

// JavaScript (simulate)
class IDataSourceJS {
    read() { throw new Error("Not implemented"); }        // AR: غير مُطبق
}
class FileSourceJS extends IDataSourceJS {
    read() { return "File data"; }                        // AR: قراءة
}

// PHP
interface IDataSourcePHP {
    public function read(): string;                           // AR: واجهة للتجريد
}
class FileSourcePHP implements IDataSourcePHP {
    public function read(): string { return "File data"; }  // AR: قراءة
}


// 1.5 Interfaces vs Abstract Classes
// EN: Interface declares methods only; Abstract can have implementations.
// AR: الواجهة فقط تعلن عن الدوال، الكلاس المجرد يمكن أن يحتوي على تنفيذات.

// C++ (simulate interface)
class IPrinter {
public:
    virtual void print() = 0;                    // AR: واجهة طباعة
};

// Abstract class
class AbstractPrinter {
public:
    virtual void print() = 0;                    // AR: دالة مطلقة
    void selfTest() { std::cout<<"Test OK\n";} // AR: اختبار داخلي
};

// JavaScript
// Interface: use duck typing (object shape)
// Abstract: use base class with throw
class AbstractPrinterJS {
    print() { throw new Error("Must implement print"); }
    selfTest() { console.log("Test OK"); }
}

// PHP
interface IPrinterPHP {
    public function print(): void;               // AR: واجهة
}
abstract class AbstractPrinterPHP {
    abstract public function print(): void;      // AR: تجريدية
    public function selfTest(): void { echo "Test OK\n"; } // AR: اختبار
}


// ===============================
// 2. COMMON PROBLEMS / المشاكل الشائعة
// ===============================

// 2.1 Multiple Inheritance / الوراثة المتعددة (Diamond Problem)
// EN: Ambiguity when two paths inherit same base.
// AR: غموض عند وجود مسارين يرثان نفس الأساس.

// C++ ambiguous
class A { public: void f(){ std::cout<<"A::f\n";} };
class B : public A {};
class C : public A {};
class D : public B, public C { /* D.f() ambiguous */ };

// C++ solution: virtual inheritance
class A2 { public: virtual void f(){ std::cout<<"A2::f\n";} };
class B2 : virtual public A2 {};
class C2 : virtual public A2 {};
class D2 : public B2, public C2 { /* no ambiguity */ };

// JS/PHP: prefer composition


// 2.2 Access Modifier Clash / تعارض private/public
// EN: Need private in class but public outside?
// AR: تريد خاص داخل الكلاس وعام خارجه؟

// Use protected + getters/setters
class Example {
protected:
    int secret = 42;                      // AR: متغير محمي
public:
    int getSecret() { return secret; }    // AR: دالة وصول
};


// 2.3 Tight Coupling & Deep Hierarchies
// EN: Deep inheritance makes code fragile.
// AR: التسلسل الوراثي العميق يؤثر على صلابة الكود.

// Solution: prefer interfaces/abstract + composition

// 2.4 Lack of Dependency Injection
// EN: Hard-coded dependencies reduce testability.
// AR: الاعتماديات المحفورة تقلل من قابلية الاختبار.

// PHP Example
interface Logger { public function log(string $m): void; }
class ConsoleLogger implements Logger {
    public function log(string $m): void { echo $m; }
}
class UserService {
    private Logger $logger;
    public function __construct(Logger $logger) { $this->logger = $logger; }
    public function register() { $this->logger->log("User registered\n"); }
}


// ===============================
// 3. SUMMARY / ملخص
// ===============================
// • Encapsulation / التغليف
// • Inheritance / الوراثة
// • Polymorphism / تعدد الأشكال
// • Abstraction / التجريد
// • Interfaces vs Abstract Classes
// • Common Problems: Multiple Inheritance, Access Clash, Coupling, DI
// • Solutions: Virtual Inheritance, Composition, Protected+Getters, DI
// ===============================
