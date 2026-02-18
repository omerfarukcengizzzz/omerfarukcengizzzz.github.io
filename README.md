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

### Professional Self-Assessment
Completing the Computer Science program at SNHU has been a journey that stretched over five years, and it has not been a straight line. Before pursuing computer science, I spent three years studying Electrical and Electronics Engineering in Turkey. That program exposed me to advanced physics, mathematics, and electronic circuit design, building an analytical foundation that still influences how I approach problem-solving today. Although I transitioned to computer science and now work as a Software Engineer, I still continue electronics as a hobby, building microcontroller projects and working with hardware whenever I get the chance. The shift from electronics to software was not a departure; it was a natural progression driven by a growing passion for writing code and creating things.

Before SNHU, I took foundational computer science courses in Turkey covering introductory programming and core concepts. Along the way, I had to pause my studies to focus on a major project at the company I was working for at the time. Balancing a full-time career as a Software Engineer with coursework has required discipline and constant prioritization, but it has also given me something that a traditional student path might not: the ability to immediately apply what I learn in the classroom to real-world problems and vice versa.

That combination of academic study and professional experience is what this ePortfolio represents. It is not just a collection of school projects. It is a demonstration of how theory and practice come together when building software that is tested, optimized, and secure. The capstone process, from the initial code review through three progressive enhancements, pushed me to take a project I built in a classroom setting and bring it up to the standards I hold myself to professionally.

## Collaborating in a Team Environment

Collaboration has been a constant throughout both my education and my career. At work, code reviews are part of the daily workflow. My teammates regularly point out things I have overlooked or suggest cleaner approaches, and I do the same for them. That back-and-forth is where a lot of real learning happens. It is not just about catching bugs; it is about building shared understanding of the codebase and holding each other to a higher standard.

The capstone code review reinforced this. Walking through the Travlr Getaways codebase on video, analyzing what worked and what needed improvement, and mapping those findings to specific enhancements mirrors what happens in any professional development team. The difference is that in a classroom setting, the code review is a formal deliverable. In a professional setting, it is something that happens naturally every day. Having done both, the process of examining code critically and communicating findings clearly is a skill that transfers regardless of the context.

Collaboration also means knowing when to bring people in rather than trying to solve everything solo. Taking ownership of a task is important, but carrying too much alone can slow a project down. Learning to delegate, ask for support early, and trust teammates with parts of the work is an ongoing area of growth. That balance between independence and teamwork is something the program reinforced and professional experience continues to sharpen.

## Communicating with Stakeholders

One of the most important things the program reinforced is that technical skill means very little if it cannot be communicated clearly. Writing code that works is one thing. Explaining why a particular approach was chosen, what trade-offs were considered, and how a solution addresses a specific problem is a different skill entirely, and one that matters just as much in a professional environment.

The capstone narratives required exactly this kind of communication. Each enhancement needed a written explanation covering what was changed, why it was changed, what skills it demonstrated, and how it aligned with specific course outcomes. This is not unlike writing documentation at work or explaining a technical decision to a non-technical stakeholder. The audience determines how deep the explanation goes, but the core requirement is the same: be clear, be specific, and make the value obvious.

The code review video added another dimension to this. Presenting technical analysis verbally while demonstrating the application live requires adapting to the format. Written communication allows for revision. A video does not. That constraint pushes for clarity and preparation, which are valuable skills whether presenting to a team, a manager, or a client.

## Data Structures and Algorithms

Courses like CS 260 (Data Structures and Algorithms) built the theoretical foundation for understanding how data is organized and processed efficiently. Learning about hash tables, trees, linked lists, and sorting algorithms provides the vocabulary and mental models needed to evaluate different approaches to a problem. But the real understanding came from applying those concepts to actual systems.

At work, algorithm selection shows up constantly. Choosing between different data structures for caching, deciding how to handle pagination in APIs, or evaluating whether a particular query pattern scales well with growing data are all decisions rooted in the fundamentals. The difference between O(n) and O(log n) is not just an academic exercise; it determines whether an application stays responsive as the user base grows from hundreds to thousands to millions.

Understanding complexity analysis also shapes how I approach problem-solving in general. Breaking a problem into smaller components, identifying bottlenecks, and evaluating trade-offs between time and space are patterns that extend well beyond code. They influence how I think about system design, testing strategies, and even project planning.

## Software Engineering and Database

CS 465 (Full Stack Development) was a turning point in the program for me. This course exposed me to a framework that I have never used before. CS 465 introduced the MEAN stack: MongoDB, Express, Angular, and Node.js, all using JavaScript. Learning a completely different tech stack was challenging, but it proved something important: the underlying concepts transfer even when the tools change. RESTful API design, MVC architecture, authentication flows, and database interactions follow the same patterns regardless of whether the implementation is in Java or JavaScript.

