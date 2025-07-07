
# Jenkins Freestyle Job - Instructions 🚀

This guide shows how to configure a **Jenkins freestyle job** to run Postman API tests via **Newman**.

---

## 📂 Prerequisites
- Jenkins installed and running (tested on Jenkins 2.504.3).
- A node with **Node.js** and **Newman** installed.
- Your repository cloned or pulled to the Jenkins workspace (recommended via Git SCM).
- Alternatively, upload your `collections` folder manually into the Jenkins workspace.

---

## ⚙️ Job configuration

### 1️⃣ Create a new freestyle project
- Go to **Jenkins Dashboard** → **New Item**.
- Enter a name (e.g. `jsonplaceholder-api-tests`), select **Freestyle project**, click **OK**.

---

### 2️⃣ Configure source code
- In **Source Code Management**, select **Git**.
- Enter repository URL `https://github.com/lukasz-ujma/jsonplaceholder-api-tests.git`
- Choose branch `main`.

---

### 3️⃣ Add build step
- In **Build**, click **Add build step** → **Execute shell** (or **Execute Windows batch command** if on Windows).

Paste the Newman command, e.g.:

```bash
newman run collections/JSONPlaceholderTests.postman_collection.json \
    -e collections/JSONPlaceholderEnv.postman_environment.json \
    -r cli,html \
    --reporter-html-export reports/newman-report.html
```

---

### 4️⃣ Archive artifacts (HTML report)
To make the HTML report downloadable from Jenkins:

- In **Post-build Actions**, click **Add post-build action** → **Archive the artifacts**.
- In **Files to archive**, enter:
```
reports/*.html
```

---

## 🚀 Run the job
- Click **Build Now**.
- Monitor the console output for results.
- After the build, under **Last Successful Artifacts**, download your HTML report.

---

> 🖋 Author: Łukasz  
> 📬 Contact: [[My GitHub](https://github.com/lukasz-ujma) / [LinkedIn](https://www.linkedin.com/in/ujma-lukasz/) / [email](ujma.lukasz@gmail.com)]
