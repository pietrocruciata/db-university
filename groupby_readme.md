1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(`id`), YEAR(`enrolment_date`) FROM `students` GROUP BY YEAR(`enrolment_date`);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(`id`), `office_address` FROM `teachers` WHERE `office_address` = `office_address` GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame

//NON è GIUSTO
SELECT COUNT(`date`), AVG(`vote`) 
FROM `exam_student`
INNER JOIN `exams`
ON `exams`.`id` = `exam_student`.`exam_id`
GROUP BY `date`,`vote`; 
//
4. Contare quanti corsi di laurea ci sono per ogni dipartimento

//NON è GIUSTO
SELECT COUNT(`degrees`.`id`) AS `corsi`, COUNT(`departments`.`id`) AS `dipartimenti`
FROM `departments`
INNER JOIN `degrees`
ON `degrees`.`department_id` = `departments`.`id`;
//