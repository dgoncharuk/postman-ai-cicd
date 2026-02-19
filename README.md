# 🧪 Postman API Automation + GitHub Actions CI

This repository demonstrates a structured approach to **API test automation using Postman and Newman**, fully integrated with a **GitHub Actions CI pipeline**.

The project simulates a production-style setup for managing Postman collections, executing automated API tests, and generating structured HTML reports in CI.

---

## 🏗 Architecture Overview
```
Postman Collection
↓
Newman (CLI runner)
↓
GitHub Actions Workflow
↓
HTML Test Report (Artifact)
```

---

## 🧪 Test Strategy

The Postman collection includes:

- ✅ Positive API scenarios  
- ❌ Negative test cases  
- 🔍 Status code validation  
- 📦 Response body validation  
- 🧾 JSON structure checks  
- 🌍 Environment-based configuration  

The goal is to demonstrate maintainable, CI-ready API automation rather than ad-hoc manual testing.

---

## 📂 Project Structure
```
.
├── .github/workflows/
│   └── postman.yml           # GitHub Actions workflow
│
├── postman/
│   ├── collections/
│   │   └── [PROJECT] BookstoreAPI.postman_collection.json
│   └── environments/
│       └── PROJECT_BOOKS.postman_environment.json
│
├── scripts/
│   ├── exportPostmanCollection.js
│   ├── exportPostmanEnvironment.js
│   └── runNewman.js
│
├── reports/                  # Generated HTML reports
│
├── .env                      # Local environment variables (ignored)
├── package.json
└── package-lock.json
```

---

## ⚙️ Local Setup

### 1️⃣ Clone the repository

```bash
git clone <REPOSITORY_URL>
cd postman-ai
```

### 2️⃣ Install dependencies

```bash
npm ci
```

---

## 🔐 Environment Variables

Create a local `.env` file:
```
POSTMAN_API_KEY=your_postman_api_key
POSTMAN_COLLECTION_ID=your_collection_id
POSTMAN_COLLECTION_NAME=your_collection_name
POSTMAN_ENVIRONMENT_ID=your_environment_id
POSTMAN_ENVIRONMENT_NAME=your_environment_name

```
> ⚠️ The `.env` file should NOT be committed to the repository (it is included in `.gitignore`).

## 📥 Export Collection & Environment
The project includes `Node.js scripts` that interact with the Postman API to retrieve the latest collection and environment versions.

```bash
npm run pm:export:col
npm run pm:export:env
npm run pm:sync
```

## 🧪 Running Tests Locally with Newman
```bash
npm run pm:test
```
After execution, the HTML report will be available at:
```
reports/newman.html
```
---

## 🤖 Continuous Integration (GitHub Actions)
The workflow is defined in:
```
.github/workflows/postman.yml
```

### CI Pipeline Steps
1. Checkout repository

2. Install Node.js

3. Install dependencies (npm ci)

4. Execute Postman tests via Newman

5. Generate HTML report

6. Upload report as a workflow artifact

The workflow returns a non-zero exit code if any assertion fails, causing the pipeline to fail automatically.

---

## 🔑 Required GitHub Secrets
Add the following secrets in:

**Settings → Secrets and variables → Actions → New repository secret**

Add the following secrets:

| Secret name | Description |
|-------------|-------------|
| `POSTMAN_API_KEY`| API key for Postman API|
| `POSTMAN_COLLECTION_ID` | Collection ID |
| `POSTMAN_ENVIRONMENT_ID` | Environment ID |

---

## 📊 Test Reports

After each workflow run:

👉 Open **GitHub Actions**  
👉 Select a workflow run  
👉 Go to **Artifacts**  
👉 Download `newman-report`  

### 📄 What the report contains

- Execution summary  
- Request and response details  
- Assertion results  
- Error traces  
---

## 🧰 Tech Stack
- **Postman** – API definition and test scripting

- **Newman** – CLI execution of Postman collections

- **Node.js** – automation scripts

- **GitHub Actions** – CI pipeline

- **HTMLExtra Reporter** – rich test reports

---

## 🎯 Purpose

This project demonstrates how to:

- Structure **Postman API tests** for automation

- Integrate **Newman** into **CI/CD pipelines**

- Maintain **environment-driven API testing**

- Generate detailed **HTML test reports** in CI

- Build a clean, **automation-ready repository structure**

---

Created by [@dgoncharuk](https://github.com/dgoncharuk)