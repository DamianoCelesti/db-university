# db-university
ex - Query SELECT
1. Selezionare tutti gli studenti nati nel 1990 (160)

SELECT * FROM students
WHERE YEAR(date_of_birth) = 1990


2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT * FROM courses
WHERE cfu > 10


3. Selezionare tutti gli studenti che hanno più di 30 anni

SELECT * FROM students
WHERE TIMESTAMPDIFF(YEAR, date_of_birth, CURDATE()) > 30


4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)

SELECT * FROM courses
WHERE YEAR = 1 AND period = 'I semestre'


5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)

SELECT * FROM exams
WHERE DATE = '2020-06-20' AND HOUR(hour) >= 14


6. Selezionare tutti i corsi di laurea magistrale (38)

SELECT * FROM degrees
WHERE level = 'magistrale'


7. Da quanti dipartimenti è composta l'università? (12)

SELECT * FROM departments


8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT * FROM teachers
WHERE phone IS NULL

ex Query GROUP

1. Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(enrolment_date), COUNT(*)
FROM students
GROUP BY YEAR(enrolment_date)

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT office_address, COUNT(*)
FROM teachers
GROUP BY office_address

3. Calcolare la media dei voti di ogni appello d'esame

SELECT exam_id, AVG(vote)
FROM exam_student
GROUP BY exam_id

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT department_id, COUNT(*) 
FROM degrees
GROUP BY department_id