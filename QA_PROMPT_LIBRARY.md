# QA Prompt Library

## Table of Contents
1. [Introduction](#introduction)
2. [What is Prompting?](#what-is-prompting)
3. [Types of Prompts](#types-of-prompts)
4. [Prompt Categories by Use Case](#prompt-categories-by-use-case)
5. [Best Practices](#best-practices)
6. [Examples by Testing Domain](#examples-by-testing-domain)

---

## Introduction

This library provides a comprehensive collection of AI prompts specifically designed for QA professionals. Whether you're writing test cases, analyzing bugs, or automating tests, these prompts will help you leverage AI tools effectively.

**Target Audience:** QA Engineers, Test Leads, SDET, QA Managers

---

## What is Prompting?

**Prompting** is the art of crafting clear, specific instructions to AI tools to get desired outputs. A well-written prompt:
- Provides context about your testing scenario
- Specifies the format you need
- Includes relevant constraints or requirements
- Uses clear, unambiguous language

### Key Components of a Good Prompt
1. **Context**: Background information about the application/feature
2. **Task**: What you want the AI to do
3. **Format**: How you want the output structured
4. **Constraints**: Any limitations or specific requirements

---

## Types of Prompts

### 1. **Instructional Prompts**
Direct commands that tell the AI exactly what to do.

**Structure:**
```
[Action Verb] + [Subject] + [Context] + [Format/Constraints]
```

**Example:**
```
Generate 10 test cases for a login feature that includes email and password fields, 
considering both positive and negative scenarios. Format as a table with columns: 
Test Case ID, Description, Steps, Expected Result, Priority.
```



### 2. **Contextual Prompts**
Provide background information before asking for output.

**Structure:**
```
[Context/Background] + [Specific Request] + [Output Format]
```

**Example:**
```
We have an e-commerce application with a shopping cart feature. Users can add items, 
update quantities, and remove items. The cart persists across sessions. 
Create a test plan covering functional, usability, and edge case scenarios.
```

### 3. **Role-Based Prompts**
Ask the AI to assume a specific role or perspective.

**Structure:**
```
Act as [Role] + [Task] + [Context]
```

**Example:**
```
Act as a senior QA engineer reviewing a mobile app. Identify potential security 
vulnerabilities in a payment processing feature that handles credit card information.
```

### 4. **Comparative Prompts**
Ask for comparisons or analysis between options.

**Structure:**
```
Compare [Option A] vs [Option B] + [Criteria] + [Context]
```

**Example:**
```
Compare Selenium and Playwright for automating tests on a React-based web application. 
Consider factors: ease of setup, browser support, speed, maintenance, and community support.
```

### 5. **Iterative/Refinement Prompts**
Build upon previous responses to refine output.

**Structure:**
```
[Reference to previous output] + [Refinement request]
```

**Example:**
```
Based on the test cases you generated, now create detailed step-by-step test scripts 
with actual test data and expected API responses for the top 5 priority test cases.
```

### 6. **Template-Based Prompts**
Request output in a specific template format.

**Structure:**
```
Create [Artifact] using this template: [Template Structure]
```

**Example:**
```
Create a bug report using this template:
- Bug ID:
- Title:
- Severity:
- Priority:
- Steps to Reproduce:
- Expected Result:
- Actual Result:
- Environment:
- Attachments:
```

---

## Prompt Categories by Use Case

### A. Test Case Design

#### Use Case 1: Functional Test Cases
**Prompt:**
```
Generate comprehensive functional test cases for [Feature Name] with the following requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Include:
1. Positive test scenarios
2. Negative test scenarios
3. Boundary value analysis
4. Equivalence partitioning

Format as: Test Case ID | Description | Preconditions | Test Steps | Expected Result | Priority
```

**Example:**
```
Generate comprehensive functional test cases for a User Registration feature with the following requirements:
- Username must be 6-20 characters
- Email must be valid format
- Password must be 8+ characters with at least 1 uppercase, 1 lowercase, 1 number, 1 special character
- Age must be 18+

Include:
1. Positive test scenarios
2. Negative test scenarios
3. Boundary value analysis
4. Equivalence partitioning

Format as: Test Case ID | Description | Preconditions | Test Steps | Expected Result | Priority
```



#### Use Case 2: API Test Cases
**Prompt:**
```
Create API test cases for [Endpoint Name] with the following details:
- Method: [GET/POST/PUT/DELETE]
- Endpoint: [URL]
- Request Parameters: [List parameters]
- Expected Response: [Response structure]

Cover:
1. Valid request scenarios
2. Invalid authentication
3. Missing required fields
4. Invalid data types
5. Response status codes
6. Response time validation
```

**Example:**
```
Create API test cases for User Login endpoint with the following details:
- Method: POST
- Endpoint: /api/v1/auth/login
- Request Parameters: email (string), password (string)
- Expected Response: { "token": "string", "userId": "string", "expiresIn": "number" }

Cover:
1. Valid request scenarios
2. Invalid authentication
3. Missing required fields
4. Invalid data types
5. Response status codes (200, 400, 401, 500)
6. Response time validation (< 2 seconds)
```

### B. Test Automation

#### Use Case 3: Selenium Test Script Generation
**Prompt:**
```
Generate a Selenium WebDriver test script in [Language] for the following scenario:
[Describe the test scenario]

Requirements:
- Use Page Object Model pattern
- Include explicit waits
- Add assertions for verification
- Include error handling
- Add comments for clarity

Framework: [TestNG/JUnit/PyTest/etc.]
```

**Example:**
```
Generate a Selenium WebDriver test script in Java for the following scenario:
1. Navigate to login page
2. Enter valid credentials
3. Click login button
4. Verify user is redirected to dashboard
5. Verify welcome message displays user's name

Requirements:
- Use Page Object Model pattern
- Include explicit waits
- Add assertions for verification
- Include error handling
- Add comments for clarity

Framework: TestNG
```

#### Use Case 4: API Automation Script
**Prompt:**
```
Create a REST API automation test using [Tool/Framework] for:
- Endpoint: [URL]
- Method: [HTTP Method]
- Test Scenario: [Description]

Include:
1. Request setup with headers and body
2. Response validation (status code, response time, schema)
3. Data-driven approach with multiple test data sets
4. Assertions for all critical fields
5. Error handling
```

**Example:**
```
Create a REST API automation test using RestAssured (Java) for:
- Endpoint: https://api.example.com/users
- Method: POST
- Test Scenario: Create a new user and verify the response

Include:
1. Request setup with headers (Content-Type, Authorization) and body
2. Response validation (status code 201, response time < 3s, schema validation)
3. Data-driven approach with 3 different user data sets
4. Assertions for userId, email, createdAt fields
5. Error handling for 400 and 500 responses
```



### C. Bug Analysis & Reporting

#### Use Case 5: Bug Report Creation
**Prompt:**
```
Create a detailed bug report for the following issue:
[Describe the issue]

Include:
- Clear, concise title
- Severity and Priority assessment
- Detailed steps to reproduce
- Expected vs Actual behavior
- Environment details
- Potential impact on users
- Suggested workaround (if any)
```

**Example:**
```
Create a detailed bug report for the following issue:
When a user tries to checkout with more than 10 items in cart, the payment page 
crashes and shows a white screen. This happens on Chrome browser version 120.

Include:
- Clear, concise title
- Severity and Priority assessment
- Detailed steps to reproduce
- Expected vs Actual behavior
- Environment details
- Potential impact on users
- Suggested workaround (if any)
```

#### Use Case 6: Root Cause Analysis
**Prompt:**
```
Analyze the following bug and suggest potential root causes:

Bug Description: [Description]
Logs: [Relevant log entries]
Environment: [Environment details]

Provide:
1. Possible root causes (ranked by likelihood)
2. Areas of code/system to investigate
3. Similar known issues
4. Recommended debugging steps
```

**Example:**
```
Analyze the following bug and suggest potential root causes:

Bug Description: Users are experiencing intermittent 504 Gateway Timeout errors 
when uploading files larger than 5MB.

Logs: 
- "Connection timeout after 30000ms"
- "Upstream server not responding"

Environment: Production, AWS EC2, Nginx reverse proxy, Node.js backend

Provide:
1. Possible root causes (ranked by likelihood)
2. Areas of code/system to investigate
3. Similar known issues
4. Recommended debugging steps
```

### D. Test Planning & Strategy

#### Use Case 7: Test Plan Creation
**Prompt:**
```
Create a comprehensive test plan for [Feature/Release] with:

Project Context:
- Application: [Name and type]
- Feature: [Description]
- Timeline: [Duration]
- Team Size: [Number]

Include:
1. Test Scope (In-scope and Out-of-scope)
2. Test Strategy (Types of testing)
3. Entry and Exit Criteria
4. Test Environment Requirements
5. Risk Assessment
6. Resource Allocation
7. Test Schedule
8. Deliverables
```

**Example:**
```
Create a comprehensive test plan for Payment Gateway Integration with:

Project Context:
- Application: E-commerce Web Application
- Feature: Integration with Stripe payment gateway for credit card processing
- Timeline: 3 weeks
- Team Size: 4 QA engineers

Include:
1. Test Scope (In-scope and Out-of-scope)
2. Test Strategy (Functional, Integration, Security, Performance testing)
3. Entry and Exit Criteria
4. Test Environment Requirements
5. Risk Assessment
6. Resource Allocation
7. Test Schedule
8. Deliverables
```



#### Use Case 8: Risk-Based Testing Strategy
**Prompt:**
```
Develop a risk-based testing strategy for [Application/Feature]:

Application Details:
- [Key details]

Identify:
1. High-risk areas (with justification)
2. Medium-risk areas
3. Low-risk areas
4. Recommended test coverage for each risk level
5. Mitigation strategies
6. Prioritized test execution order
```

**Example:**
```
Develop a risk-based testing strategy for Online Banking Mobile App:

Application Details:
- Handles financial transactions
- Stores sensitive user data
- Integrates with multiple third-party services
- Used by 500K+ active users

Identify:
1. High-risk areas (with justification)
2. Medium-risk areas
3. Low-risk areas
4. Recommended test coverage for each risk level
5. Mitigation strategies
6. Prioritized test execution order
```

### E. Performance & Load Testing

#### Use Case 9: Performance Test Scenarios
**Prompt:**
```
Design performance test scenarios for [Application/Feature]:

Requirements:
- Expected concurrent users: [Number]
- Peak load: [Number]
- Response time SLA: [Time]
- Key transactions: [List]

Create scenarios for:
1. Baseline performance test
2. Load test
3. Stress test
4. Spike test
5. Endurance test

Include: User load pattern, duration, success criteria, and monitoring metrics
```

**Example:**
```
Design performance test scenarios for E-commerce Checkout Process:

Requirements:
- Expected concurrent users: 1000
- Peak load: 5000 users
- Response time SLA: < 3 seconds
- Key transactions: Add to cart, View cart, Checkout, Payment processing

Create scenarios for:
1. Baseline performance test
2. Load test
3. Stress test
4. Spike test
5. Endurance test

Include: User load pattern, duration, success criteria, and monitoring metrics
```

### F. Security Testing

#### Use Case 10: Security Test Cases
**Prompt:**
```
Generate security test cases for [Feature/Application]:

Focus Areas:
- Authentication and Authorization
- Input Validation
- Data Encryption
- Session Management
- [Other specific areas]

Cover OWASP Top 10 vulnerabilities:
1. Injection attacks
2. Broken authentication
3. Sensitive data exposure
4. XML external entities
5. Broken access control
6. Security misconfiguration
7. Cross-site scripting (XSS)
8. Insecure deserialization
9. Using components with known vulnerabilities
10. Insufficient logging and monitoring
```

**Example:**
```
Generate security test cases for User Profile Management Feature:

Focus Areas:
- Authentication and Authorization
- Input Validation (profile fields)
- Data Encryption (password, personal info)
- Session Management
- File upload security (profile picture)

Cover OWASP Top 10 vulnerabilities:
1. SQL Injection in search/filter fields
2. Broken authentication (password reset flow)
3. Sensitive data exposure (PII in logs)
4. XML external entities (if XML processing exists)
5. Broken access control (accessing other user profiles)
6. Security misconfiguration (default credentials)
7. Cross-site scripting (XSS) in bio/description fields
8. Insecure deserialization
9. Using components with known vulnerabilities
10. Insufficient logging and monitoring
```



### G. Mobile Testing

#### Use Case 11: Mobile Test Cases
**Prompt:**
```
Create mobile-specific test cases for [App Feature]:

Platform: [iOS/Android/Both]
Device Coverage: [Phones/Tablets/Both]

Include tests for:
1. Device compatibility (screen sizes, OS versions)
2. Network conditions (WiFi, 4G, 3G, offline)
3. Interruptions (calls, SMS, notifications)
4. Battery consumption
5. Permissions (camera, location, storage, etc.)
6. Gestures (swipe, pinch, rotate)
7. Orientation changes
8. App lifecycle (background, foreground, killed)
```

**Example:**
```
Create mobile-specific test cases for Photo Sharing Feature:

Platform: Both iOS and Android
Device Coverage: Phones and Tablets

Include tests for:
1. Device compatibility (iPhone 12-15, Samsung S20-S24, various screen sizes)
2. Network conditions (WiFi, 4G, 3G, offline mode with sync)
3. Interruptions (incoming call during upload, low battery warning)
4. Battery consumption during photo upload
5. Permissions (camera access, photo library access, storage)
6. Gestures (swipe to delete, pinch to zoom, rotate image)
7. Orientation changes (portrait to landscape)
8. App lifecycle (upload continues in background, resume after app killed)
```

### H. Data Testing

#### Use Case 12: Database Testing Queries
**Prompt:**
```
Generate SQL test queries for [Feature] to validate:

Database: [Database type]
Tables involved: [Table names]

Create queries to verify:
1. Data integrity (foreign keys, constraints)
2. Data accuracy (calculations, aggregations)
3. Data completeness (no missing required fields)
4. Data consistency (across related tables)
5. Performance (query execution time)
6. Edge cases (null values, duplicates, special characters)
```

**Example:**
```
Generate SQL test queries for Order Management System to validate:

Database: PostgreSQL
Tables involved: orders, order_items, products, customers

Create queries to verify:
1. Data integrity (order_items.order_id references orders.id)
2. Data accuracy (order total = sum of order_items prices)
3. Data completeness (all orders have customer_id, created_at)
4. Data consistency (product prices match between orders and products table)
5. Performance (queries with indexes vs without)
6. Edge cases (orders with 0 items, null shipping addresses, special characters in names)
```

### I. Accessibility Testing

#### Use Case 13: Accessibility Test Cases
**Prompt:**
```
Create accessibility test cases for [Feature/Page] following WCAG 2.1 guidelines:

Level: [A/AA/AAA]

Cover:
1. Perceivable (text alternatives, captions, adaptable content, distinguishable)
2. Operable (keyboard accessible, enough time, seizures, navigable)
3. Understandable (readable, predictable, input assistance)
4. Robust (compatible with assistive technologies)

Include:
- Screen reader testing steps
- Keyboard navigation testing
- Color contrast validation
- Focus indicators
- ARIA labels verification
```

**Example:**
```
Create accessibility test cases for Login Form following WCAG 2.1 guidelines:

Level: AA

Cover:
1. Perceivable (labels for email/password fields, error messages readable)
2. Operable (tab navigation works, no time limits, focus visible)
3. Understandable (clear error messages, consistent navigation)
4. Robust (works with JAWS, NVDA, VoiceOver)

Include:
- Screen reader testing steps (announces field labels, errors)
- Keyboard navigation testing (Tab, Enter, Escape keys)
- Color contrast validation (4.5:1 for text)
- Focus indicators (visible outline on focused elements)
- ARIA labels verification (aria-label, aria-describedby for errors)
```



### J. Test Data Management

#### Use Case 14: Test Data Generation
**Prompt:**
```
Generate realistic test data for [Feature/Entity]:

Entity: [Name]
Fields: [List fields with data types and constraints]
Number of records: [Count]

Requirements:
1. Include edge cases (min/max values, special characters)
2. Include invalid data for negative testing
3. Ensure data diversity (different patterns)
4. Consider data relationships (if applicable)
5. Format: [JSON/CSV/SQL/Excel]
```

**Example:**
```
Generate realistic test data for User Registration:

Entity: User
Fields: 
- firstName (string, 2-50 chars)
- lastName (string, 2-50 chars)
- email (string, valid email format)
- phone (string, 10 digits)
- dateOfBirth (date, age 18-100)
- country (string, from predefined list)

Number of records: 20

Requirements:
1. Include edge cases (2-char names, 50-char names, special chars in names)
2. Include invalid data (invalid emails, wrong phone format, underage users)
3. Ensure data diversity (different countries, age ranges, name patterns)
4. Consider data relationships (N/A for this entity)
5. Format: JSON
```

### K. Regression Testing

#### Use Case 15: Regression Test Suite
**Prompt:**
```
Design a regression test suite for [Application/Feature]:

Context:
- Recent changes: [Description]
- Affected areas: [List]
- Risk areas: [List]

Create:
1. Critical path test cases (must pass)
2. High-priority regression tests
3. Medium-priority regression tests
4. Smoke test subset
5. Recommended automation candidates
6. Execution frequency (per build/daily/weekly)
```

**Example:**
```
Design a regression test suite for E-commerce Application after Payment Gateway Update:

Context:
- Recent changes: Migrated from PayPal to Stripe payment gateway
- Affected areas: Checkout flow, order processing, refunds, payment history
- Risk areas: Payment processing, order confirmation, email notifications

Create:
1. Critical path test cases (complete purchase flow, payment success/failure)
2. High-priority regression tests (refund processing, saved payment methods)
3. Medium-priority regression tests (payment history display, invoice generation)
4. Smoke test subset (add to cart, checkout page loads, payment page loads)
5. Recommended automation candidates (happy path checkout, payment validations)
6. Execution frequency (smoke: per build, full suite: daily, extended: weekly)
```

### L. Exploratory Testing

#### Use Case 16: Exploratory Testing Charter
**Prompt:**
```
Create an exploratory testing charter for [Feature]:

Session Duration: [Time]
Tester: [Role/Level]

Charter Structure:
1. Mission: What are we testing and why?
2. Areas to explore: [List specific areas]
3. Test ideas: [Suggested approaches]
4. Risks to investigate: [Potential issues]
5. Data needed: [Test data requirements]
6. Tools: [Tools to use]
7. Session notes template
8. Bug reporting guidelines
```

**Example:**
```
Create an exploratory testing charter for Social Media Sharing Feature:

Session Duration: 90 minutes
Tester: Mid-level QA Engineer

Charter Structure:
1. Mission: Explore social media sharing functionality to find usability issues and edge cases
2. Areas to explore: Share buttons, preview generation, multiple platform sharing, error handling
3. Test ideas: Try different content types (text, images, videos), test character limits, 
   test with/without login, test network failures
4. Risks to investigate: Privacy concerns, broken links, incorrect previews, performance with large files
5. Data needed: Test accounts for Facebook, Twitter, LinkedIn; various content types
6. Tools: Browser DevTools, Charles Proxy for network simulation, screenshot tool
7. Session notes template: Time | Action | Observation | Issue? | Priority
8. Bug reporting guidelines: Include screenshots, network logs, steps to reproduce
```



### M. CI/CD & DevOps

#### Use Case 17: CI/CD Test Integration
**Prompt:**
```
Design a CI/CD testing strategy for [Application]:

Pipeline: [Jenkins/GitLab CI/GitHub Actions/etc.]
Deployment: [Environment details]

Include:
1. Test stages in pipeline (unit, integration, E2E, performance)
2. Trigger conditions (on commit, PR, merge, schedule)
3. Parallel execution strategy
4. Failure handling (retry logic, notifications)
5. Test reports and metrics
6. Deployment gates (quality gates)
7. Rollback criteria
```

**Example:**
```
Design a CI/CD testing strategy for Microservices-based Web Application:

Pipeline: GitHub Actions
Deployment: Kubernetes on AWS EKS

Include:
1. Test stages: Unit tests → Integration tests → Contract tests → E2E tests → Security scan → Performance tests
2. Trigger conditions: Unit/Integration on every commit, E2E on PR to main, Performance on merge to main
3. Parallel execution: Run unit tests for all services in parallel, E2E tests in 3 parallel threads
4. Failure handling: Retry flaky tests once, notify Slack channel on failure, block merge on critical failures
5. Test reports: JUnit XML reports, coverage reports (80% threshold), Allure reports for E2E
6. Deployment gates: All tests pass, code coverage ≥ 80%, no critical security vulnerabilities
7. Rollback criteria: Error rate > 5%, response time > 3s, failed health checks
```

### N. Test Metrics & Reporting

#### Use Case 18: Test Metrics Dashboard
**Prompt:**
```
Design a test metrics dashboard for [Project/Team]:

Stakeholders: [List]
Reporting Frequency: [Daily/Weekly/Sprint]

Include metrics for:
1. Test Execution (pass/fail rate, execution time)
2. Test Coverage (requirements coverage, code coverage)
3. Defect Metrics (defect density, defect aging, severity distribution)
4. Automation Metrics (automation coverage, ROI)
5. Quality Trends (over time)
6. Team Productivity (test cases created, bugs found)
7. Visualizations (charts/graphs)
8. Actionable insights
```

**Example:**
```
Design a test metrics dashboard for Agile Development Team:

Stakeholders: QA Lead, Dev Manager, Product Owner, Scrum Master
Reporting Frequency: Daily (automated), Weekly (detailed review)

Include metrics for:
1. Test Execution: Daily pass rate (target: >95%), avg execution time per suite
2. Test Coverage: User story coverage (target: 100%), API coverage (target: 90%)
3. Defect Metrics: Bugs by severity (Critical/High/Medium/Low), avg resolution time, 
   defect leakage to production
4. Automation Metrics: % automated tests (target: 70%), automation execution time trend
5. Quality Trends: Sprint-over-sprint defect trend, test stability (flaky test %)
6. Team Productivity: Test cases per sprint, bugs found per tester
7. Visualizations: Line charts for trends, pie charts for distribution, bar charts for comparison
8. Actionable insights: Highlight areas needing attention, suggest improvements
```

---

## Best Practices

### 1. Be Specific and Clear
❌ **Bad:** "Write test cases for login"
✅ **Good:** "Generate 15 functional test cases for a login feature with email and password fields, including positive scenarios, negative scenarios, and boundary value testing. Format as a table."

### 2. Provide Context
❌ **Bad:** "Create automation script"
✅ **Good:** "Create a Selenium WebDriver script in Python using pytest framework to test the checkout flow of an e-commerce site. Include page object model pattern and explicit waits."

### 3. Specify Output Format
❌ **Bad:** "List security vulnerabilities"
✅ **Good:** "List potential security vulnerabilities in JSON format with fields: vulnerability_name, severity, description, affected_component, remediation_steps"

### 4. Include Constraints
❌ **Bad:** "Generate test data"
✅ **Good:** "Generate 50 test user records in CSV format with fields: username (6-20 chars), email (valid format), age (18-65), country (US, UK, CA only)"

### 5. Use Examples When Needed
Include sample inputs or expected outputs to clarify your requirements.

### 6. Iterate and Refine
Start with a basic prompt, review the output, then refine your prompt for better results.

### 7. Break Down Complex Tasks
For complex requirements, break them into multiple prompts rather than one large prompt.



---

## Examples by Testing Domain

### Web Application Testing

**Scenario:** Testing a search functionality

**Prompt:**
```
Create comprehensive test cases for a search feature on an e-commerce website:

Feature Details:
- Search bar accepts text input (max 100 characters)
- Auto-suggestions appear after 3 characters
- Results display with filters (price, category, rating, brand)
- Pagination shows 20 results per page
- Search history is saved for logged-in users

Include:
1. Functional test cases (valid search, empty search, special characters)
2. UI/UX test cases (auto-suggestions, filters, sorting)
3. Performance test cases (search response time < 2s)
4. Accessibility test cases (keyboard navigation, screen reader)
5. Edge cases (very long queries, SQL injection attempts, concurrent searches)

Format: Test Case ID | Title | Steps | Expected Result | Priority | Test Type
```

### API Testing

**Scenario:** Testing a RESTful API

**Prompt:**
```
Generate API test cases for a User Management REST API:

Endpoints:
1. POST /api/users - Create user
2. GET /api/users/{id} - Get user by ID
3. PUT /api/users/{id} - Update user
4. DELETE /api/users/{id} - Delete user
5. GET /api/users - List all users (with pagination)

For each endpoint, create test cases covering:
- Happy path scenarios
- Authentication/Authorization (valid token, invalid token, missing token)
- Input validation (required fields, data types, field lengths)
- Error handling (404, 400, 401, 403, 500)
- Response validation (schema, data accuracy)
- Performance (response time < 500ms)

Include sample request/response payloads for each test case.
```

### Mobile App Testing

**Scenario:** Testing a mobile banking app

**Prompt:**
```
Design a test strategy for a mobile banking app's fund transfer feature:

Platform: iOS and Android
Feature: Transfer money between accounts

Create test cases for:
1. Functional testing (successful transfer, insufficient funds, invalid account)
2. Security testing (authentication, encryption, session timeout)
3. Usability testing (intuitive flow, error messages, confirmation screens)
4. Performance testing (transaction processing time, app responsiveness)
5. Device-specific testing (different screen sizes, OS versions)
6. Network testing (WiFi, 4G, 3G, offline mode, network interruption)
7. Interruption testing (incoming call, low battery, app backgrounded)

Include:
- Test case priority (P0/P1/P2)
- Device/OS coverage matrix
- Risk assessment for each test area
```

### Database Testing

**Scenario:** Testing data migration

**Prompt:**
```
Create a test plan for migrating customer data from MySQL to PostgreSQL:

Migration Scope:
- Tables: customers, orders, payments, addresses
- Total records: ~5 million
- Downtime window: 4 hours

Test Plan should include:
1. Pre-migration validation (data profiling, row counts, data quality checks)
2. Migration testing (data accuracy, referential integrity, data types)
3. Post-migration validation (row count comparison, data sampling, checksum validation)
4. Performance testing (query performance comparison)
5. Rollback testing (restore from backup)
6. SQL queries for each validation step
7. Success criteria and acceptance criteria
8. Risk mitigation strategies
```

### Performance Testing

**Scenario:** Load testing an e-commerce site

**Prompt:**
```
Design a performance test plan for Black Friday sale on an e-commerce website:

Expected Load:
- Normal: 5,000 concurrent users
- Peak: 50,000 concurrent users
- Duration: 24 hours

Critical User Journeys:
1. Browse products (40% of users)
2. Search products (30% of users)
3. Add to cart and checkout (25% of users)
4. View order history (5% of users)

Create:
1. Load test scenarios with ramp-up strategy
2. Performance benchmarks (response time, throughput, error rate)
3. Monitoring plan (CPU, memory, database connections, API response times)
4. Bottleneck identification strategy
5. JMeter/Gatling test script outline
6. Success criteria and SLAs
7. Recommendations for infrastructure scaling
```

---

## Quick Reference Guide

### Common Prompt Starters

| Purpose | Prompt Starter |
|---------|---------------|
| Test Case Generation | "Generate test cases for..." |
| Test Automation | "Create an automated test script for..." |
| Bug Analysis | "Analyze this bug and suggest..." |
| Test Strategy | "Design a test strategy for..." |
| Test Data | "Generate test data for..." |
| Code Review | "Review this test code and suggest improvements..." |
| Documentation | "Create test documentation for..." |
| Comparison | "Compare [Tool A] vs [Tool B] for..." |
| Troubleshooting | "Debug this test failure..." |
| Optimization | "Optimize this test suite for..." |

### Prompt Enhancement Keywords

Add these to make prompts more effective:
- **Specificity:** "detailed", "comprehensive", "specific to"
- **Format:** "in table format", "as JSON", "step-by-step"
- **Quality:** "best practices", "industry standard", "production-ready"
- **Scope:** "including", "covering", "focusing on"
- **Constraints:** "within", "limited to", "excluding"

---

## Contributing

This is a living document. QA team members are encouraged to:
1. Add new prompt templates based on your experience
2. Share successful prompts that generated great results
3. Update examples with real-world scenarios
4. Suggest improvements to existing prompts

**How to Contribute:**
1. Fork this repository
2. Add your prompts following the existing format
3. Include clear examples and use cases
4. Submit a pull request with description

---

## Additional Resources

### Recommended Reading
- "The Art of Prompt Engineering" - Best practices for AI interactions
- "Test Automation Patterns" - Common patterns applicable to prompt design
- ISTQB Syllabus - For standard testing terminology

### Tools That Work Well With Prompts
- ChatGPT / Claude / Gemini - General purpose AI assistants
- GitHub Copilot - Code generation and test automation
- Postman AI - API testing assistance
- Selenium IDE - Test recording and generation

### Community
- Share your prompts with the team
- Discuss what works and what doesn't
- Collaborate on complex testing scenarios

---

## Version History

- **v1.0** - Initial release with 18 use cases across 14 categories
- Created: [Current Date]
- Last Updated: [Current Date]
- Maintainer: QA Team

---

## License

This prompt library is open for use by all QA team members. Feel free to adapt and customize for your specific needs.

---

**Happy Testing! 🚀**

