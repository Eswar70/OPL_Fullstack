## **📌 Updated README.md**
```md
# Task Management Application 🚀

## 📌 Overview
The **Task Management Application** is a full-stack web application that allows users to **create, update, delete, and search tasks** using a **secure authentication system**.

### 🔹 Technologies Used
- **Backend:** Node.js, Express.js, MongoDB
- **Frontend:** React.js, Styled Components
- **Authentication:** JWT-based authentication
- **Database:** MongoDB with Mongoose ORM

---

## 📌 Database Design

### 🔹 ER Diagram

+------------------+       +------------------+
|      User       |       |      Task        |
+------------------+       +------------------+
| _id (PK)        |<----->| _id (PK)         |
| name            |       | title            |
| email (Unique)  |       | description      |
| password        |       | dueDate          |
+------------------+       | status           |
                           | remarks          |
                           | createdBy (FK)   |
                           | lastUpdatedBy (FK) |
                           +------------------+


### 🔹 Data Dictionary
| Table    | Column          | Type      | Description |
|----------|-----------------|-----------|-------------|
| **User** | `_id`           | ObjectId  | Primary Key |
| **User** | `name`          | String    | User's full name |
| **User** | `email`         | String    | Unique email for authentication |
| **User** | `password`      | String    | Hashed password |
| **Task** | `_id`           | ObjectId  | Primary Key |
| **Task** | `title`         | String    | Task title |
| **Task** | `description`   | String    | Task details |
| **Task** | `dueDate`       | Date      | Task deadline |
| **Task** | `status`        | String    | Task status (Pending/Completed) |
| **Task** | `remarks`       | String    | Additional notes |
| **Task** | `createdBy`     | ObjectId  | Foreign Key (User ID) |
| **Task** | `lastUpdatedBy` | ObjectId  | Foreign Key (User ID) |

### 🔹 Indexes
- **Users:** `email` (Unique Index)
- **Tasks:** `title` (Text Index for search optimization)

---

## 📌 Backend & Frontend Structure

### 🔹 Backend (Node.js + Express + MongoDB)

backend/
│── models/
│   ├── User.js
│   ├── Task.js
│── routes/
│   ├── auth.js
│   ├── tasks.js
│── middleware/
│   ├── auth.js
│── config/
│   ├── db.js
│── server.js
│── .env


### 🔹 Frontend (React.js + Styled Components)

frontend/
│── src/
│   ├── components/
│   │   ├── Header.js
│   │   ├── Footer.js
│   │   ├── TaskSearch.js
│   │   ├── TaskForm.js
│   │   ├── TaskList.js
│   │   ├── TaskEdit.js
│   ├── pages/
│   │   ├── Register.js
│   │   ├── Login.js
│   │   ├── Dashboard.js
│   │   ├── Tasks.js
│   │   ├── TaskFormPage.js
│   │   ├── TaskEditPage.js
│   ├── context/
│   │   ├── AuthContext.js
│   ├── api/
│   │   ├── api.js
│   ├── styles/
│   │   ├── global.css
│   │   ├── theme.css
│   ├── App.js
│   ├── index.js
│── package.json
│── README.md




## 📌 Setup Instructions

### 🔹 Clone the Repository
```bash
git clone https://github.com/your-repo/task-manager.git
cd task-manager
```

### 🔹 Backend Setup
```bash
cd backend
npm install
```
✅ **Create `.env` file**
```plaintext
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
PORT=5000
```
✅ **Run the Backend Server**
```bash
npm start
```

### 🔹 Frontend Setup
```bash
cd frontend
npm install
npm start
```

---

## 📌 Testing Instructions

### 🔹 Backend API Testing (Postman or cURL)
✅ **Register User**
```bash
curl -X POST http://localhost:5000/api/auth/register -H "Content-Type: application/json" -d '{"name":"John Doe","email":"john@example.com","password":"123456"}'
```

✅ **Login User**
```bash
curl -X POST http://localhost:5000/api/auth/login -H "Content-Type: application/json" -d '{"email":"john@example.com","password":"123456"}'
```

✅ **Create Task**
```bash
curl -X POST http://localhost:5000/api/tasks -H "Authorization: Bearer YOUR_TOKEN" -H "Content-Type: application/json" -d '{"title":"Task 1","description":"Complete project","dueDate":"2023-12-31","status":"Pending","remarks":"Urgent"}'
```

✅ **Search Task by Title**
```bash
curl -X GET "http://localhost:5000/api/tasks/search?title=Task 1" -H "Authorization: Bearer YOUR_TOKEN"
```

✅ **Search Task by User Name**
```bash
curl -X GET "http://localhost:5000/api/tasks/search?name=John Doe" -H "Authorization: Bearer YOUR_TOKEN"
```

✅ **Delete Task**
```bash
curl -X DELETE "http://localhost:5000/api/tasks/TASK_ID" -H "Authorization: Bearer YOUR_TOKEN"
```

---

## 📌 Testing Results
| Test Case | Expected Result | Status |
|-----------|----------------|--------|
| User Registration | User should be created successfully | ✅ Passed |
| User Login | User should receive JWT token | ✅ Passed |
| Create Task | Task should be added to the database | ✅ Passed |
| Search Task by Title | Should return matching tasks | ✅ Passed |
| Search Task by User Name | Should return tasks created by the user | ✅ Passed |
| Edit Task | Task details should be updated | ✅ Passed |
| Delete Task | Task should be removed from the database | ✅ Passed |

---

## 📌 Deployment Instructions
### 🔹 Backend Deployment (Render/Vercel/Heroku)
1. Push the backend code to GitHub
2. Deploy using **Render** or **Vercel**
3. Set environment variables (`MONGO_URI`, `JWT_SECRET`)

### 🔹 Frontend Deployment (Netlify/Vercel)
1. Push the frontend code to GitHub
2. Deploy using **Netlify** or **Vercel**
3. Set API base URL in `api.js`

---

## 📌 Contributors
- **Your Name** (Developer)
- **Other Contributors**

---

## 📌 License
This project is licensed under the **MIT License**.

---
