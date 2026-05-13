# internal-assessment-db
# Internal Assessment Database 📚

A MySQL relational database designed to manage internal assessments for college departments, including faculty, subjects, branches, and question mapping.

---

## 🛠️ Tech Stack

- **Database:** MySQL
- **Tool:** MySQL Workbench / MySQL CLI

---

## 📂 Database Name

---

## 🗂️ Tables Overview

### 1. `department`
Stores department information.

| Column | Type | Description |
|--------|------|-------------|
| DEPT_ID | INT (PK) | Department ID |
| Dept_Name | VARCHAR(50) | Department Name |
| Address | VARCHAR(100) | Department Address |
| YOE | INT | Year of Establishment |

---

### 2. `branch`
Stores branch details under departments.

| Column | Type | Description |
|--------|------|-------------|
| Branch_Id | INT (PK) | Branch ID |
| Branch_Name | VARCHAR(50) | Branch Name |

---

### 3. `faculty`
Stores faculty member details.

| Column | Type | Description |
|--------|------|-------------|
| F_ID | INT (PK) | Faculty ID |
| F_Name | VARCHAR(150) | Faculty Name |
| F_Contact | VARCHAR(15) | Contact Number |
| Dept_ID | INT (FK) | Department ID |

---

### 4. `subject`
Stores subject details.

| Column | Type | Description |
|--------|------|-------------|
| Sub_Id | INT (PK) | Subject ID |
| Sub_Name | VARCHAR(100) | Subject Name |
| Sub_Credits | INT | Credit Points (default: 4) |

---

### 5. `subject_branch_mapping`
Maps subjects to branches.

| Column | Type | Description |
|--------|------|-------------|
| Sub_Branch_Id | INT (PK) | Mapping ID |
| Sub_ID | INT (FK) | Subject ID |
| Branch_Id | INT (FK) | Branch ID |

---

### 6. `faculty_subject_mapping`
Maps faculty to subjects and branches for a semester.

| Column | Type | Description |
|--------|------|-------------|
| FS_Id | INT (PK) | Mapping ID |
| F_Id | INT (FK) | Faculty ID |
| Sub_Branch_Id | INT (FK) | Subject-Branch Mapping ID |
| Semester | INT | Semester Number |
| AY | VARCHAR(20) | Academic Year (default: 2025-2026) |

---

### 7. `questions`
Stores assessment questions.

| Column | Type | Description |
|--------|------|-------------|
| Q_Id | INT (PK) | Question ID |
| Q_Description | TEXT | Question Text |
| KL | VARCHAR(10) | Knowledge Level |
| CO | VARCHAR(10) | Course Outcome |
| Topic | VARCHAR(100) | Topic |
| Sub_Topic | VARCHAR(100) | Sub Topic |

---

### 8. `assessment`
Stores assessment details linked to faculty-subject mapping and questions.

| Column | Type | Description |
|--------|------|-------------|
| Assess_Id | INT (PK) | Assessment ID |
| Type | VARCHAR(50) | Type (default: Internal) |
| Max_Marks | INT | Maximum Marks (default: 100) |
| Date_Of_Issue | DATE | Issue Date |
| FS_Id | INT (FK) | Faculty-Subject Mapping ID |
| Q_Id | INT (FK) | Question ID |

---

## 🔗 Relationships

- `faculty` → `department` (Dept_ID)
- `subject_branch_mapping` → `subject`, `branch`
- `faculty_subject_mapping` → `faculty`, `subject_branch_mapping`
- `assessment` → `faculty_subject_mapping`, `questions`

---

## 🚀 How to Use

1. Clone the repository:
```bash
   git clone https://github.com/Aryan30-Jngec/internal-assessment-db.git
```

2. Open MySQL and run:
```sql
   source internal_assessment.sql;
```

3. Verify:
```sql
   USE internal_assessment;
   SHOW TABLES;
```

---

## 👨‍💻 Author

**Aryan** — [GitHub](https://github.com/Aryan30-Jngec)