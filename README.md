# Library Management System

A relational database project built using **MySQL** to manage library members, librarians, books, authors, book copies, borrowing transactions, and fines.

## 1. Project Overview

The Library Management System is designed to store and manage the essential information required to operate a library.

### Key Features

- Manage student and teacher memberships.
- Maintain book categories and book details.
- Store author information and book-author relationships.
- Track individual book copies using unique barcodes.
- Manage book borrowing and returning records.
- Identify overdue books.
- Maintain fine records and payment status.
- Generate reports using SQL queries and joins.

## 2. Technologies Used

- **Database:** MySQL
- **Database Management Tool:** MySQL Workbench
- **Language:** SQL

## 3. Database Information

- **Database Name:** `library_management`
- **DBMS:** MySQL
- **Recommended Version:** MySQL 8.0 or later

## 4. Database Schema

The database consists of the following nine tables:

| Table Name | Description |
|---|---|
| `members` | Stores student and teacher information. |
| `librarians` | Stores librarian details. |
| `categories` | Stores book categories. |
| `books` | Stores book information. |
| `authors` | Stores author details. |
| `book_authors` | Establishes relationships between books and authors. |
| `book_copies` | Maintains individual copies of books and their availability. |
| `borrowings` | Stores book checkout, due, and return information. |
| `fines` | Maintains fine amounts and payment status. |

## 5. Entity Relationships

The database follows relational database design principles.

- One category can contain multiple books.
- One book can have multiple authors.
- One author can write multiple books.
- One book can have multiple physical copies.
- One member can have multiple borrowing records.
- One book copy can have multiple borrowing records over time.
- One librarian can handle multiple borrowing transactions.
- One borrowing transaction can have at most one fine record.

The `book_authors` table handles the many-to-many relationship between books and authors.

## 6. Database Setup

### Prerequisites

- MySQL Server 8.0 or later.
- MySQL Workbench or any MySQL client.

### Installation Steps

1. Open MySQL Workbench.
2. Connect to your MySQL server.
3. Open a new SQL query tab.
4. Copy and execute the complete SQL script.
5. Refresh the Schemas panel.
6. Select the `library_management` database.

The SQL script automatically:

- Creates the database.
- Creates all nine tables.
- Defines primary and foreign keys.
- Adds constraints and indexes.
- Inserts sample records.
- Executes verification queries.
- Displays book details, borrowing history, and fine information.

### Run Using Terminal

Save the SQL script as `library_management.sql` and execute:

```bash
mysql -u your_username -p < library_management.sql
```

Replace `your_username` with your MySQL username.

## 7. Sample Data

The project includes the following sample records:

| Table | Records |
|---|---:|
| Categories | 5 |
| Authors | 10 |
| Books | 10 |
| Book Authors | 10 |
| Book Copies | 15 |
| Members | 8 |
| Librarians | 3 |
| Borrowings | 10 |
| Fines | 3 |

The sample data helps demonstrate database relationships, SQL joins, filtering, and aggregate queries.

## 8. SQL Queries Implemented

### 1. Verify Table Records

Uses `COUNT()` and `UNION ALL` to display the total number of records in each table.

### 2. Display Book Details

Uses multiple joins to retrieve:

- Book code
- Book title
- Author name
- Category name
- Copy barcode
- Copy availability status

### 3. Display Borrowing History

Retrieves borrowing information along with member and book details.

A `CASE` statement determines the borrowing status:

- **Returned:** Book has been returned.
- **Overdue:** Book has not been returned and the due date has passed.
- **Borrowed:** Book has not been returned and the due date has not passed.

### 4. Display Fine Details

Retrieves:

- Fine ID
- Member name
- Book title
- Fine amount
- Payment status

## 9. Constraints and Indexing

The database uses several SQL constraints to maintain data integrity.

| Constraint | Purpose |
|---|---|
| PRIMARY KEY | Uniquely identifies each record. |
| FOREIGN KEY | Maintains relationships between tables. |
| UNIQUE | Prevents duplicate values. |
| NOT NULL | Ensures mandatory fields contain values. |
| CHECK | Validates data based on specified conditions. |
| DEFAULT | Assigns default values when no value is provided. |
| ENUM | Restricts columns to predefined values. |

### Indexes

Indexes are created on frequently searched columns to improve query performance.

Examples include:

- Book title
- Book category
- Member name
- Member type
- Author name
- Book copy status
- Borrowing member
- Borrowing due date
- Return date

## 10. Future Improvements

The project can be extended with the following features:

- Implement stored procedures for issuing and returning books.
- Automatically update book availability after borrowing and returning.
- Calculate overdue fines automatically.
- Add fine payment dates and payment methods.
- Prevent multiple active borrowings of the same physical book copy.
- Create views for available books and overdue transactions.
- Develop a frontend application for library staff and members.
- Implement user authentication and role-based access.

## 11. Important Notes

- The sample borrowing dates are fixed test data.
- The `CURDATE()` function determines overdue status based on the current system date.
- Book copy availability is not automatically synchronized with borrowing records in the current implementation.
- Additional business rules can be implemented using triggers, stored procedures, or application logic.
