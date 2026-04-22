MASTER REQUIREMENT DOCUMENT
Sri Sastha Paruthipaal Billing and Shop Operations System

Version: 2.0
Date: April 22, 2026
Project Type: Mobile-First Web Application
Prepared For: Sri Sastha Paruthipaal
Prepared By: Product / Engineering Requirement Draft

1. Executive Summary

Sri Sastha Paruthipaal requires a simple, fast, and reliable billing application for day-to-day counter operations. The system must help staff generate bills quickly, print receipts through a Bluetooth thermal printer, maintain product and pricing records, track sales, and give the admin visibility into daily business performance.

This is not just a billing screen. It is a small business operations platform designed for a beverage shop, with support for product management, billing, bill history, reports, user access control, printer setup, daily closing, audit tracking, backup support, and structured deployment using Docker and Azure DevOps.

The solution must be mobile-first because the staff will primarily use it on a phone or tablet at the billing counter.

2. Business Context
2.1 Business Overview
Business Name: Sri Sastha Paruthipaal
Business Type: Beverage Shop / Counter Sales Shop
Nature of Business: Walk-in customer billing
Current Problem: Manual or semi-manual billing is slower and harder to track
Main Need: Fast billing, accurate records, and easy reporting
Location Model: Single shop location initially
2.2 Products Sold

The current product list includes:

Rose Milk
Badam Milk
Water Bottle
Paruthipaal
Sugar Cane Juice

The system must support adding, editing, enabling, disabling, and expanding products in the future.

2.3 Primary Business Goals
Reduce billing time at the counter
Maintain accurate sales records
Print receipts immediately
Track daily sales and top products
Reduce human calculation errors
Support multiple staff users
Give the owner an easy admin dashboard
Prepare the system for future expansion
3. Project Objectives

The application must:

Provide fast and simple billing
Work well on mobile devices
Support role-based access
Track bills and product sales
Print thermal receipts
Support daily business reporting
Support deployment through Docker
Support CI/CD through Azure DevOps
Separate development and production environments
Be scalable for future features like stock, online orders, and Android app integration
4. Scope
4.1 In Scope
Admin and Staff login
User management
Product management
Billing module
Bill history
Bill reprint
Bluetooth printer integration
Sales dashboard
Daily / monthly / product reports
Shop settings
Shift open / close or daily closing
Payment mode tracking
Bill cancellation / void
Audit logs
Backup and restore planning
Docker-based deployment
Azure DevOps pipeline setup
Dev and production environment setup
Testing, release, and support plan
4.2 Out of Scope for Phase 1
Online payment gateway integration
Customer loyalty points
Supplier management
Payroll / HR
Multi-branch management
Native Android app
Online order aggregation integration
Full warehouse-level inventory management
5. Users and Roles
5.1 Admin

Admin has access to:

Dashboard
User management
Product management
Billing
Bill history
Reports
Printer settings
Shop configuration
Shift closing reports
Audit logs
Deployment/configuration support views if required
5.2 Staff

Staff has access to:

