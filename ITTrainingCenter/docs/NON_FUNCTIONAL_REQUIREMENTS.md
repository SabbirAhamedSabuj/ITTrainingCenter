
Conversation with Gemini
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











(markdown the content for .md file )

Your Markdown file is ready!

MD icon
Functional_Requirements_Document
 MD 
Open
I have saved the Functional Requirements Document (FRD) exactly as provided into a .md file. Let me know if you need to add any other sections or if you want to convert this into a PDF!

🛡️ Non-Functional Requirements (NFR) Document

This document defines the quality attributes, constraints, and performance expectations for the IT Trainz platform.

1. Security

Authentication: Must use ASP.NET Core Identity for user authentication. Passwords must be hashed (never stored in plain text).

Authorization: Role-Based Access Control (RBAC) must be enforced using the [Authorize] attribute. Admin areas must be strictly restricted.

CSRF Protection: All POST forms must include anti-forgery tokens (@Html.AntiForgeryToken()).

SQL Injection Prevention: Must use Entity Framework Core (parameterized queries) exclusively. No raw SQL strings concatenated with user input.

XSS Prevention: Razor views automatically encode output. Must avoid @Html.Raw() unless data is strictly sanitized.

Secrets Management: Database connection strings and sensitive credentials must not be committed to Git. Must use appsettings.Development.json (ignored by Git) or User Secrets.

2. Performance & Scalability

Asynchronous Operations: All database I/O operations must use async/await (e.g., ToListAsync(), SaveChangesAsync()).

Response Time: Public pages should load in under 2 seconds on a standard 4G connection. Admin dashboard queries should be optimized to load in under 1.5 seconds.

Data Pagination: Course lists and Admin tables must implement pagination (e.g., 10-20 records per page) to prevent loading excessive data.

Scalability: The architecture must be stateless (except for session/cookie auth) so it can be hosted on multi-server environments (like IIS/Web Farm) in the future.

3. Usability & UI/UX

Responsiveness: The UI must be mobile-first and fully responsive across desktop, tablet, and mobile devices using Bootstrap 5.

Browser Compatibility: Must support modern browsers (Chrome, Firefox, Edge, Safari).

Form Validation: Must implement both client-side (jQuery Unobtrusive Validation) and server-side (Data Annotations) validation.

Feedback: UI must provide immediate feedback for actions (e.g., success/error toasts, loading spinners for long operations).

Accessibility: Follow basic WCAG guidelines (sufficient color contrast, alt text for images, proper HTML semantic tags).

4. Localization (Bangladesh Context)

Currency: All monetary values must be displayed in BDT (৳).

Phone Format: Validation should accept standard Bangladeshi mobile number formats (e.g., +8801XXXXXXXXX or 01XXXXXXXXX).

Payment Methods: System must support local payment gateways/manual tracking (bKash, Nagad, Rocket) alongside Cash and Bank Transfer.

Timezone: All dates/times should default to Bangladesh Standard Time (BST, UTC+6).

5. Maintainability & Architecture

Separation of Concerns: Strict adherence to MVC architecture.

ViewModels: Views must never bind directly to database entities. ViewModels must be used to transfer data between Controllers and Views.

Service Layer: Business logic (e.g., calculating remaining balances, enrollment validation) should be extracted into injectable Services (IEnrollmentService, IPaymentService).

Dependency Injection: Must use ASP.NET Core built-in DI for all services and contexts.

Fluent API: Database constraints and relationships should be configured using EF Core Fluent API inside ApplicationDbContext to keep entity classes clean.

6. Reliability & Availability

Error Handling: Global exception handling middleware must be configured to catch unhandled errors and display a custom error page (not stack traces).

Logging: Errors and significant events (e.g., failed logins, successful payments) must be logged using ASP.NET Core ILogger.

Database Backups: (Operational requirement) Database must be backed up periodically.

6. Explanation

6.1 — Security & NFRs

Security is the most critical NFR for a system handling payments and user data. By writing this down, we commit to never writing raw SQL queries with user input and to always use Identity's built-in hashing.

6.2 — The "ViewModel" Rule

Notice the maintainability rule: Views must never bind directly to database entities. This is a common beginner mistake. Later, when we create a Course, the database entity will have navigation properties (like Batches and Instructor), but the view creating the course only needs a DropdownList of Categories. We will use a CourseCreateViewModel to pass only what the UI needs.

6.3 — Localization Constraints

By specifying the timezone (UTC+6) and currency (BDT) now, we know exactly how to format our HTML helpers and validation attributes in Phase 4 and 5.

I have successfully generated and saved the Non-Functional Requirements Document as a Markdown file for you. You can access it here: 
MD icon
Non_Functional_Requirements_Document
 MD 
Open
.

