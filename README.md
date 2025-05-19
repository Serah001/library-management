# Library Management System

## Description
A MySQL-based Library Management System database to store and manage books, authors, members, and book loans with proper relational constraints.

## How to run/setup the project
1. Install MySQL server.
2. Import the SQL script:
   ```bash
   mysql -u your_username -p < library_management.sql
+-------------+           +-------------+          +--------------+
|   Authors   |           |    Books    |          |    Members   |
+-------------+           +-------------+          +--------------+
| author_id PK|<--------->| book_id PK  |          | member_id PK |
| first_name  |           | title       |          | name         |
| last_name   |           | isbn UNIQUE |          | email UNIQUE |
+-------------+           | published_year|        | phone        |
                          +-------------+          +--------------+
                               ^
                               |
                               | (M:N via BookAuthors)
                               |
                    +-----------------------+
                    |    BookAuthors        |
                    +-----------------------+
                    | book_id PK, FK        |
                    | author_id PK, FK      |
                    +-----------------------+

                                    |
                                    | 1:N
                                    v

                          +-------------------+
                          |      Loans        |
                          +-------------------+
                          | loan_id PK        |
                          | book_id FK        |
                          | member_id FK      |
                          | loan_date         |
                          | return_date       |
                          +-------------------+
# library-management
