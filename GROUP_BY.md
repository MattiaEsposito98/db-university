### 1. Contare quanti iscritti ci sono stati ogni anno
```` SQL
SELECT 
  YEAR(enrolment_date) AS anno,
  COUNT(*) AS numero_iscritti
FROM 
  `students`
GROUP BY 
  YEAR(enrolment_date)
ORDER BY 
  anno;
````

### 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
```` SQL
SELECT 
  office_address,
  COUNT(*) AS stesso_ufficio
FROM 
  db_university.teachers
GROUP BY 
  office_address
ORDER BY 
  stesso_ufficio DESC;
````

### 3. Calcolare la media dei voti di ogni appello d'esame
```` SQL
SELECT AVG(`vote`) AS `avg`, `exam_id`
FROM `exam_student`
GROUP BY `exam_id`
````

### 4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```` SQL
SELECT 
	department_id,
  COUNT(*) AS number_department 
FROM 
	db_university.degree
GROUP BY
	department_id
ORDER BY
	department_id ASC
````

