# 📘 **Course Registration System – Full Stack Project**

A simple and functional **Course Registration System** built using **Spring Boot (Backend)** and **HTML, CSS, JavaScript (Frontend)**. The system allows users to:

✅ View all available courses
✅ Register/enroll for a course
✅ View the list of all enrolled students

This project follows a **clean 3-layer architecture** (Controller → Service → Repository) and includes a fully working frontend integrated via REST APIs.

---

## 🧩 **Table of Contents**

* [Project Overview](#project-overview)
* [Features](#features)
* [System Architecture](#system-architecture)
* [Tech Stack](#tech-stack)
* [API Endpoints](#api-endpoints)
* [Project Structure](#project-structure)
* [Database Schema](#database-schema)
* [Frontend Overview](#frontend-overview)
* [How It Works](#how-it-works)
* [How to Run the Project](#how-to-run-the-project)
* [Future Enhancements](#future-enhancements)
* [Screenshots](#screenshots)
* [Author](#author)

---

# 📌 **Project Overview**

The **Course Registration System** is a full-stack web application that allows students to:

* Browse available courses
* Enroll in a selected course through a form
* View all existing enrollments

The backend exposes **REST APIs** using Spring Boot, while the frontend is built using **HTML, CSS animations, and JavaScript (Fetch API)**. CORS is enabled to allow the frontend (running on a different port) to communicate with the backend.

---

# ⭐ **Features**

### 👨‍🎓 Students:

* View course catalog
* Register for any course
* Receive success confirmation

### 👨‍🏫 Admin:

* View list of all registered students

### ⚙ General Features:

* REST API architecture
* Automatic table creation using Hibernate
* Clean UI with CSS animations
* Input validation on frontend
* Modular layered backend design

---

# 🏗 **System Architecture**

### 🔹 **Backend Architecture (Spring Boot)**

```
┌───────────────────────────────┐
│        Controller Layer        │  → Handles API endpoints
└───────────────┬───────────────┘
                ↓
┌───────────────────────────────┐
│         Service Layer          │  → Business logic
└───────────────┬───────────────┘
                ↓
┌───────────────────────────────┐
│        Repository Layer        │  → JPA Repositories (DAO)
└───────────────┬───────────────┘
                ↓
┌───────────────────────────────┐
│          MySQL Database        │
└───────────────────────────────┘
```

### 🔹 **Frontend Architecture**

```
HTML Pages → JavaScript Fetch API → Calls Spring Boot REST APIs
```

---

# 🛠 **Tech Stack**

### **Backend**

* Spring Boot
* Spring Web
* Spring Data JPA
* Hibernate
* MySQL
* Maven

### **Frontend**

* HTML
* CSS (Animations + Gradients)
* JavaScript (Fetch API)

### **Tools**

* IntelliJ / VS Code
* MySQL Workbench
* Live Server

---

# 🔗 **API Endpoints**

### 📍 **GET /courses**

Returns list of all available courses.

### 📍 **GET /courses/enrolled**

Returns list of all enrolled students.

### 📍 **POST /courses/register**

Registers a student for a course.
Parameters:

* name
* emailId
* courseName

### Example Response:

```
Congratulations! <name> Enrollment Successful for <courseName>
```

---

# 📁 **Project Structure**

```
Course-Registration-System/
│
├── src/main/java/com/project/
│   ├── controller/
│   │   └── CourseController.java
│   ├── service/
│   │   └── CourseService.java
│   ├── repository/
│   │   ├── CourseRepo.java
│   │   └── CourseRegistryRepo.java
│   ├── model/
│   │   ├── Course.java
│   │   └── CourseRegistry.java
│   └── CourseRegistrationSystemApplication.java
│
├── src/main/resources/
│   └── application.properties
│
├── frontend/
│   ├── index.html
│   ├── register.html
│   ├── availcourses.html
│   ├── enrolled.html
│   └── styles.css
│
└── README.md
```

---

# 🗄 **Database Schema**

### 🧩 Table: **course**

| Column            | Type    | Description    |
| ----------------- | ------- | -------------- |
| course_id         | VARCHAR | Primary Key    |
| course_name       | VARCHAR | Name of course |
| trainer           | VARCHAR | Trainer name   |
| duration_in_weeks | INT     | Duration       |

### 🧩 Table: **course_registry**

| Column      | Type    | Description                |
| ----------- | ------- | -------------------------- |
| id          | INT     | Auto-generated primary key |
| name        | VARCHAR | Student name               |
| email       | VARCHAR | Student email              |
| course_name | VARCHAR | Registered course          |

Hibernate automatically creates these tables (ddl-auto=update).

---

# 💻 **Frontend Overview**

### ✔ index.html

Navigation page with animated buttons.
Options:

* Register Course
* View Courses
* View Enrolled Students

### ✔ register.html

Form for entering student details.
Direct POST request to `/courses/register`.

### ✔ availcourses.html

Loads all courses using:

```javascript
fetch("http://localhost:8080/courses")
```

Dynamically inserts rows into `<table>`.

### ✔ enrolled.html

Loads all registered students using:

```javascript
fetch("http://localhost:8080/courses/enrolled")
```

---

# 🔄 **How It Works (Flow Explanation)**

### Step 1: User visits frontend

HTML pages are opened in browser using Live Server.

### Step 2: User selects an action

Examples:

* View courses
* Register for a course

### Step 3: Frontend sends request to backend

Via **Fetch API** or HTML form POST.

### Step 4: Controller receives request

Example:

```java
@PostMapping("/courses/register")
```

### Step 5: Service processes business logic

* Create registry object
* Store into database

### Step 6: Repository layer interacts with MySQL

```java
courseRegistryRepo.save(courseRegistry);
```

### Step 7: Backend returns response

Displayed instantly on the frontend.

---

# ▶ **How to Run the Project**

### **1. Clone this repository**

```
git clone https://github.com/your-username/course-registration-system.git
```

### **2. Configure MySQL**

Create database:

```
CREATE DATABASE course_reg_sys;
```

### **3. Update `application.properties`**

```
spring.datasource.url=jdbc:mysql://localhost:3306/course_reg_sys
spring.datasource.username=<your-username>
spring.datasource.password=<your-password>
spring.jpa.hibernate.ddl-auto=update
```

### **4. Run Backend**

```
mvn spring-boot:run
```

Server starts at:

```
http://localhost:8080
```

### **5. Run Frontend**

Open the frontend folder with VS Code
→ Right-click `index.html`
→ Click **Open with Live Server**

---

# 🚀 **Future Enhancements**

* Add authentication for admin
* Add course creation & editing panel
* Prevent duplicate enrollments
* Add email confirmation system
* Convert frontend to React.js
* Add pagination for enrolled students
* Validation for backend inputs

---

# 👨‍💻 **Author**

**Sandeep Rishi J B**
B.E Computer Science & Engineering
Skills: Java, Spring Boot, Python, ML, Full Stack, Firebase, MySQL, Streamlit
