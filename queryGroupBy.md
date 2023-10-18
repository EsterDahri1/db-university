## Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT COUNT(*) AS `iscritti_di_ogni_anno`, YEAR(`enrolment_date`) AS `anno_di_iscrizione` 
FROM `students` 
GROUP BY `anno_di_iscrizione`;
```

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql

```
## Calcolare la media dei voti di ogni appello d'esame
## Contare quanti corsi di laurea ci sono per ogni dipartimento