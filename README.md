# API Testing with Postman – JSONPlaceholder

## 📌 Project Description
This repository presents a complete example of REST API testing using Postman and JavaScript-based tests. The project is based on the public JSONPlaceholder API, which is commonly used for learning and practicing API testing. The main goal of this project is to demonstrate API testing skills, proper test design and documentation, usage of Postman environments, positive and negative test scenarios, and basic automation with reporting.

## 🧰 Tools & Technologies
- Postman
- JavaScript (Postman Tests)

## 🌐 API Under Test
JSONPlaceholder API – public REST API for testing purposes  
Base URL: https://jsonplaceholder.typicode.com/

## 🧪 Scope of Testing
- Functional API tests (GET, POST, PUT, DELETE)
- Positive test scenarios
- Negative test scenarios
- HTTP status code validation
- Response body validation
- Basic performance checks
- Usage of environment variable

## 📂 Project Structure
```text
├── jsonplaceholder-postman/
│ ├── README.md
│ ├── docs/
│ │ ├── test-cases.md
│ │ ├── test-scenarios.md
│ │ └── test-scenarios-negative.md
│ └── postman/
│ ├── collections/
│ │ └── JSONPlaceholder_Full.postman_collection.json
│ └── environments/
│ └── dev.postman_environment.json

```
## ▶️ How to Run Tests in Postman
1. Clone the repository: git clone https://github.com/your-username/api-testing-postman.git
2. Open Postman
3. Import the collection from /postman/collections
4. Import the environment from /postman/environments
5. Select the environment and run tests manually or using the Collection Runner


## 📝 Test Documentation
Additional test documentation is available in the /docs directory:
- test-scenarios.md 
- test-cases.md 
- test-scenarios-negative

## ✅ Key Features
- Clean and readable project structure
- Well-organized Postman collection
- JavaScript-based assertions
- Positive and negative test coverage

## 📚 What I Learned
- Designing API test scenarios
- Writing maintainable Postman tests
- Working with REST APIs

## 👤 Author
Created by Maciej Miszewski – QA / Software Tester

## 📎 Notes
This project was created for educational and portfolio purposes. The ReqRes API is a public API intended for testing and learning.