CS 320 (Software Testing, Automation, and Quality Assurance) changed how I approach writing code. Before that course, testing was something that happened after the code was written. CS 320 taught me to think about testability from the start: how to structure code so it can be tested, how to identify edge cases before they become bugs, and how to write tests that actually validate behavior rather than just achieving coverage numbers. That mindset has become central to how I work professionally. It is one of the most directly applicable skills from the entire program.

Beyond coursework, software engineering is not just my job but my passion. I consider myself a true DIY person. I have built projects spanning automation, API development, frontend and backend web applications, microcontroller design, and even game development. That drive to build things, whether it is a home automation system, a custom API, or an IoT project wired together on a workbench, keeps me constantly learning and experimenting with new technologies and frameworks. That range of experience reinforces the adaptability that this field demands. Frameworks and languages evolve constantly, but the fundamentals of good software engineering, including clean architecture, separation of concerns, proper error handling, and maintainable code, remain consistent.

## Security

CS 405 (Secure Coding) and CS 410 (Software Reverse Engineering) shaped how I think about security from two different angles. Secure coding taught the proactive side: input validation, secure authentication patterns, and defensive programming practices that prevent vulnerabilities from being introduced in the first place. Reverse engineering taught the analytical side: understanding how software works at a binary level, how compiled code behaves without source access, and how attackers can identify and exploit weaknesses in software systems.

Together, these courses built a security mindset that goes beyond following a checklist. It is about thinking like an attacker while building like a defender. Every API endpoint is a potential attack surface. Every user input is potentially malicious. Every authentication flow is a target for exploitation. That perspective does not make development slower; it makes it more intentional. When security considerations are part of the design process from the beginning, the resulting code is more robust and the cost of addressing vulnerabilities is significantly lower than retrofitting security after the fact.

In the industry, this aligns directly with the shift-left security movement. Organizations are increasingly expecting developers to own security rather than treating it as a separate team's responsibility. Having both the theoretical knowledge from coursework and the practical experience of implementing security controls professionally puts me in a strong position to meet that expectation.

## Portfolio Summary: How the Artifacts Fit Together

For this capstone, I chose a single artifact for all three enhancement categories: Travlr Getaways, a full-stack travel booking application built with the MEAN stack in CS 465. The application includes a customer-facing website built with Express and Handlebars, an Angular admin dashboard for managing trip listings, a REST API connecting both frontends, and a MongoDB database with JWT authentication. Using one artifact across all three categories was a deliberate choice. It allows the portfolio to tell a cohesive story where each enhancement builds on the previous one, rather than presenting three disconnected projects.

Enhancement One (Software Design and Engineering) established the foundation by adding 54 end-to-end tests using Playwright. The application originally had zero meaningful tests. The test suite now covers customer browsing flows, admin CRUD operations, and authentication security behaviors across both frontends. This enhancement demonstrated test strategy design, modern tooling with an industry-standard framework, and a security-aware approach to validating that protected resources actually require authentication. Critically, the tests also discovered a real bug in the search functionality, which directly motivated the second enhancement.

Enhancement Two (Algorithms and Data Structures) addressed that search bug by replacing the entire search implementation. The original approach fetched all trips from the database and filtered them in JavaScript using the includes() method, which is O(n) complexity. The enhanced version uses MongoDB text indexes backed by B-tree structures, reducing search complexity to O(log n). With weighted fields, the search now returns results ranked by relevance: a trip with the search term in its name scores higher than one that only mentions it in the description. This enhancement demonstrated algorithm analysis, understanding of database indexing internals, and the ability to evaluate trade-offs between different approaches.

Enhancement Three (Databases) added layered security controls to the application. Rate limiting on authentication endpoints blocks brute force attacks. Role-based access control with a new role field in the User schema ensures only administrators can create, update, or delete trips. Input sanitization using express-mongo-sanitize strips dangerous MongoDB operators from user input to prevent NoSQL injection attacks. Password hashing was also upgraded from 1,000 to 600,000 PBKDF2 iterations to meet current OWASP standards. This enhancement demonstrated the security mindset in practice: identifying specific attack vectors and implementing appropriate defenses at the middleware level.

The three enhancements are interconnected. The Playwright tests from Enhancement One verified the search fix in Enhancement Two and provided the infrastructure to validate the security controls in Enhancement Three. The search optimization from Enhancement Two improved the data layer that Enhancement Three then secured. Together, they take a classroom project and transform it into something closer to production-ready software: tested, performant, and secure.

This portfolio, along with the code review and narratives that accompany each enhancement, demonstrates the full range of skills developed throughout the Computer Science program. It shows not just the ability to write code, but the ability to evaluate it critically, optimize it strategically, and secure it proactively. These are the skills that separate a developer who ships working features from an engineer who builds reliable systems.

