# Todo App with Go and React

## Table of Contents
- [Overview](#overview)
- [Technologies](#technologies)
- [Deployment](#deployment)
- [Backend Setup](#backend-setup)
- [API Endpoints](#api-endpoints)
- [Running the Application](#running-the-application)
- [Usage](#usage)

## Overview
A Todo application that allows users to create, read, update, and delete (CRUD) their todo tasks. The app consists of a backend built with Go and a frontend built with React.

## Technologies
### Backend
- Go
- ScyllaDB (via gocql)
- Gorilla Mux

### Frontend
- React
- Axios
- CSS


## Deployment
This application is deployed on Vercel and Railway.

Frontend: `https://todo-app-with-go-react-fe.vercel.app/`

Backend: `todoapp-with-go-react-be-production.up.railway.app/todos`

## Backend Setup

### Prerequisites
- Go installed
- ScyllaDB instance (or Cassandra)

### Installation
1. **Clone the repository:**
   ```bash
   git clone https://github.com/Atmalviya/TodoAPP-with-GO-React-BE.git
   cd todo-app/backend

## Install dependencies:
    go mod tidy

## Setup ScyllaDB:
Ensure you have a running ScyllaDB instance and update the connection details in your code.

## Create and configure .env file:
    SCYLLA_HOST=node-0.aws-ap-south-1.2b1f25afd030301fb144.clusters.scylla.cloud
    SCYLLA_PORT=9042
    SCYLLA_USERNAME=scyllaDB_Username
    SCYLLA_PASSWORD=scylla_password
    SCYLLA_KEYSPACE=todo_keyspace


## Run the backend server:
    go run main.go
## API Endpoints

### Get Todos
- **URL:** `/todos`
- **Method:** `GET`
- **Query Parameters:**
  - `user_id` (required): The ID of the user whose todos are being requested.
  - `status` (optional): The status of the todos to filter by (e.g., `pending`, `completed`).
  - `page_size` (optional, default is 10): The number of todos to return per page.
  - `page_token` (optional): The token for the next page of results.
- **Response:**
  ```json
  {
    "todos": [
      {
        "id": "todo-id",
        "user_id": "user-id",
        "title": "Todo title",
        "description": "Todo description",
        "status": "pending",
        "created": "timestamp",
        "updated": "timestamp"
      },
      ...
    ],
    "next_page_token": "..."
  }

### Create Todos
- **URL:** `/todos`
- **Method:** `POST`
- **Request body:**
  - `title` (required): Title of the todo.
  - `description` (optional): Description about todo.
  - `status` (optional): The status of the todos to filter by (e.g., `pending`, `completed`).
- **Response:**
  ```json
  {
  "id": "new-todo-id",
  "user_id": "user-id",
  "title": "Todo title",
  "description": "Todo description",
  "status": "pending",
  "created": "timestamp",
  "updated": "timestamp"
}

### Update  Todos
- **URL:** `/todos/{id}`
- **Method:** `PUT`
- **Request body:**
  - `title` (optional): Updated title of the todo.
  - `description` (optional): Updated description about todo.
  - `status` (optional): Updated status of the todos to filter by (e.g., `pending`, `completed`).
- **Response:**
  ```json
  {
  "id": "todo-id",
  "user_id": "user-id",
  "title": "Updated title",
  "description": "Updated description",
  "status": "completed",
  "created": "timestamp",
  "updated": "timestamp"
  }

### Delete  Todos
- **URL:** `/todos/{id}`
- **Method:** `DELETE`
- **Response:**
  ```json
  {
    "message": "Todo deleted successfully"
  }
## Usage
Open the application in your browser:

Navigate to http://localhost:3000 or https://todo-app-with-go-react-fe.vercel.app/

Interact with the Todo App:

Create, update, and delete todos

Filter todos by status

Paginate through todos


