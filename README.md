# PostgreeSQL-ODEV1
-- Departments tablosunun oluşturulması ve veri eklenmesi
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50) NOT NULL
);

INSERT INTO Departments (DepartmentID, DepartmentName) VALUES
(1, 'IT'),
(2, 'HR'),
(3, 'Finance');

SELECT * FROM Departments;

-- Employees tablosunun oluşturulması ve veri eklenmesi
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Age INT,
    DepartmentID INT,
    Salary DECIMAL(10,2),
    JoinDate DATE,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);

INSERT INTO Employees (EmployeeID, FirstName, LastName, Age, DepartmentID, Salary, JoinDate) VALUES
(1, 'John', 'Doe', 30, 1, 55000, '2020-01-15'),
(2, 'Jane', 'Smith', 45, 2, 65000, '2018-07-20'),
(3, 'Sam', 'Brown', 28, 1, 52000, '2021-04-25'),
(4, 'Lisa', 'White', 35, 3, 70000, '2019-03-18'),
(5, 'Mark', 'Black', 50, 1, 75000, '2015-11-05'),
(6, 'Lucy', 'Green', 40, 2, 60000, '2017-10-10');

SELECT * FROM Employees;

--a.Çalışanların isim, soyisim ve maaşlarını getirme.
SELECT FirstName, LastName, Salary FROM Employees;

--b.Çalışan departmanlarını beznersiz olarak gösterme.
SELECT DISTINCT * FROM Departments;

--c.Sadece IT departmanında çalışanların bilgilerini getirme.
SELECT * FROM Departments
Where DepartmentName = 'IT';

--d.Çalışanların maaşlarına göre büyükten küçüğe sıralanmış hali.
SELECT * FROM Employees
ORDER BY Salary DESC;

--e.Çalışanların isim ve soyisimlerini birleştirerek yeni bir kolon oluşturma.
SELECT CONCAT(FirstName, ' ', LastName) AS FullName
FROM Employees
ORDER BY FullName DESC;