Login
Billing
Bill history
Bill reprint
Limited bill cancellation based on permission
Shift-related basic actions if allowed
5.3 Future Optional Roles
Supervisor
Cashier
Auditor
6. Functional Requirements
6.1 Authentication and Access Control
FR-1 Login
Users must log in with username and password
System must validate credentials securely
Clear error message must be shown for invalid login
FR-2 Session Handling
Session timeout after inactivity
Warning before automatic logout
Manual logout available at all times
FR-3 Role-Based Access
Admin can access all modules
Staff can access only allowed modules
Unauthorized access attempts must be blocked and logged
FR-4 Password Security
Passwords must be hashed
Password reset option for admin-managed users
Admin can create and disable staff accounts
6.2 User Management
FR-5 Create User
Admin can create staff users
Required fields: username, password, role, status
FR-6 Edit User
Admin can update user details
Admin can activate or deactivate a user
FR-7 Reset Password
Admin can reset user password
FR-8 User Status
Disabled users must not be able to log in
6.3 Product Management
FR-9 View Product List
Admin can view all products
Product list must show name, price, status, and created date
FR-10 Add Product
Admin can create new products
Required: name and price
Optional: description, display order, category
FR-11 Edit Product
Admin can update product details
New price must apply only to future bills
Previous bills must preserve old price values
FR-12 Activate / Deactivate Product
Inactive products must not appear in billing screen
Admin can change product status at any time
FR-13 Product Search and Filter
Search by name
Filter by active/inactive status
FR-14 Bulk Status Update
Admin can activate or deactivate multiple products together
6.4 Billing Module
FR-15 Billing Screen
Staff must see active products only
Products must be shown in large mobile-friendly buttons or cards
FR-16 Add Product to Bill
Staff can tap a product to add it to the current bill
FR-17 Quantity Update
Quantity must be editable
Support whole numbers, and optional decimal quantity if required by product type
FR-18 Auto Calculation
System must automatically calculate subtotal and total
FR-19 Remove Item
Staff can remove items before finalizing the bill
FR-20 Clear Bill
Staff can reset the current bill after confirmation
FR-21 Bill Number
System must generate a unique bill number
FR-22 Finalize Bill
Bill must be stored only after validation succeeds
Bill creation must be atomic
FR-23 Bill Preview
Staff must see the bill preview before printing if configured
FR-24 Quick Billing UX
Recent products shortcut
Quick quantity controls like +1 / -1
Fast search inside billing screen
Auto focus behavior for faster usage
FR-25 Payment Mode
Bill must capture payment mode
Phase 1 modes: Cash, UPI, Card
Cash is default if not changed
FR-26 Void / Cancel Bill
Authorized users can cancel or void a bill
Reason is mandatory
Original bill must remain in audit history
6.5 Printer Integration
FR-27 Bluetooth Printer Connection
System must detect or allow manual selection of Bluetooth printer
FR-28 Print Receipt
Bill can be printed after generation
FR-29 Reprint Bill
Existing bills can be reprinted from bill history
FR-30 Receipt Format

Receipt must include:

Shop name
Date and time
Bill number
Items
Quantity
Unit price
Line total
Payment mode
Grand total
Footer message
Reprint mark if applicable
FR-31 Test Print
Admin must be able to perform test print
FR-32 Printer Error Handling
Printer disconnected
Printer not found
Print failed
Retry option
6.6 Bill History
FR-33 View Bills
View all bills in descending order by latest first
FR-34 Search Bill
Search by bill number
FR-35 Date Filter
Filter by today, week, month, custom range
FR-36 Bill Details
Open full bill details including item list and payment mode
FR-37 Reprint from History
Reprint directly from bill details or list
FR-38 Export Bills
Export filtered bills to CSV
FR-39 Pagination
Bill list must support pagination
6.7 Dashboard
FR-40 Daily Summary
Total sales
Number of bills
Total items sold
Average bill amount
FR-41 Top Products
Best selling products by quantity
Highest revenue products
FR-42 Sales Trend
Hourly or daily sales trend where applicable
FR-43 Peak Hour
Show peak sales hour
FR-44 Comparison
Today vs yesterday comparison
Optional weekly trend
6.8 Reports
FR-45 Daily Report
Daily sales summary and product breakdown
FR-46 Monthly Report
Monthly summary and day-wise totals
FR-47 Product Report
Product-wise quantity and revenue
FR-48 Custom Date Report
Start date and end date selection
FR-49 Export
CSV export in Phase 1
PDF export optional in next phase
6.9 Shift / Daily Closing
FR-50 Shift Open
System may support day open/start shift action
FR-51 Shift Close
End of day summary must be generated
FR-52 Closing Summary

Must include:

