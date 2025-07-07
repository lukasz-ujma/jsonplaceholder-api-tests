
# JSONPlaceholder API Tests 🧪

## 📌 Project Description
This project demonstrates my skills in testing REST APIs using:
- **Postman** (creating collections with GET, POST, PUT, PATCH, DELETE requests)
- parameters and variables (global, environment, collection)
- running tests with the Postman Collection Runner
- automating tests using **Postman Monitors**
- executing tests from the command line with **Newman**, generating an HTML report
- integrating API tests into CI with **Jenkins (freestyle job)**

Target API:  
➡️ [JSONPlaceholder](https://jsonplaceholder.typicode.com/) — a free, fake online REST API for testing and prototyping.

---

## ⚠️ Notes
This collection does **not include assertions in Postman tests (JavaScript)**.  
I intentionally focused on request configuration, parameters, variables, and CI/CD integration, as I plan to develop my automation skills primarily with **Python** (using tools like Pytest or Robot Framework).

---

## 🛠️ Stack / Tools
- **Postman** (collections, environments, global variables)
- **Newman** (CLI for Postman)
- **Jenkins** (Freestyle project)
- **Postman Monitors**

---

## 📝 Test scope
In the Postman collection, I test the following endpoints:
- `GET /posts`
- `POST /posts`
- `PUT /posts/:id`
- `PATCH /posts/:id`
- `DELETE /posts/:id`

Additionally:
- I use **global**, **environment** and **collection** variables
- I set request parameters and dynamically replace `:id` with `{{postId}}`

---

## 🚀 Postman Collection Runner
I executed the tests directly in **Postman Collection Runner** to manually verify all requests.
Screenshot of the runner results is in:
- [`reports/collection-runner-results.png`](reports/collection-runner-results.png)

---

## 🧪 Postman Monitors
I configured a **Monitor w Postman** that runs the collection every 2 hours.  
This allows tracking the API health on a recurring schedule.
Chart from Postman Monitors is in:
- [`reports/postman-monitors-summary.png`](reports/postman-monitors-summary.png)

---

## 🚀 How to run

### ✅ 1. Locally with Newman
Install Newman globally:
```bash
npm install -g newman
```

Install Newman Reporter HTML globally:
```bash
npm install -g newman-reporter-html
```

Run the tests with CLI and HTML reports:
```bash
newman run collections/JSONPlaceholderTests.postman_collection.json -e collections/JSONPlaceholderEnv.postman_environment.json -r cli,html --reporter-html-export reports/newman-report.html
```

After execution, you’ll find the HTML report in:
```
reports/newman-report.html
```

---

### ⚙️ 2. In Jenkins
- I set up a **freestyle job** in Jenkins that runs the Newman command above in the `Build` step.
- Results are visible in the Jenkins console output and the HTML report can be downloaded.

Detailed freestyle job instructions are in:
- [`jenkins/freestyle-job-instructions.md`](jenkins/freestyle-job-instructions.md)

---

## 🗂️ Repository structure
```
jsonplaceholder-api-tests/
├── README.md
├── collections/
│   ├── JSONPlaceholderTests.postman_collection.json
│   └── JSONPlaceholderEnv.postman_environment.json
├── reports/
│   └── newman-report.html
│   └── postman-monitors-summary.png
├── jenkins/
│   └── freestyle-job-instructions.md
```

---

## 🙋‍♂️ Author

**Łukasz**  
🔗 [LinkedIn – Łukasz Ujma](https://www.linkedin.com/in/ujma-lukasz)  
📧 ujma.lukasz@gmail.com