Now that we have both the Functional and Non-Functional Requirements documented, would you like me to start designing the database schema or drafting the C# Entity classes next?

Gemini is AI and can make mistakes.





# 🛡️ Non-Functional Requirements (NFR) Document

This document defines the quality attributes, constraints, and performance expectations for the IT Trainz platform.

## 1. Security
*   **Authentication:** Must use ASP.NET Core Identity for user authentication. Passwords must be hashed (never stored in plain text).
*   **Authorization:** Role-Based Access Control (RBAC) must be enforced using the `[Authorize]` attribute. Admin areas must be strictly restricted.
*   **CSRF Protection:** All POST forms must include anti-forgery tokens (`@Html.AntiForgeryToken()`).
*   **SQL Injection Prevention:** Must use Entity Framework Core (parameterized queries) exclusively. No raw SQL strings concatenated with user input.
*   **XSS Prevention:** Razor views automatically encode output. Must avoid `@Html.Raw()` unless data is strictly sanitized.
*   **Secrets Management:** Database connection strings and sensitive credentials must not be committed to Git. Must use `appsettings.Development.json` (ignored by Git) or User Secrets.

## 2. Performance & Scalability
*   **Asynchronous Operations:** All database I/O operations must use `async/await` (e.g., `ToListAsync()`, `SaveChangesAsync()`).
*   **Response Time:** Public pages should load in under 2 seconds on a standard 4G connection. Admin dashboard queries should be optimized to load in under 1.5 seconds.
*   **Data Pagination:** Course lists and Admin tables must implement pagination (e.g., 10-20 records per page) to prevent loading excessive data.
*   **Scalability:** The architecture must be stateless (except for session/cookie auth) so it can be hosted on multi-server environments (like IIS/Web Farm) in the future.

## 3. Usability & UI/UX
*   **Responsiveness:** The UI must be mobile-first and fully responsive across desktop, tablet, and mobile devices using Bootstrap 5.
*   **Browser Compatibility:** Must support modern browsers (Chrome, Firefox, Edge, Safari).
*   **Form Validation:** Must implement both client-side (jQuery Unobtrusive Validation) and server-side (Data Annotations) validation.
*   **Feedback:** UI must provide immediate feedback for actions (e.g., success/error toasts, loading spinners for long operations).
*   **Accessibility:** Follow basic WCAG guidelines (sufficient color contrast, alt text for images, proper HTML semantic tags).

## 4. Localization (Bangladesh Context)
*   **Currency:** All monetary values must be displayed in BDT (৳).
*   **Phone Format:** Validation should accept standard Bangladeshi mobile number formats (e.g., +8801XXXXXXXXX or 01XXXXXXXXX).
*   **Payment Methods:** System must support local payment gateways/manual tracking (bKash, Nagad, Rocket) alongside Cash and Bank Transfer.
*   **Timezone:** All dates/times should default to Bangladesh Standard Time (BST, UTC+6).

## 5. Maintainability & Architecture
*   **Separation of Concerns:** Strict adherence to MVC architecture.
*   **ViewModels:** Views must never bind directly to database entities. ViewModels must be used to transfer data between Controllers and Views.
*   **Service Layer:** Business logic (e.g., calculating remaining balances, enrollment validation) should be extracted into injectable Services (`IEnrollmentService`, `IPaymentService`).
*   **Dependency Injection:** Must use ASP.NET Core built-in DI for all services and contexts.
*   **Fluent API:** Database constraints and relationships should be configured using EF Core Fluent API inside `ApplicationDbContext` to keep entity classes clean.

## 6. Reliability & Availability
*   **Error Handling:** Global exception handling middleware must be configured to catch unhandled errors and display a custom error page (not stack traces).
*   **Logging:** Errors and significant events (e.g., failed logins, successful payments) must be logged using ASP.NET Core `ILogger`.
*   **Database Backups:** (Operational requirement) Database must be backed up periodically.

---

## Explanation

### 6.1 — Security & NFRs
Security is the most critical NFR for a system handling payments and user data. By writing this down, we commit to never writing raw SQL queries with user input and to always use Identity's built-in hashing.

### 6.2 — The "ViewModel" Rule
Notice the maintainability rule: Views must never bind directly to database entities. This is a common beginner mistake. Later, when we create a Course, the database entity will have navigation properties (like Batches and Instructor), but the view creating the course only needs a DropdownList of Categories. We will use a `CourseCreateViewModel` to pass only what the UI needs.

### 6.3 — Localization Constraints
By specifying the timezone (UTC+6) and currency (BDT) now, we know exactly how to format our HTML helpers and validation attributes in Phase 4 and 5.
Non_Functional_Requirements_Document.md
Displaying Non_Functional_Requirements_Document.md.