Opening time
Closing time
Total bills
Total collection
Payment mode summary
Cancelled bills count
Reprint count if needed
FR-53 Cash Verification
Admin can enter actual cash counted
Difference between system and manual entry can be shown
6.10 Shop Settings / Configuration
FR-54 Shop Profile
Shop name
Address
Contact number
Receipt footer
FR-55 Billing Settings
Currency symbol
Tax visibility if enabled later
Decimal settings
Printer paper width
Bill preview enable/disable
FR-56 Product Display Settings
Product sort order
Category grouping if required later
6.11 Audit and Logs
FR-57 Audit Logging

System must log:

User login
User logout
Product create/edit/status change
Bill creation
Bill cancel/void
Password reset
Printer setting change
FR-58 Audit View
Admin can view key audit records
6.12 Backup and Recovery
FR-59 Backup Planning
Database backup must be taken regularly
FR-60 Restore Support
Restore process must be documented
7. Non-Functional Requirements
7.1 Performance
Product load under 1 second for normal product count
Billing interaction must feel immediate
Bill generation target under 2 seconds
Dashboard under 3 seconds
Reports under 10 seconds for expected data size
7.2 Mobile Responsiveness
Fully usable on mobile phones and tablets
No horizontal scrolling in standard screens
Buttons must be touch-friendly
7.3 Reliability
No partial bill save
System must fail safely
Clear retry/recovery messaging
7.4 Security
Hashed passwords
JWT or secure token-based authentication
HTTPS required in production
Role-based route and API protection
Validation against SQL injection and XSS
7.5 Availability
System should be available during business hours
Planned maintenance must be controlled
7.6 Maintainability
Proper code structure
Modular backend and frontend architecture
Environment-based configuration
Clear documentation
7.7 Scalability
Support future product growth
Support more users and larger bill history over time
7.8 Auditability
Critical actions must be traceable by user and timestamp
8. Data Requirements and High-Level Schema
8.1 Main Tables
roles
users
products
product_price_history
bills
bill_items
bill_payments
bill_status_history
shifts
printer_settings
app_settings
audit_logs
8.2 Important Data Rules
Bills must preserve historical price
Deleted products should be soft deleted or disabled
Cancelled bills must remain in the database
User actions must be traceable
9. API Requirements
9.1 API Architecture
REST API
JSON request/response
Protected endpoints require authentication
9.2 Main API Groups
Auth APIs
User APIs
Product APIs
Billing APIs
Bill history APIs
Reports APIs
Dashboard APIs
Printer APIs
Settings APIs
Audit APIs
9.3 Standard Response Model
success flag
message
data
error code if applicable
timestamp
10. User Interface Requirements
10.1 Design Principles
Mobile-first
Fast and simple
Minimum training required
Clear labels
Minimal steps for billing
Error messages in simple language
10.2 Main Screens
Login page
Dashboard
Product management
User management
Billing screen
Bill preview
Bill history
Reports
Shift closing
Printer settings
Shop settings
Audit logs
10.3 Billing Screen UX Requirements
Product grid/cards
Fast add/remove
Running total always visible
Quick payment mode selection
Print action visible after valid bill
Search products in billing screen
Good touch spacing
11. Business Rules
Only active products can be billed
Completed bills cannot be edited directly
Cancelled bills must stay in history
Bill number must be unique
Prices used in a bill must remain unchanged for that bill forever
Staff access must be restricted
User deactivation blocks login
Audit log must capture critical actions
Payment mode is mandatory before completion if configured as required
Bill save must be atomic
Printer configuration must be admin controlled
Shift closing data must reflect actual bills in the system
12. Validation Rules
12.1 User Validation
Username required
Password required
Role required
Status required
12.2 Product Validation
Product name required
Price must be greater than zero
Duplicate active product names should be prevented or warned
Status required
12.3 Billing Validation
At least one item required
Quantity must be positive
Total must match calculated amount
Payment mode required if enabled
Product must be active at billing time
12.4 Settings Validation
Paper width must be valid
Shop configuration fields must respect max length
13. Error Handling

