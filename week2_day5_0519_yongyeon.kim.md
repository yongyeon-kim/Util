# SQL 이란. 

- Structured Query Language
- 관계형 데이터베이스 관리 시스템(RDBMS : Relational Database Management System)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어이다.
- ANSI (American National Standards Institute) 표준이다.
- 여러 데이터베이스에 접근할 수 있다.
- server-side scripting language


### table

- row(가로줄)와 column(세로)으로 이루어짐
- 1개의 row가 1개의 record를 담고 있음

#### SQL

1. 소문자와 대문자를 구별하지 않는다.
2. 단, 문장끝에 세미콜론을 써줄 것

#### 자주 쓰이는 명령어

 * SELECT 데이터베이스에서 데이터를 추출
 * UPDATE 데이터베이스의 데이터를 업데이트
 * DELETE 데이터베이스의 데이터를 삭제
 * INSERT INTO 데이터베이스에 데이터를 추가
 * CREAT DATABASE 데이터베이스를 생성
 * ALTER DATABASE 데이터베이스의 구조를 수정
 * CREATE TABLE 데이터베이스 안에 테이블을 생성
 * ALTER TABLE 테이블의 구조를 바꿈
 * DROP TABLE 데이터베이스의 테이블을 삭제
 * CREATE INDEX 데이터의 인덱스 생성
 * DROP INDEX 데이터의 인덱스 삭제

------

## SELECT ( 조회절 )

#### SLECT

- 데이터 조회(추출)
- 조회 한 데이터는 가공하여 화면에 출력 한다.

```
SELECT column1, conlum2, ... FROM table_name;
```

#### DISTINCT

- 중복 된 데이터를 제거한다.

```
SELECT DISTINCT column1, column2, ... FROM [table_name];
```

------

## SQL 조건절 ( WHERE )

#### WHERE 구문

- 특정 조건을 걸어서 레코드들을 추출할 수 있음.
- 텍스트 필드는 `' '` 또는 `" "`가 필요하지만 숫자는 필요없다.

```
SELECT column1, column2, ... FROM [table_name] WHERE [조건]
```

## 연산자 ( 조건절 )

#### 연산자 종류

연산자 | 설명
|-----|----|
 = | Equal
 <> | Not equal. (또는 !=)
 \> | Greater than
 < | Less than
 >= | Grear than or Equal
 <= | Less than or Equal
 BETWEEN | Between an inclusive range
 LIKE | Search for a pattern
 IN | To specify multiple possible values for a column


#### 연산자 AND, OR, NOT

- 복 수의 조건을 사용 할 경우 사용한다.

```
[조건1] AND [조건2] : 조건 1 이면서 조건2에 해당하는 데이터
[조건1] OR [조건2] : 조건 1 이거나 조건2에 해당하는 데이터
NOT [조건1] : 조건 1 이 아닌 데이터
```

#### SQL ORDER BY Keyword

- 결과값을 내림차순 또는 오름차순으로 정렬할 수 있다.
- ASC : 내림차순, 정렬 조건생략시 기본 값
- DESC : 오름차순

```
SELECT [column_name], [column_name], ...
FROM [table_name]
ORDER BY [column_name], [column_name], ... ASC / DESC;
```


## 데이터 추가

#### INSERT INTO
- 데이터를 추가 하기 위한 쿼리
- 데이터를 지정하지 않을 경우 테이블 컬럼의 속성에 따른 기본 값이 저장 된다.

```
# 칼럼의 이름과 값을 명시하며, 두 데이터의 순서를 맞춰야 함
INSERT INTO table_name (column1, colum2, colum3, ...)
VALUES (value1, value2, value3, ...);
```

