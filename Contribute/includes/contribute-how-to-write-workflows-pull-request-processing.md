## <a name="pull-request-processing"></a>Behandling av pull-forespørsel

Den forrige delen tok deg gjennom prosessen med å sende inn foreslåtte endringer ved å pakke dem i en ny pull-forespørsel (PR) som legges til målleverandørrepositoriets PR-kø. En pull-forespørsel muliggjør GitHubs samarbeidsmodell ved å be om at endringer fra din arbeidsgren trekkes og slås sammen til en annen gren. I de fleste tilfeller er den andre grenen standard/hoved-grenen i hovedrepositoriet.

### <a name="validation"></a>Validering

Før din pull-forespørsel kan flettes inn i sin mål-gren, kan det være nødvendig å kjøre den gjennom en eller flere PR-valideringsprosesser. Valideringsprosesser kan variere avhengig av omfanget av foreslåtte endringer og reglene for mål-repositoriet. Etter at pull-forespørselen er sendt, kan du forvente at et eller flere av følgende skjer:

- **Fusjonerbarhet**: en GitHub-fusjonerbarhetstest skjer først, for å bekrefte om de foreslåtte endringene i grenen er i konflikt med målgrenen. Hvis pull-forespørselen angir at denne testen mislyktes, må du avstemme innholdet som forårsaker sammenslåingskonflikten før behandling kan fortsette.
- **CLA**: Hvis du bidrar til et offentlig repositorium og ikke er en Microsoft-ansatt, kan du, avhengig av størrelsen på de foreslåtte endringene, bli bedt om å fullføre en kort Bidragslisensvtale (CLA) første gang du sender en pull-forespørsel til repositoriet. Når CLA-trinnet er ferdig, behandles pull-forespørselen.
- **Merking**: Etiketter brukes automatisk på din pull-forespørsel for å angi statusen for pull-forespørselen når den passerer gjennom valideringsarbeidsflyten. Nye pull-forespørsler kan for eksempel automatisk få «ikke slå sammen»-etiketten, noe som indikerer at pull-forespørselen ikke ennå har fullført trinnene for validering, gjennomgang og godkjenning.
- **Validering og build**: Automatiserte kontrollerer verifiserer om endringene dine består valideringstester. Valideringstestene kan gi advarsler eller feil, som krever at man gjør endringer i en eller flere filer i pull-forespørselen før den kan slås sammen. Valideringstestresultatene legges til som en kommentar i pull-forespørselen for gjennomgang, og de kan sendes til deg via e-post.
- **Sette opp**: Artikkelsidene som berøres av endringene dine distribueres automatisk til et oppsettmiljø for gjennomgang etter vellykket validering og build. Forhåndsvisning av URL-adresser vises i en PR-kommentar.
- **Automatisk sammenslåing**: Pull-forespørselen kan slås sammen automatisk hvis den passer valideringstestene og visse kriterier. I dette tilfellet trenger du ikke gjøre noe mer.

### <a name="review-and-sign-off"></a>Gjennomgang og godkjenning

Etter at all PR-behandling fullføres, bør du gå gjennom resultatene (PR-kommentarer, forhåndsvisning av URL-er, osv.) for å fastslå om det er nødvendig med flere endringer i filene før du godkjenner sammenslåing. Hvis en PR-anmelder har gått gjennom din pull-forespørsel, kan de også gi tilbakemelding via kommentarer hvis det er gjenværende problemer/spørsmål som må løses før sammenslåingen.

[!INCLUDE[contribute-how-to-pull-requests-apex-automation.md](contribute-how-to-pull-requests-apex-automation.md)]

Når pull-forespørselen er problemfri og godkjent, slås endringene dine sammen igjen i den overordnede grenen og pull-forespørselen lukkes.

### <a name="publishing"></a>Publisering

Husk at pull-forespørselen din må slås sammen av en PR-anmelder før endringene kan tas med i den neste planlagte publiseringen. Pull-forespørsler blir vanligvis gått gjennom/slått sammen i innsendingsrekkefølgen. Hvis din pull-forespørsel krever sammenslåing for en spesifikk publiseringskjøring, må du jobbe med PR-anmelderen før tiden for å sørge for at sammenslåing skjer før publisering.

Etter at bidragene dine godkjennes og slås sammen, plukker publiseringsprosessen docs.microsoft.com dem opp. Avhengig av teamet som administrerer repositoriet du bidrar til, kan publiseringstidene variere. Artikler publisert under følgende baner distribueres normalt omtrent 10:30 og 15:30 Stillehavstid, mandag–fredag:

- https://docs.microsoft.com/azure/
- https://docs.microsoft.com/aspnet/
- https://docs.microsoft.com/dotnet/
- https://docs.microsoft.com/enterprise-mobility-security

Det kan ta opptil 45 minutter før artikler vises på nett etter publisering. Etter at artikkelen er publisert, kan du kontrollere endringene på den aktuelle URL-adressen: `https://docs.microsoft.com/<path-to-your-article-without-the-md-extension>`.
