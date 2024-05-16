1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT * FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'corso di laurea in economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

SELECT * FROM `departments` INNER JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT * FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` INNER JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` WHERE `teachers`.`name` = 'fulvio' AND `teachers`.`surname` = 'amato';

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

SELECT * FROM `students` INNER JOIN `degrees` ON `degrees`.`id`= `students`.`degree_id` INNER JOIN `departments` ON `departments`.`id`= `degrees`.`department_id` ORDER BY `students`.`name`,`students`.`surname` ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name`,`courses`.`name`,`teachers`.`name`,`teachers`.`surname` FROM `degrees` INNER JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id` INNER JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id` INNER JOIN `teachers` ON `teachers`.`id`= `course_teacher`.`teacher_id`;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

SELECT DISTINCT `teachers`.`name`,`teachers`.`surname`,`degrees`.`name` FROM `departments` INNER JOIN `degrees` ON `degrees`.`department_id`= `departments`.`id` INNER JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id` INNER JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id` INNER JOIN `teachers` ON `teachers`.`id`= `course_teacher`.`teacher_id` WHERE `departments`.`name` = 'dipartimento di matematica';

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.