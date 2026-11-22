# SDA-Constraction-Management-System-

SDA Construction Management System —
System Requirements Specification (SRS) |
Date: November 19, 2026
1. Introduction & System Overview
Purpose
The purpose of this document is to define the functional, non-functional, and technical
architectural requirements for the SDA Construction Management System. The platform
serves as a centralized web-based solution designed to streamline multi-site construction
operations, financial tracking, material logistics, daily site execution, and enterprise reporting.
Scope
The SDA Construction Management System encompasses end-to-end management of civil
and general construction projects. Key operational capabilities include:
● Centralized multi-site tracking and project milestone progression.
● Fine-grained Role-Based Access Control (RBAC) across corporate and field
operations.
● Bill of Quantities (BoQ) establishment and real-time financial budget monitoring.
● End-to-end digital material requisition and site inventory tracking.
● Daily field logging, workforce attendance, safety reporting, and photo documentation.
● Automated financial reporting, variance analysis, and operational summary exports.
2. Functional Requirements
2.1 User Roles & Authentication
● Admin / Director: Holds global system administrative privileges. Responsible for user
account lifecycle management, global financial approvals, policy enforcement, and
audit log inspection.
● Project Manager (Engineer / Architect): Responsible for creating and configuring
construction projects, structuring phase tasks, uploading technical blueprints and
permits, and reviewing/approving field material requisitions.
● Site Supervisor: Enforces field-level operations. Responsible for submitting daily site
progress logs, tracking trade workforce attendance, recording safety incidents, and
initiating field material requisitions.
● Procurement / Accountant: Manages vendor quotes, issues purchase orders, logs site
material deliveries, tracks phase-wise project expenses, and reconciles financial
budgets.
2.2 Project & Task Management
● Multi-Site Administration: Create, update, and manage multiple concurrent
construction sites. Store core project metadata including start dates, projected target
completion dates, client/stakeholder contacts, and geographical site coordinates.
● Phase & Milestone Breakdown: Divide projects into structured Work Breakdown
Structures (WBS) across standard execution phases (e.g., Site Preparation,
Foundation, Framing, Roofing, Electrical & Plumbing, Finishing). Track phase-specific
target completion percentages and dependencies.
● Document Management: Centralized repository to upload, store, categorize, and
version-control key project documentation including architectural drawings,
engineering blueprints, municipal permits, and legal contracts (supporting PDF, CAD
formats, and high-resolution raster images).
2.3 Budget & Financial Tracking
● Bill of Quantities (BoQ) Allocation: Establish baseline BoQ financial allocations per
project phase prior to project kickoff.
● Real-Time Expense & Variance Monitoring: Track actual expenditures against
allocated phase budgets in real time. Automatically flag cost overruns, pending
liabilities, and significant financial variances via dashboard notifications.
● Financial Reporting & Data Export: Generate structured, client-ready financial
summaries, cost-to-complete forecasts, and progress reports exportable in
standardized PDF and Microsoft Excel formats.
2.4 Materials & Inventory Management
● Site Inventory Tracking: Maintain real-time stock levels of critical construction
materials (e.g., cement bags, structural steel, timber, aggregates, electrical/plumbing
fixtures) per project location.
● Digital Material Requisition Workflow:
a. Site Supervisor drafts and submits a material request based on site
consumption needs.
b. Project Manager reviews, validates quantities, and grants engineering approval.
c. Procurement / Accountant issues purchase orders, logs incoming vendor
deliveries, and automatically updates site inventory stock.
● Automated Threshold Alerts: System triggers immediate low-stock notifications to
procurement personnel when on-site material inventories fall below pre-configured
safety thresholds.
2.5 Workforce & Daily Site Logs
● Workforce & Wage Management: Record daily labor headcount categorized by
specialized trade (e.g., masons, carpenters, electricians, steel fixers, general laborers).
Compute daily and weekly wage totals based on logged attendance.
● Daily Site Logs: Submit structured end-of-day site reports capturing operational
metrics:
○ Weather conditions and operational impact.
○ Work completed per phase against schedule.
○ Heavy equipment usage and machinery hours.
○ Safety incidents, near-misses, or hazardous site conditions.
○ Timestamped site progress photos with descriptive captions.
3. Non-Functional Requirements
● Security: Enforce strict Role-Based Access Control (RBAC). User authentication must
utilize secure salted password hashing via ASP.NET Core Identity. Protect active user
sessions against cross-site request forgery (CSRF) and enforce enterprise-wide
HTTPS/TLS encryption for all data in transit.
● Auditability: Maintain an immutable operational audit log recording user identity,
precise UTC timestamps, IP addresses, and before/after state values for all financial
approvals, budget revisions, user privilege changes, and inventory adjustments.
● Performance: Standard web pages, operational dashboards, and database queries
must achieve end-to-end rendering in under 2.0 seconds under a baseline load of up
to 50 concurrent active users.
● Usability & Responsiveness: Deliver a fully responsive web application interface. UI
components must seamlessly adapt for desktop web browsers (used for office
management and financial administration) and mobile/tablet touch screens (optimized
for field entry by Site Supervisors).
● Reliability & Backup: Configure automated daily database backups alongside
continuous transaction logging to guarantee a Recovery Point Objective (RPO) of < 1
hour and prevent loss of core financial, inventory, or legal records.
4. Hardware & Software Requirements (.NET Implementation)
Category Development Environment Production / Deployment
Environment
Runtime / SDK .NET 8 SDK (LTS) .NET 8 Runtime / ASP.NET
Core Hosting Bundle
Backend & UI Framework ASP.NET Core MVC, Razor
Pages, or Blazor
ASP.NET Core on Linux
(Ubuntu 22.04 LTS+) or
Windows Server 2022
Database Engine SQL Server Express,
PostgreSQL, or SQLite
SQL Server Standard Edition or
PostgreSQL 15+
Server Hardware Specs 8 GB RAM, Quad-core CPU, 20
GB free SSD
4–8 GB RAM, 2–4 vCPUs, 50+
GB SSD storage
Category Development Environment Production / Deployment
Environment
Client Browser Google Chrome, Microsoft
Edge, or Mozilla Firefox
(Latest)
Any modern desktop or mobile
web browser (Chrome, Safari,
Edge, Firefox)
