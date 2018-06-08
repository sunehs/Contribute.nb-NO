---
title: Slik bruker du Markdown for å skrive dokumenter
description: Denne artikkelen inneholder grunnleggende informasjon og referanseinformasjon for Markdown-språket som brukes for å skrive artikler for docs.microsoft.com.
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 07/13/2017
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: 041398361aef90c44bdf3a0dad4aaa2d40a38289
ms.sourcegitcommit: 782b689882cce3ce07f5613763322989f2d0d63f
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/05/2018
ms.locfileid: "34469950"
---
# <a name="how-to-use-markdown-for-writing-docs"></a><span data-ttu-id="efab1-103">Slik bruker du Markdown for å skrive dokumenter</span><span class="sxs-lookup"><span data-stu-id="efab1-103">How to use Markdown for writing Docs</span></span>

<span data-ttu-id="efab1-104">Docs.microsoft.com-artikler som er skrevet i et lett markeringsspråk som kalles [Markdown](https://daringfireball.net/projects/markdown/), som er både lett å lese og lett å lære.</span><span class="sxs-lookup"><span data-stu-id="efab1-104">Docs.microsoft.com articles are written in a lightweight markup language called [Markdown](https://daringfireball.net/projects/markdown/), which is both easy to read and easy to learn.</span></span> <span data-ttu-id="efab1-105">På grunn av dette, har det raskt blitt en bransjestandard.</span><span class="sxs-lookup"><span data-stu-id="efab1-105">Because of this, it has quickly become an industry standard.</span></span>

<span data-ttu-id="efab1-106">Fordi Docs-innhold lagres på GitHub, kan den bruke et overordnet sett for Markdown kalt [GitHub Flavored Markdown (GFM)](https://help.github.com/categories/writing-on-github/), som gir flere funksjoner for vanlige formateringsbehov.</span><span class="sxs-lookup"><span data-stu-id="efab1-106">Because Docs content is stored in GitHub, it can use a superset of Markdown called [GitHub Flavored Markdown (GFM)](https://help.github.com/categories/writing-on-github/), which provides additional functionality for common formatting needs.</span></span> <span data-ttu-id="efab1-107">I tillegg implementerer Open Publishing Services (OPS) Markdig Markdown Parser.</span><span class="sxs-lookup"><span data-stu-id="efab1-107">Additionally, Open Publishing Services (OPS) implements Markdig Markdown Parser.</span></span> <span data-ttu-id="efab1-108">Markdig er svært kompatibel med GitHub Flavored Markdown (GFM), noe som gjør at det legges til funksjonalitet for å aktivere spesifikke funksjoner for Docs.</span><span class="sxs-lookup"><span data-stu-id="efab1-108">Markdig is highly compatible with GitHub Flavored Markdown (GFM), adding functionality to enable Docs-specific features.</span></span>

* <span data-ttu-id="efab1-109">Markdig er en rask, kraftig Markdown-prosessor for NET som kan utvides, og som er kompatibel med CommonMark.</span><span class="sxs-lookup"><span data-stu-id="efab1-109">Markdig is a fast, powerful, CommonMark compliant, extensible Markdown processor for .NET.</span></span>
* https://github.com/lunet-io/markdig
* <span data-ttu-id="efab1-110">Bedre støtte for fellesskap</span><span class="sxs-lookup"><span data-stu-id="efab1-110">Better community support</span></span>
* <span data-ttu-id="efab1-111">Bedre støtte for standarder</span><span class="sxs-lookup"><span data-stu-id="efab1-111">Better standards support</span></span>

## <a name="markdown-basics"></a><span data-ttu-id="efab1-112">Grunnleggende om Markdown</span><span class="sxs-lookup"><span data-stu-id="efab1-112">Markdown basics</span></span>

### <a name="headings"></a><span data-ttu-id="efab1-113">Overskrifter</span><span class="sxs-lookup"><span data-stu-id="efab1-113">Headings</span></span>

<span data-ttu-id="efab1-114">Hvis du vil opprette en overskrift, kan du bruke et nummertegn (#), som følger:</span><span class="sxs-lookup"><span data-stu-id="efab1-114">To create a heading, you use a hash mark (#), as follows:</span></span>

```markdown
    # This is heading 1
    ## This is heading 2
    ### This is heading 3
    #### This is heading 4
```

### <a name="bold-and-italic-text"></a><span data-ttu-id="efab1-115">Fet og kursivert tekst</span><span class="sxs-lookup"><span data-stu-id="efab1-115">Bold and italic text</span></span>

<span data-ttu-id="efab1-116">For å formatere tekst som **fet**, legger du ved to stjerner:</span><span class="sxs-lookup"><span data-stu-id="efab1-116">To format text as **bold**, you enclose it in two asterisks:</span></span>

```markdown
    This text is **bold**.
```

<span data-ttu-id="efab1-117">For å formatere tekst som *kursiv*, legger du ved en stjerne:</span><span class="sxs-lookup"><span data-stu-id="efab1-117">To format text as *italic*, you enclose it in a single asterisk:</span></span>

```markdown
    This text is *italic*.
```

<span data-ttu-id="efab1-118">For å formatere tekst som både ***fet og kursiv***, legger du ved tre stjerner:</span><span class="sxs-lookup"><span data-stu-id="efab1-118">To format text as both ***bold and italic***, you enclose it in three asterisks:</span></span>

```markdown
    This is text is both ***bold and italic***.
```

### <a name="lists"></a><span data-ttu-id="efab1-119">Lister</span><span class="sxs-lookup"><span data-stu-id="efab1-119">Lists</span></span>

#### <a name="unordered-list"></a><span data-ttu-id="efab1-120">Usortert liste</span><span class="sxs-lookup"><span data-stu-id="efab1-120">Unordered list</span></span>

<span data-ttu-id="efab1-121">Hvis du vil formatere en ikke-sortert/punktmerket liste, kan du bruke stjerner eller bindestreker.</span><span class="sxs-lookup"><span data-stu-id="efab1-121">To format an unordered/bulleted list, you can use either asterisks or dashes.</span></span> <span data-ttu-id="efab1-122">For eksempel følgende markdown:</span><span class="sxs-lookup"><span data-stu-id="efab1-122">For example, the following Markdown:</span></span>

```markdown
- List item 1
- List item 2
- List item 3
```

<span data-ttu-id="efab1-123">blir gjengitt som:</span><span class="sxs-lookup"><span data-stu-id="efab1-123">will be rendered as:</span></span>

- <span data-ttu-id="efab1-124">Listeelement 1</span><span class="sxs-lookup"><span data-stu-id="efab1-124">List item 1</span></span>
- <span data-ttu-id="efab1-125">Listeelement 2</span><span class="sxs-lookup"><span data-stu-id="efab1-125">List item 2</span></span>
- <span data-ttu-id="efab1-126">Listeelement 3</span><span class="sxs-lookup"><span data-stu-id="efab1-126">List item 3</span></span>

<span data-ttu-id="efab1-127">Hvis du vil neste en liste i en annen liste, rykker du inn de underordnede elementene.</span><span class="sxs-lookup"><span data-stu-id="efab1-127">To nest a list within another list, indent the child list items.</span></span> <span data-ttu-id="efab1-128">For eksempel følgende markdown:</span><span class="sxs-lookup"><span data-stu-id="efab1-128">For example, the following Markdown:</span></span>

```markdown
- List item 1
  - List item A
  - List item B
- List item 2
```

<span data-ttu-id="efab1-129">blir gjengitt som:</span><span class="sxs-lookup"><span data-stu-id="efab1-129">will be rendered as:</span></span>

- <span data-ttu-id="efab1-130">Listeelement 1</span><span class="sxs-lookup"><span data-stu-id="efab1-130">List item 1</span></span>
  - <span data-ttu-id="efab1-131">Listeelement A</span><span class="sxs-lookup"><span data-stu-id="efab1-131">List item A</span></span>
  - <span data-ttu-id="efab1-132">Listeelement B</span><span class="sxs-lookup"><span data-stu-id="efab1-132">List item B</span></span>
- <span data-ttu-id="efab1-133">Listeelement 2</span><span class="sxs-lookup"><span data-stu-id="efab1-133">List item 2</span></span>

#### <a name="ordered-list"></a><span data-ttu-id="efab1-134">Sortert liste</span><span class="sxs-lookup"><span data-stu-id="efab1-134">Ordered list</span></span>

<span data-ttu-id="efab1-135">Hvis du vil formatere en liste som er sortert/trinnvis, kan du bruke tilsvarende tall.</span><span class="sxs-lookup"><span data-stu-id="efab1-135">To format an ordered/stepwise list, you use corresponding numbers.</span></span> <span data-ttu-id="efab1-136">For eksempel følgende markdown:</span><span class="sxs-lookup"><span data-stu-id="efab1-136">For example, the following Markdown:</span></span>

```markdown
1. First instruction
2. Second instruction
3. Third instruction
```

<span data-ttu-id="efab1-137">blir gjengitt som:</span><span class="sxs-lookup"><span data-stu-id="efab1-137">will be rendered as:</span></span>

1. <span data-ttu-id="efab1-138">Første instruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-138">First instruction</span></span>
2. <span data-ttu-id="efab1-139">Andre instruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-139">Second instruction</span></span>
3. <span data-ttu-id="efab1-140">Tredje instruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-140">Third instruction</span></span>

<span data-ttu-id="efab1-141">Hvis du vil neste en liste i en annen liste, rykker du inn de underordnede elementene.</span><span class="sxs-lookup"><span data-stu-id="efab1-141">To nest a list within another list, indent the child list items.</span></span> <span data-ttu-id="efab1-142">For eksempel følgende markdown:</span><span class="sxs-lookup"><span data-stu-id="efab1-142">For example, the following Markdown:</span></span>

```markdown
1. First instruction
    1. Sub-instruction
    2. Sub-instruction
2. Second instruction
```

<span data-ttu-id="efab1-143">blir gjengitt som:</span><span class="sxs-lookup"><span data-stu-id="efab1-143">will be rendered as:</span></span>

1. <span data-ttu-id="efab1-144">Første instruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-144">First instruction</span></span>
    1. <span data-ttu-id="efab1-145">Underinstruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-145">Sub-instruction</span></span>
    2. <span data-ttu-id="efab1-146">Underinstruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-146">Sub-instruction</span></span>
2. <span data-ttu-id="efab1-147">Andre instruksjon</span><span class="sxs-lookup"><span data-stu-id="efab1-147">Second instruction</span></span>

### <a name="tables"></a><span data-ttu-id="efab1-148">Tabeller</span><span class="sxs-lookup"><span data-stu-id="efab1-148">Tables</span></span>

<span data-ttu-id="efab1-149">Tabeller er ikke en del av Markdown-kjernespesifikasjonen, men GFM støtter dem.</span><span class="sxs-lookup"><span data-stu-id="efab1-149">Tables are not part of the core Markdown specification, but GFM supports them.</span></span> <span data-ttu-id="efab1-150">Du kan opprette tabeller ved hjelp av vertikal strek (|) og bindestreker (-).</span><span class="sxs-lookup"><span data-stu-id="efab1-150">You can create tables by using the pipe (|) and hyphen (-) characters.</span></span> <span data-ttu-id="efab1-151">Bindestreker oppretter hver kolonneoverskrift, mens vertikale streker skiller hver kolonne.</span><span class="sxs-lookup"><span data-stu-id="efab1-151">Hyphens create each column's header, while pipes separate each column.</span></span> <span data-ttu-id="efab1-152">Ta med en tom linje før tabellen slik at den gjengis riktig.</span><span class="sxs-lookup"><span data-stu-id="efab1-152">Include a blank line before your table so it's rendered correctly.</span></span>

<span data-ttu-id="efab1-153">For eksempel følgende markdown:</span><span class="sxs-lookup"><span data-stu-id="efab1-153">For example, the following Markdown:</span></span>

```markdown
| Fun                  | With                 | Tables          |
| :------------------- | -------------------: |:---------------:|
| left-aligned column  | right-aligned column | centered column |
| $100                 | $100                 | $100            |
| $10                  | $10                  | $10             |
| $1                   | $1                   | $1              |
```

<span data-ttu-id="efab1-154">blir gjengitt som:</span><span class="sxs-lookup"><span data-stu-id="efab1-154">will be rendered as:</span></span>

| <span data-ttu-id="efab1-155">Moro</span><span class="sxs-lookup"><span data-stu-id="efab1-155">Fun</span></span>                  | <span data-ttu-id="efab1-156">Med</span><span class="sxs-lookup"><span data-stu-id="efab1-156">With</span></span>                 | <span data-ttu-id="efab1-157">Tabeller</span><span class="sxs-lookup"><span data-stu-id="efab1-157">Tables</span></span>          |
| :------------------- | -------------------: |:---------------:|
| <span data-ttu-id="efab1-158">venstrejustert kolonne</span><span class="sxs-lookup"><span data-stu-id="efab1-158">left-aligned column</span></span>  | <span data-ttu-id="efab1-159">høyrejustert kolonne</span><span class="sxs-lookup"><span data-stu-id="efab1-159">right-aligned column</span></span> | <span data-ttu-id="efab1-160">midtstilt kolonne</span><span class="sxs-lookup"><span data-stu-id="efab1-160">centered column</span></span> |
| <span data-ttu-id="efab1-161">$100</span><span class="sxs-lookup"><span data-stu-id="efab1-161">$100</span></span>                 | <span data-ttu-id="efab1-162">$100</span><span class="sxs-lookup"><span data-stu-id="efab1-162">$100</span></span>                 | <span data-ttu-id="efab1-163">$100</span><span class="sxs-lookup"><span data-stu-id="efab1-163">$100</span></span>            |
| <span data-ttu-id="efab1-164">$10</span><span class="sxs-lookup"><span data-stu-id="efab1-164">$10</span></span>                  | <span data-ttu-id="efab1-165">$10</span><span class="sxs-lookup"><span data-stu-id="efab1-165">$10</span></span>                  | <span data-ttu-id="efab1-166">$10</span><span class="sxs-lookup"><span data-stu-id="efab1-166">$10</span></span>             |
| <span data-ttu-id="efab1-167">$1</span><span class="sxs-lookup"><span data-stu-id="efab1-167">$1</span></span>                   | <span data-ttu-id="efab1-168">$1</span><span class="sxs-lookup"><span data-stu-id="efab1-168">$1</span></span>                   | <span data-ttu-id="efab1-169">$1</span><span class="sxs-lookup"><span data-stu-id="efab1-169">$1</span></span>              |

<span data-ttu-id="efab1-170">For mer informasjon om å opprette tabeller, se:</span><span class="sxs-lookup"><span data-stu-id="efab1-170">For more information on creating tables, see:</span></span>

- <span data-ttu-id="efab1-171">Markdig [-funksjonen for tekstbryting i tabeller](#table-wrapping) som kan hjelpe deg med formatering av brede tabeller</span><span class="sxs-lookup"><span data-stu-id="efab1-171">The Markdig [table wrapping feature](#table-wrapping), which can help with formatting of wide tables</span></span>
- <span data-ttu-id="efab1-172">Githubs [Organisere informasjon med tabeller](https://help.github.com/articles/organizing-information-with-tables/)</span><span class="sxs-lookup"><span data-stu-id="efab1-172">GitHub's [Organizing information with tables](https://help.github.com/articles/organizing-information-with-tables/)</span></span>
- <span data-ttu-id="efab1-173">Webappen [Markdown-tabellgenerator](https://www.tablesgenerator.com/markdown_tables) </span><span class="sxs-lookup"><span data-stu-id="efab1-173">The [Markdown Tables Generator](https://www.tablesgenerator.com/markdown_tables) web app</span></span>
- [<span data-ttu-id="efab1-174">Adam Pritchards Markdown-jukseark</span><span class="sxs-lookup"><span data-stu-id="efab1-174">Adam Pritchard's Markdown Cheatsheet</span></span>](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#wiki-tables)
- [<span data-ttu-id="efab1-175">Michel Fortins Markdown-ekstra</span><span class="sxs-lookup"><span data-stu-id="efab1-175">Michel Fortin's Markdown Extra</span></span>](https://michelf.ca/projects/php-markdown/extra/#table)
- [<span data-ttu-id="efab1-176">Konverter HTML-tabeller til Markdown</span><span class="sxs-lookup"><span data-stu-id="efab1-176">Convert HTML tables to Markdown</span></span>](https://jmalarcon.github.io/markdowntables/)

### <a name="links"></a><span data-ttu-id="efab1-177">Koblinger</span><span class="sxs-lookup"><span data-stu-id="efab1-177">Links</span></span>

<span data-ttu-id="efab1-178">Markdown-syntaksen for en innebygd kobling består av `[link text]`-delen, som er teksten som blir hyperkoblet, etterfulgt av `(file-name.md)`-delen, som er navnet på URL-adressen eller en fil som er koblet til:</span><span class="sxs-lookup"><span data-stu-id="efab1-178">The Markdown syntax for an inline link consists of the `[link text]` portion, which is the text that will be hyperlinked, followed by the `(file-name.md)` portion, which is the URL or file name that's being linked to:</span></span>

 `[link text](file-name.md)`

<span data-ttu-id="efab1-179">Hvis du vil ha mer informasjon om kobling, se:</span><span class="sxs-lookup"><span data-stu-id="efab1-179">For more information on linking, see:</span></span>

- <span data-ttu-id="efab1-180">[Markdown-syntaksveiledning](https://daringfireball.net/projects/markdown/syntax#link) for detaljer om Markdowns støtte for kobling.</span><span class="sxs-lookup"><span data-stu-id="efab1-180">The [Markdown syntax guide](https://daringfireball.net/projects/markdown/syntax#link) for details on Markdown's base linking support.</span></span>
- <span data-ttu-id="efab1-181">[Koblinger](how-to-write-links.md)-delen i denne veiledningen for informasjon om ekstra koblingsfeltsyntaks som Markdig gir.</span><span class="sxs-lookup"><span data-stu-id="efab1-181">The [Links](how-to-write-links.md) section of this guide for details on additional linking syntax that Markdig provides.</span></span>

### <a name="code-snippets"></a><span data-ttu-id="efab1-182">Kodesnutter</span><span class="sxs-lookup"><span data-stu-id="efab1-182">Code snippets</span></span>

<span data-ttu-id="efab1-183">Markdown støtter plasseringen av kodesnutter, både innebygd i en setning og som en separat «inngjerdet» blokk mellom setninger.</span><span class="sxs-lookup"><span data-stu-id="efab1-183">Markdown supports the placement of code snippets both inline in a sentence and as a separate "fenced" block between sentences.</span></span> <span data-ttu-id="efab1-184">For detaljer, se:</span><span class="sxs-lookup"><span data-stu-id="efab1-184">For details, see:</span></span>

- [<span data-ttu-id="efab1-185">Markdowns innebygde støtte for kodeblokker</span><span class="sxs-lookup"><span data-stu-id="efab1-185">Markdown's native support for code blocks</span></span>](https://daringfireball.net/projects/markdown/syntax#precode)
- [<span data-ttu-id="efab1-186">GFM-støtte for kodeinngjerding og syntaksutheving</span><span class="sxs-lookup"><span data-stu-id="efab1-186">GFM support for code fencing and syntax highlighting</span></span>](https://help.github.com/articles/creating-and-highlighting-code-blocks/)

<span data-ttu-id="efab1-187">Inngjerdede kodeblokker er en enkel måte å aktivere syntaksutheving for kodesnuttene dine.</span><span class="sxs-lookup"><span data-stu-id="efab1-187">Fenced code blocks are an easy way to enable syntax highlighting for your code snippets.</span></span> <span data-ttu-id="efab1-188">Det generelle formatet for inngjerdede kodeblokker er:</span><span class="sxs-lookup"><span data-stu-id="efab1-188">The general format for fenced code blocks is:</span></span>

    ```alias
    ...
    your code goes in here
    ...
    ```

<span data-ttu-id="efab1-189">Aliaset etter de første tre tegnene for backtick (') definerer syntaksutheving som skal brukes.</span><span class="sxs-lookup"><span data-stu-id="efab1-189">The alias after the initial three backtick (\`) characters defines the syntax highlighting to be used.</span></span> <span data-ttu-id="efab1-190">Følgende er en liste av ofte brukte programmeringsspråk i Docs-innhold og tilsvarende etikett:</span><span class="sxs-lookup"><span data-stu-id="efab1-190">The following is a list of commonly used programming languages in Docs content and the matching label:</span></span>

<span data-ttu-id="efab1-191">Disse språkene har støtte for egendefinert navn, og de fleste har språkutheving.</span><span class="sxs-lookup"><span data-stu-id="efab1-191">These languages have friendly name support and most have language highlighting.</span></span>

|<span data-ttu-id="efab1-192">Navn</span><span class="sxs-lookup"><span data-stu-id="efab1-192">Name</span></span>|<span data-ttu-id="efab1-193">Markdown Label</span><span class="sxs-lookup"><span data-stu-id="efab1-193">Markdown Label</span></span>|
|-----|-------|
|<span data-ttu-id="efab1-194">.NET-konsoll</span><span class="sxs-lookup"><span data-stu-id="efab1-194">.NET Console</span></span>|<span data-ttu-id="efab1-195">dotnetcli</span><span class="sxs-lookup"><span data-stu-id="efab1-195">dotnetcli</span></span>|
|<span data-ttu-id="efab1-196">ASP.NET (C#)</span><span class="sxs-lookup"><span data-stu-id="efab1-196">ASP.NET (C#)</span></span>|<span data-ttu-id="efab1-197">aspx-csharp</span><span class="sxs-lookup"><span data-stu-id="efab1-197">aspx-csharp</span></span>|
|<span data-ttu-id="efab1-198">ASP.NET (VB)</span><span class="sxs-lookup"><span data-stu-id="efab1-198">ASP.NET (VB)</span></span>|<span data-ttu-id="efab1-199">aspx-vb</span><span class="sxs-lookup"><span data-stu-id="efab1-199">aspx-vb</span></span>|
|<span data-ttu-id="efab1-200">AzCopy</span><span class="sxs-lookup"><span data-stu-id="efab1-200">AzCopy</span></span>|<span data-ttu-id="efab1-201">azcopy</span><span class="sxs-lookup"><span data-stu-id="efab1-201">azcopy</span></span>|
|<span data-ttu-id="efab1-202">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="efab1-202">Azure CLI</span></span>|<span data-ttu-id="efab1-203">azurecli</span><span class="sxs-lookup"><span data-stu-id="efab1-203">azurecli</span></span>|
|<span data-ttu-id="efab1-204">Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="efab1-204">Azure PowerShell</span></span>|<span data-ttu-id="efab1-205">azurepowershell</span><span class="sxs-lookup"><span data-stu-id="efab1-205">azurepowershell</span></span>|
|<span data-ttu-id="efab1-206">C++</span><span class="sxs-lookup"><span data-stu-id="efab1-206">C++</span></span>|<span data-ttu-id="efab1-207">cpp</span><span class="sxs-lookup"><span data-stu-id="efab1-207">cpp</span></span>|
|<span data-ttu-id="efab1-208">C++/CX</span><span class="sxs-lookup"><span data-stu-id="efab1-208">C++/CX</span></span>|<span data-ttu-id="efab1-209">cppcx</span><span class="sxs-lookup"><span data-stu-id="efab1-209">cppcx</span></span>|
|<span data-ttu-id="efab1-210">C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="efab1-210">C++/WinRT</span></span>|<span data-ttu-id="efab1-211">cppwinrt</span><span class="sxs-lookup"><span data-stu-id="efab1-211">cppwinrt</span></span>|
|<span data-ttu-id="efab1-212">C#</span><span class="sxs-lookup"><span data-stu-id="efab1-212">C#</span></span>|<span data-ttu-id="efab1-213">csharp</span><span class="sxs-lookup"><span data-stu-id="efab1-213">csharp</span></span>|
|<span data-ttu-id="efab1-214">CSHTML</span><span class="sxs-lookup"><span data-stu-id="efab1-214">CSHTML</span></span>|<span data-ttu-id="efab1-215">cshtml</span><span class="sxs-lookup"><span data-stu-id="efab1-215">cshtml</span></span>|
|<span data-ttu-id="efab1-216">DAX</span><span class="sxs-lookup"><span data-stu-id="efab1-216">DAX</span></span>|<span data-ttu-id="efab1-217">dax</span><span class="sxs-lookup"><span data-stu-id="efab1-217">dax</span></span>|
|<span data-ttu-id="efab1-218">F#</span><span class="sxs-lookup"><span data-stu-id="efab1-218">F#</span></span>|<span data-ttu-id="efab1-219">fsharp</span><span class="sxs-lookup"><span data-stu-id="efab1-219">fsharp</span></span>|
|<span data-ttu-id="efab1-220">Go</span><span class="sxs-lookup"><span data-stu-id="efab1-220">Go</span></span>|<span data-ttu-id="efab1-221">go</span><span class="sxs-lookup"><span data-stu-id="efab1-221">go</span></span>|
|<span data-ttu-id="efab1-222">HTML</span><span class="sxs-lookup"><span data-stu-id="efab1-222">HTML</span></span>|<span data-ttu-id="efab1-223">html</span><span class="sxs-lookup"><span data-stu-id="efab1-223">html</span></span>|
|<span data-ttu-id="efab1-224">HTTP</span><span class="sxs-lookup"><span data-stu-id="efab1-224">HTTP</span></span>|<span data-ttu-id="efab1-225">http</span><span class="sxs-lookup"><span data-stu-id="efab1-225">http</span></span>|
|<span data-ttu-id="efab1-226">Java</span><span class="sxs-lookup"><span data-stu-id="efab1-226">Java</span></span>|<span data-ttu-id="efab1-227">java</span><span class="sxs-lookup"><span data-stu-id="efab1-227">java</span></span>|
|<span data-ttu-id="efab1-228">JavaScript</span><span class="sxs-lookup"><span data-stu-id="efab1-228">JavaScript</span></span>|<span data-ttu-id="efab1-229">javascript</span><span class="sxs-lookup"><span data-stu-id="efab1-229">javascript</span></span>|
|<span data-ttu-id="efab1-230">JSON</span><span class="sxs-lookup"><span data-stu-id="efab1-230">JSON</span></span>|<span data-ttu-id="efab1-231">json</span><span class="sxs-lookup"><span data-stu-id="efab1-231">json</span></span>|
|<span data-ttu-id="efab1-232">Markdown</span><span class="sxs-lookup"><span data-stu-id="efab1-232">Markdown</span></span>|<span data-ttu-id="efab1-233">md</span><span class="sxs-lookup"><span data-stu-id="efab1-233">md</span></span>|
|<span data-ttu-id="efab1-234">NodeJS</span><span class="sxs-lookup"><span data-stu-id="efab1-234">NodeJS</span></span>|<span data-ttu-id="efab1-235">nodejs</span><span class="sxs-lookup"><span data-stu-id="efab1-235">nodejs</span></span>|
|<span data-ttu-id="efab1-236">Objective-C</span><span class="sxs-lookup"><span data-stu-id="efab1-236">Objective-C</span></span>|<span data-ttu-id="efab1-237">objc</span><span class="sxs-lookup"><span data-stu-id="efab1-237">objc</span></span>|
|<span data-ttu-id="efab1-238">OData</span><span class="sxs-lookup"><span data-stu-id="efab1-238">OData</span></span>|<span data-ttu-id="efab1-239">odata</span><span class="sxs-lookup"><span data-stu-id="efab1-239">odata</span></span>|
|<span data-ttu-id="efab1-240">PHP</span><span class="sxs-lookup"><span data-stu-id="efab1-240">PHP</span></span>|<span data-ttu-id="efab1-241">php</span><span class="sxs-lookup"><span data-stu-id="efab1-241">php</span></span>|
|<span data-ttu-id="efab1-242">Power Apps-formel</span><span class="sxs-lookup"><span data-stu-id="efab1-242">Power Apps Formula</span></span>|<span data-ttu-id="efab1-243">powerappsfl</span><span class="sxs-lookup"><span data-stu-id="efab1-243">powerappsfl</span></span>|
|<span data-ttu-id="efab1-244">PowerShell</span><span class="sxs-lookup"><span data-stu-id="efab1-244">PowerShell</span></span>|<span data-ttu-id="efab1-245">powershell</span><span class="sxs-lookup"><span data-stu-id="efab1-245">powershell</span></span>|
|<span data-ttu-id="efab1-246">Python</span><span class="sxs-lookup"><span data-stu-id="efab1-246">Python</span></span>|<span data-ttu-id="efab1-247">python</span><span class="sxs-lookup"><span data-stu-id="efab1-247">python</span></span>|
|<span data-ttu-id="efab1-248">Q#</span><span class="sxs-lookup"><span data-stu-id="efab1-248">Q#</span></span>|<span data-ttu-id="efab1-249">qsharp</span><span class="sxs-lookup"><span data-stu-id="efab1-249">qsharp</span></span>|
|<span data-ttu-id="efab1-250">Ruby</span><span class="sxs-lookup"><span data-stu-id="efab1-250">Ruby</span></span>|<span data-ttu-id="efab1-251">ruby</span><span class="sxs-lookup"><span data-stu-id="efab1-251">ruby</span></span>|
|<span data-ttu-id="efab1-252">SQL</span><span class="sxs-lookup"><span data-stu-id="efab1-252">SQL</span></span>|<span data-ttu-id="efab1-253">sql</span><span class="sxs-lookup"><span data-stu-id="efab1-253">sql</span></span>|
|<span data-ttu-id="efab1-254">Swift</span><span class="sxs-lookup"><span data-stu-id="efab1-254">Swift</span></span>|<span data-ttu-id="efab1-255">swift</span><span class="sxs-lookup"><span data-stu-id="efab1-255">swift</span></span>|
|<span data-ttu-id="efab1-256">TypeScript</span><span class="sxs-lookup"><span data-stu-id="efab1-256">TypeScript</span></span>|<span data-ttu-id="efab1-257">typescript</span><span class="sxs-lookup"><span data-stu-id="efab1-257">typescript</span></span>|
|<span data-ttu-id="efab1-258">VB</span><span class="sxs-lookup"><span data-stu-id="efab1-258">VB</span></span>|<span data-ttu-id="efab1-259">vb</span><span class="sxs-lookup"><span data-stu-id="efab1-259">vb</span></span>|
|<span data-ttu-id="efab1-260">VSTS CLI</span><span class="sxs-lookup"><span data-stu-id="efab1-260">VSTS CLI</span></span>|<span data-ttu-id="efab1-261">vstscli</span><span class="sxs-lookup"><span data-stu-id="efab1-261">vstscli</span></span>|
|<span data-ttu-id="efab1-262">XAML</span><span class="sxs-lookup"><span data-stu-id="efab1-262">XAML</span></span>|<span data-ttu-id="efab1-263">xaml</span><span class="sxs-lookup"><span data-stu-id="efab1-263">xaml</span></span>|
|<span data-ttu-id="efab1-264">XML</span><span class="sxs-lookup"><span data-stu-id="efab1-264">XML</span></span>|<span data-ttu-id="efab1-265">xml</span><span class="sxs-lookup"><span data-stu-id="efab1-265">xml</span></span>|

#### <a name="example-c"></a><span data-ttu-id="efab1-266">Eksempel: C\#</span><span class="sxs-lookup"><span data-stu-id="efab1-266">Example: C\#</span></span>

<span data-ttu-id="efab1-267">__Markdown__</span><span class="sxs-lookup"><span data-stu-id="efab1-267">__Markdown__</span></span>

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

<span data-ttu-id="efab1-268">__Gjengi__</span><span class="sxs-lookup"><span data-stu-id="efab1-268">__Render__</span></span>

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

#### <a name="example-sql"></a><span data-ttu-id="efab1-269">Eksempel: SQL</span><span class="sxs-lookup"><span data-stu-id="efab1-269">Example: SQL</span></span>

<span data-ttu-id="efab1-270">__Markdown__</span><span class="sxs-lookup"><span data-stu-id="efab1-270">__Markdown__</span></span>

    ```sql
    CREATE TABLE T1 (
      c1 int PRIMARY KEY,
      c2 varchar(50) SPARSE NULL
    );
    ```

<span data-ttu-id="efab1-271">__Gjengi__</span><span class="sxs-lookup"><span data-stu-id="efab1-271">__Render__</span></span>

```sql
CREATE TABLE T1 (
  c1 int PRIMARY KEY,
  c2 varchar(50) SPARSE NULL
);
```

## <a name="ops-custom-markdown-extensions"></a><span data-ttu-id="efab1-272">OPS egendefinerte markdown-utvidelser</span><span class="sxs-lookup"><span data-stu-id="efab1-272">OPS custom Markdown extensions</span></span>

> [!NOTE]
> <span data-ttu-id="efab1-273">Open Publishing Services (OPS) implementerer en Markdig-analyse for Markdown som er svært kompatibel med GitHub Flavored Markdown (GFM).</span><span class="sxs-lookup"><span data-stu-id="efab1-273">Open Publishing Services (OPS) implements a Markdig Parser for Markdown, which is highly compatible with GitHub Flavored Markdown (GFM).</span></span> <span data-ttu-id="efab1-274">Markdig legger til en del funksjonalitet gjennom Markdown-utvidelser.</span><span class="sxs-lookup"><span data-stu-id="efab1-274">Markdig adds some functionality through Markdown extensions.</span></span> <span data-ttu-id="efab1-275">Følgelig er valgte artikler fra den komplette OPS-oppretterveiledningen inkludert i denne veiledningen som referanse.</span><span class="sxs-lookup"><span data-stu-id="efab1-275">As such, selected articles from the full OPS Authoring Guide are included in this guide for reference.</span></span> <span data-ttu-id="efab1-276">(Se for eksempel Markdig- og Markdown-utvidelser og Kodesnutter i innholdsfortegnelsen.)</span><span class="sxs-lookup"><span data-stu-id="efab1-276">(For example, see "Markdig and Markdown extensions" and "Code snippets" in the table of contents.)</span></span>

<span data-ttu-id="efab1-277">Docs-artiklene bruker GFM for mesteparten av artikkelformatering, som avsnitt, koblinger, lister og overskrifter.</span><span class="sxs-lookup"><span data-stu-id="efab1-277">Docs articles use GFM for most article formatting, such as paragraphs, links, lists, and headings.</span></span> <span data-ttu-id="efab1-278">For å oppnå rikere formatering kan artikler bruke Markdig-funksjoner som:</span><span class="sxs-lookup"><span data-stu-id="efab1-278">For richer formatting, articles can use Markdig features such as:</span></span>

- <span data-ttu-id="efab1-279">Notatblokker</span><span class="sxs-lookup"><span data-stu-id="efab1-279">Note blocks</span></span>
- <span data-ttu-id="efab1-280">Inkluderinger</span><span class="sxs-lookup"><span data-stu-id="efab1-280">Includes</span></span>
- <span data-ttu-id="efab1-281">Velgere</span><span class="sxs-lookup"><span data-stu-id="efab1-281">Selectors</span></span>
- <span data-ttu-id="efab1-282">Innebygde videoer</span><span class="sxs-lookup"><span data-stu-id="efab1-282">Embedded videos</span></span>
- <span data-ttu-id="efab1-283">Kodesnutter/prøver</span><span class="sxs-lookup"><span data-stu-id="efab1-283">Code snippets/samples</span></span>

<span data-ttu-id="efab1-284">For en fullstendig liste kan du se Markdig- og Markdown-utvidelser og Kodesnutter i innholdsfortegnelsen.</span><span class="sxs-lookup"><span data-stu-id="efab1-284">For the complete list, refer to "Markdig and Markdown extensions" and "Code snippets" in the table of contents.</span></span>

### <a name="note-blocks"></a><span data-ttu-id="efab1-285">Notatblokker</span><span class="sxs-lookup"><span data-stu-id="efab1-285">Note blocks</span></span>

<span data-ttu-id="efab1-286">Du kan velge mellom fire typer notatblokker for å trekke oppmerksomheten mot et bestemt innhold:</span><span class="sxs-lookup"><span data-stu-id="efab1-286">You can choose from four types of note blocks to draw attention to specific content:</span></span>

- <span data-ttu-id="efab1-287">OBS</span><span class="sxs-lookup"><span data-stu-id="efab1-287">NOTE</span></span>
- <span data-ttu-id="efab1-288">ADVARSEL</span><span class="sxs-lookup"><span data-stu-id="efab1-288">WARNING</span></span>
- <span data-ttu-id="efab1-289">TIPS</span><span class="sxs-lookup"><span data-stu-id="efab1-289">TIP</span></span>
- <span data-ttu-id="efab1-290">VIKTIG</span><span class="sxs-lookup"><span data-stu-id="efab1-290">IMPORTANT</span></span>

<span data-ttu-id="efab1-291">Merk at notatblokker bør brukes sparsomt fordi de kan virke forstyrrende.</span><span class="sxs-lookup"><span data-stu-id="efab1-291">In general, note blocks should be used sparingly because they can be disruptive.</span></span> <span data-ttu-id="efab1-292">Selv om de også støtter kodeblokker, bilder, lister og koblinger, kan du prøve å holde notatblokkene enkle.</span><span class="sxs-lookup"><span data-stu-id="efab1-292">Although they also support code blocks, images, lists, and links, try to keep your note blocks simple and straightforward.</span></span>

### <a name="includes"></a><span data-ttu-id="efab1-293">Inkluderinger</span><span class="sxs-lookup"><span data-stu-id="efab1-293">Includes</span></span>

<span data-ttu-id="efab1-294">Når du har tekst- eller bildefiler som kan brukes på nytt, og som skal tas med i artikkelfiler, kan du bruke en referanse til filen som skal inkluderes via funksjonen for Markdig-filinkludering.</span><span class="sxs-lookup"><span data-stu-id="efab1-294">When you have reusable text or image files that need to be included in article files, you can use a reference to the "include" file via the Markdig file include feature.</span></span> <span data-ttu-id="efab1-295">Denne funksjonen ber OPS om å inkludere filen i artikkelfilen ved buildtid, noe som gjør den til en del av den publiserte artikkelen.</span><span class="sxs-lookup"><span data-stu-id="efab1-295">This feature instructs OPS to include the file in your article file at build time, making it part of your published article.</span></span> <span data-ttu-id="efab1-296">Tre typer inkluderinger er tilgjengelige for å hjelpe deg med å bruke innhold på nytt:</span><span class="sxs-lookup"><span data-stu-id="efab1-296">Three types of includes are available to help you reuse content:</span></span>

- <span data-ttu-id="efab1-297">Innebygd: Bruke en vanlig tekstsnutt innebygd i en annen setning.</span><span class="sxs-lookup"><span data-stu-id="efab1-297">Inline: Reuse a common text snippet inline with within another sentence.</span></span>
- <span data-ttu-id="efab1-298">Blokk: Bruke en hel Markdown-fil på nytt som en blokk, nestet i en del av en artikkel.</span><span class="sxs-lookup"><span data-stu-id="efab1-298">Block: Reuse an entire Markdown file as a block, nested within a section of an article.</span></span>
- <span data-ttu-id="efab1-299">Bilde: Dette er slik standard bildeinkludering implementeres i Docs.</span><span class="sxs-lookup"><span data-stu-id="efab1-299">Image: This is how standard image inclusion is implemented in Docs.</span></span>

<span data-ttu-id="efab1-300">En innebygd eller blokk-inkludering er bare en enkel Markdown-fil (.md).</span><span class="sxs-lookup"><span data-stu-id="efab1-300">An inline or block include is just a simple Markdown (.md) file.</span></span> <span data-ttu-id="efab1-301">Den kan inneholde en hvilken som helst gyldig Markdown.</span><span class="sxs-lookup"><span data-stu-id="efab1-301">It can contain any valid Markdown.</span></span> <span data-ttu-id="efab1-302">Alle inkluderte Markdown-filer skal plasseres i en [vanlig `/includes` underkatalog](git-github-fundamentals.md#includes-subdirectory) i roten av repositoriet.</span><span class="sxs-lookup"><span data-stu-id="efab1-302">All include Markdown files should be placed in a [common `/includes` subdirectory](git-github-fundamentals.md#includes-subdirectory), in the root of the repository.</span></span> <span data-ttu-id="efab1-303">Når artikkelen er publisert, blir den inkluderte filen sømløst integrert i den.</span><span class="sxs-lookup"><span data-stu-id="efab1-303">When the article is published, the included file is seamlessly integrated into it.</span></span>

<span data-ttu-id="efab1-304">Her er krav og hensyn for inkluderinger:</span><span class="sxs-lookup"><span data-stu-id="efab1-304">Here are requirements and considerations for includes:</span></span>

- <span data-ttu-id="efab1-305">Bruk inkluderinger når du trenger at den samme teksten vises i flere artikler.</span><span class="sxs-lookup"><span data-stu-id="efab1-305">Use includes whenever you need the same text to appear in multiple articles.</span></span>
- <span data-ttu-id="efab1-306">Bruk blokkinkludering for betydelige mengder innhold – et avsnitt eller to, en delt prosedyre eller en delt inndeling.</span><span class="sxs-lookup"><span data-stu-id="efab1-306">Use block includes for significant amounts of content--a paragraph or two, a shared procedure, or a shared section.</span></span> <span data-ttu-id="efab1-307">Ikke bruk dem til noe mindre enn en setning.</span><span class="sxs-lookup"><span data-stu-id="efab1-307">Do not use them for anything smaller than a sentence.</span></span>
- <span data-ttu-id="efab1-308">Inkluderinger gjengis ikke i GitHub-visningen av artikkelen fordi de er avhengige av Markdig-utvidelser.</span><span class="sxs-lookup"><span data-stu-id="efab1-308">Includes won't be rendered in the GitHub rendered view of your article, because they rely on Markdig extensions.</span></span> <span data-ttu-id="efab1-309">De gjengis kun etter publisering.</span><span class="sxs-lookup"><span data-stu-id="efab1-309">They'll be rendered only after publication.</span></span>
- <span data-ttu-id="efab1-310">Kontroller at all teksten i en inkludering er skrevet i fullstendige setninger eller uttrykk som ikke avhenger av foregående tekst eller påfølgende tekst i artikkelen som refererer til inkluderingen.</span><span class="sxs-lookup"><span data-stu-id="efab1-310">Ensure that all the text in an include is written in complete sentences or phrases that do not depend on preceding text or following text in the article that references the include.</span></span> <span data-ttu-id="efab1-311">Å ignorere denne veiledningen fører til en uoversettelig streng i artikkelen som bryter den lokaliserte opplevelsen.</span><span class="sxs-lookup"><span data-stu-id="efab1-311">Ignoring this guidance creates an untranslatable string in the article that breaks the localized experience.</span></span>
- <span data-ttu-id="efab1-312">Ikke bygg inn inkluderinger med andre inkluderinger.</span><span class="sxs-lookup"><span data-stu-id="efab1-312">Don't embed includes within other includes.</span></span> <span data-ttu-id="efab1-313">De støttes ikke.</span><span class="sxs-lookup"><span data-stu-id="efab1-313">They are not supported.</span></span>
- <span data-ttu-id="efab1-314">Plasser media-filer i en mediemappe som er spesifikk for inkluderinger-undermappe – for eksempel, `<repo>` /inkluderinger/media-mappen.</span><span class="sxs-lookup"><span data-stu-id="efab1-314">Place media files in a media folder that's specific to the include subdirectory--for instance, the `<repo>`/includes/media folder.</span></span> <span data-ttu-id="efab1-315">Media-katalogen bør ikke inneholde noen bilder i roten.</span><span class="sxs-lookup"><span data-stu-id="efab1-315">The media directory should not contain any images in its root.</span></span> <span data-ttu-id="efab1-316">Hvis inkluderingen ikke har bilder, er det ikke nødvendig med en korresponderende media-katalog.</span><span class="sxs-lookup"><span data-stu-id="efab1-316">If the include does not have images, a corresponding media directory is not required.</span></span>
- <span data-ttu-id="efab1-317">Som med vanlige artikler, må du ikke dele medier mellom inkluderingsfiler.</span><span class="sxs-lookup"><span data-stu-id="efab1-317">As with regular articles, don't share media between include files.</span></span> <span data-ttu-id="efab1-318">Bruk en separat fil med et unikt navn for hver inkludering og artikkel.</span><span class="sxs-lookup"><span data-stu-id="efab1-318">Use a separate file with a unique name for each include and article.</span></span> <span data-ttu-id="efab1-319">Lagre media-filen i mediemappen som er knyttet til inkluderingen.</span><span class="sxs-lookup"><span data-stu-id="efab1-319">Store the media file in the media folder that's associated with the include.</span></span>
- <span data-ttu-id="efab1-320">Ikke bruk inkluderingen som det eneste innholdet i en artikkel.</span><span class="sxs-lookup"><span data-stu-id="efab1-320">Don't use an include as the only content of an article.</span></span>  <span data-ttu-id="efab1-321">Inkluderinger er ment å utfylle innholdet i resten av artikkelen.</span><span class="sxs-lookup"><span data-stu-id="efab1-321">Includes are meant to be supplemental to the content in the rest of the article.</span></span>

### <a name="selectors"></a><span data-ttu-id="efab1-322">Velgere</span><span class="sxs-lookup"><span data-stu-id="efab1-322">Selectors</span></span>

<span data-ttu-id="efab1-323">Bruk velgere i tekniske artikler når du oppretter flere utgaver av den samme artikkelen for å adressere forskjeller i implementeringen på tvers av teknologier og plattformer.</span><span class="sxs-lookup"><span data-stu-id="efab1-323">Use selectors in technical articles when you author multiple flavors of the same article, to address differences in implementation across technologies or platforms.</span></span> <span data-ttu-id="efab1-324">Dette er vanligvis mest aktuelt for vårt mobile plattforminnhold for utviklere.</span><span class="sxs-lookup"><span data-stu-id="efab1-324">This is typically most applicable to our mobile platform content for developers.</span></span> <span data-ttu-id="efab1-325">Det finnes for øyeblikket to forskjellige typer velgere i Markdig, en enkeltvelger og en multivelger.</span><span class="sxs-lookup"><span data-stu-id="efab1-325">There are currently two different types of selectors in Markdig, a single selector and a multi-selector.</span></span>

<span data-ttu-id="efab1-326">Fordi den samme Markdown-velgeren går i hver artikkel i valget, anbefaler vi å sette velgeren for artikkelen din i en inkludering.</span><span class="sxs-lookup"><span data-stu-id="efab1-326">Because the same selector Markdown goes in each article in the selection, we recommend placing the selector for your article in an include.</span></span> <span data-ttu-id="efab1-327">Deretter kan du referere til den inkluderingen i alle artikler som bruker samme velgeren.</span><span class="sxs-lookup"><span data-stu-id="efab1-327">Then you can reference that include in all your articles that use the same selector.</span></span>

### <a name="code-snippets"></a><span data-ttu-id="efab1-328">Kodesnutter</span><span class="sxs-lookup"><span data-stu-id="efab1-328">Code snippets</span></span>

<span data-ttu-id="efab1-329">Markdig støtter avansert inkludering av koden i en artikkel via kodesnuttutvidelsen den bruker.</span><span class="sxs-lookup"><span data-stu-id="efab1-329">Markdig supports advanced inclusion of code in an article, via its code snippet extension.</span></span> <span data-ttu-id="efab1-330">Den gir avansert gjengivelse som bygger på GFM-funksjoner som valg av programmeringsspråk og syntaksfarger, i tillegg til flotte funksjoner som:</span><span class="sxs-lookup"><span data-stu-id="efab1-330">It provides advanced rendering that builds on GFM features such as programming language selection and syntax coloring, plus nice features such as:</span></span>

- <span data-ttu-id="efab1-331">Inkludering av sentraliserte eksempler/kodesnutter fra et eksternt repositorium.</span><span class="sxs-lookup"><span data-stu-id="efab1-331">Inclusion of centralized code samples/snippets from an external repository.</span></span>
- <span data-ttu-id="efab1-332">Fanebasert brukergrensesnitt for å vise flere versjoner av kodeeksempler på forskjellige språk.</span><span class="sxs-lookup"><span data-stu-id="efab1-332">Tabbed UI to show multiple versions of code samples in different languages.</span></span>

## <a name="gotchas-and-troubleshooting"></a><span data-ttu-id="efab1-333">Feller og feilsøking</span><span class="sxs-lookup"><span data-stu-id="efab1-333">Gotchas and troubleshooting</span></span>

### <a name="alt-text"></a><span data-ttu-id="efab1-334">Alt-tekst</span><span class="sxs-lookup"><span data-stu-id="efab1-334">Alt text</span></span>

<span data-ttu-id="efab1-335">Alternativ tekst som inneholder understrekingstegn gjengis ikke riktig.</span><span class="sxs-lookup"><span data-stu-id="efab1-335">Alt text that contains underscores won't be rendered properly.</span></span> <span data-ttu-id="efab1-336">For eksempel, i stedet for å bruke dette:</span><span class="sxs-lookup"><span data-stu-id="efab1-336">For example, instead of using this:</span></span>

```markdown
![ADextension_2FA_Configure_Step4] (./media/bogusfilename/ADextension_2FA_Configure_Step4.PNG)
```

<span data-ttu-id="efab1-337">Unngå understrekingstegn som dette:</span><span class="sxs-lookup"><span data-stu-id="efab1-337">Escape the underscores like this:</span></span>

```markdown
![ADextension\_2FA\_Configure\_Step4] (./media/bogusfilename/ADextension_2FA_Configure_Step4.PNG)
```

### <a name="apostrophes-and-quotation-marks"></a><span data-ttu-id="efab1-338">Apostrofer og anførselstegn</span><span class="sxs-lookup"><span data-stu-id="efab1-338">Apostrophes and quotation marks</span></span>

<span data-ttu-id="efab1-339">Hvis du kopierer fra Word til et redigeringsprogram for Markdown, kan teksten inneholde «smarte» (doble) apostrofer eller anførselstegn.</span><span class="sxs-lookup"><span data-stu-id="efab1-339">If you copy from Word into a Markdown editor, the text might contain "smart" (curly) apostrophes or quotation marks.</span></span> <span data-ttu-id="efab1-340">Disse må være kodet eller endret til enkle apostrofer eller anførselstegn.</span><span class="sxs-lookup"><span data-stu-id="efab1-340">These need to be encoded or changed to basic apostrophes or quotation marks.</span></span> <span data-ttu-id="efab1-341">Ellers ender du opp med ting som dette når filen er blitt publisert: pcâ€™s</span><span class="sxs-lookup"><span data-stu-id="efab1-341">Otherwise, you end up with things like this when the file is published: Itâ€™s</span></span>

<span data-ttu-id="efab1-342">Her er kodingen for «smarte»-versjoner av disse skilletegnene:</span><span class="sxs-lookup"><span data-stu-id="efab1-342">Here are the encodings for the "smart" versions of these punctuation marks:</span></span>

- <span data-ttu-id="efab1-343">Venstre (innledende) anførselstegn: `&#8220;`</span><span class="sxs-lookup"><span data-stu-id="efab1-343">Left (opening) quotation mark: `&#8220;`</span></span>
- <span data-ttu-id="efab1-344">Høyre (avsluttende) anførselstegn: `&#8221;`</span><span class="sxs-lookup"><span data-stu-id="efab1-344">Right (closing) quotation mark: `&#8221;`</span></span>
- <span data-ttu-id="efab1-345">Høyre (avsluttende) enkle anførselstegnet eller apostrof: `&#8217;`</span><span class="sxs-lookup"><span data-stu-id="efab1-345">Right (closing) single quotation mark or apostrophe: `&#8217;`</span></span>
- <span data-ttu-id="efab1-346">Venstre (innledende) enkelt anførselstegn (brukes sjelden): `&#8216;`</span><span class="sxs-lookup"><span data-stu-id="efab1-346">Left (opening) single quotation mark (rarely used): `&#8216;`</span></span>

### <a name="angle-brackets"></a><span data-ttu-id="efab1-347">Vinkelparenteser</span><span class="sxs-lookup"><span data-stu-id="efab1-347">Angle brackets</span></span>

<span data-ttu-id="efab1-348">Hvis du bruker vinkelparenteser i teksten (ikke kode) i filen, for eksempel for å angi en plassholder – må du kode vinkelparentesene manuelt.</span><span class="sxs-lookup"><span data-stu-id="efab1-348">If you use angle brackets in text (not code) in your file--for example, to denote a placeholder--you need to manually encode the angle brackets.</span></span> <span data-ttu-id="efab1-349">Ellers tror Markdown at de er ment å være en HTML-kode.</span><span class="sxs-lookup"><span data-stu-id="efab1-349">Otherwise, Markdown thinks that they're intended to be an HTML tag.</span></span>

<span data-ttu-id="efab1-350">Kode for eksempel `<script name>` som `&lt;script name&gt;`</span><span class="sxs-lookup"><span data-stu-id="efab1-350">For example, encode `<script name>` as `&lt;script name&gt;`</span></span>

## <a name="see-also"></a><span data-ttu-id="efab1-351">Se også</span><span class="sxs-lookup"><span data-stu-id="efab1-351">See also</span></span>

### <a name="markdown-resources"></a><span data-ttu-id="efab1-352">Markdown-ressurser</span><span class="sxs-lookup"><span data-stu-id="efab1-352">Markdown resources</span></span>

- [<span data-ttu-id="efab1-353">Introduksjon til Markdown</span><span class="sxs-lookup"><span data-stu-id="efab1-353">Introduction to Markdown</span></span>](https://daringfireball.net/projects/markdown/syntax)
- [<span data-ttu-id="efab1-354">Docs Markdown-jukseark</span><span class="sxs-lookup"><span data-stu-id="efab1-354">Docs Markdown cheat sheet</span></span>](./media/documents/markdown-cheatsheet.pdf?raw=true)
- [<span data-ttu-id="efab1-355">Grunnleggende om GitHubs Markdown</span><span class="sxs-lookup"><span data-stu-id="efab1-355">GitHub's Markdown Basics</span></span>](https://help.github.com/articles/markdown-basics/)
