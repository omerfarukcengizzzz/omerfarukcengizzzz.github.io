# Omer Cengiz

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

The original application had no meaningful automated tests. This enhancement added 53 end-to-end tests using Playwright, organized into three test suites:

- **Customer Tests** — Homepage loading, trip browsing, search functionality, login/logout, and cart access
- **Admin Tests** — Login, trip listing, full CRUD operations (create, read, update, delete) including browser dialog handling
- **Auth Tests** — Protected route verification, API token validation, and login error message security (ensuring no email enumeration)

Technical implementation includes separate Playwright projects for the customer site (port 3000) and admin SPA (port 4200), helper functions for user registration and login, global setup for test data seeding, and conditional screenshot/video capture on failure.

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

**Enhancement:** Security Hardening (Rate Limiting, RBAC, Input Sanitization)

The original application had JWT authentication and PBKDF2 password hashing but lacked several critical security controls. This enhancement added three layers of protection:

- **Rate Limiting** — express-rate-limit middleware protects authentication endpoints. Login is limited to 5 attempts per 15-minute window, registration to 3 attempts per hour. Exceeded limits return a 429 status with a clear retry message.
- **Role-Based Access Control (RBAC)** — The User schema was extended with a role field ('user' or 'admin', defaulting to 'user'). The JWT payload now includes the role, and a requireAdmin middleware verifies permissions before allowing trip creation, update, or delete operations.
- **NoSQL Injection Prevention** — express-mongo-sanitize runs as global middleware, stripping $ and . characters from request bodies and query parameters before they reach route handlers.

**Skills Demonstrated:** API security, rate limiting, role-based access control, input sanitization, middleware architecture

**Course Outcomes:** 4 (Tools and techniques), 5 (Security mindset)

---

### Code

[View the Travlr Getaways Repository](https://github.com/omerfarukcengizzzz/CS-499)

---

### Coming Soon
- Professional Self-Assessment

---

### Contact
- GitHub: [omerfarukcengizzzz](https://github.com/omerfarukcengizzzz)
