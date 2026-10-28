# Serverless Task Management API on AWS

A fully serverless CRUD backend for managing tasks, built with core AWS services, without managing a single server.

Users can create tasks, fetch all tasks, update their status, and delete them through a RESTful API.

## Tech Stack

| Service | Role |
|---|---|
| **AWS Lambda** | 4 separate functions for Create, Read, Update and Delete operations |
| **Amazon DynamoDB** | NoSQL database for storing task data |
| **Amazon API Gateway** | RESTful endpoints exposing the backend to the internet |
| **IAM** | Fine-grained permissions between services |

## API Operations

| Operation | HTTP Method | Lambda Function |
|---|---|---|
| Create a task | `POST` | Create |
| Get all tasks | `GET` | Read |
| Update task status | `PUT` | Update |
| Delete a task | `DELETE` | Delete |

## Architecture

```
Client (Postman / App)
        |
        v
 Amazon API Gateway  (proxy integration)
        |
        v
   AWS Lambda (Create | Read | Update | Delete)
        |
        v
   Amazon DynamoDB
```

IAM roles control which Lambda functions can access DynamoDB.

## Screenshots

### AWS Lambda Functions
Four separate functions for Create, Read, Update and Delete.

<img width="1354" height="768" alt="Lambda Functions" src="https://github.com/user-attachments/assets/a00cbdeb-d123-4416-b70d-1294a048ec7b" />


### DynamoDB Table
`TaskFlowItems` table with partition key `id`.

<img width="1354" height="768" alt="DynamoDB Table" src="https://github.com/user-attachments/assets/615a921a-55ae-4905-b28a-a7bd0b9e348f" />


### DynamoDB Items
Task items stored with `id`, `status` and `title`.

<img width="1376" height="768" alt="DynamoDB Items" src="https://github.com/user-attachments/assets/972b68fa-fa47-4543-ac3f-3324d1fea8e9" />


### API Gateway
`TaskFlow-API`, a regional REST API.

<img width="1354" height="768" alt="API Gateway" src="https://github.com/user-attachments/assets/181894ec-7408-46dc-a9b6-30e388ca0f2b" />


### API Gateway Resources
`/tasks` (GET, POST) and `/tasks/{id}` (PUT, DELETE) with Lambda proxy integration.

<img width="1376" height="768" alt="API Gateway Resources" src="https://github.com/user-attachments/assets/99cf41d0-a551-4db5-ad43-e5e372318233" />


### IAM Role
Execution role with the required policy attached.

<img width="1376" height="768" alt="IAM Role" src="https://github.com/user-attachments/assets/bcfa7407-d07e-4996-82a4-b043b855f16b" />


## What I Learned

- How serverless architecture eliminates infrastructure management
- Designing RESTful APIs with proper HTTP methods (POST, GET, PUT, DELETE)
- Connecting Lambda functions to API Gateway with proxy integration
- Debugging real-world issues (IAM permissions, syntax errors, deployment stages)
- Testing APIs end-to-end using Postman

## Real-World Use Cases

The Lambda + API Gateway + DynamoDB pattern is the same foundation used in:

- Mobile app backends
- E-commerce order processing
- IoT data pipelines

## Next Steps

- Add authentication with **Amazon Cognito**
- Add security with **AWS WAF**

## Author

**Ganiha Siddiqui**
Cloud & DevOps learner | [GitHub](https://github.com/ganiha123)

---

Would love to hear how others are using serverless architectures in production!
