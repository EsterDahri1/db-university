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

```

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql

```

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql

```

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql

```

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```sql

```
