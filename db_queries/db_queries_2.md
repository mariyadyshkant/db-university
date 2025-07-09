### Group by:
1. Contare quanti iscritti ci sono stati ogni anno 

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio 

3. Calcolare la media dei voti di ogni appello d'esame 

4. Contare quanti corsi di laurea ci sono per ogni dipartimento


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

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44) 

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome 

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti 

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54) 

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.