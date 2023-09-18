# Task Tracker

Task Tracker is a comprehensive application that manages tasks and sends notifications to users. This repository serves as the central hub for the Task Tracker project, orchestrating the core components.

## Overview

The Task Tracker system consists of the following microservices:

The Task Tracker application provides a complete solution for task management and notifications. It consists of the following key components:

- **[Task Tracker Backend](https://github.com/MKotlov789/task-tracker-backend):** This service provides provides RESTful API endpoints for tasks, user registration, login, and more. It also handles authentication using JWT tokens and integrates with Kafka for sending welcoming emails to newly registered users. Additionally, it implements custom validation for email, username, and password.

- **[Task Tracker Email Scheduler](https://github.com/MKotlov789/task-tracker-email-scheduler):** Task Tracker Email Scheduler is responsible for scheduling and dispatching daily task notifications to users. It collaborates seamlessly with [Task Tracker Email Sender](https://github.com/MKotlov789/task-tracker-email-sender) to deliver these notifications effectively. It utilizes Java, Spring Framework, Apache Kafka, and Spring Scheduler.

- **[Task Tracker Email Sender](https://github.com/MKotlov789/task-tracker-email-sender):** Task Tracker Email Sender is tasked with sending email notifications based on incoming Kafka messages. It receives welcoming emails from [Task Tracker Backend](https://github.com/MKotlov789/task-tracker-backend) and scheduled notification messages from Task Tracker Email Scheduler. It relies on Java, Spring Framework, Apache Kafka, and Spring Mail.


## Technologies Used
### Common Technologies for All Services
- **Java**: The primary programming language for the backend logic.
- **Spring Boot**: Framework for building Java-based microservices.
- **Spring Data JPA**: For data access and persistence.
- **MySQL**: As the relational database for storing task and user data.
- **Apache Kafka:** For message queueing and asynchronous communication between microservices.

### Task Tracker Backend
- **JSON Web Tokens (JWT)**: for authentication
- **Spring Security**: For user authentication and authorization.

### Task Tracker Email Scheduler

- **Spring Scheduler**: For scheduling and executing tasks at specific times.

### Task Tracker Email Sender

- **Spring Mail**: For sending email notifications.

## API Endpoints

The backend component exposes the following API endpoints:

- `POST /api/auth/register`: User registration.
- `POST /api/auth/login`: User login.
- `GET /api/tasks`: Retrieve all tasks for the authenticated user.
- `GET /api/tasks/{taskId}`: Retrieve a specific task.
- `POST /api/tasks`: Create a new task.
- `PUT /api/tasks/{taskId}`: Update an existing task.
- `DELETE /api/tasks/{taskId}`: Delete a task.

## CI/CD 

Within the project, automated Docker image build and upload to a public repository (Docker Hub) were implemented for each microservice using GitHub Actions. This process is triggered automatically upon pushing changes to the master branch.

## Running Locally

To run the application on your local machine, follow these steps:

1. Install Docker on your local machine: [Docker Installation Guide](https://docs.docker.com/get-docker/)
2. Clone the task-tracker-stack repository:
```bash
git clone https://github.com/MKotlov789/task-tracker
```
3. Configure SMTP and DB settings in the `secret.env` file.
```bash
#example:
MYSQL_ROOT_PASSWORD = root
MYSQL_DATABASE = task_manager_db
SMTP_USERNAME=your.email@gmail.com
SMTP_PASSWORD=yourpass
```
4. Start the application using the following command:
```bash
docker-compose up
```
5. The application will be accessible at: [http://localhost:8080](http://localhost:8081])
