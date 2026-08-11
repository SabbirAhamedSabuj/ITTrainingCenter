# 🎓 IT Trainz — IT Training Center

A professional, responsive website for a Bangladeshi IT training center, built as a real-world learning project using **ASP.NET Core MVC, Entity Framework Core, SQL Server, and ASP.NET Core Identity**.

---

## 📌 Project Overview

**IT Trainz** is an IT training center management and learning platform designed for Bangladesh.

The platform allows students to:

- Browse available courses
- View course details
- Explore instructors
- View upcoming batches and schedules
- Register and log in
- Enroll in courses
- Track enrollment status
- View payment history
- Manage their profile

Administrators can manage the complete training center through a dedicated **Admin Panel**.

---

## 👥 User Roles

| Role | Capabilities |
|------|--------------|
| 👤 **Guest** | Browse courses, instructors, batches, and submit contact forms |
| 🎓 **Student** | Register, login, enroll in courses, view dashboard, track payments |
| 👨‍🏫 **Instructor** | View assigned batches and students *(Future Feature)* |
| 🛡️ **Admin** | Full CRUD over students, instructors, courses, categories, batches, enrollments, and payments |

---

## 🧰 Technology Stack

| Technology | Purpose |
|------------|---------|
| **ASP.NET Core MVC** | Web application framework |
| **C#** | Backend programming language |
| **Entity Framework Core** | ORM and database access |
| **SQL Server** | Relational database |
| **SQL Server Management Studio (SSMS)** | Database management |
| **ASP.NET Core Identity** | Authentication and authorization |
| **Bootstrap 5** | Responsive UI |
| **Razor Views** | Server-side HTML rendering |
| **HTML5 / CSS3 / JavaScript** | Frontend |
| **Git** | Version control |
| **GitHub** | Source code management |

### Development Environment

- **Visual Studio 2026**
- **.NET 9 / latest stable version compatible with Visual Studio 2026**
- Windows

---

## 🏗️ Architecture

The project follows a clean and maintainable **ASP.NET Core MVC architecture**.

### Main Architectural Components

- **MVC Architecture**
- **Controllers**
- **Services**
- **Repositories where appropriate**
- **Entities / Models**
- **ViewModels**
- **Entity Framework Core**
- **Fluent API**
- **Dependency Injection**
- **ASP.NET Core Identity**
- **Role-Based Authorization**
- **Area-Based Admin Panel**
- **EF Core Migrations**

### Architecture Principles

- ViewModels are used instead of directly exposing database entities to views.
- Entity Framework Core handles database access.
- Fluent API is used for complex entity relationships and constraints.
- Dependency Injection is used throughout the application.
- ASP.NET Core Identity handles authentication and password security.
- The Admin Panel is implemented using an MVC **Area**.

---

# 🗂️ Project Modules

## 🌐 Public Website

### 🏠 Home

The homepage will include:

- Hero section
- Training center introduction
- Popular courses
- Course categories
- Why choose IT Trainz
- Training statistics
- Featured instructors
- Student testimonials
- Upcoming batches
- Call-to-action sections
- Contact information
- Footer

### ℹ️ About

Includes:

- About IT Trainz
- Mission
- Vision
- Objectives
- Training facilities
- Trainers
- Achievements

### 📚 Courses

Users can:

- Browse courses
- Search courses
- Filter by category
- View course details
- View course duration
- View course fee
- View syllabus
- View available batches
- View instructors
- Apply/enroll

### 📖 Course Details

Each course can contain:

- Course name
- Description
- Category
- Duration
- Course fee
- Discount
- Syllabus
- Prerequisites
- Instructor
- Batch schedule
- Available seats
- Enrollment option

### 👨‍🏫 Instructors

Instructor profiles include:

- Name
- Profile image
- Designation
- Expertise
- Experience
- Biography
- Assigned courses

### 📅 Batches / Schedule

Display:

- Course
- Batch name
- Start date
- End date
- Class days
- Class time
- Training mode
- Available seats
- Batch status

### 📞 Contact

Includes:

- Training center address
- Phone number
- Email
- Google Maps location
- Contact form
- Social media links

---

# 🎓 Student System

Students will be able to:

- Register
- Login
- Logout
- Reset password
- Change password
- Manage profile
- Browse courses
- Enroll in courses
- View enrolled courses
- View upcoming classes
- Track enrollment status
- View payment history
- View outstanding balance

### Student Dashboard

The dashboard will provide:

- Student profile
- Enrolled courses
- Upcoming batches
- Enrollment status
- Payment summary
- Payment history
- Course progress/status

---

# 📝 Enrollment System

Students can:

1. Select a course
2. Select an available batch
3. Submit an enrollment request
4. Wait for administrator approval
5. View enrollment status

### Enrollment Information

Each enrollment can contain:

- Student
- Course
- Batch
- Enrollment date
- Enrollment status
- Notes

Possible statuses:

- Pending
- Approved
- Rejected
- Cancelled
- Completed

---

# 💳 Payment System

The system supports course payments through:

- Full payment
- Installment payments

### Payment Information

Each payment record contains:

- Student
- Enrollment
- Amount
- Payment date
- Payment method
- Payment status
- Transaction/reference number
- Notes

### Supported Payment Methods

- 💵 Cash
- 📱 bKash
- 📱 Nagad
- 🏦 Bank Transfer
- 💳 Card
- Other

> **Note:** The first version will not implement a real online payment gateway. Payments will be recorded and managed by administrators.

### Payment Tracking

The system will calculate:

```text
Course Fee
    ↓
Total Paid
    ↓
Remaining Balance
