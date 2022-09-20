1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    SELECT `students`.`id`,`students`.`name`, `students`.`surname`, `degrees`.`name`
    FROM `students`
    JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
    WHERE `degrees`.`name` = "Corso di Laurea in Economia"


2. Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
    SELECT `degrees`.`id` AS "degrees_id", `degrees`.`name`, `degrees`.`level`, `departments`.`name`, `departments`.`id` AS "departments_id"
    FROM `degrees` 
    JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
    WHERE `departments`.`name` = "Dipartimento di Neuroscienze"


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    SELECT `teachers`.`id` AS "id_teachers", `teachers`.`name`, `teachers`.`surname`, `courses`.`name`, `courses`.`year`
    FROM `courses` 
    JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
    JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
    WHERE `teachers`.`name` = "Fulvio"
    AND `teachers`.`surname` = "Amato"


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome
    SELECT `students`.`id` AS "students_id",  `students`.`name`, `students`.`surname`, `students`.`date_of_birth`, `degrees`.`name` AS "nome_corso_laurea", `departments`.`name` AS "nome_dipartimento"
    FROM `students` 
    JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
    JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
    ORDER BY `students`.`name` ASC


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    SELECT `teachers`.`name`, `teachers`.`surname`, `degrees`.`id` AS "degrees_id", `degrees`.`name`, `degrees`.`level`, `courses`.`name` AS "corses_name", `courses`.`year`, `courses`.`cfu`
    FROM `degrees`
    JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
    JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
    JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`


6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    SELECT DISTINCT `teachers`.`name`, `teachers`.`surname`, `teachers`.`phone`, `teachers`.`email`, `departments`.`name`
    FROM `teachers`
    JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
    JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
    JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
    JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
    WHERE `departments`.`name` = "Dipartimento di Matematica"

7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per
superare ciascuno dei suoi esami 