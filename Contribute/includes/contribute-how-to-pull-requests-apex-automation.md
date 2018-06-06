Kommentarautomatisering gjør at brukere på lesenivå (brukere som ikke har skrivetillatelser i en repo) kan utføre en handling på skrivenivå ved å tilordne den aktuelle etiketten til en pull-forespørsel. Hvis du arbeider i et repositorium der kommentarautomatisering er implementert, kan du bruke hashtagkommentarer som er oppført i tabellen nedenfor til å tilordne etiketter, endre etiketter eller lukke en pull-forespørsel. Microsoft-ansatte vil også bli varslet via e-post for gjennomgang og godkjenning av offentlige PR-repositorier når endringer er foreslått til artikler som du er forfatter for.


| Hashtagkommentar | Hva den gjør | Repo-tilgjengelighet |
| --- | --- | --- |
| #sign-off |Når forfatteren av en artikkel skriver **#sign-off** kommentar i kommentar-strømmen, tilordnes **klar til sammenslåing**-etiketten. Denne etiketten lar anmelderne i repo vite når en pull-forespørsel er klar for gjennomgang/sammenslåing. |Offentlig og privat |
| #sign-off |Hvis en bidragsyter som *ikke* er oppført forfatter forsøker å godkjenne en offentlig pull-forespørsel ved hjelp av **#sign-off**-kommentar, skrives en melding til pull-forespørselen som indikerer at bare forfatteren kan tildele etiketten. |Offentlig |
| #hold-off |Forfattere kan skrive inn **#hold-off** i en PR-kommentar for å fjerne **klar til å slå sammen**-etiketten – i tilfelle de endrer mening eller gjør en feil. I privat repo tilordnes dette **ikke slå sammen**-etiketten. |Offentlig og privat |
| #please-close |Forfattere kan skrive inn **#please-close** i kommentarstrømmen for å lukke pull-forespørselen hvis de ikke vil at disse endringene skal slås sammen. |Offentlig |