```
# 테이블 생성시 확정 된 컬럼의 순서대로 입력해야 함
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

#### NULL 테스트
- 필드에 데이터가 없을 경우
- 0과 같은 값이 아니다.
```
SELECT column_names FROM table_name WHERE column_name IS NULL;
SELECT column_names FROM table_name WHERE column_name IS NOT NULL;
```

## 데이터 수정

#### Update
- 데이터를 수정 한다.
- WHERE 절을 사용하지 않으면 테이블의 해당 컬럼의 모든 로우 데이터를 변경 한다.

```
UPDATE table_name SET column1 = value1, colum2 = value2, ... WHERE condition;
```


## 데이터 삭제

#### Delete
- 데이터를 삭제 한다.
- WHERE 절을 사용하지 않으면 해당 테이블의 모든 데이터를 삭제 한다.

```
DELETE FROM table_name WHERE condition;
```


## 구간조회 ( 페이징 처리시 사용 )

#### SELECT TOP 구문
- 가져오는 데이터의 수를 제한한다.
- 데이터가 많을때 유용하다.
- 모든 데이터 베이스 시스템이 `SELECT TOP`을 지원하지 않는다. 각 DB마다 구문이 다르다.

```
# MSSQL
SELECT TOP number|percent column_name(s)
FROM table_name
WHERE condition;

# MYSQL
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;

# ORACLE
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```


-------
## 내장함수

#### MIN(), MAX()

MIN() : 칼럼에서 가장 작은 값을 출력하는 함수
MAX() : 칼럼에서 가장 큰 값을 출력하는 함수

- MIN
```
SELECT MIN(column_name) FROM table_name WHERE condition;
```

- MAX
```
SELECT MAX(column_names) FROM table_name WHERE condition;
```


#### COUNT(), AVG(), SUM()

- COUNT() 선택된 데이터의 개수를 반환한다.

```
SELECT COUNT(column_names)
FROM table_name
WHERE condition;
```

- AVG() 선택된 데이터의 평균을 반환한다.

```
SELECT AVG(column_names)
FROM table_name
WHERE condition;
```


- SUM() 선택된 데이터의 합을 반환한다.

```
SELECT SUM(colum_name)
FROM table_name
WHERE condition;
```

- LEN()

```
SELECT LEN(column_name) FROM table_name;
```

-----

## LIKE

#### LIKE / NOT LIKE

- WHERE 이하에 사용하여 가져올 데이터의 패턴을 정해준다
- 와일드카드를 통해 조건의 유연함을 더할 수 있다.

```
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;

# Customers 테이블에서 CustomerNAme이 a로 시작되는 모든 데이터
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';

# Customers 테이블에서 Country에 land가 포함되지 않은 모든 데이터
SELECT * FROM Customers
WHERE Counrty NOT LIKE '%land%';
```

#### 예제
| 와일드카드 | 설명     |
| :------------- | :------------- |
| LIKE 'a%'       | a로 시작       |
|LIKE %a| a로 끝나는|
|LIKE %or% | 자리에 상관없이 'or'만 있으면 됨|
|LIKE _r% | 두번째 위치에 r이 있어야 함|
|LIKE a_%_%| a로 시작하되, 3글자 이상이어야 함|
|LIKE a%o| a로 시작하고, o로 끝나야 함.|
|LIKE '[a-c]%' | a, b, c로 시작되는 모든 값 |
|LIKE '[rfg]%' | r, f, g로 시작되는 모든 값 |



## IN

- WHERE 이하에 사용하여 IN 이하에 언급된 값들을 가지고 온다.

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```


## BETWEEN

- WHERE 이하에 사용하여 가지고 올 값의 범위를 정해준다.

```
SELECT column_name(s) FROM table_name
WHERE column_name BETWEEN value1 and value2;
```

```
SELECT * FROM Proudcts
WHERE PIRCE BETWEEN 10 AND 20;

SELECT * FROM Proudcts
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```


## SQL Aliases

- 테이블이나 컬럼의 별명을 부를때 쓴다.
- 테이블 이나 컬럼의 이름이 길거나, 여러개를 선택해야 할때..
- 가지고온 데이터에도 별명이 계속 사용된다.
- 여러개의 이름을 묶을때도 사용한다.
- 가독성을 높이기 위해 사용하기도 한다.

