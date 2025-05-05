# Cloud Computing Fundamentals / أساسيات الحوسبة السحابية

## Summary / الملخص

**English:**
Cloud Computing is the delivery of computing services (servers, storage, databases, networking, software) over the internet, allowing businesses to scale, reduce cost, and innovate faster.

**العربية:**
الحوسبة السحابية هي تقديم خدمات الحوسبة (الخوادم، التخزين، قواعد البيانات، الشبكات، والبرمجيات) عبر الإنترنت، مما يُمكّن الشركات من التوسع، تقليل التكاليف، وتسريع الابتكار.

---

## 1. Concept / المفهوم

### 1.1 Cloud Models / نماذج السحابة

* **IaaS (Infrastructure as a Service):** Raw compute resources (e.g., AWS EC2).
* **PaaS (Platform as a Service):** Tools and platforms for developers (e.g., Heroku, Google App Engine).
* **SaaS (Software as a Service):** Ready-to-use applications (e.g., Gmail, Dropbox).

### 1.2 Deployment Types / أنواع النشر

* **Public Cloud:** Shared infrastructure (e.g., AWS, Azure, GCP).
* **Private Cloud:** Used exclusively by one organization.
* **Hybrid Cloud:** Combines public and private.

### 1.3 Key Benefits / الفوائد الرئيسية

* Cost-efficiency / فعالية التكلفة
* Scalability / قابلية التوسع
* Availability / التوفر العالي
* Security / الأمان
* Global Reach / الوصول العالمي

---

## 2. Code Examples / أمثلة الكود

### Python – Upload File to AWS S3

```python
import boto3
s3 = boto3.client('s3')
s3.upload_file('file.txt', 'mybucket', 'file.txt')
```

### JavaScript – Connect to Firebase

```javascript
import { initializeApp } from 'firebase/app';
const firebaseConfig = {
  apiKey: "API_KEY",
  authDomain: "yourapp.firebaseapp.com",
};
initializeApp(firebaseConfig);
```

### PHP – Use Google Cloud Storage

```php
use Google\Cloud\Storage\StorageClient;
$storage = new StorageClient();
$bucket = $storage->bucket('my-bucket');
$bucket->upload(fopen('/path/to/file', 'r'));
```

### C++ – REST API Call to Cloud

```cpp
#include <cpprest/http_client.h>
using namespace web::http;
using namespace web::http::client;

http_client client(U("https://api.cloudservice.com/data"));
client.request(methods::GET).then([](http_response response) {
    std::wcout << response.to_string().c_str();
});
```

---

## 3. Real-World Use Cases / أمثلة سوق العمل

* **Startups:** Host scalable apps using AWS or GCP.
* **Enterprises:** Hybrid cloud for secure and cost-effective data processing.
* **AI/ML:** Training models on GPU-backed cloud environments.
* **DevOps:** CI/CD pipelines running in the cloud.

---

## 4. Job Market Relevance / أهمية في سوق العمل

* Essential for backend and DevOps roles.
* Common in remote and distributed applications.
* Frequently listed in job descriptions for full-stack, cloud, and platform engineers.

---

## 5. Interview Questions & Answers / أسئلة مقابلات وإجاباتها

1. **What is the difference between IaaS, PaaS, and SaaS? / ما الفرق بين IaaS وPaaS وSaaS؟**

   * **Answer / الإجابة:** IaaS offers infrastructure, PaaS offers development platforms, and SaaS offers ready-to-use applications.

2. **What are the advantages of cloud computing? / ما هي فوائد الحوسبة السحابية؟**

   * **Answer / الإجابة:** Lower costs, flexible resources, faster innovation, and global access.

3. **How is data secured in the cloud? / كيف يتم تأمين البيانات في السحابة؟**

   * **Answer / الإجابة:** Through encryption, identity management, access controls, and compliance.

4. **What tools and platforms are commonly used? / ما الأدوات والمنصات الشائعة؟**

   * **Answer / الإجابة:** AWS, Azure, GCP, Firebase, DigitalOcean.

---

*Cloud Computing is a backbone of modern software infrastructure — scalable, efficient, and global.*
