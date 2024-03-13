# **CSE 212 - Database Systems Lab Notes #0**

## *Introduction*

Hello, and welcome to the CSE 212 Database Systems Lab Notes! Here I will be making notes on the lab sessions and the topics covered in the lab sessions. I hope you find these notes helpful. One thing is consider, I will use MySQL as the database management system (DBMS) for the lab sessions. So, if you are using a different DBMS, you may find some differences in the commands and the syntax. However, the concepts will be the same. In this introduction section, I will cover the following topics:

- **Creating a database.**
- **Creating a table.**
- **Inserting data into a table.**
- **Providing a code that will create the database and the table and insert some data into the table. All the code will execute at once. This database will be used in the follow-up sections.**

### *Creating a database*

To create a database, we use the following command:

```sql
CREATE DATABASE database_name;
```

Here, `database_name` is the name of the database that we want to create. For example, to create a database named `university`, we use the following command:

```sql
CREATE DATABASE university;
```

### *Creating a table*

To create a table, we use the following command:

```sql
CREATE TABLE table_name (
    column1_name column1_datatype,
    column2_name column2_datatype,
    ...
);
```

Here, `table_name` is the name of the table that we want to create. `column1_name`, `column2_name`, etc. are the names of the columns of the table. `column1_datatype`, `column2_datatype`, etc. are the datatypes of the columns. For example, to create a table named `student` with columns `id`, `name`, and `age`, we use the following command:

```sql
CREATE TABLE student (
    id INT,
    name VARCHAR(50),
    age INT
);
```

### *Inserting data into a table*

To insert data into a table, we use the following command:

```sql
INSERT INTO table_name (column1_name, column2_name, ...)
VALUES (value1, value2, ...);
```

Here, `table_name` is the name of the table into which we want to insert data. `column1_name`, `column2_name`, etc. are the names of the columns into which we want to insert data. `value1`, `value2`, etc. are the values that we want to insert into the columns. For example, to insert data into the `student` table, we use the following command:

```sql
INSERT INTO student (id, name, age)
VALUES (1, 'John Doe', 20);
```

### *Creating a database, creating a table, and inserting data into the table*

To create a database, create a table, and insert data into the table, we use the following commands:

```sql
CREATE DATABASE university;
USE university;
CREATE TABLE student (
    id INT,
    name VARCHAR(50),
    age INT
);
INSERT INTO student (id, name, age)
VALUES (1, 'John Doe', 20);
```

Here, the `CREATE DATABASE` command creates a database named `university`. The `USE` command selects the `university` database. The `CREATE TABLE` command creates a table named `student` with columns `id`, `name`, and `age`. The `INSERT INTO` command inserts data into the `student` table. The data that is inserted is `1` into the `id` column, `'John Doe'` into the `name` column, and `20` into the `age` column.

### *All the code at once*