The system must handle:

Invalid login
Session expiry
Unauthorized access
Product not found
Invalid quantity
Bill save failure
Network failure
Printer disconnected
Printer not found
Database unavailable
Unexpected server errors

Each error must provide:

Clear user-facing message
Logging on backend
Recovery path where possible
14. Technology Stack
14.1 Frontend
Angular
TypeScript
Angular Router
Reactive Forms
HTTP Client
Angular Material or equivalent UI library
Mobile-responsive styling
14.2 Backend
FastAPI
Python
SQLAlchemy
Alembic for migrations
JWT authentication
Pydantic for validation
14.3 Database
PostgreSQL
14.4 Infrastructure and DevOps
Docker
Docker Compose for local or simple server orchestration
Azure DevOps for CI/CD
GitHub as source repository if preferred
Azure VM / VPS / Linux server for deployment target
15. Environment Strategy

The system must support at least two environments.

15.1 Development Environment
Purpose: local development and internal testing
Database: billing_dev_db
User: billing_dev_user
Separate environment variables
Separate Docker Compose override if needed
15.2 Production Environment
Purpose: live shop use
Database: billing_prod_db
User: billing_prod_user
Separate secrets
Separate deployment pipeline stage
15.3 Optional Future Environment
QA/UAT/Staging
16. Docker Requirements
16.1 Backend Container
Must package FastAPI app and dependencies
Must run database migrations as part of deployment process or pre-start step
16.2 Frontend Container
Must build Angular production bundle
Must serve build output through a web server such as Nginx
16.3 Database Container
PostgreSQL container can be used for local development
Production DB may be containerized or hosted separately
16.4 Docker Compose

Must support:

frontend
backend
db
shared network
environment-specific configuration
volume for database persistence in local or simple server setup
17. Azure DevOps Requirements
17.1 Source Control Flow
Code stored in GitHub or Azure Repos
Branching strategy:
main for production
develop for ongoing integration
feature branches for development
17.2 CI Pipeline

On code push or pull request:

Install frontend dependencies
Run frontend lint/tests
Build frontend
Install backend dependencies
Run backend lint/tests
Build Docker images
Publish artifacts or images
17.3 CD Pipeline

For approved branches:

Pull latest image or artifact
Run migration
Deploy frontend and backend containers
Restart services safely
Validate health check
17.4 Secret Management

Use secure pipeline variables for:

DB username
DB password
JWT secret
API keys if added later
17.5 Deployment Targets
Linux VM
VPS
Azure VM
Future: Azure Container Apps / Kubernetes if scaling grows
18. Testing Strategy
18.1 Backend Testing
Unit tests for services
API integration tests
Authentication and permission tests
Billing calculation tests
18.2 Frontend Testing
Component testing
Form validation tests
Critical billing flow tests
18.3 End-to-End Testing
Login
Product add/edit
Billing complete flow
Bill reprint
Report generation
Shift close
18.4 Performance Testing
Bill save performance
Report generation
Concurrent small-user activity
18.5 UAT
Shop owner review
Staff trial usage
Printer validation in real environment
19. Security Requirements
Password hashing with bcrypt or equivalent
Role-based API protection
Secure token handling
HTTPS in production
Input validation on both client and server
Sanitization of sensitive logs
Rate limiting for login if needed
Secure CORS policy
Restricted admin features
20. Monitoring and Logging

The solution should support:

Application logs
Error logs
Audit logs
Deployment logs
Health check endpoint
Restart / failure investigation capability

Optional future:

Email or messaging alerts on production failure
21. Backup and Recovery Strategy
21.1 Backup
Daily PostgreSQL backup
Retention plan for backup files
21.2 Recovery
Restore steps must be documented
Recovery must be tested before production go-live where possible
21.3 Minimum Goal
Data loss must be minimized
Business-critical billing history must be protected
22. Development Schedule
Total Estimated Delivery

