### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
````SQL
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

### 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
````SQL
SELECT 
  degrees.`name` AS degree_name,
  departments.`name` AS department_name
FROM 
  degrees	
JOIN 
  departments 
ON 
  degrees.department_id = departments.id
WHERE 
  departments.`name` = 'Dipartimento di Neuroscienze'    AND degrees.`level` = 'Magistrale';
````

### 3.  Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
````SQL
SELECT 
  courses.`name` AS course_name
FROM
  courses
JOIN
  course_teacher ON course_teacher.course_id = courses.id
JOIN
  teachers ON course_teacher.teacher_id = teachers.id
WHERE
  teachers.id = 44;
````

### 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
````SQL
SELECT 
  s.id AS student_id,
  s.name,
  s.surname,
  d.name AS degree_name,
  dep.name AS department_name
FROM 
  students AS s
JOIN 
  degrees AS d ON s.degree_id = d.id
JOIN 
  departments AS dep ON d.department_id = dep.id
ORDER BY 
  s.surname ASC,
	s.name ASC;
````

### 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
````SQL
SELECT 
	degrees.name AS degrees_name, courses.name AS courses_name, teachers.name, teachers.surname 
FROM 
	degrees
JOIN 	
	course_teacher ON degrees.id = course_teacher.course_id
JOIN 
	courses ON course_teacher.course_id = courses.id
JOIN 
	teachers ON course_teacher.teacher_id = teachers.id
````

### 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
````SQL
SELECT  
	t.* 
FROM 
	`teachers` t
JOIN 
	`course_teacher` ct ON t.`id` = ct.`teacher_id`
JOIN 
	`courses` c ON ct.`course_id` = c.`id`
JOIN 
	`degrees` deg ON c.`degree_id` = deg.`id`
WHERE 
	deg.`department_id` = (
		SELECT 
			`id` 
		FROM 
			`departments` 
    WHERE 
			`name` = 'Dipartimento di Matematica');
````

### 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
````SQL
SELECT 
  es.student_id,
  es.exam_id,
  COUNT(*) AS num_attempts,            
  MAX(es.vote) AS max_vote              
FROM 
  exam_student es
WHERE 
  es.vote >= 18                        
GROUP BY 
  es.student_id, es.exam_id          
ORDER BY 
  es.student_id, es.exam_id;          
````