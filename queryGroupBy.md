## Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT COUNT(*) AS `iscritti_di_ogni_anno`, YEAR(`enrolment_date`) AS `anno_di_iscrizione` 
FROM `students` 
GROUP BY `anno_di_iscrizione`;
```

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT COUNT(*) AS `number_of_teachers`,  `office_address` 
FROM `teachers` 
GROUP BY `office_address`;
```
## Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT AVG(`vote`) AS `media_dei_voti`, `exam_id` 
FROM `exam_student` 
GROUP BY `exam_id`;
```

## Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT COUNT(*) AS `total_degrees`, `department_id` 
FROM `degrees` 
GROUP BY `department_id`;
```