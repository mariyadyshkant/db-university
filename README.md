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
- id_dipartimento (PK)
- nome 
- sede
- telefono
- email

### Corso di Laurea
- id_corso_laurea (PK)
- id_dipartimento (FK)
- nome
- cfu
- durata

### Corso
- id_corso (PK)
- id_corso_laurea (FK)
- nome
- cfu
- durata

## Insegnante
- id_insegnante
- nome
- cognome
- email
- telefono

## Appello d'Esame
- id_appello
- data
- id_corso (FK)

## Studente
- id_studente
- nome
- cognome
- email
- anno iscrizione

## Voto esame
- id_voto
- id_studente (FK)
- id_appello (FK)
- voto
- data
