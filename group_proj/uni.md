# db-university
-------------------------------------
## universita
- id  
- Laboratori 
- presenza 
- remoto 
- tipologia  (: magistrale triennale)
- lingua |varchart(5 es: it-IT)
- note 
- about_us  
- privata | default(0)
- attivita extra-curricolari 



## diparimento 
- id 
- sede 
- corso di laurea_id
- capo diparimento


## corso di laurea 
- id 
- nome 


## corso 
- id
- crediti 
- materia  
- esami (n esami )
- obbligo_frequenza  (0-1)
- insegnate 
- tutor
- materiale  
- disponibile 

## insegnate  
- id
- nome_cognome  
- ruolo 
- docente_visitatore 


## studente
- id
- nome_cognome  
- facolta 
- N_matricola (solo numeri )| increment unique 
- email 
- moodle 
- conto_bancario 
- libretto (media in 30)
- media_tot (media in 100)
- titolo_tesi 


## esami 
- crediti 
- scelta 
- tipologia 
- nome_corso 