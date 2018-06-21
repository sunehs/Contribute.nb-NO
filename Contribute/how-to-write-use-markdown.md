---
title: Slik bruker du Markdown for å skrive dokumenter
description: Denne artikkelen inneholder grunnleggende informasjon og referanseinformasjon for Markdown-språket som brukes for å skrive artikler for docs.microsoft.com.
ms.date: 07/13/2017
ms.openlocfilehash: dca1ccba2ae4ebd08b6039f5d780e7a7ac92e79f
ms.sourcegitcommit: 92aef5ea8bdd692c5c393d5c8f99b9e4f672ef2b
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238970"
---
# <a name="how-to-use-markdown-for-writing-docs"></a>Slik bruker du Markdown for å skrive dokumenter

Docs.microsoft.com-artikler som er skrevet i et lett markeringsspråk som kalles [Markdown](https://daringfireball.net/projects/markdown/), som er både lett å lese og lett å lære. På grunn av dette, har det raskt blitt en bransjestandard.

Fordi Docs-innhold lagres på GitHub, kan den bruke et overordnet sett for Markdown kalt [GitHub Flavored Markdown (GFM)](https://help.github.com/categories/writing-on-github/), som gir flere funksjoner for vanlige formateringsbehov. I tillegg implementerer Open Publishing Services (OPS) Markdig Markdown Parser. Markdig er svært kompatibel med GitHub Flavored Markdown (GFM), noe som gjør at det legges til funksjonalitet for å aktivere spesifikke funksjoner for Docs.

* Markdig er en rask, kraftig Markdown-prosessor for NET som kan utvides, og som er kompatibel med CommonMark.
* https://github.com/lunet-io/markdig
* Bedre støtte for fellesskap
* Bedre støtte for standarder

## <a name="markdown-basics"></a>Grunnleggende om Markdown

### <a name="headings"></a>Overskrifter

Hvis du vil opprette en overskrift, kan du bruke et nummertegn (#), som følger:

```markdown
    # This is heading 1
    ## This is heading 2
    ### This is heading 3
    #### This is heading 4
```

### <a name="bold-and-italic-text"></a>Fet og kursivert tekst

For å formatere tekst som **fet**, legger du ved to stjerner:

```markdown
    This text is **bold**.
```

For å formatere tekst som *kursiv*, legger du ved en stjerne:

```markdown
    This text is *italic*.
```

For å formatere tekst som både ***fet og kursiv***, legger du ved tre stjerner:

```markdown
    This is text is both ***bold and italic***.
```

### <a name="lists"></a>Lister

#### <a name="unordered-list"></a>Usortert liste

Hvis du vil formatere en ikke-sortert/punktmerket liste, kan du bruke stjerner eller bindestreker. For eksempel følgende markdown:

```markdown
- List item 1
- List item 2
- List item 3
```

blir gjengitt som:

- Listeelement 1
- Listeelement 2
- Listeelement 3

Hvis du vil neste en liste i en annen liste, rykker du inn de underordnede elementene. For eksempel følgende markdown:

```markdown
- List item 1
  - List item A
  - List item B
- List item 2
```

blir gjengitt som:

- Listeelement 1
  - Listeelement A
  - Listeelement B
- Listeelement 2

#### <a name="ordered-list"></a>Sortert liste

Hvis du vil formatere en liste som er sortert/trinnvis, kan du bruke tilsvarende tall. For eksempel følgende markdown:

```markdown
1. First instruction
2. Second instruction
3. Third instruction
```

blir gjengitt som:

1. Første instruksjon
2. Andre instruksjon
3. Tredje instruksjon

Hvis du vil neste en liste i en annen liste, rykker du inn de underordnede elementene. For eksempel følgende markdown:

```markdown
1. First instruction
    1. Sub-instruction
    2. Sub-instruction
2. Second instruction
```

blir gjengitt som:

1. Første instruksjon
    1. Underinstruksjon
    2. Underinstruksjon
2. Andre instruksjon

### <a name="tables"></a>Tabeller

Tabeller er ikke en del av Markdown-kjernespesifikasjonen, men GFM støtter dem. Du kan opprette tabeller ved hjelp av vertikal strek (|) og bindestreker (-). Bindestreker oppretter hver kolonneoverskrift, mens vertikale streker skiller hver kolonne. Ta med en tom linje før tabellen slik at den gjengis riktig.

For eksempel følgende markdown:

```markdown
| Fun                  | With                 | Tables          |
| :------------------- | -------------------: |:---------------:|
| left-aligned column  | right-aligned column | centered column |
| $100                 | $100                 | $100            |
| $10                  | $10                  | $10             |
| $1                   | $1                   | $1              |
```

blir gjengitt som:

| Moro                  | Med                 | Tabeller          |
| :------------------- | -------------------: |:---------------:|
| venstrejustert kolonne  | høyrejustert kolonne | midtstilt kolonne |
| $100                 | $100                 | $100            |
| $10                  | $10                  | $10             |
| $1                   | $1                   | $1              |

For mer informasjon om å opprette tabeller, se:

- Markdig [-funksjonen for tekstbryting i tabeller](#table-wrapping) som kan hjelpe deg med formatering av brede tabeller
- Githubs [Organisere informasjon med tabeller](https://help.github.com/articles/organizing-information-with-tables/)
- Webappen [Markdown-tabellgenerator](https://www.tablesgenerator.com/markdown_tables) 
- [Adam Pritchards Markdown-jukseark](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#wiki-tables)
- [Michel Fortins Markdown-ekstra](https://michelf.ca/projects/php-markdown/extra/#table)
- [Konverter HTML-tabeller til Markdown](https://jmalarcon.github.io/markdowntables/)

### <a name="links"></a>Koblinger

Markdown-syntaksen for en innebygd kobling består av `[link text]`-delen, som er teksten som blir hyperkoblet, etterfulgt av `(file-name.md)`-delen, som er navnet på URL-adressen eller en fil som er koblet til:

 `[link text](file-name.md)`

Hvis du vil ha mer informasjon om kobling, se:

- [Markdown-syntaksveiledning](https://daringfireball.net/projects/markdown/syntax#link) for detaljer om Markdowns støtte for kobling.
- [Koblinger](how-to-write-links.md)-delen i denne veiledningen for informasjon om ekstra koblingsfeltsyntaks som Markdig gir.

### <a name="code-snippets"></a>Kodesnutter

Markdown støtter plasseringen av kodesnutter, både innebygd i en setning og som en separat «inngjerdet» blokk mellom setninger. For detaljer, se:

- [Markdowns innebygde støtte for kodeblokker](https://daringfireball.net/projects/markdown/syntax#precode)
- [GFM-støtte for kodeinngjerding og syntaksutheving](https://help.github.com/articles/creating-and-highlighting-code-blocks/)

Inngjerdede kodeblokker er en enkel måte å aktivere syntaksutheving for kodesnuttene dine. Det generelle formatet for inngjerdede kodeblokker er:

    ```alias
    ...
    your code goes in here
    ...
    ```

Aliaset etter de første tre tegnene for backtick (') definerer syntaksutheving som skal brukes. Følgende er en liste av ofte brukte programmeringsspråk i Docs-innhold og tilsvarende etikett:

Disse språkene har støtte for egendefinert navn, og de fleste har språkutheving.

|Navn|Markdown Label|
|-----|-------|
|.NET-konsoll|dotnetcli|
|ASP.NET (C#)|aspx-csharp|
|ASP.NET (VB)|aspx-vb|
|AzCopy|azcopy|
|Azure CLI|azurecli|
|Azure PowerShell|azurepowershell|
|C++|cpp|
|C++/CX|cppcx|
|C++/WinRT|cppwinrt|
|C#|csharp|
|CSHTML|cshtml|
|DAX|dax|
|F#|fsharp|
|Go|go|
|HTML|html|
|HTTP|http|
|Java|java|
|JavaScript|javascript|
|JSON|json|
|Markdown|md|
|NodeJS|nodejs|
|Objective-C|objc|
|OData|odata|
|PHP|php|
|Power Apps-formel|powerappsfl|
|PowerShell|powershell|
|Python|python|
|Q#|qsharp|
|Ruby|ruby|
|SQL|sql|
|Swift|swift|
|TypeScript|typescript|
|VB|vb|
|VSTS CLI|vstscli|
|XAML|xaml|
|XML|xml|

#### <a name="example-c"></a>Eksempel: C\#

__Markdown__

    ```csharp
    // Hello1.cs
    public class Hello1
    {
        public static void Main()
        {
            System.Console.WriteLine("Hello, World!");
        }
    }
    ```

__Gjengi__

```csharp
// Hello1.cs
public class Hello1
{
    public static void Main()
    {
        System.Console.WriteLine("Hello, World!");
    }
}
```

#### <a name="example-sql"></a>Eksempel: SQL

__Markdown__

    ```sql
    CREATE TABLE T1 (
      c1 int PRIMARY KEY,
      c2 varchar(50) SPARSE NULL
    );
    ```

__Gjengi__

```sql
CREATE TABLE T1 (
  c1 int PRIMARY KEY,
  c2 varchar(50) SPARSE NULL
);
```

## <a name="ops-custom-markdown-extensions"></a>OPS egendefinerte markdown-utvidelser

> [!NOTE]
> Open Publishing Services (OPS) implementerer en Markdig-analyse for Markdown som er svært kompatibel med GitHub Flavored Markdown (GFM). Markdig legger til en del funksjonalitet gjennom Markdown-utvidelser. Følgelig er valgte artikler fra den komplette OPS-oppretterveiledningen inkludert i denne veiledningen som referanse. (Se for eksempel Markdig- og Markdown-utvidelser og Kodesnutter i innholdsfortegnelsen.)

Docs-artiklene bruker GFM for mesteparten av artikkelformatering, som avsnitt, koblinger, lister og overskrifter. For å oppnå rikere formatering kan artikler bruke Markdig-funksjoner som:

- Notatblokker
- Inkluderinger
- Velgere
- Innebygde videoer
- Kodesnutter/prøver

For en fullstendig liste kan du se Markdig- og Markdown-utvidelser og Kodesnutter i innholdsfortegnelsen.

### <a name="note-blocks"></a>Notatblokker

Du kan velge mellom fire typer notatblokker for å trekke oppmerksomheten mot et bestemt innhold:

- OBS
- ADVARSEL
- TIPS
- VIKTIG

Merk at notatblokker bør brukes sparsomt fordi de kan virke forstyrrende. Selv om de også støtter kodeblokker, bilder, lister og koblinger, kan du prøve å holde notatblokkene enkle.

### <a name="includes"></a>Inkluderinger

Når du har tekst- eller bildefiler som kan brukes på nytt, og som skal tas med i artikkelfiler, kan du bruke en referanse til filen som skal inkluderes via funksjonen for Markdig-filinkludering. Denne funksjonen ber OPS om å inkludere filen i artikkelfilen ved buildtid, noe som gjør den til en del av den publiserte artikkelen. Tre typer inkluderinger er tilgjengelige for å hjelpe deg med å bruke innhold på nytt:

- Innebygd: Bruke en vanlig tekstsnutt innebygd i en annen setning.
- Blokk: Bruke en hel Markdown-fil på nytt som en blokk, nestet i en del av en artikkel.
- Bilde: Dette er slik standard bildeinkludering implementeres i Docs.

En innebygd eller blokk-inkludering er bare en enkel Markdown-fil (.md). Den kan inneholde en hvilken som helst gyldig Markdown. Alle inkluderte Markdown-filer skal plasseres i en [vanlig `/includes` underkatalog](git-github-fundamentals.md#includes-subdirectory) i roten av repositoriet. Når artikkelen er publisert, blir den inkluderte filen sømløst integrert i den.

Her er krav og hensyn for inkluderinger:

- Bruk inkluderinger når du trenger at den samme teksten vises i flere artikler.
- Bruk blokkinkludering for betydelige mengder innhold – et avsnitt eller to, en delt prosedyre eller en delt inndeling. Ikke bruk dem til noe mindre enn en setning.
- Inkluderinger gjengis ikke i GitHub-visningen av artikkelen fordi de er avhengige av Markdig-utvidelser. De gjengis kun etter publisering.
- Kontroller at all teksten i en inkludering er skrevet i fullstendige setninger eller uttrykk som ikke avhenger av foregående tekst eller påfølgende tekst i artikkelen som refererer til inkluderingen. Å ignorere denne veiledningen fører til en uoversettelig streng i artikkelen som bryter den lokaliserte opplevelsen.
- Ikke bygg inn inkluderinger med andre inkluderinger. De støttes ikke.
- Plasser media-filer i en mediemappe som er spesifikk for inkluderinger-undermappe – for eksempel, `<repo>` /inkluderinger/media-mappen. Media-katalogen bør ikke inneholde noen bilder i roten. Hvis inkluderingen ikke har bilder, er det ikke nødvendig med en korresponderende media-katalog.
- Som med vanlige artikler, må du ikke dele medier mellom inkluderingsfiler. Bruk en separat fil med et unikt navn for hver inkludering og artikkel. Lagre media-filen i mediemappen som er knyttet til inkluderingen.
- Ikke bruk inkluderingen som det eneste innholdet i en artikkel.  Inkluderinger er ment å utfylle innholdet i resten av artikkelen.

### <a name="selectors"></a>Velgere

Bruk velgere i tekniske artikler når du oppretter flere utgaver av den samme artikkelen for å adressere forskjeller i implementeringen på tvers av teknologier og plattformer. Dette er vanligvis mest aktuelt for vårt mobile plattforminnhold for utviklere. Det finnes for øyeblikket to forskjellige typer velgere i Markdig, en enkeltvelger og en multivelger.

Fordi den samme Markdown-velgeren går i hver artikkel i valget, anbefaler vi å sette velgeren for artikkelen din i en inkludering. Deretter kan du referere til den inkluderingen i alle artikler som bruker samme velgeren.

### <a name="code-snippets"></a>Kodesnutter

Markdig støtter avansert inkludering av koden i en artikkel via kodesnuttutvidelsen den bruker. Den gir avansert gjengivelse som bygger på GFM-funksjoner som valg av programmeringsspråk og syntaksfarger, i tillegg til flotte funksjoner som:

- Inkludering av sentraliserte eksempler/kodesnutter fra et eksternt repositorium.
- Fanebasert brukergrensesnitt for å vise flere versjoner av kodeeksempler på forskjellige språk.

## <a name="gotchas-and-troubleshooting"></a>Feller og feilsøking

### <a name="alt-text"></a>Alt-tekst

Alternativ tekst som inneholder understrekingstegn gjengis ikke riktig. For eksempel, i stedet for å bruke dette:

```markdown
![ADextension_2FA_Configure_Step4] (./media/bogusfilename/ADextension_2FA_Configure_Step4.PNG)
```

Unngå understrekingstegn som dette:

```markdown
![ADextension\_2FA\_Configure\_Step4] (./media/bogusfilename/ADextension_2FA_Configure_Step4.PNG)
```

### <a name="apostrophes-and-quotation-marks"></a>Apostrofer og anførselstegn

Hvis du kopierer fra Word til et redigeringsprogram for Markdown, kan teksten inneholde «smarte» (doble) apostrofer eller anførselstegn. Disse må være kodet eller endret til enkle apostrofer eller anførselstegn. Ellers ender du opp med ting som dette når filen er blitt publisert: pcâ€™s

Her er kodingen for «smarte»-versjoner av disse skilletegnene:

- Venstre (innledende) anførselstegn: `&#8220;`
- Høyre (avsluttende) anførselstegn: `&#8221;`
- Høyre (avsluttende) enkle anførselstegnet eller apostrof: `&#8217;`
- Venstre (innledende) enkelt anførselstegn (brukes sjelden): `&#8216;`

### <a name="angle-brackets"></a>Vinkelparenteser

Hvis du bruker vinkelparenteser i teksten (ikke kode) i filen, for eksempel for å angi en plassholder – må du kode vinkelparentesene manuelt. Ellers tror Markdown at de er ment å være en HTML-kode.

Kode for eksempel `<script name>` som `&lt;script name&gt;`

## <a name="see-also"></a>Se også

### <a name="markdown-resources"></a>Markdown-ressurser

- [Introduksjon til Markdown](https://daringfireball.net/projects/markdown/syntax)
- [Docs Markdown-jukseark](./media/documents/markdown-cheatsheet.pdf?raw=true)
- [Grunnleggende om GitHubs Markdown](https://help.github.com/articles/markdown-basics/)
