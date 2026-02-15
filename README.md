# Omer CENGIZ

## Computer Science ePortfolio

Welcome to my professional portfolio for the CS 499 Computer Science Capstone at SNHU.

---

### Code Review

A comprehensive code review of my capstone artifact, Travlr Getaways - a full-stack MEAN application.

[![Code Review Video](https://img.youtube.com/vi/LIy8FtGkRko/0.jpg)](https://youtu.be/LIy8FtGkRko)

[Watch the Code Review on YouTube](https://youtu.be/LIy8FtGkRko)

---

### Enhancement One: Software Design & Engineering

**Artifact:** Travlr Getaways — MEAN Stack Travel Booking Application (CS 465)

**Enhancement:** End-to-End Testing with Playwright

The original application had no meaningful automated tests. This enhancement added 54 end-to-end tests using Playwright, achieving a 100% pass rate. Tests are organized into three suites:

- **Customer Tests** — Homepage loading, trip browsing, search functionality, login/logout, and cart access
- **Admin Tests** — Login, trip listing, full CRUD operations (create, read, update, delete) including browser dialog handling
- **Auth Tests** — Protected route verification, API token validation, and login error message security (ensuring no email enumeration)

Technical implementation includes separate Playwright projects for the customer site (port 3000) and admin SPA (port 4200), helper functions for user registration and login, global setup for test data seeding, and conditional screenshot/video capture on failure. After all enhancements were merged, 14 post-merge test failures caused by schema changes, pagination response formats, and rate limiter configuration were identified and resolved.

The tests discovered a real bug in the search functionality, which was subsequently fixed in Enhancement Two.

**Skills Demonstrated:** E2E test design, browser automation, cross-frontend testing, security validation

**Course Outcomes:** 3 (Design and evaluate solutions), 4 (Tools and techniques), 5 (Security mindset)

---

### Enhancement Two: Algorithms & Data Structures

**Artifact:** Travlr Getaways — MEAN Stack Travel Booking Application (CS 465)

**Enhancement:** MongoDB Text Indexes and Optimized Search

The original search fetched all trips from the database and filtered them client-side using JavaScript's includes() method — an O(n) approach that checked every trip for every search. This enhancement replaced that with MongoDB text indexes, reducing search complexity to O(log n).

A compound text index was added with weighted fields: name (weight: 10), resort (weight: 5), category (weight: 3), and description (weight: 1). The weights ensure that a trip with the search term in its name ranks higher than one that only mentions it in the description. MongoDB calculates relevance scores automatically using the $meta: 'textScore' operator.

The API controller now accepts search and category as query parameters, building MongoDB queries with the $text operator. Both filters work together, allowing users to search within a specific category. Category tab badges display accurate counts through a separate aggregation call.

**Scalability:** With 100 trips, client-side filtering performs ~400 comparisons versus ~7 index lookups. With 10,000 trips, that gap grows to ~40,000 comparisons versus ~13 lookups.

**Skills Demonstrated:** Algorithm analysis, database indexing, MongoDB aggregation pipelines, performance optimization

**Course Outcomes:** 3 (Design and evaluate solutions), 4 (Tools and techniques)

---

### Enhancement Three: Databases

**Artifact:** Travlr Getaways — MEAN Stack Travel Booking Application (CS 465)

**Enhancement:** Comprehensive Security Hardening

The original application had JWT authentication and basic PBKDF2 password hashing but lacked several critical security controls. This enhancement implemented multiple layers of protection across nine improvement branches:

**Authentication & Password Security**
- Upgraded PBKDF2 password hashing from 1,000 to 600,000 iterations, meeting OWASP 2023 standards

**Rate Limiting**
- express-rate-limit middleware protects authentication endpoints. Login is limited to 5 attempts per 15-minute window, registration to 3 attempts per hour. Smart rate limiting differentiates between brute force attacks and legitimate users.

**Role-Based Access Control (RBAC)**
- The User schema was extended with a role field ('user' or 'admin', defaulting to 'user'). A requireAdmin middleware verifies permissions, and ownership checks were added across all 12 sensitive endpoints to ensure users can only modify their own data.

**Input Validation & Sanitization**
- express-mongo-sanitize runs as global middleware, stripping $ and . characters to prevent NoSQL injection. Comprehensive express-validator schemas were added to every POST/PUT/PATCH route for strict input validation.

**Frontend Security**
- Angular admin SPA secured with CanActivateFn route guards, preventing unauthorized navigation to admin pages.

**Skills Demonstrated:** API security, rate limiting, role-based access control, input validation and sanitization, middleware architecture, frontend route protection

**Course Outcomes:** 4 (Tools and techniques), 5 (Security mindset)

---

### Additional Improvements

Beyond the three core enhancements, the following architectural improvements were made:

- **Controller Modernization** — Refactored 7 controllers from the deprecated request module to native fetch with async/await
- **Direct Database Queries** — Replaced inefficient HTTP self-calls in the customer app with direct Mongoose queries
- **Scalable Pagination** — Added pagination to the trips and bookings APIs to handle both small datasets and thousands of records
- **Data Model Standardization** — Converted pricing fields from strings to proper numeric types to prevent calculation bugs

---

### Code

[View the Enhanced Travlr Getaways Repository](https://github.com/omerfarukcengizzzz/CS-499)

---

### Coming Soon
- Professional Self-Assessment