```
SELECT coumn_name AS alias_name FROM table_name;

SELECT column_name(s) FROM table_name AS allias_name;
```



## Join

- 2개 이상의 테이블에서 데이터를 합칠때 사용한다.

```
SELECT Orders.OrderID, Customers.CustomerName, Order.OrderDate
FROM Oredrs
INNER JOIN Customers ON Orders.CustomersID = Customers.CustomerID;
```


#### INNER JOIN

- 교집합
- 일치하는 컬럼이름 기준으로 데이터를 가지고 온다.

```
SELECT column_name(s) FROM table
INNER JOIN table2 ON table1.column_name = table2.column_name;

SELECT Orders.OrderID, Customers.CusomterName FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomersID;
```


2. 세 테이블 합치기
```
SELECT Orders.OrderID, Customers.CustomerID, Shippers.ShipperName
FROM ((Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
```


#### LEFT JOIN

- table1에 해당하는 테이블의 모든 데이터와 조건에 맞는 table2 데이터를 가지고 온다.

```
SELECT column_name(s) FROM table1
LEFT JOIN table2 ON table1.column_name = table2.column_name;

SELECT Customers.CustomerName, Orders.OrderID FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
ORDER BY Customers.CustomerName;
```


#### RIGHT Join

- table2에 해당하는 테이블의 모든 데이터와 조건에 맞는 table1 데이터를 가지고 온다.

```
SELECT column_names(s)
FROM table1
RIGHT JOIN table2 ON table1.column_name = table2.column_name;

SELECT Orders.OrderID, Employees.LastName, Employees.FirstName
FROM Orders
RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
ORDER BY Orders.OrderID;
```


#### FULL OUTER JOIN

- table1과 table2의 데이터를 모두 가지고 오면서 조건에 맞는 값은 중복되지 않게 가지고 온다.
- MySql은 지원하지 않는다. (LEFT JOIN과 RIGHT JOIN을 UNION해서 해결)

```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2 ON table1.column_name = table2.column_name;

SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
```

#### SQL Self JOIN

- table 간의  JOIN

```
SELECT column_name(s)
FROM table T1, table T2
WHERE condition;

SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID # `<>` 같지 않다
AND A.City = B.City
ORDER BY A.City;
```

#### Union
- 각각의 SELECT가 가지고 온 데이터들을 합쳐준다.
- column의 수가 같아야 한다.
- 데이터 타입이 유사해야된다.
- 각각의 SELECT는 정렬 순서가 같아야 한다.
- 같은 데이터는 중복되게 가지고 오지 않는다.

```
# UNION
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

```
# UNION ALL
SELECT column_name(s) FROM table1
UNION All
SELECT column_name(s) FROM table2;
ORDER BY City;
```

#### Group By

- COUNT, MAX, MIN, SUM, AVG와 함께 사용하여 집계 범위를 정한다.

```
SELECT column_name(s), 집계함수(column_name)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);

SELECT Shippers.ShipperName, 
COUNT(Orders.OrderID) AS NumberOfOrders 
FROM Orders
LEFT JOIN Shippers 
ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
```

#### Having
- 집계함수와 GROUP BY와 같이 사용된다. (집계함수에 WHERE는 함께 사용할 수 없다.)
- 특정한 조건에 맞는 데이터만 가지고 온다.

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

#### Exists
- 하위 쿼리의 레코드 존재 여부를 테스트하는 데 사용된다.
- 연산자는 하위 쿼리가 하나 이상의 데이터를 반환하면 true를 반환한다.

```
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```

#### Any, All
- WHERE 이하 HAVING 이하에 사용한다.
- ANY : 조건에 맞는 데이터가 하나라도 있을때 True를 리턴
- ALL : 모든 데이터가 조건에 맞을때 True를 리턴

```
SELECT ProductName
FROM Products
WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);

