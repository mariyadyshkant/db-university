### Group by:
1. Contare quanti iscritti ci sono stati ogni anno 

SELECT COUNT(*) AS `number_of_students`, YEAR(students.enrolment_date) AS `year`
FROM `students`
GROUP BY YEAR(students.enrolment_date);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(*) AS `teachers`, `office_address`
FROM `teachers`
GROUP BY (office_address);

3. Calcolare la media dei voti di ogni appello d'esame 

SELECT AVG(vote) AS `average_vote`, `exam_id`
FROM `exam_student`
GROUP BY (exam_id);

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(*) AS `number_of_degrees`, `department_id` 
FROM `degrees`
GROUP BY (department_id);

### Join:
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia (68)

SELECT students.id, students.name, students.surname, students.registration_number, degrees.name AS `department_name`
FROM `students`
JOIN `degrees` ON degrees.id = students.degree_id
WHERE degrees.name = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze (1)

SELECT degrees.department_id, degrees.name AS degree_name, degrees.level, departments.name AS department_name
FROM `departments`
JOIN `degrees` ON departments.id = degrees.department_id
WHERE departments.name = 'Dipartimento di Neuroscienze'
AND degrees.level = 'magistrale';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44) (11)

SELECT teachers.id, teachers.name, teachers.surname, courses.id AS course_id, courses.name AS course_name
FROM `teachers`
JOIN `course_teacher` ON course_teacher.teacher_id = teachers.id
JOIN `courses` ON course_teacher.course_id = courses.id
WHERE teachers.name = 'Fulvio'
AND teachers.surname = 'Amato';

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome (5000)

SELECT students.surname, students.name, students.degree_id, degrees.name AS degree_name, departments.name AS department_name
FROM `students`
JOIN `degrees` ON students.degree_id = degrees.id
JOIN `departments` ON degrees.department_id = departments.id
ORDER BY `surname`ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti (1317)

SELECT degrees.name AS degree_name, courses.name AS course_name, teachers.surname, teachers.name
FROM `degrees`
JOIN `courses` ON courses.degree_id = degrees.id
JOIN `course_teacher` ON course_teacher.course_id = courses.id
JOIN `teachers`ON course_teacher.teacher_id = teachers.id;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54) 

SELECT DISTINCT teachers.surname, teachers.name, departments.name
FROM `teachers`
JOIN `course_teacher` ON course_teacher.teacher_id = teachers.id
JOIN `courses`ON course_teacher.course_id = courses.id
JOIN `degrees`ON courses.degree_id = degrees.id
JOIN `departments`ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Matematica';

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.