A practical end-to-end first production version can be planned for 10 to 12 weeks for a small team.

Phase 1: Requirement Finalization and Architecture (Week 1)
Freeze scope
Confirm flows
Finalize database model
Finalize UI wireframe
Confirm printer approach
Finalize deployment target

Deliverables

Approved requirement document
Architecture note
Initial database plan
Phase 2: Project Setup and Foundation (Week 2)
Backend
FastAPI setup
Config management
DB connection
Base models
Migration setup
Auth setup
Frontend
Angular project setup
Routing
Layout
Login module
Shared UI structure
DevOps
Repository setup
Docker base files
Azure DevOps pipeline skeleton

Deliverables

App runs locally
Auth base flow ready
CI basic pipeline ready
Phase 3: User and Product Management (Week 3)
User CRUD
Product CRUD
Status management
Search/filter
Validation
Audit integration

Deliverables

User management ready
Product management ready
Phase 4: Billing Core (Week 4 and Week 5)
Billing screen
Item add/remove/update
Bill number generation
Total calculation
Payment mode capture
Bill preview
Bill save logic
Printer integration first pass

Deliverables

Core billing flow ready
Test receipt output available
Phase 5: Bill History and Reprint (Week 6)
Bill listing
Search and filter
Details view
Reprint
CSV export

Deliverables

Bill history functional
Phase 6: Dashboard, Reports, and Shift Closing (Week 7 and Week 8)
Dashboard cards
Top products
Daily and monthly reports
Product reports
Shift open/close
Summary screen

Deliverables

Admin reporting flow ready
Phase 7: Settings, Audit, Error Handling, and Hardening (Week 9)
Printer settings
Shop configuration
Audit log UI
Better validations
Error handling improvements
Security review

Deliverables

Production feature completeness
Phase 8: Testing and Bug Fixing (Week 10)
Integration testing
End-to-end tests
Performance checks
Mobile testing
Printer real testing

Deliverables

Stable release candidate
Phase 9: Docker, Azure DevOps, and Production Deployment (Week 11)
Docker image optimization
CI/CD finalization
Production environment setup
Migration and deployment testing
Backup process setup

Deliverables

Production deployment ready
Phase 10: UAT, Training, and Go-Live (Week 12)
Owner testing
Staff training
Fix final issues
Go-live
Hypercare support

Deliverables

Live production system
23. Team Plan and Responsibility
Suggested Small Team Structure
Frontend Developer
Backend Developer
QA / DevOps Engineer
Optional UI/Business Reviewer
Optional DBA support
Responsibility Breakdown
Frontend
UI, routing, forms, validations, responsive design
Backend
APIs, auth, business rules, DB operations, logging
QA / DevOps
test plans, regression, Docker, Azure DevOps pipeline, release coordination
24. Acceptance Criteria

The system will be considered ready when:

Login works correctly
Admin and staff permissions work correctly
Product management works correctly
Bills can be generated and stored
Receipts can be printed and reprinted
Bill history works
Reports show correct totals
Shift close summary works
Audit logs are captured
Docker deployment works
Azure DevOps pipeline builds and deploys successfully
Production configuration is stable
Shop owner validates real billing flow
25. Risks and Mitigation
Risk 1: Printer Compatibility

Mitigation:

Validate printer model early
Build retry/error flow
Keep fallback reprint option
Risk 2: Slow Billing UX

Mitigation:

Mobile-first design
Keep billing screen lightweight
Avoid heavy calculations on client
Risk 3: Wrong Production Config

Mitigation:

Separate env files
Secret management in Azure DevOps
Health check after deployment
Risk 4: Data Loss

Mitigation:

Daily backup
Tested restore process
Soft delete where needed
Risk 5: Scope Creep

Mitigation:

Freeze Phase 1 scope
Move extra features to Phase 2 list