# 1 Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia.

```
SELECT `students`.*, `degrees`.`name` 
    FROM `students`
        JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
        WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
```

# 2 Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze.

```
SELECT `degrees`.*, `departments`.`name` 
    FROM `degrees`
        JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
        WHERE `departments`.`name` = 'Dipartimento di Neuroscienze';
```

# 3 Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44).

```
SELECT `courses`.*, `teachers`.`name`, `teachers`.`surname`
    FROM `courses`
        JOIN `course_teacher`
    ON `course_teacher`.`course_id` = `courses`.`id`
        JOIN `teachers`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
            WHERE `teachers`.`name` = 'Fulvio'
                AND `teachers`.`surname` = 'Amato'
                    AND `teachers`.`id` = 44;

```

# 4 Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome.

```
SELECT `students`.`surname`, `students`.`name`, `degrees`.`name`, `degrees`.`level`, `departments`.`name`
    FROM `students`
        JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
        JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC, `students`.`name` ASC;

```

# 5 Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti.

```
SELECT `degrees`.`name`, `courses`.*, `teachers`.`name`, `teachers`.`surname`
    FROM `teachers`
        JOIN `course_teacher`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
        JOIN `courses`
    ON `course_teacher`.`course_id` = `courses`.`id`
        JOIN `degrees`
    ON `courses`.`degree_id` = `degrees`.`id`;

```

# 6 Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54).

```
SELECT DISTINCT `teachers`.`name`, `teachers`.`surname`, `departments`.`name`
    FROM `teachers`
        JOIN `course_teacher`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
        JOIN `courses`
    ON `course_teacher`.`course_id` = `courses`.`id`
        JOIN `degrees`
    ON `courses`.`degree_id` = `degrees`.`id`
        JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
        WHERE `departments`.`name` = 'Dipartimento di Matematica';

```

# 7 BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```
SELECT `students`.`name`, `students`.`surname`, COUNT(*) AS `numero esami sostenuto`, MAX(`exam_student`.`vote`) AS `voto_massimo`, `courses`.`name`
    FROM `exams`
        JOIN `courses`
    ON `exams`.`course_id` = `courses`.`id`
        JOIN `exam_student`
    ON `exam_student`.`exam_id` = `exams`.`id`
        JOIN `students`
    ON `exam_student`.`student_id` = `students`.`id`
        WHERE `exam_student`.`vote` >= 18
            GROUP BY `students`.`id`, `courses`.`id`;
```
