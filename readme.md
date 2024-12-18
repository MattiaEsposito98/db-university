### Selezionare tutti gli studenti nati nel 1990 (160)
````SQL
SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;
````

### Selezionare tutti i corsi che valgono più di 10 crediti (479)
````SQL
SELECT * FROM db_university.courses
WHERE `cfu` >10
````

### Selezionare tutti gli studenti che hanno più di 30 anni
````SQL
SELECT * FROM db_university.students
WHERE 2024 - YEAR (`date_of_birth`) >= 30
````