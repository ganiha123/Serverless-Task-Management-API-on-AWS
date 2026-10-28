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

### DynamoDB Table
`TaskFlowItems` table with partition key `id`.

### DynamoDB Items
Task items stored with `id`, `status` and `title`.

### API Gateway
`TaskFlow-API`, a regional REST API.

### API Gateway Resources
`/tasks` (GET, POST) and `/tasks/{id}` (PUT, DELETE) with Lambda proxy integration.

### IAM Role
Execution role with the required policy attached.

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
