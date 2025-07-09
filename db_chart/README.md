# db-university

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più `Corsi di Laurea` (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi `Corsi` (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi `Insegnanti`;
- ogni Corso prevede più `appelli d'Esame`;
- ogni `Studente` è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il `voto ottenuto`, anche se non sufficiente.

### Dipartimento
- id_dipartimento (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)*
- nome *NOT NULL VARCHAR(50)*
- sede *VARCHAR(50)*
- telefono *CHAR(9)*
- email *VARCHAR(50)*

### Corso di Laurea
- id_corso_laurea (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)*
- id_dipartimento (FK) *NOT NULL VARCHAR(10)*
- nome *NOT NULL VARCHAR(50)*
- cfu *TINYINT*
- durata *TINYINT*

## Studente
- id_studente (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)*
- id_corso_laurea (FK) *NOT NULL VARCHAR(10)*
- nome *NOT NULL VARCHAR(50)*
- cognome *NOT NULL VARCHAR(50)*
- email *VARCHAR(50)*
- anno_iscrizione *YEAR*


### Corso
- id_corso (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)*
- id_corso_laurea (FK) *NOT NULL VARCHAR(10)*
- nome *NOT NULL VARCHAR(50)*
- cfu *TINYINT*
- durata *TINYINT*

## Insegnante
- id_insegnante (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)*
- nome *NOT NULL VARCHAR(50)*
- cognome *NOT NULL VARCHAR(50)*
- email *VARCHAR(50)*
- telefono *CHAR(9)*

## Appello d'Esame
- id_appello (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)* 
- id_corso (FK) *NOT NULL VARCHAR(10)*
- id_studente (FK) *NOT NULL VARCHAR(10)*
- data_appello *DATE*

## Voto esame
- id_voto (PK) *NOT NULL AUTO_INCREMENT VARCHAR(10)*
- id_studente (FK) *NOT NULL VARCHAR(10)*
- id_appello (FK) *NOT NULL VARCHAR(10)*
- voto *TINYINT*
