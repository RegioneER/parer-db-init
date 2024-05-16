# Guida alla prima installazione base dati Oracle 19c

Fonte template redazione documento:  https://www.makeareadme.com/.


# Descrizione

La seguente guida descrive i passaggi attraverso i quali è possibile importare o ripristinare i dump Oracle DB, con l'obbietivo di creare il modello E-R attraverso i seguenti schemi:

- SACER (progetti di riferimento: [Sacer](https://github.com/RegioneER/parer-sacer) e [SacerWS](https://github.com/RegioneER/parer-sacerws))
- SACER_IAM (progetto di riferimento [SacerIAM](https://github.com/RegioneER/parer-sacer-iam))
- SACER_LOG (progetto di riferimento [SacerIAM](https://github.com/RegioneER/parer-sacer-iam))
- SACER_PING (progetto di riferimento [Ping](https://github.com/RegioneER/parer-ping))
- SACER_RIC (progetto di riferimento [Dips](https://github.com/RegioneER/parer-dips))
- SACER_VERSO (progetto di riferimento [SacerIAM](https://github.com/RegioneER/parer-verso))

Al termine delle operazioni descritte in questo documento, verranno quindi creati gli schemi sopra elencati e un set di configurazioni al loro interno utili agli applicativi citati.

# Requisiti database

- installazione **Oracle DB** alla versione consigliata **19c**;
- la configurazin

# Import / ripristino dump

L'operazione di import / ripritino dei dump occorre eseguire i seguenti passaggi: 

- TODO .... unzip file;
- eseguire il seguente comando: 

  ```
  impdp userid="'/ as sysdba'" Directory=<dir logica che mappa la cartella fisica dove si trova il dumpset>   dumpFile=PARERT03.IMRF153643.%u.DMP Parallel=4  Remap_Tablespace=%:<metti_il_nome_del_ts_in_cui_vuoi_fare_andare_i_dati>  
  ```
  Opzionalmente:  
    - exclude=USER se i vari schemi sono già presenti nel DB di arrivo
    - omettere Remap_Tablespace se nel database Oracle di arrivo esistono già tutti i tablespace di cui il dump ha bisogno 


Al termine saranno presenti i seguenti schemi sopra elencati su l'istanza OracleDB opportunamente predisposta:

- SACER;
- SACER_IAM; 
- SACER_LOG;
- SACER_PING;
- SACER_RIC;
- SACER_VERSO.
  

# Supporto

Mantainer del progetto è [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it/).

# Contributi

Se interessati a crontribuire alla crescita del progetto potete scrivere all'indirizzo email <a href="mailto:areasviluppoparer@regione.emilia-romagna.it">areasviluppoparer@regione.emilia-romagna.it</a>.

# Credits

Progetto di proprietà di [Regione Emilia-Romagna](https://www.regione.emilia-romagna.it/) sviluppato a cura di [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it/).

# Licenza

Questo progetto è rilasciato sotto licenza GNU Affero General Public License v3.0 or later ([LICENSE.txt](LICENSE.txt)).

# Appendice

## Documentazione aggiuntiva

Alcuni riferimenti:

* Sito ParER: https://poloarchivistico.regione.emilia-romagna.it/
* Manuale di conservazione: https://poloarchivistico.regione.emilia-romagna.it/documentazione/documenti_open/manualeconservazione_v5-0.pdf/@@download/file/ManualeConservazione_v2.0.pdf 