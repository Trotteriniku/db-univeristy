# SELECT EX

## 1. Selezionare tutti gli studenti nati nel 1990 (160)

```sql
 SELECT \*
  FROM `students`
  WHERE YEAR(`date_of_birth`) = '1990';
```

## 2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

```sql
 SELECT \*
  FROM `courses`
  WHERE `cfu` > 10 ;
```

## 3. Selezionare tutti gli studenti che hanno più di 30 anni

```sql
 SELECT \*
  FROM `students`
  WHERE DATEDIFF(CURRENT_DATE(), date_of_birth) / 365 > 30;
```

## 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

```sql
 SELECT \*
  FROM `courses`
  WHERE `period` = 'I semestre' AND `year` = '1';
```

## 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

```sql
 SELECT `date` AS `exam_on_2020-06-20_after_14:00`
 FROM `exams`
 WHERE `hour`> '14:00'
 AND `date` = '2020-06-20';
```

## 6. Selezionare tutti i corsi di laurea magistrale (38)

```sql
 SELECT `name`,`department_id`
  FROM `degrees`
  WHERE `level` = 'magistrale';
```

## 7. Da quanti dipartimenti è composta l'università? (12)

```sql
 SELECT COUNT(\*) AS `number_of_departments`
  FROM `departments` ;
```

## 8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```sql
  SELECT COUNT(\*) AS `teachers_whitout_phoneNumber`
  FROM `teachers`
  WHERE `phone` IS NULL ;
```

# GROUP BY EX

## 1. Contare quanti iscritti ci sono stati ogni anno

```sql
 SELECT COUNT(\*) AS `number_of_attendent_for_year`,
  YEAR(`enrolment_date`) AS `registration_date`
  FROM `students`
  GROUP BY `registration_date`;
```

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
 SELECT COUNT(\*) AS `teachers_in_the_same_office`,
  `office_address` AS `teachers_office`
  FROM `teachers`
  GROUP BY `office_address`;
```

## 3. Calcolare la media dei voti di ogni appello d'esame

```sql
  SELECT AVG(`vote`) AS `vote_average`,
  `exam_id` AS `selected_exam`
  FROM `exam_student`
  GROUP BY `selected_exam`;
```

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT COUNT(*) AS `number_of_degrees_for_departments`,
`department_id` AS `department_selected`
FROM  `degrees`
GROUP BY `department_selected`;
```