SELECT ProductName
FROM Products
WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity > 99);

SELECT ProductName
FROM Products
WHERE ProductID = ALL (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
```

## Select Into

- 특정 테이블의 데이터를 조회와 동시에 저장한다
- 하나의 테이블로부터 데이터를 복사하여 새로운 테이블로 옮긴다.

```
# 모든 데이터
SELECT *
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;

# 일부 columns
SELECT column1, column2, column3, ...
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;

# Customers 테이블을 복사하여 백업을 만든다.
SELECT * INTO CustomersBackup2017
FROM Customers;

# Backup.mdb라는 데이터베이스 안에 Customers 테이블을 복사하여 백업을 만든다.
SELECT * INTO CustomersBackup2017 IN 'Backup.mdb'
FROM Customers;

# 기존 테이블과 함께 조작
SELECT Customers.CustomerName, Orders.OrderID
INTO CustomersOrderBackup2017
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;

# 기존 테이블의 구조만 복사하여 새로운 테이블을 만든다. (데이터는 가지고 오지 않음)
SELECT * INTO newtable
FROM oldtable
WHERE 1 = 0;
```


#### Insert Into Select

- 하나의 테이블로부터 데이터를 가지고 와서 이미 존재하는 테이블에 데이터를 추가한다.
- 기존 데이터들에 영향을 주지 않는다.

```
INSERT INTO table2
SELECT * FROM table1
WHERE condition;

INSERT INTO table2 (colum1, colum2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```

#### 주석 --

- -- : 주석이 1줄일때
- /* ... */ : 여러줄 주석일때

```
--Select all;
SELECT * FROM Customers;

/* Select all the columns of all the records
in the Customers table:*/

SELECT * FROM Customers;

```

### Database

#### Create Database

- 새로운 데이터 베이스 만들기

```
CREATE DATABASE databasename;
```

#### Drop DB

- 데이터 베이스를 삭제 한다.
- 데이터 베이스의 모든 정보를 삭제하기 때문에 함부로 사용해서는 안된다.

```
DROP DATABASE databasename;
```

#### Create table

- 데이터베이스 내에 테이블을 생성한다.
- 테이블 이름이 꼭 필요하다.
- 테이블 내에 column들을 만들어준다. 데이터타입 (컬럼의 데이터 사이즈를 지정)

```
CREATE TABLE table_name {
  column1 datattype,
  column2 datatype,
  column3 datatype,
  ....
};
```

#### Drop Table

- 테이블을 삭제한다.

```
DROP TABLE table_name;
```

#### Alter Table

- 이미 만들어진 테이블에서 데이터를 추가하거나, 삭제하거나 변경할때 사용

#### 구문

```
# add column
ALTER TABLE table_name
ADD column_name datatype;

# drop column
ALTER TABLE table_name
DROP COLUMN column_name;

# alter/modify column
# SQL Server / MS Access
ALTER TABLE table_name
ALTER COLUMN column_name datatype;

# My SQL / Oracle (prior version 10G)
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;

# Oracle 10G and later
ALTER TABLE table_name
MODIFY column_name datatype;
```


#### Constraints

- 테이블 내 데이터의 규칙

```
CREATE TABLE table_name (
  column1 datatype constraint,
  column2 datatype constraint,
  column3 datatype constraint,
  ...
);
```

#### Constraints 조건들
| 조건 |설명 |
| :------------- | :------------- |
| NOT NULL | NULL 값을 가지면 안됨.|
| UNIQUE | 칼럼 내 값들이 모두 다름을 보증함|
| PRIMARY KEY | NOT NULL + UNIQUE (값이 있되, 중복하지 않는다)|
| FOREIGN KEY | 다른 테이블의 값과 일치하며, 다른 테이블의 특정 값 외에는 가질 수 없다.|
| CHECK | 해당 칼럼에 저장 가능한 데이터 값의 범위나 조건을 지정해준다.|
| DEFAULT | 디폴트 값을 부여한다|
| INDEX | 색인, 조회할 때 원하는 행을 빠르게 찾을 수 있게 준비해둔 데이터|



#### Not Null

- 비어있는 경우를 허용하지 않는다.
- INSERT INTO로 데이터를 입력할때 NOT NULL이 설정된 필드 데이터가 비어있으면 에러가 발생한다.

```
CREATE TABLE  Persons (
  ID int NOT NULL,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255) NOT NULL,
  Age int
);
```

#### Unique

- 유일한 값을 갖게 한다.
- 1 테이블 내에 여러개의 유니크 값을 가질 수 있다.
- 하나 이상의 컬럼에 유니크를 지정할 수 있다.

```
CREATE TABLE Persons{
  ID int NOT NULL UNIQUE,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255),
  Age int
};