```sql
CREATE DATABASE SharifdotG;

USE SharifdotG;

CREATE TABLE classroom (
    building VARCHAR(15), room_number VARCHAR(7), capacity NUMERIC(4, 0), PRIMARY KEY (building, room_number)
);

CREATE TABLE department (
    dept_name VARCHAR(20), building VARCHAR(15), budget NUMERIC(12, 2) CHECK (budget > 0), PRIMARY KEY (dept_name)
);

CREATE TABLE course (
    course_id VARCHAR(7), title VARCHAR(50), dept_name VARCHAR(20), credits NUMERIC(2, 0) CHECK (credits > 0), PRIMARY KEY (course_id), FOREIGN KEY (dept_name) REFERENCES department (dept_name)
);

CREATE TABLE instructor (
    ID VARCHAR(5), name VARCHAR(20), dept_name VARCHAR(20), salary NUMERIC(8, 2) CHECK (salary > 29000), PRIMARY KEY (ID), FOREIGN KEY (dept_name) REFERENCES department (dept_name)
);

CREATE TABLE section (
    course_id VARCHAR(8), sec_id VARCHAR(8), semester VARCHAR(6) CHECK (
        semester IN (
            "Fall", "Winter", "Spring", "Summer"
        )
    ), year NUMERIC(4, 0) CHECK (
        year > 1701
        AND year < 2100
    ), building VARCHAR(15), room_number VARCHAR(7), time_slot_id VARCHAR(4), PRIMARY KEY (
        course_id, sec_id, semester, year
    ), FOREIGN KEY (course_id) REFERENCES course (course_id), FOREIGN KEY (building, room_number) REFERENCES classroom (building, room_number)
);

CREATE TABLE teaches (
    ID VARCHAR(5), course_id VARCHAR(8), sec_id VARCHAR(8), semester VARCHAR(6), year NUMERIC(4, 0), PRIMARY KEY (
        ID, course_id, sec_id, semester, year
    ), FOREIGN KEY (
        course_id, sec_id, semester, year
    ) REFERENCES section (
        course_id, sec_id, semester, year
    ), FOREIGN KEY (ID) REFERENCES instructor (ID)
);

CREATE TABLE student (
    ID VARCHAR(5), name VARCHAR(20), dept_name VARCHAR(20), tot_cred NUMERIC(3, 0) CHECK (tot_cred >= 0), PRIMARY KEY (ID), FOREIGN KEY (dept_name) REFERENCES department (dept_name)
);

CREATE TABLE takes (
    ID VARCHAR(5), course_id VARCHAR(8), sec_id VARCHAR(8), semester VARCHAR(6), year NUMERIC(4, 0), grade VARCHAR(2), PRIMARY KEY (
        ID, course_id, sec_id, semester, year
    ), FOREIGN KEY (
        course_id, sec_id, semester, year
    ) REFERENCES section (
        course_id, sec_id, semester, year
    ), FOREIGN KEY (ID) REFERENCES student (ID)
);

CREATE TABLE advisor (
    s_ID VARCHAR(5), i_ID VARCHAR(5), PRIMARY KEY (s_ID), FOREIGN KEY (s_ID) REFERENCES student (ID), FOREIGN KEY (i_ID) REFERENCES instructor (ID)
);

CREATE TABLE timeslot (
    time_slot_id VARCHAR(4), day VARCHAR(1) CHECK (
        day IN (
            'M', 'T', 'W', 'R', 'F', 'S', 'U'
        )
    ), start_time time, end_time time, PRIMARY KEY (time_slot_id, day, start_time)
);

CREATE TABLE prereq (
    course_id VARCHAR(8), prereq_id VARCHAR(8), PRIMARY KEY (course_id, prereq_id), FOREIGN KEY (course_id) REFERENCES course (course_id), FOREIGN KEY (prereq_id) REFERENCES course (course_id)
);

INSERT INTO
    classroom
VALUES ('Packard', '101', 500),
    ('Painter', '514', 10),
    ('Taylor', '3128', 70),
    ('Watson', '100', 30),
    ('Watson', '120', 50);

INSERT INTO
    department
VALUES ('Biology', 'Watson', 90000),
    (
        'Comp. Sci.', 'Taylor', 100000
    ),
    ('Elec. Eng.', 'Taylor', 85000),
    ('Finance', 'Painter', 120000),
    ('History', 'Painter', 50000),
    ('Music', 'Packard', 80000),
    ('Physics', 'Watson', 70000);

INSERT INTO
    course
VALUES (
        'BIO-101', 'Intro. to Biology', 'Biology', 4
    ),
    (
        'BIO-301', 'Genetics', 'Biology', 4
    ),
    (
        'BIO-399', 'Computational Biology', 'Biology', 3
    ),
    (
        'CS-101', 'Intro. to Computer Science', 'Comp. Sci.', 4
    ),
    (
        'CS-190', 'Game Design', 'Comp. Sci.', 4
    ),
    (
        'CS-315', 'Robotics', 'Comp. Sci.', 3
    ),
    (
        'CS-319', 'Image Processing', 'Comp. Sci.', 3
    ),
    (
        'CS-347', 'Database System Concepts', 'Comp. Sci.', 3
    ),
    (
        'EE-181', 'Intro. to Digital Systems', 'Elec. Eng.', 3
    ),
    (
        'FIN-201', 'Investment Banking', 'Finance', 3
    ),
    (
        'HIS-351', 'World History', 'History', 3
    ),
    (
        'MU-199', 'Music Video Production', 'Music', 3
    ),
    (
        'PHY-101', 'Physical Principles', 'Physics', 4
    );

INSERT INTO
    instructor
VALUES (
        '10101', 'Srinivasan', 'Comp. Sci.', 65000
    ),
    (
        '12121', 'Wu', 'Finance', 90000
    ),
    (
        '15151', 'Mozart', 'Music', 40000
    ),
    (
        '22222', 'Einstein', 'Physics', 95000
    ),
    (
        '32343', 'El Said', 'History', 60000
    ),
    (
        '33456', 'Gold', 'Physics', 87000
    ),
    (
        '45565', 'Katz', 'Comp. Sci.', 75000
    ),
    (
        '58583', 'Califieri', 'History', 62000
    ),
    (
        '76543', 'Singh', 'Finance', 80000
    ),
    (
        '76766', 'Crick', 'Biology', 72000
    ),
    (
        '83821', 'Brandt', 'Comp. Sci.', 92000
    ),
    (
        '98345', 'Kim', 'Elec. Eng.', 80000
    );

INSERT INTO
    section
VALUES (
        'BIO-101', '1', 'Summer', 2017, 'Painter', '514', 'B'
    ),
    (
        'BIO-301', '1', 'Summer', 2018, 'Painter', '514', 'A'
    ),
    (
        'CS-101', '1', 'Fall', 2017, 'Packard', '101', 'H'
    ),
    (
        'CS-101', '1', 'Spring', 2018, 'Packard', '101', 'F'
    ),
    (
        'CS-190', '1', 'Spring', 2017, 'Taylor', '3128', 'E'
    ),
    (
        'CS-190', '2', 'Spring', 2017, 'Taylor', '3128', 'A'
    ),
    (
        'CS-315', '1', 'Spring', 2018, 'Watson', '120', 'D'
    ),
    (
        'CS-319', '1', 'Spring', 2018, 'Watson', '100', 'B'
    ),
    (
        'CS-319', '2', 'Spring', 2018, 'Taylor', '3128', 'C'
    ),
    (
        'CS-347', '1', 'Fall', 2017, 'Taylor', '3128', 'A'
    ),
    (
        'EE-181', '1', 'Spring', 2017, 'Taylor', '3128', 'C'
    ),
    (
        'FIN-201', '1', 'Spring', 2018, 'Packard', '101', 'B'
    ),
    (
        'HIS-351', '1', 'Spring', 2018, 'Painter', '514', 'C'
    ),
    (
        'MU-199', '1', 'Spring', 2018, 'Packard', '101', 'D'
    ),
    (
        'PHY-101', '1', 'Fall', 2017, 'Watson', '100', 'A'
    );

INSERT INTO
    teaches
VALUES (
        '10101', 'CS-101', '1', 'Fall', 2017
    ),
    (
        '10101', 'CS-315', '1', 'Spring', 2018
    ),
    (
        '10101', 'CS-347', '1', 'Fall', 2017
    ),
    (
        '12121', 'FIN-201', '1', 'Spring', 2018
    ),
    (
        '15151', 'MU-199', '1', 'Spring', 2018
    ),
    (
        '22222', 'PHY-101', '1', 'Fall', 2017
    ),
    (
        '32343', 'HIS-351', '1', 'Spring', 2018
    ),
    (
        '45565', 'CS-101', '1', 'Spring', 2018
    ),
    (
        '45565', 'CS-319', '1', 'Spring', 2018
    ),
    (
        '76766', 'BIO-101', '1', 'Summer', 2017
    ),
    (
        '76766', 'BIO-301', '1', 'Summer', 2018
    ),
    (
        '83821', 'CS-190', '1', 'Spring', 2017
    ),
    (
        '83821', 'CS-190', '2', 'Spring', 2017
    ),
    (
        '83821', 'CS-319', '2', 'Spring', 2018
    ),
    (
        '98345', 'EE-181', '1', 'Spring', 2017
    );

INSERT INTO
    student
VALUES (
        '00128', 'Zhang', 'Comp. Sci.', 102
    ),
    (
        '12345', 'Shankar', 'Comp. Sci.', 32
    ),
    (
        '19991', 'Brandt', 'History', 80
    ),
    (
        '23121', 'Chavez', 'Finance', 110
    ),
    (
        '44553', 'Peltier', 'Physics', 56
    ),
    (
        '45678', 'Levy', 'Physics', 46
    ),
    (
        '54321', 'Williams', 'Comp. Sci.', 54
    ),
    (
        '55739', 'Sanchez', 'Music', 38
    ),
    ('70557', 'Snow', 'Physics', 0),
    (
        '76543', 'Brown', 'Comp. Sci.', 58
    ),
    (
        '76653', 'Aoi', 'Elec. Eng.', 60
    ),
    (
        '98765', 'Bourikas', 'Elec. Eng.', 98
    ),
    (
        '98988', 'Tanaka', 'Biology', 120
    );

INSERT INTO
    takes
VALUES (
        '00128', 'CS-101', '1', 'Fall', 2017, 'A'
    ),
    (
        '00128', 'CS-347', '1', 'Fall', 2017, 'A'
    ),
    (
        '12345', 'CS-190', '2', 'Spring', 2017, 'A'
    ),
    (
        '12345', 'CS-315', '1', 'Spring', 2018, 'A'
    ),
    (
        '12345', 'CS-347', '1', 'Fall', 2017, 'A'
    ),
    (
        '19991', 'HIS-351', '1', 'Spring', 2018, 'B'
    ),
    (
        '23121', 'FIN-201', '1', 'Spring', 2018, 'C+'
    ),
    (
        '44553', 'PHY-101', '1', 'Fall', 2017, 'B'
    ),
    (
        '45678', 'CS-101', '1', 'Fall', 2017, 'F'
    ),
    (
        '45678', 'CS-101', '1', 'Spring', 2018, 'B+'
    ),
    (
        '45678', 'CS-319', '1', 'Spring', 2018, 'B'
    ),
    (
        '54321', 'CS-101', '1', 'Fall', 2017, 'A'
    ),
    (
        '54321', 'CS-190', '2', 'Spring', 2017, 'B+'
    ),
    (
        '55739', 'MU-199', '1', 'Spring', 2018, 'A'
    ),
    (
        '76543', 'CS-101', '1', 'Fall', 2017, 'A'
    ),
    (
        '76543', 'CS-319', '2', 'Spring', 2018, 'A'
    ),
    (
        '76653', 'EE-181', '1', 'Spring', 2017, 'C'
    ),
    (
        '98765', 'CS-101', '1', 'Fall', 2017, 'C'
    ),
    (
        '98765', 'CS-315', '1', 'Spring', 2018, 'B'
    ),
    (
        '98988', 'BIO-101', '1', 'Summer', 2017, 'A'
    ),
    (
        '98988', 'BIO-301', '1', 'Summer', 2018, null
    );

INSERT INTO
    advisor
VALUES ('00128', '45565'),
    ('12345', '10101'),
    ('23121', '76543'),
    ('44553', '22222'),
    ('45678', '22222'),
    ('55739', '15151'),
    ('76543', '45565'),
    ('76653', '98345'),
    ('98765', '98345'),
    ('98988', '76766');

INSERT INTO
    prereq
VALUES ('BIO-301', 'BIO-101'),
    ('BIO-399', 'BIO-101'),
    ('CS-190', 'CS-101'),
    ('CS-315', 'CS-101'),
    ('CS-319', 'CS-101'),
    ('CS-347', 'CS-101'),
    ('EE-181', 'PHY-101');

INSERT INTO
    timeslot
VALUES ('A', 'M', '8:00', '8:50'),
    ('A', 'W', '8:00', '8:50'),
    ('A', 'F', '8:00', '8:50'),
    ('B', 'M', '9:00', '9:50'),
    ('B', 'W', '9:00', '9:50'),
    ('B', 'F', '9:00', '9:50'),
    ('C', 'M', '11:00', '11:50'),
    ('C', 'W', '11:00', '11:50'),
    ('C', 'F', '11:00', '11:50'),
    ('D', 'M', '13:00', '13:50'),
    ('D', 'W', '13:00', '13:50'),
    ('D', 'F', '13:00', '13:50'),
    ('E', 'T', '10:30', '11:45'),
    ('E', 'R', '10:30', '11:45'),
    ('F', 'T', '14:30', '15:45'),
    ('F', 'R', '14:30', '15:45'),
    ('G', 'M', '16:00', '16:50'),
    ('G', 'W', '16:00', '16:50'),
    ('G', 'F', '16:00', '16:50'),
    ('H', 'W', '10:00', '12:30');
```

