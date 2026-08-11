# 📋 Functional Requirements Document (FRD)

This document outlines the specific functional requirements for the IT Trainz platform, broken down by module.

---

## 1. Public Website Module

### 1.1 Home Page

- **Hero Section:** Display center name, tagline, and CTA buttons ("View Courses", "Contact Us").
- **Statistics:** Display total students trained, courses offered, active batches, and instructors.
- **Popular Courses:** Display top 6 courses (cards) with thumbnail, title, duration, and fee.
- **Upcoming Batches:** Display next 4 starting batches with course name, start date, and available seats.
- **Testimonials:** Display 3 student success stories.

### 1.2 About Us Page

- Display Mission, Vision, and Objectives.
- Display Center Facilities (e.g., lab specs, online support).
- Display Achievements (e.g., total graduates, placement rate).

### 1.3 Courses Module

- **Course List:** Display all active courses in a grid.
- **Search:** Text search by course name.
- **Filter:** Dropdown to filter by Course Category.
- **Course Details:**
  - Display Full Description, Syllabus (list of modules), Prerequisites.
  - Display Course Fee, Discount (if any), and Duration.
  - Display assigned Instructor (with link to profile).
  - Display available upcoming batches for this course.
  - "Enroll Now" button (visible only to logged-in Students).

### 1.4 Instructors Module

- **Instructor List:** Grid of all active instructors.
- **Instructor Profile:** Display photo, name, designation, expertise, biography, and assigned courses.

### 1.5 Batches / Schedule Module

- **Batch List:** Table view of upcoming batches.
- **Columns:** Course Name, Batch Name, Start Date, Class Days, Class Time, Mode (Online/Offline), Available Seats, Status.

### 1.6 Contact Module

- **Contact Form:** Fields for Name, Email, Subject, Message. Validates input and saves to database.
- **Contact Info:** Display Address (Bangladesh format), Phone, Email, and Google Maps iframe.

---

## 2. Authentication & Profile Module (Identity)

### 2.1 Registration

- Form fields: Full Name, Email, Phone Number, Password, Confirm Password.
- Assign "Student" role by default upon registration.
- Create a linked `StudentProfile` record upon registration.

### 2.2 Login / Logout

- Form fields: Email, Password, "Remember Me" checkbox.
- Redirect to Student Dashboard upon success.
- Redirect back to Login with error message on failure.

### 2.3 Profile Management

- View Profile: Display Name, Email, Phone, Address.
- Edit Profile: Update Name, Phone, Address.
- Change Password: Standard Identity change password flow.

---

## 3. Student Dashboard Module

### 3.1 Dashboard Summary

- Cards showing: Total Enrolled Courses, Active Courses, Pending Payments (Count), Total Due Amount (BDT).

### 3.2 Enrolled Courses

- Table listing course name, batch name, enrollment date, and enrollment status (Pending, Approved, Rejected).

### 3.3 Payment History

- Table listing course, total fee, amount paid, remaining balance, and payment status (Paid, Partial, Due).
- Expandable view to see installment history per enrollment.

---

## 4. Enrollment & Payment Module (Student Side)

### 4.1 Enrollment Process

- Student clicks "Enroll" on a Course Details page.
- Selects an available batch from a dropdown.
- Submits enrollment request.
- System sets status to "Pending" and redirects to Student Dashboard with a success message.

---

## 5. Admin Panel Module (`/Admin`)

### 5.1 Admin Dashboard

- **Stat Cards:** Total Students, Total Instructors, Active Batches, Total Revenue (this month), Pending Enrollments.
- **Recent Activities:** Latest 5 enrollment requests.

### 5.2 Category Management

- CRUD operations for Course Categories (e.g., Web Dev, Networking).
- Fields: Category Name, Description, IsActive.

### 5.3 Course Management

- CRUD operations for Courses.
- Fields: Title, Category, Description, Duration (months), Total Fee (BDT), Discount, Prerequisites, Syllabus (multiple items), Thumbnail Image, IsActive.

### 5.4 Instructor Management

- CRUD operations for Instructors.
- Fields: Name, Photo, Designation, Expertise, Bio, IsActive.

### 5.5 Batch Management

- CRUD operations for Batches.
- Fields: Batch Name, Course (Dropdown), Instructor (Dropdown), Start Date, End Date, Class Days, Class Time, Mode, Total Seats, IsActive.

### 5.6 Enrollment Management

- View all enrollment requests.
- Approve / Reject pending enrollments.
- View student enrollment history.

### 5.7 Payment Management

- View all payment records.
- Record New Payment: Select Student, Select Enrollment, Enter Amount (BDT), Select Method (Cash, bKash, Nagad, Bank, Card), Enter Transaction ID/Note.
- System automatically calculates Remaining Balance and updates Payment Status (Paid, Partial, Due).
- Admin can view total collected amount and total outstanding.

---

### 6. Explanation

#### 6.1 — Granular Inputs and Outputs

Notice how we specified exact fields (e.g., "Fields: Name, Email, Subject, Message"). This is crucial for the next phases. When we design ViewModels and database tables, we won't have to guess what columns are needed—the FRD tells us exactly what to build.

#### 6.2 — State Management

We explicitly defined states like **`Pending`**, **`Approved`**, and **`Rejected`** for enrollments, and **`Paid`**, **`Partial`**, **`Due`** for payments. This tells us we need **`Enums`** or status columns in our database, and it dictates the business logic for calculating balances.

#### 6.3 — Admin vs. Student Boundaries

The FRD clearly separates the Student's enrollment process (submitting a request) from the Admin's process (approving it and recording payments). This prevents students from self-approving or manipulating payment data, enforcing the security rules we established in Step 2.