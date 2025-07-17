# 🎓 Student Marks SQL Analysis

This project demonstrates how to design and query a SQL table that stores student performance data. It also includes a stored procedure for adding student records and sample SQL logic to retrieve the **Nth highest grade** from the dataset.
---

## 📌 Features

- SQL table for managing student grades  
- Stored procedure for inserting records  
- Logic to retrieve the Nth highest grade  
- Sample data and queries  
- Useful for learning SQL concepts 

---

## 🗃️ Table Structure

The table is called `StudentsMarks` with the following columns:

| Column            | Type           | Description                        |
|-------------------|----------------|------------------------------------|
| `ID`              | `INT`          | Primary Key (auto-increment)       |
| `StudentName`     | `NVARCHAR(50)` | First name of the student          |
| `StudentSurname`  | `NVARCHAR(50)` | Last name of the student           |
| `Gender`          | `NVARCHAR(50)` | Gender of the student              |
| `GradePercentage` | `INT`          | Grade in percentage (0 - 100)      |

---

## 📈 Sample Data

Here’s a snapshot of example records inserted into the table:

![StudentMarks Table](https://github.com/user-attachments/assets/ffe1412e-d282-4fe0-b927-53577583a64f)


---

## 🛠️ SQL Code

### ✅ Create Table

```sql
CREATE TABLE StudentsMarks (
    ID INT PRIMARY KEY IDENTITY,
    StudentName NVARCHAR(50),
    StudentSurname NVARCHAR(50),
    Gender NVARCHAR(50),
    GradePercentage INT
);
```

___


### ✅ Stored Procedure to Insert Records
```sql
CREATE PROCEDURE spAddingStudent  
    @StudentName NVARCHAR(50),
    @StudentSurname NVARCHAR(50),
    @Gender NVARCHAR(50),
    @GradePercentage INT
AS
BEGIN
    INSERT INTO StudentsMarks (StudentName, StudentSurname, Gender, GradePercentage)
    VALUES (@StudentName, @StudentSurname, @Gender, @GradePercentage)
END;
```

___
### ✅ How to INSERT data into the table using the Stored Procedure
```sql
EXECUTE spAddingStudent 'Max', 'Stanmore', 'Male', 100;
```
![image](https://github.com/user-attachments/assets/39103473-0795-4e8c-950c-38d8bb347cdc)
![image](https://github.com/user-attachments/assets/7cd90d23-c02e-41a6-90c9-7b6693136f95)

___

### ✅ Retriving All data in the table

```sql
SELECT * FROM StudentsMarks;
```
![image](https://github.com/user-attachments/assets/609fa467-c29f-471d-a39a-5791b5ef4c6d)

___
### ✅ Retriving the highest Grade in the table
```sql
SELECT max(GradePercentage) AS highestGrade FROM StudentsMarks;
```
![image](https://github.com/user-attachments/assets/9e9f4508-22a5-4157-9459-c32b26e2988b)

![image](https://github.com/user-attachments/assets/fbc1749b-261f-4d03-8fee-6c2b6a91141d)

___

### ✅ Retriving all female students

```sql
  SELECT * FROM StudentsMarks WHERE Gender = 'Female';
```
![image](https://github.com/user-attachments/assets/7cc07e20-1dc4-4fdd-90c1-1504615439fc)

### ✅ Retriving the number of Males and Females in the table
```sql
SELECT Gender, COUNT(*) AS Total FROM StudentsMarks  GROUP BY Gender;

```
![image](https://github.com/user-attachments/assets/dc463a57-f428-4fc0-be4f-4c9b29eda01d)

___

### ✅ Retriving Average grade percentage of all students

```sql
SELECT AVG(GradePercentage) AS GradeAvg FROM StudentsMarks;
```
![image](https://github.com/user-attachments/assets/81c90372-5b63-43c6-9641-007143d34d55)

___


### ✅ Retriving student(s) with the highest grade percentage.
```sql
SELECT * FROM StudentsMarks WHERE GradePercentage = (SELECT MAX(GradePercentage) FROM StudentsMarks)
```
![image](https://github.com/user-attachments/assets/439980c6-31a4-4657-aacf-482c6f76f246)

___

### ✅ Retriving student(s) with the lowest grade percentage.
```sql
SELECT * FROM StudentsMarks WHERE GradePercentage = (SELECT MIN(GradePercentage) FROM StudentsMarks)
```
![image](https://github.com/user-attachments/assets/acefe329-c48d-486b-b30c-b9c7dc3993ab)

___

### ✅ Retriving students with grades above the class average.

```sql
SELECT * FROM StudentsMarks WHERE GradePercentage > (SELECT AVG(GradePercentage) AS AVERAGE FROM StudentsMarks)
```
![image](https://github.com/user-attachments/assets/2bc479b7-e6e1-472c-be2c-85f814e79801)

___

### ✅ Retriving students full names of all students (concatenated).

```sql
SELECT StudentName + ' ' + StudentSurname AS FullName FROM StudentsMarks;
```
![image](https://github.com/user-attachments/assets/d0af89a4-158b-47f0-b3d0-232cb82df2ea)

___



