### 1. Contare quanti iscritti ci sono stati ogni anno
SELECT * 
FROM 
	db_university.courses
JOIN
	degrees
ON
	degrees.id = courses.degree_id
WHERE
	degrees.name= 'Corso di Laurea in Economia'
````