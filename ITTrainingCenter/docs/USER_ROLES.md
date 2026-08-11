# 👥 User Roles & Personas

This document defines the user personas and the **Role-Action Matrix** for the **IT Trainz** platform. This drives our **ASP.NET Core Identity** configuration and authorization policies.

---

## 1. User Personas

### Persona 1: Rahim — The Guest

- **Profile:** A recent HSC graduate exploring IT career paths.
- **Goals:**
  - Wants to understand what courses are available.
  - Wants to see course fees.
  - Wants to know when batches start.
- **Pain Points:**
  - Hates hidden fees.
  - Wants to see instructor profiles before committing.
- **Capabilities:**
  - Browse public pages.
  - Search courses.
  - Submit inquiries via the contact form.

---

### Persona 2: Karim — The Student

- **Profile:** A university student or junior developer looking to upskill.
- **Goals:**
  - Wants to enroll in a Web Development batch.
  - Wants to pay in installments via bKash.
  - Wants to track his payment status.
- **Pain Points:**
  - Needs a dashboard to quickly see his remaining balance.
  - Wants to view his class schedule without calling the admin.
- **Capabilities:**
  - Register/Login.
  - Update profile.
  - Enroll in batches.
  - View payment history.

---

### Persona 3: Sarah — The Instructor

- **Profile:** A Senior Software Engineer who teaches on weekends.
- **Goals:**
  - **MVP:** Wants to see which students are in her upcoming batch.
- **Pain Points:**
  - Currently has to ask the admin for the student list.
- **Capabilities:**
  - **MVP:** View assigned batches.
  - **Future:** Take attendance.
  - **Future:** Upload course resources.

---

### Persona 4: Mr. Hasan — The Administrator

- **Profile:** Owner/Manager of the IT Training Center.
- **Goals:**
  - Wants a dashboard showing:
    - Total revenue.
    - Active batches.
    - Pending enrollment requests.
- **Pain Points:**
  - Currently managing everything in Excel.
  - Needs a centralized system to track:
    - Student payments.
    - Outstanding balances.
    - Enrollment requests.
- **Capabilities:**
  - Full CRUD access to all modules:
    - Students.
    - Instructors.
    - Courses.
    - Batches.
    - Enrollments.
    - Payments.

---

# 2. Role-Action Matrix

This matrix defines which **ASP.NET Core Identity roles** can perform specific actions.

Authorization will be implemented using ASP.NET Core Identity role-based authorization, for example:

```csharp
[Authorize(Roles = "Admin")]