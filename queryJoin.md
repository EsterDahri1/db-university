## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.`id`, `students`.`name`, `students`.`surname`, `students`.`degree_id`, `students`.`registration_number`, `degrees`.`name` 
FROM `students` 
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` 
WHERE `degrees`.name = 'Corso di laurea in Economia';
```

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT `degrees`.`id`, `degrees`.`department_id`, `degrees`.`name` AS `degrees_name`, `degrees`.`level`, `departments`.`name` AS `department_name`, `departments`.`email` 
FROM `degrees` 
JOIN `departments` ON  `degrees`.`department_id` =`departments`.`id` 
WHERE `degrees`.`level` = 'magistrale' 
AND `departments`.`name` = 'Dipartimento di Neuroscienze'; 
```

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT `teachers`.`id`, `teachers`.`name`, `teachers`.`surname`, `courses`.`id` AS `courses_id`, `courses`.`name`, `courses`.`description`, `courses`.`period`, `courses`.`year` 
FROM `teachers` 
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` 
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` 
WHERE `teachers`.name = 'Fulvio' 
AND `teachers`.`surname` = 'Amato' 
AND `teachers`.`id` = 44; 
```

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT `students`.`id`, `students`.`surname` AS `students_surname`, `students`.`name` AS `students_name`, `degrees`.`name` AS `degrees_name`, `degrees`.`level`, `departments`.`name` AS `departments_name` 
FROM `students` 
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` 
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` 
ORDER BY `students`.`name`, `students`.`surname` ASC;
```

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT `degrees`.`id` AS `degrees_id`, `degrees`.`name` AS `degrees_name`, `degrees`.`level`, `courses`.`name` AS `courses_name`, `teachers`.`name` AS `teachers_name`, `teachers`.`surname` AS `teachers_surname`
FROM `degrees`
INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT DISTINCT `teachers`.`id`, `teachers`.`name` AS `teachers_name`,`teachers`.`surname` AS `teachers_surname`, `departments`.`name` AS `departments_name`
FROM `teachers`
INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';
```

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```sql
SELECT COUNT(`exam_student`.`exam_id`) AS `numero_tenativi`, `students`.`id` AS `students_id`, `students`.`name` AS `students_name`, `students`.`surname`, `students`.`registration_number`, `courses`.`name` AS `courses_name`, MAX(`exam_student`.`vote`) AS `voto_massimo`
FROM `students`
JOIN `exam_student`ON `students`.`id` = `exam_student`.`exam_id`
JOIN `exams`ON `exams`.`id` = `exam_student`.`exam_id`
JOIN `courses`ON `courses`.`id` = `exams`.`course_id`
GROUP BY `courses`.`id`, `students`.`id`
HAVING `voto_massimo` >= 18
GROUP BY `courses`.`id`, `students`.`id`
ORDER BY `numero_tenativi` DESC;
```
