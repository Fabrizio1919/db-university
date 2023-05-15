<!-- 
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per
superare ciascuno dei suoi esami -->

# QUERY CON JOIN


## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`name`,`students`.`surname`, `students`.`degree_id`, `degrees`.`name` 
FROM `degrees` 
INNER JOIN `students` 
ON `degrees`.`id` = `students`.`degree_id` 
WHERE `degrees`.`name` = 'corso di laurea in economia';


## 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT * 
FROM `departments` 
INNER JOIN `degrees` 
ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name`= 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale';


## 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `courses`.`name` AS 'corso:', `teachers`.`name`, `teachers`.`surname` 
FROM `courses` 
INNER JOIN `course_teacher` 
ON `courses`.`id` = `course_teacher`.`course_id` 
INNER JOIN `teachers` 
ON `course_teacher`.`teacher_id`= `teachers`.`id` 
WHERE `teachers`.`id`=44;


## 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine  alfabetico per cognome e nome
SELECT `students`.`id`,`students`.`surname`,`students`.`name`,`degrees`.`name`,`degrees`.`level`,`departments`.`name` 
FROM `students` 


## 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT `degrees`.`name` AS 'Corso di Laurea' ,`courses`.`name` AS 'Materia',`teachers`.`name`,`teachers`.`surname` 
FROM `degrees` 
INNER JOIN `courses` 
ON `degrees`.`id`=`courses`.`degree_id` 
INNER JOIN `course_teacher` 
ON `courses`.`id`=`course_teacher`.`course_id` 
INNER JOIN `teachers` 
ON `course_teacher`.`teacher_id` = `teachers`.`id` 
ORDER BY degrees.name ASC;


## 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT `teachers`.`name`,`teachers`.`surname` 
FROM `teachers` 
INNER JOIN `course_teacher` 
ON `teachers`.`id` = `course_teacher`.`teacher_id` 
INNER JOIN `courses` 
ON `course_teacher`.`course_id` = `courses`.`id` 
INNER JOIN `degrees` 
ON `courses`.`degree_id`= `degrees`.`id` 
INNER JOIN `departments` 
ON `degrees`.`department_id`=`departments`.`id` 
WHERE `departments`.`name`='Dipartimento di Matematica' 
ORDER BY `teachers`.`name` DESC;


## 7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami