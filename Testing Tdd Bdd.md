# Testing (TDD, BDD) / الاختبار (الاختبار المعتمد على الاختبارات والوصف)

## Summary / الملخص

**English:**
Testing is the process of validating that software works as expected. TDD (Test-Driven Development) and BDD (Behavior-Driven Development) are modern methodologies that improve code quality and team collaboration.

**العربية:**
الاختبار هو عملية التحقق من أن البرمجيات تعمل كما هو متوقع. TDD (التطوير المعتمد على الاختبارات) وBDD (التطوير المعتمد على السلوك) هما منهجيتان حديثتان لتحسين جودة الكود والتعاون بين أعضاء الفريق.

---

## 1. Concept / المفهوم

### 1.1 TDD (Test-Driven Development) / التطوير المعتمد على الاختبارات

* **English:** Write tests before writing the actual code.
* **العربية:** اكتب الاختبارات أولاً قبل كتابة الكود الفعلي.

**Cycle / دورة TDD:**

1. Write a test.
2. Run the test (should fail).
3. Write the code to pass the test.
4. Refactor the code.

### 1.2 BDD (Behavior-Driven Development) / التطوير المعتمد على السلوك

* **English:** Describe behavior in natural language (often Gherkin syntax), then implement the behavior.
* **العربية:** وصف السلوك بلغة طبيعية (غالباً باستخدام Gherkin)، ثم تنفيذ السلوك.

**Format:**

```
Given [initial context]
When [event occurs]
Then [expected result]
```

---

## 2. Code Examples / أمثلة الكود

### TDD in C++

```cpp
// Test
assert(add(2, 3) == 5);

// Implementation
int add(int a, int b) {
    return a + b;
}
```

### TDD in PHP

```php
// PHPUnit Test
$this->assertEquals(5, add(2, 3));

// Implementation
function add($a, $b) {
    return $a + $b;
}
```

### TDD in JavaScript

```js
test('adds 2 + 3 to equal 5', () => {
  expect(add(2, 3)).toBe(5);
});

function add(a, b) {
  return a + b;
}
```

### BDD in Python (Using Behave)

**Feature File (login.feature):**

```gherkin
Feature: User Login
  Scenario: Successful login
    Given the user is on login page
    When they enter valid credentials
    Then they should see the dashboard
```

**Step Definitions (steps/login\_steps.py):**

```python
@given('the user is on login page')
def step_login_page(context):
    open_login_page()

@when('they enter valid credentials')
def step_enter_creds(context):
    enter_credentials("user", "pass")

@then('they should see the dashboard')
def step_dashboard(context):
    assert is_dashboard_visible()
```

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **Startups:** Use TDD to quickly validate small features.
* **Large Teams:** BDD aligns business requirements with technical implementation.
* **APIs:** Write BDD specs for endpoint behaviors and use TDD to test request/response.

---

## 4. Job Market Relevance / أهمية في سوق العمل

* TDD improves code reliability and lowers bug rates.
* BDD enhances collaboration between developers, QA, and stakeholders.
* Required in companies with CI/CD pipelines and agile methodology.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **What is TDD? / ما هو TDD؟**

   * **Answer / الإجابة:** Writing tests before writing production code, ensuring better code coverage.

2. **How does BDD differ from TDD? / كيف يختلف BDD عن TDD؟**

   * **Answer / الإجابة:** BDD focuses on behavior and uses natural language, while TDD focuses on individual units of code.

3. **Why is testing important? / لماذا الاختبار مهم؟**

   * **Answer / الإجابة:** It ensures that the application behaves as expected and reduces production bugs.

4. **Can you apply TDD in frontend development? / هل يمكن تطبيق TDD في تطوير الواجهة الأمامية؟**

   * **Answer / الإجابة:** Yes, using tools like Jest for JavaScript or unittest for Python-based UIs.

---

*Testing is not just about finding bugs—it's about building trust in your software.*