CREATE TABLE Persons{
  ID int NOT NULL,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255),
  Age int,
  CONSTARINT UC_Persons UNIQUE (ID, LastName)
};

ALTER TABLE Persons
ADD CONSTARINT UC_Person UNIQUE (ID, LastName);

ALTER TABLE Persons
DROP INDEX UC_Persons;
```

#### Primary Key

- null 값을 가질 수 없다.
- table당 PK는 1개

```
# MySQL
CREATE TABLE Persons{
  ID Int NOT NULL,
  LastName varchar(255) NOT NULL,
  FIrstName varchar(255),
  Age int,
  PRIMARY KEY (ID)
}

# SQL Server / Oracer / MS Access:
CREAT TABLE Persons{
  ID int NOT NULL PRIMARY KEY,
  LastName varchar(255) NOT NULL,
  FristName varchar(255),
  Age int
};

# MySQL / SQL Server / Oracle / MS Access
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName) # 테이블 하나에 PRIMARY KEY 하나
);
```

#### Foreign Key

- 외래키, 다른 데이터베이스와의 연결을 위한 키
- 다른 테이터베이스의 PK와 연결됨

```
(MySQL)
CREATE TABLE Orders{
  OrderID int NOT NULL,
  OrderNumber int NOT NULL,
  PersonsID int,
  PRIMARY KEY (OrderID),
  FOREIGN KEY (PersonID) REFERENCS Persons (PersonID)
};

(SQL Server / Oracle / MS Access)
CREAT TABLE Orders{
  OrderID int NOT NULL PRIMARY KEY,
  OrderNumber int NOT NULL,
  PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
}

(FOREIGN KEY 제약 조건의 이름 지정 및 여러 열의 제약 조건 정의)
CREATE TABLE ORDERS{
  OrderID int NOT NULL,
  OrderNumber int NOT NULL,
  PersonID int,
  PRIMARY KEY (OrderID),
  CONSTARINT FK_PersonsOrder FOREIGN KEY (PersonID)
  REFERENCES Persons(PersonID)
}

(ALTER TABLE 이용하기)
ALTER TABLE Orders
ADD FOREIGN KEY (personID) REFERENCES Persons(PersonID);

(`FOREIGN KEY` 해제하기)
ALTER TABLE Orders
DROP FOREIGN KEY FK_PersonsOrder;
```

#### Check

- 특정 컬럼에 입력되는 데이터의 범위를 한정한다.
- 데이터 입력 시 설정된 범위에 맞지 않을 경우 에러가 발생

```
CREAE TABLE Persons{
  ID int NOT NULL,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255),
  Age int,
  CHECK (Age >= 18)
};

ALTER TABLE Persons
ADD CHECK (Age >= 18);

ALTER TABLE Persons
DROP CONSTAINT CHK_PersonAge CHECK (Age>=18 AND City='Sandness');

