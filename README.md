# student-management-in-sql
Built a student management database using SQL Queries. I was learning keys in SQL and thought of implementing practically.
# 🎓 Student Management Database using SQL Keys

A mini project demonstrating how **SQL Keys** (Primary, Foreign, Unique, Composite, Candidate, and Alternate) work together inside a **Student Management System** database.

This project is perfect for students learning database design or showcasing their SQL fundamentals in a GitHub portfolio.

---

## 📘 Overview

This database manages information about:

* Students 👩‍🎓
* Subjects 📚
* Marks 🧮
* Attendance 🗓️

It also enforces **data integrity** using SQL Keys.

---

## 🗝️ SQL Keys Used

| Key Type      | Example Column(s)             | Table        | Description                         |
| ------------- | ----------------------------- | ------------ | ----------------------------------- |
| Primary Key   | RollNo                        | Students     | Uniquely identifies each student    |
| Foreign Key   | RollNo (in Marks, Attendance) | Links tables | Connects related tables             |
| Unique Key    | AadharNo, Email               | Students     | Prevents duplicate entries          |
| Composite Key | (RollNo, SubjectCode)         | Marks        | Ensures unique row combinations     |
| Candidate Key | RollNo, AadharNo              | Students     | Possible unique identifiers         |
| Alternate Key | AadharNo                      | Students     | Candidate key not chosen as primary |

---

## 🧩 Project Structure

```
student-management-sql/
│
├── README.md
├── schema.sql
└── sample_data.sql
```

---

## 🧱 schema.sql

```sql
CREATE DATABASE StudentManagement;
USE StudentManagement;

-- 1. STUDENTS TABLE

CREATE TABLE Students (
    RollNo INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Class VARCHAR(10),
    AadharNo CHAR(12) UNIQUE,
    Email VARCHAR(50) UNIQUE
);

-- 2. SUBJECTS TABLE

CREATE TABLE Subjects (
    SubjectCode VARCHAR(10) PRIMARY KEY,
    SubjectName VARCHAR(50) NOT NULL
);

-- 3. MARKS TABLE

CREATE TABLE Marks (
    RollNo INT,
    SubjectCode VARCHAR(10),
    Marks INT,
    PRIMARY KEY (RollNo, SubjectCode),
    FOREIGN KEY (RollNo) REFERENCES Students(RollNo),
    FOREIGN KEY (SubjectCode) REFERENCES Subjects(SubjectCode)
);

-- 4. ATTENDANCE TABLE

CREATE TABLE Attendance (
    RollNo INT,
    Date DATE,
    Status VARCHAR(10),
    PRIMARY KEY (RollNo, Date),
    FOREIGN KEY (RollNo) REFERENCES Students(RollNo)
);
```

---

## 🧾 sample_data.sql

```sql
USE StudentManagement;

INSERT INTO Students (RollNo, Name, Class, AadharNo, Email)
VALUES 
(101, 'Ravi Kumar', '10A', '123456789012', 'ravi@example.com'),
(102, 'Sneha Reddy', '10A', '234567890123', 'sneha@example.com'),
(103, 'Amit Singh', '10B', '345678901234', NULL);


INSERT INTO Subjects (SubjectCode, SubjectName)
VALUES 
('MATH', 'Mathematics'),
('ENG', 'English'),
('SCI', 'Science');

INSERT INTO Marks (RollNo, SubjectCode, Marks)
VALUES 
(101, 'MATH', 88),
(101, 'ENG', 91),
(102, 'SCI', 76),
(103, 'ENG', 85);


INSERT INTO Attendance (RollNo, Date, Status)
VALUES
(101, '2025-11-01', 'Present'),
(101, '2025-11-02', 'Absent'),
(102, '2025-11-01', 'Present'),
(103, '2025-11-02', 'Present');
```

---

## ⚙️ How to Run

### 🧩 Using MySQL Workbench or CLI

1. Clone or download this repo:

   ```bash
   git clone https://github.com/yourusername/student-management-sql.git
   cd student-management-sql
   ```

2. Open MySQL and run:

   ```bash
   SOURCE schema.sql;
   SOURCE sample_data.sql;
   ```

3. View results:

   ```sql
   SELECT * FROM Students;
   SELECT * FROM Marks;
   SELECT * FROM Attendance;
   ```

---

## 🧠 Learning Outcomes

✅ Understand different SQL keys and their relationships.
✅ Learn how data integrity is maintained in relational databases.
✅ Practice database normalization through key constraints.

---

## Future Enhancements

* Add a **Teachers** table.
* Create **Views** for student performance reports.
* Write **JOIN queries** for combined analytics.
* Add **Stored Procedures** to generate report cards automatically.


Ashok Krishna N
📍 Electronics and Communication Engineering | India
💼 Exploring AI, Embedded Systems, and Databases