In the above code, I have created a database named `SharifdotG`. I have created 13 tables: `classroom`, `department`, `course`, `instructor`, `section`, `teaches`, `student`, `takes`, `advisor`, `timeslot`, `prereq`, and `timeslot`. I have inserted data into the tables. The data that I have inserted is the data of a university. The data is inserted into the tables in such a way that the tables are related to each other. For example, the `course` table is related to the `department` table. The `instructor` table is related to the `department` table. The `section` table is related to the `course` table and the `classroom` table. The `teaches` table is related to the `instructor` table and the `section` table. The `student` table is related to the `department` table. The `takes` table is related to the `student` table and the `section` table. The `advisor` table is related to the `student` table and the `instructor` table. The `timeslot` table is related to the `section` table. The `prereq` table is related to the `course` table. The `timeslot` table is related to the `section` table. The data that I have inserted into the tables is the data of a university. The data is inserted into the tables in such a way that the tables are related to each other. For example, the `course` table is related to the `department` table. The `instructor` table is related to the `department` table. The `section` table is related to the `course` table and the `classroom` table. The `teaches` table is related to the `instructor` table and the `section` table. The `student` table is related to the `department` table. The `takes` table is related to the `student` table and the `section` table. The `advisor` table is related to the `student` table and the `instructor` table. The `timeslot` table is related to the `section` table. The `prereq` table is related to the `course` table. The `timeslot` table is related to the `section` table. This code will create the database, create the tables, and insert the data into the tables. The data that is inserted is the data of a university. The data is inserted into the tables in such a way that the tables are related to each other. This database will be used in the follow-up sections.

---

## *Conclusion*

In this introduction section, I have covered the following topics:

- **Creating a database.**
- **Creating a table.**
- **Inserting data into a table.**
- **Providing a code that will create the database and the table and insert some data into the table. All the code will execute at once. This database will be used in the follow-up sections.**

I hope you find this introduction helpful. In the follow-up sections, I will cover the topics that are related to the lab sessions. If you have any questions, feel free to ask. I will be happy to help you.

---