ALTER TABLE Persons
DROP CONSTRAINT CHK_PersonAge;
```


#### Default

- 특정 컬럼에 사용자의 입력이 없을 경우 자동으로 입력될 값을 정해준다.
- 시스템값을 자동으로 입력되게 설정할 수 있다.

```
CREATE TABLE Persons{
  ID int NOT NULL,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255),
  Age int,
  City varchar(255) DEFAULT 'Sandens'
};

CREATE TABLE Orders (
    ID int NOT NULL,
    OrderNumber int NOT NULL,
    OrderDate date DEFAULT GETDATE() /* System Value 값을 넣을 수도 있다. */
);

ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';

ALTER TABLE Persons
ALTER City DROP DEFAULT;
```

#### index

- 검색이 잦은 컬럼에 인덱스를 부여하면 속도가 빨라진다.
- 업데이트가 잦은 컬럼의 경우에는 효율적이지 않다.
- 중복값이 허용된다. (유니크 인덱스일경우 중복값이 허용되지 않음)

```
CREATE INDEX Index_name
ON table_name (column1, column2, ...);

CREATE UNIQUE INDEX Index_name
ON  table_name (column1, column2, ...);

CREATE INDEX idx_lastname
ON Persons (LastName);

CREATE INDEX idx_pname
ON Persons (LastName, FirstName);

# 제거
DROP INDEX index_name ON table_name;
```

#### Auto Increment

- PK와 함께 사용되어 유일한 값을 생성한다.
- 데이터가 추가될 경우 설정된 컬럼에 기본적으로 1로 시작하여 1씩 추가되어 입력된다.

```
# MySQL
CREATE TABLE Persons (
    ID int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);

# 100부터 시작
ALTER TABLE Persons AUTO_INCREMENT=100;


# SQL Server
CREATE TABLE Persons (
    ID int IDENTITY(1,1) PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);

# 10부터 시작하여 5씩 증가
CREATE TABLE Persons (
    ID int IDENTITY(10,5) PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);


# MS Access
CREATE TABLE Persons (
    ID Integer PRIMARY KEY AUTOINCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);

# 10부터 시작하여 5씩 증가
CREATE TABLE Persons (
    ID Integer PRIMARY KEY AUTOINCREMENT(10, 5),
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);

# Oracle
# 시퀀스 객체를 따로 만들어 만들어진 값을 입력
CREATE SEQUENCE seq_person
MINVALUE 1
START WITH 1
INCREMENT BY 1
CACHE 10;

# 위 시퀀스에서 생성된 값을 ID 컬럼에 입력
INSERT INTO Persons (ID,FirstName,LastName)
VALUES (seq_person.nextval,'Lars','Monsen');
```


## Views

- SELECT로 가져올 데이터에 대한 가상테이블
- 실제 테이블처럼 동작하기도 한다.
- 가장 최근의 데이터로 만들어준다.
- 가상테이블의 데이터로 가상테이블을 만들 수도 있다.

```
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;

# 사용예
CREATE VIEW [Current Product List] AS  /* 가상 테이블의 이름을 가지는 View 를 만듦 */
SELECT ProductID, ProductName
FROM Products
WHERE Discontinued = No;

# VIEW 업데이트
CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;

# VIEW 삭제
DROP VIEW view_name;

```

### Injection

- 데이터베이스를 파괴할 수 있다.
- 악의적인 사용자가 웹페이지 코드에 사용된 SQL구문을 해석하여 해킹을 시도할 수 있음

SQL문의 일괄처리(A batch of SQL statment)는 세미콜론으로 구분 된 두 개 이상의 SQL 구문이다.

코드 삽입을 방지하기 위해서 `SQL Parameters`를 이용할 수 있다.
예를 들어서 SQL 매개변수는 실행 시간에 제어된 방식으로 SQL 쿼리에 추가된다.
```
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = @0";
db.Execute(txtSQL,txtUserId);
```

매개변수는 `@`로 알아볼 수 있다.
SQL 엔진은 각각의 파라미터들을 체크하면서 SQL문의 일부가 아닌지를 확인한다.
