Natural Language to SQL Query Generator

## Overview

The **Natural Language to SQL Query Generator** is an AI-powered application that converts human language queries into structured SQL statements. This project enables users to interact with databases using simple English sentences rather than writing complex SQL queries manually.

The system is designed to demonstrate how **Natural Language Processing (NLP), Large Language Models (LLMs), and rule-based logic** can be combined to build intelligent database query systems.

Users can type requests such as:

* "Show me users who signed up last month"
* "Find orders with amount greater than 500"
* "List active users"

The system automatically converts these requests into **valid SQLite SQL queries**.

Example:

Natural language input:

```
Show me users who signed up last month
```

Generated SQL query:

```sql
SELECT * FROM users
WHERE DATE(signup_date) >= DATE('now', '-1 month')
LIMIT 10;
```

This project demonstrates practical applications of **AI-assisted query generation**, which is useful in modern **data analytics, business intelligence systems, and database interfaces**.

---

# Key Features

### Natural Language Query Processing

Users can interact with the system using normal English sentences instead of SQL syntax.

### Automatic SQL Query Generation

The system analyzes the input text and generates a valid SQL query based on the database schema.

### Intelligent Table Detection

The program detects which database table should be used based on keywords in the user query.

Example mapping:

| Keyword              | Table        |
| -------------------- | ------------ |
| user, customer       | users        |
| order, purchase      | orders       |
| product, item        | products     |
| transaction, payment | transactions |

---

### Column Detection

The system automatically determines which columns should be selected.

Example:

User input:

```
Show user name and email
```

Generated SQL:

```sql
SELECT name, email FROM users;
```

---

### Condition Extraction

The program detects filters and conditions from natural language.

Examples:

| Natural Language        | SQL Condition                               |
| ----------------------- | ------------------------------------------- |
| last month              | DATE(signup_date) >= DATE('now','-1 month') |
| today                   | DATE(signup_date) = DATE('now')             |
| active users            | status = 'active'                           |
| amount greater than 500 | amount > 500                                |

---

### SQL Security Protection

The project includes a **basic SQL injection prevention system**.

Dangerous SQL operations are blocked such as:

* DROP
* DELETE
* ALTER
* TRUNCATE
* INSERT
* UPDATE

The system checks user input and prevents unsafe queries from being generated.

---

### Interactive Web Interface

The application uses **Gradio** to create an interactive web-based user interface.

Users can:

* Enter natural language queries
* View generated SQL queries
* See query explanations
* Maintain query history

The UI is simple and responsive, making the tool easy to use.

---

### Query History Tracking

All generated queries are stored in a history list with:

* User input
* Generated SQL
* Timestamp

This allows users to review previously generated queries.

---

### Export Query Reports

Users can export generated queries as reports.

Supported formats:

* PDF Report
* TXT File

PDF reports include:

* User requests
* Generated SQL queries
* Timestamp information

The report is generated using the **ReportLab library**.

---

### Social Sharing

The application can generate shareable links to send queries via:

* WhatsApp
* Facebook

This feature demonstrates integration with external platforms.

---

# Technology Stack

This project uses the following technologies:

### Programming Language

Python

### AI / NLP

Transformers Library

Model used:
IBM Granite 3.3B Instruct Model

Model Source:
[https://huggingface.co/ibm-granite/granite-3.3-2b-instruct](https://huggingface.co/ibm-granite/granite-3.3-2b-instruct)

---

### Web Interface

Gradio

Used for building the interactive application interface.

---

### Database

SQLite

Used as the backend database schema for generating SQL queries.

---

### Report Generation

ReportLab

Used to generate downloadable PDF reports.

---

### Other Libraries

* transformers
* torch
* gradio
* sqlite3
* requests
* reportlab
* autopep8
* black

---

# Database Schema

The project simulates a small database with four tables.

### Users Table

| Column      | Type    |
| ----------- | ------- |
| id          | INTEGER |
| name        | TEXT    |
| email       | TEXT    |
| signup_date | DATE    |
| age         | INTEGER |
| country     | TEXT    |
| status      | TEXT    |

---

### Orders Table

| Column       | Type    |
| ------------ | ------- |
| id           | INTEGER |
| user_id      | INTEGER |
| product_name | TEXT    |
| amount       | REAL    |
| order_date   | DATE    |
| status       | TEXT    |

---

### Products Table

| Column   | Type    |
| -------- | ------- |
| id       | INTEGER |
| name     | TEXT    |
| price    | REAL    |
| category | TEXT    |
| stock    | INTEGER |

---

### Transactions Table

| Column  | Type    |
| ------- | ------- |
| id      | INTEGER |
| user_id | INTEGER |
| amount  | REAL    |
| date    | DATE    |
| type    | TEXT    |

---

# How the System Works

The workflow of the system can be described in several steps.

### Step 1: User Input

The user enters a natural language request in the web interface.

Example:

```
Show me active users who joined last month
```

---

### Step 2: Security Check

The system checks whether the input contains dangerous SQL keywords.

Unsafe queries are blocked to prevent malicious operations.

---

### Step 3: Table Detection

The program analyzes keywords to determine which table should be used.

---

### Step 4: Column Selection

Relevant columns are selected based on detected keywords.

If no column is detected, the system defaults to:

```
SELECT *
```

---

### Step 5: Condition Extraction

The system extracts conditions like:

* date ranges
* status filters
* numeric comparisons

---

### Step 6: SQL Query Generation

All components are combined to create the final SQL query.

Example:

```sql
SELECT name, email
FROM users
WHERE status='active'
AND DATE(signup_date) >= DATE('now','-1 month')
LIMIT 10;
```

---

### Step 7: Display Result

The generated SQL query is displayed in the chatbot interface.

---

# Installation

Install required dependencies:

```bash
pip install transformers
pip install gradio torch reportlab requests
```

---

# Running the Application

Run the Python script:

```
python app.py
```

Gradio will launch a local web interface.

You can interact with the SQL generator through your browser.

---

# Example Queries

Example inputs the system can handle:

```
Show all users
List users who joined last month
Find orders above 1000
Show active users
List products with price below 500
Show transactions today
```

---

# Future Improvements

Possible future improvements include:

* Support for more complex SQL queries
* JOIN operations between tables
* Integration with real databases
* Improved NLP understanding using LLMs
* Multi-language support
* Query visualization
* Data analytics dashboards

---

# Educational Purpose

This project demonstrates concepts from several important areas:

* Natural Language Processing
* Database Query Generation
* AI-powered automation
* Web-based application development
* Secure query handling

It is particularly useful for students studying:

* Computer Science
* Information Technology
* Data Science
* Artificial Intelligence

---

# Conclusion

The Natural Language to SQL Query Generator shows how AI can simplify interactions with databases by allowing users to communicate in natural language. This approach reduces the learning barrier for SQL and makes data retrieval more accessible for non-technical users.

The project demonstrates a practical combination of **AI models, rule-based logic, and web interfaces**, making it a valuable example of modern AI-powered software development.

---

