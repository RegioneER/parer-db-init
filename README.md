# Guida alla prima installazione base dati Oracle 19c

Fonte template redazione documento:  https://www.makeareadme.com/.

# Descrizione

La seguente guida descrive i passaggi attraverso i quali è possibile importare o ripristinare i dump Oracle DB contenti i modelli E-R utilizzati delle applicazioni ParER.
Verranno creati nell'istanza Oracle opportunamente predisposta i seguenti schemi:

- SACER ([Sacer 9.3.0](https://github.com/RegioneER/parer-sacer/releases/tag/sacer-jboss-9.3.0) e [SacerWS 5.2.0](https://github.com/RegioneER/parer-sacerws](https://github.com/RegioneER/parer-sacerws/releases/tag/sacerws-5.2.0)))
- SACER_IAM ([SacerIAM 5.2.0](https://github.com/RegioneER/parer-sacer-iam/releases/tag/saceriam-jboss-5.2.0))
- SACER_LOG ([SacerIAM 5.2.0](https://github.com/RegioneER/parer-sacer-iam/releases/tag/saceriam-jboss-5.2.0))
- SACER_PING ([Ping](https://github.com/RegioneER/parer-ping))
- SACER_RIC (applicazione non presente su GitHub per il momento)
- SACER_VERSO ([Verso](https://github.com/RegioneER/parer-verso))

## Pre requisito

Al fine di estrarre i file .DUMP è scaricare di "7 zip" [https://www.7-zip.org/download.html](https://www.7-zip.org/download.html) con il quale estrarre i file originali.


# Requisiti database

- installazione **Oracle DB** alla versione consigliata **19c**;

# Import / ripristino dump

L'operazione di import / ripritino dei dump occorre eseguire i seguenti passaggi: 

- estrazione dei file dump attraverso il tool [7z](https://www.7-zip.org/download.html) vedi [ora-dump/Oracle19c_dump.7z.001](ora-dump/Oracle19c_dump.7z.001);
  
  **Nota**: nella directory [ora-dump](ora-dump) sono presenti più file Oracle19c_dump.Zz.00*, per ottenere l'export dei file originali è sufficiente estrarre il file denominato [Oracle19c_dump.7z.001](ora-dump/Oracle19c_dump.7z.001), è automaticamente verranno estratti anche tutti gli altri

- una volta estratti i file .DMP su apposita directory, eseguire il seguente comando: 

  ```
  impdp userid="'/ as sysdba'" Directory=<dir logica che mappa la cartella fisica dove si trova il dumpset>   dumpFile=Oracle19c_dump.%u.DMP Parallel=4  Remap_Tablespace=%:<metti_il_nome_del_ts_in_cui_vuoi_fare_andare_i_dati>  
  ```
  Opzionalmente:  
    - exclude=USER se i vari schemi sono già presenti nel DB di arrivo
    - omettere Remap_Tablespace se nel database Oracle di arrivo esistono già tutti i tablespace di cui il dump ha bisogno 


Al termine, su istanza OracleDB opportunamente predisposta, saranno presenti i seguenti schemi:

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

Tool utilizzati: 

* 7 zip: https://www.7-zip.org/download.html/
* Oracle DB : https://www.oracle.com/it/database/
