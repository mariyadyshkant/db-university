raggruppare gli appelli per giorno
```sql

SELECT COUNT(*) as `number_of_exams`, `day_of_exam`
FROM `exams`
WHERE `date` LIKE `2020-07`
GROUP BY DAY(`date`)


-- Selezionare tutti i corsi del Corso di Laurea in Informatica (22)

SELECT *
FROM `courses`
JOIN `degrees`
ON courses.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Informatica';

-- Selezionare le informazioni sul corso con id=144, con tutti i relativi appelli d'esame
SELECT courses.id as `course_id`
FROM `courses`
JOIN `exams`
ON exams.course_id = courses.id
WHERE course_id = 144;

-- Selezionare a quale dipartimento appartiene il Corso di Laurea in Diritto dell'Economia (Dipartimento di Scienze politiche, giuridiche e studi internazionali

SELECT departments.*
FROM `departments`
JOIN `degrees`
ON department_id = departments.id
WHERE degrees.name = 'Corso di Laurea in Diritto dell'Economia';

-- Selezionare tutti gli appelli d'esame del Corso di Laurea Magistrale in Fisica del primo anno

SELECT `degrees`.`name` as `degree_name`, `courses`.`name`, `courses`.`period`, `courses`.`year`, `courses`.`cfu`, `exams`.`date`, `exams`.`location`, `exams`.`hour`, `exams`.`address`
FROM courses
JOIN degrees ON courses.degree_id = degrees.id
JOIN exams ON exams.course_id = courses.id
WHERE degrees.name = 'Corso di Laurea Magistrale in Fisica'
AND courses.year = 1;

-- Selezionare tutti i docenti che insegnano nel Corso di Laurea in Lettere (21)

SELECT DISTINCT teachers.id, teachers.name, teachers.surname, teachers.phone
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id`= `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id`= `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Lettere';

-- Selezionare il libretto universitario di Mirco Messina (matricola n. 620320)

SELECT students.name, students.surname, students.registration_number, courses.id AS course_id, courses.name AS course_name, exams.date, exam_student.vote
FROM `students`
JOIN `exam_student` ON exam_student.student_id = students.id
JOIN `exams` ON exam_student.exam_id = exams.id
JOIN `courses` ON exams.course_id = courses.id
WHERE students.name = 'Mirco'
AND students.surname = 'Messina'
AND exam_student.vote >= 18;