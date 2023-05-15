<!-- 

1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento -->

# QUERY CON GROUP BY

## 1. Contare quanti iscritti ci sono stati ogni anno 
SELECT YEAR(`enrolment_date`) AS 'ANNO', COUNT('id') AS 'NUOVI STUDENTI' 
FROM `students` 
GROUP BY YEAR(`enrolment_date`);

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT `office_address` AS 'Indirizzo ufficio', COUNT('id') AS 'Numero di insegnanti' 
FROM `teachers` 
GROUP BY `office_address`;


## 3. Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(`vote`) AS 'media', `exam_id` AS 'id esame'
 FROM `exam_student`
 GROUP BY `exam_id`;

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento 
SELECT COUNT(`id`) AS 'numero di corsi', `department_id` AS 'ID dipartimento' 
FROM `degrees` 
GROUP BY `department_id`;