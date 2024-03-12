# 1 Selezionare tutti gli studenti nati nel 1990
```
SELECT * FROM `students` 
    WHERE `date_of_birth` 
        LIKE '1990%'

```

# 2 Selezionare tutti i corsi che valgono più di 10 crediti
```
SELECT * FROM `courses` 
    WHERE `cfu` >= '10'
```

# 3 Selezionare tutti gli studenti che hanno più di 30 anni
```
SELECT * FROM `students` 
    WHERE `date_of_birth` <= '1993%';
```

# 4 Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea
```
SELECT * FROM `courses` 
    WHERE `period` 
        LIKE 'I semestre';
```

# 5 Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020
```
SELECT * FROM `exams` 
    WHERE `date` 
        LIKE '2020-06-20' AND `hour` >= '14:00:00';
```

# 6 Selezionare tutti i corsi di laurea magistrale
```
SELECT * FROM `degrees` 
    WHERE `name` 
        LIKE 'Corso di Laurea Magistrale%';
```

# 7 Da quanti dipartimenti è composta l'università?
```
SELECT COUNT(*) AS `Numero_di_Dipartimenti` FROM `departments`;
```

# 8 Quanti sono gli insegnanti che non hanno un numero di telefono?
```
SELECT COUNT(*) AS `Senza_Numero` FROM `teachers` WHERE `phone` IS NULL;
```