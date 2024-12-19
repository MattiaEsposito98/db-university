### Contare quanti iscritti ci sono stati ogni anno
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

### Contare gli insegnanti che hanno l'ufficio nello stesso edificio
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

### Calcolare la media dei voti di ogni appello d'esame
```` SQL
SELECT 
    e.`date` AS data_esame,
    AVG(e_s.`vote`) AS media_voti
FROM 
    `exams` AS e
JOIN 
    `exam_student` AS e_s 
ON 
    e.`id` = e_s.`exam_id`
GROUP BY 
    e.`date`
ORDER BY 
    media_voti DESC;
````

### Contare quanti corsi di laurea ci sono per ogni dipartimento
```` SQL

````

