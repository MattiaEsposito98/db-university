### 1. Selezionare tutti gli studenti nati nel 1990 (160)
````SQL
SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;
````

### 2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
````SQL
SELECT * FROM db_university.courses
WHERE `cfu` >10
````

### 3. Selezionare tutti gli studenti che hanno più di 30 anni
````SQL
SELECT * FROM db_university.students
WHERE 2024 - YEAR (`date_of_birth`) >= 30
````

### 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di Laurea (286)
````SQL
SELECT * FROM db_university.courses
WHERE `period` = 'I semestre' AND `year` = 1
````

### 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
````SQL
SELECT * 
FROM db_university.exams
WHERE date = '2020-06-20' 
AND TIME(hour) >= '14:00:00';
````  

### 6. Selezionare tutti i corsi di laurea magistrale (38)
````SQL
SELECT * FROM db_university.degrees
WHERE `name` LIKE 'Corso di Laurea Magistrale %' 
````

### 7. Da quanti dipartimenti è composta l'università? (12)
````SQL
SELECT COUNT(*) AS `total_departments` FROM db_university.departments
````

### 8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
````SQL
SELECT COUNT(*) AS `teachers_without_number` FROM db_university.teachers
WHERE `phone` IS NOT NULL
````

### 9. Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo degree_id, inserire un valore casuale)
````SQL
INSERT INTO db_university.students (degree_id, name, surname, date_of_birth, fiscal_code, enrolment_date, registration_number, email) 
VALUES (12, 'Mattia', 'Esposito', '1998-01-31', 'spsmtt98a31f839j', '2021-09-01', 1234556, 'esposito.matty@hotmail.it');
````

### 10. Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126
````SQL
UPDATE db_university.teachers
SET office_number = 126 
WHERE name = 'Pietro' AND surname = 'Rizzo'	
````

### 11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9
````SQL
delete from db_university.students
where name= 'Mattia' AND surname = 'Esposito' 
````