🎓 IT Trainz — IT Training Center (ASP.NET Core MVC)
A professional, responsive website for a Bangladeshi IT training center.
Built as a real-world learning project using ASP.NET Core MVC, Entity Framework Core, and SQL Server.

📌 Project Overview
IT Trainz allows students to browse courses, view batches, enroll online, and track payments. Administrators can manage the entire training center through a dedicated admin panel.

👥 User Roles
Role	Capabilities
Guest	Browse courses, instructors, batches; submit contact form
Student	Register, enroll, view dashboard, track payments
Instructor	(Future) View assigned batches and students
Admin	Full CRUD over students, instructors, courses, batches, enrollments, payments
🧰 Technology Stack
ASP.NET Core MVC (.NET 9 / latest stable for VS 2026)
C#
Entity Framework Core
SQL Server + SSMS
ASP.NET Core Identity
Bootstrap 5
Razor Views
Git & GitHub
🗂️ Project Modules
Public Website
Home, About, Contact
Courses listing & details
Instructors
Batches / Schedule
Student Area
Registration & Login
Dashboard
Enrolled Courses
Payment History
Profile Management
Admin Panel (/Admin)
Dashboard with statistics
Student / Instructor / Course / Category / Batch management
Enrollment approval
Payment tracking (Cash, bKash, Nagad, Bank, Card)
📐 Architecture
Controllers / Services / Repositories
ViewModels (no entities exposed to views)
EF Core Fluent API configuration
Dependency Injection
Role-based Authorization
Area-based Admin Panel
🚀 Setup (Will be documented as we build)
Clone the repo
Configure connection string in appsettings.json
Run EF Core migrations
Run the project
(Detailed instructions will be added after Step 13.)

📈 Roadmap Status
 Phase 0 — Planning & Requirements
 Phase 1 — Environment Setup
 Phase 2 — Database & EF Core
 Phase 3 — Authentication & Authorization
 Phase 4 — Layout & UI
 Phase 5 — Public Website
 Phase 6 — Student System
 Phase 7 — Enrollment & Payment
 Phase 8 — Admin Panel
 Phase 9 — Security & Validation
 Phase 10 — UI/UX Polish
 Phase 11 — Testing
 Phase 12 — Documentation
 Phase 13 — Deployment
 Phase 14 — Final Review
🔒 Security
ASP.NET Core Identity (hashed passwords)
Role-based authorization
Anti-forgery tokens on all POST forms
No secrets committed to Git
Input validation on every form
📜 License
MIT License — free to use for learning purposes.

