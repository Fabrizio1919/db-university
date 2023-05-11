<!-- Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. -->






TABELLA Dipartimenti
id_dipartimento (chiave primaria)
nome_dipartimento


TABELLA Corsi_di_Laurea
id_corso_laurea (chiave primaria)
nome_corso_laurea
id_dipartimento (chiave esterna che fa riferimento all'id_dipartimento della tabella Dipartimenti)


TABELLA Corsi
id_corso (chiave primaria)
nome_corso
id_corso_laurea (chiave esterna che fa riferimento all'id_corso_laurea della tabella Corsi_di_Laurea)


TABELLA Insegnanti
id_insegnante (chiave primaria)
nome_insegnante
cognome_insegnante



TABELLA Corsi_Insegnanti
id_corso (chiave esterna che fa riferimento all'id_corso della tabella Corsi)
id_insegnante (chiave esterna che fa riferimento all'id_insegnante della tabella Insegnanti)



TABELLA Appelli 
id_appello (chiave primaria)
data_appello
id_corso (chiave esterna che fa riferimento all'id_corso della tabella Corsi)



TABELLA Studenti
id_studente (chiave primaria)
nome_studente
cognome_studente
id_corso_laurea (chiave esterna che fa riferimento all'id_corso_laurea della tabella Corsi_di_Laurea)



TABELLA Iscrizioni
id_iscrizione (chiave primaria)
id_studente (chiave esterna che fa riferimento all'id_studente della tabella Studenti)
id_appello (chiave esterna che fa riferimento all'id_appello della tabella Appelli)



TABELLA Voti
id_voto (chiave primaria)
voto
id_iscrizione (chiave esterna che fa riferimento all'id_iscrizione della tabella Iscrizioni)