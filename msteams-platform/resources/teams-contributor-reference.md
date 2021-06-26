---
title: Mitwirken an Teams Dokumentation
description: Schritte zum Erstellen und Veröffentlichen Teams Dokumentation
author: surbhigupta
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: a567b0462397780650d6173df9dae1b340a06f97
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140513"
---
# <a name="contribute-to-teams-documentation"></a><span data-ttu-id="56b25-103">Mitwirken an Teams Dokumentation</span><span class="sxs-lookup"><span data-stu-id="56b25-103">Contribute to Teams documentation</span></span>

<span data-ttu-id="56b25-104">Teams Dokumentation ist Teil der technischen **Dokumentationsbibliothek von Microsoft Docs.**</span><span class="sxs-lookup"><span data-stu-id="56b25-104">Teams documentation is part of the **Microsoft Docs** technical documentation library.</span></span> <span data-ttu-id="56b25-105">Der Inhalt ist in Gruppen unterteilt, die als Docsets bezeichnet werden und jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="56b25-105">The content is organized into groups called docsets, each representing a group of related documents managed as a single entity.</span></span> <span data-ttu-id="56b25-106">Artikel im selben Dokumentsatz weisen nach docs.microsoft.com die gleiche URL-Pfaderweiterung **auf.**</span><span class="sxs-lookup"><span data-stu-id="56b25-106">Articles in the same docset have the same URL path extension after **docs.microsoft.com**.</span></span> <span data-ttu-id="56b25-107">Ist beispielsweise `/docs.microsoft.com/microsoftteams/...` der Anfang des Teams Docset-Dateipfads.</span><span class="sxs-lookup"><span data-stu-id="56b25-107">For example, `/docs.microsoft.com/microsoftteams/...` is the beginning of the Teams docset file path.</span></span> <span data-ttu-id="56b25-108">Teams Artikel werden in markdown-Syntax geschrieben und auf GitHub gehostet.</span><span class="sxs-lookup"><span data-stu-id="56b25-108">Teams articles are written in Markdown syntax and hosted on GitHub.</span></span>

## <a name="set-up-your-workspace"></a><span data-ttu-id="56b25-109">Einrichten des Arbeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="56b25-109">Set up your workspace</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="56b25-110">Installieren Sie [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).</span><span class="sxs-lookup"><span data-stu-id="56b25-110">Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).</span></span>
> * <span data-ttu-id="56b25-111">Installieren Sie [Visual Studio Code](https://code.visualstudio.com/) (VS Code).</span><span class="sxs-lookup"><span data-stu-id="56b25-111">Install [Visual Studio Code](https://code.visualstudio.com/) (VS Code).</span></span>
> * <span data-ttu-id="56b25-112">Installieren Sie [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt aus dem VS Code Marketplace.</span><span class="sxs-lookup"><span data-stu-id="56b25-112">Install [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) directly from the VS Code Marketplace.</span></span>
<br><span data-ttu-id="56b25-113">&emsp;&emsp; Oder</span><span class="sxs-lookup"><span data-stu-id="56b25-113">&emsp;&emsp; or</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="56b25-114">Installieren in VS Code:</span><span class="sxs-lookup"><span data-stu-id="56b25-114">Install within VS Code:</span></span>

   1. <span data-ttu-id="56b25-115">Wählen Sie das **Erweiterungssymbol** auf der Seitenaktivitätsleiste aus, oder verwenden Sie den Befehl **Ansicht => Erweiterungen** oder STRG+UMSCHALT+X, und suchen Sie nach **Microsoft Docs Authoring Pack.**</span><span class="sxs-lookup"><span data-stu-id="56b25-115">Select the **Extensions icon** on the side activity bar or use the **View => Extensions** command or Ctrl+Shift+X and, search for **Microsoft Docs Authoring Pack**.</span></span>
   1. <span data-ttu-id="56b25-116">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="56b25-116">Select **Install**.</span></span>
   1. <span data-ttu-id="56b25-117">Nach der Installation wird die Schaltfläche **"Install"** auf die Schaltfläche "Zahnrad **verwalten"** geändert.</span><span class="sxs-lookup"><span data-stu-id="56b25-117">After installation, the **Install** changes to the **Manage** gear button.</span></span>

## <a name="review-the-microsoft-docs-contributors-guide"></a><span data-ttu-id="56b25-118">Überprüfen des Leitfadens für Mitwirkende zu Microsoft-Dokumenten</span><span class="sxs-lookup"><span data-stu-id="56b25-118">Review the Microsoft Docs Contributors Guide</span></span>

<span data-ttu-id="56b25-119">Der Leitfaden für Mitwirkende gibt die Richtung zum Erstellen, Veröffentlichen und Aktualisieren von technischen Inhalten auf der **Microsoft Docs-Plattform an.**</span><span class="sxs-lookup"><span data-stu-id="56b25-119">The contributors guide provides direction to create, publish, and update technical content on the **Microsoft Docs** platform.</span></span> 

## <a name="microsoft-writing-style-and-content-guides"></a><span data-ttu-id="56b25-120">Microsoft Writing-, Style- und Inhaltshandbücher</span><span class="sxs-lookup"><span data-stu-id="56b25-120">Microsoft Writing, Style, and Content Guides</span></span>

* <span data-ttu-id="56b25-121">**[Microsoft Writing Style Guide:](/style-guide/welcome)** Microsoft Writing Style Guide ist eine umfassende Ressource für technisches Schreiben und spiegelt den modernen Ansatz von Microsoft für Sprache und Stil wider.</span><span class="sxs-lookup"><span data-stu-id="56b25-121">**[Microsoft Writing Style Guide](/style-guide/welcome)**: Microsoft Writing Style Guide is a comprehensive resource for technical writing and reflects Microsoft's modern approach to voice and style.</span></span> <span data-ttu-id="56b25-122">Fügen Sie dieses Onlinehandbuch zum **Favoritenmenü** Ihres Browsers hinzu.</span><span class="sxs-lookup"><span data-stu-id="56b25-122">For easy reference, add this online guide to your browser's **Favorites** menu.</span></span>

* <span data-ttu-id="56b25-123">**[Schreiben von Entwicklerinhalten:](/style-guide/developer-content/)** Teams bestimmte Inhalte richten sich an eine Entwicklergruppe mit grundlegendem Verständnis von Programmierkonzepten und -prozessen.</span><span class="sxs-lookup"><span data-stu-id="56b25-123">**[Writing developer content](/style-guide/developer-content/)**: Teams specific content is aimed at a developer audience with a fundamental understanding of programming concepts and processes.</span></span> <span data-ttu-id="56b25-124">Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und gleichzeitig den Ton und Stil von Microsoft beibehalten.</span><span class="sxs-lookup"><span data-stu-id="56b25-124">It is important that you must provide clear, technically accurate information in a compelling manner while maintaining Microsoft's tone and style.</span></span>

* <span data-ttu-id="56b25-125">Schrittweise Anleitungen schreiben: Angewendete und interaktive Benutzeroberflächen sind eine großartige Möglichkeit für Entwickler, sich über **[Microsoft-Produkte](/style-guide/procedures-instructions/writing-step-by-step-instructions)** und -Technologien zu informieren.</span><span class="sxs-lookup"><span data-stu-id="56b25-125">**[Writing step-by-step instructions](/style-guide/procedures-instructions/writing-step-by-step-instructions)**: Applied and interactive experiences are a great way for developers to learn about Microsoft products and technologies.</span></span> <span data-ttu-id="56b25-126">Das Darstellen komplexer oder einfacher Prozeduren in einem progressiven Format ist natürlich und benutzerfreundlicher.</span><span class="sxs-lookup"><span data-stu-id="56b25-126">Presenting complex or simple procedures in a progressive format is natural and user friendly.</span></span>

## <a name="markdown-reference"></a><span data-ttu-id="56b25-127">MarkDown-Referenz</span><span class="sxs-lookup"><span data-stu-id="56b25-127">MarkDown reference</span></span>

<span data-ttu-id="56b25-128">**Microsoft Docs-Seiten** werden in **MarkDown-Syntax** geschrieben und über ein [Markdig-Modul](https://github.com/lunet-io/markdig) analysiert.</span><span class="sxs-lookup"><span data-stu-id="56b25-128">**Microsoft Docs** pages are written in **MarkDown** syntax and parsed through a [Markdig](https://github.com/lunet-io/markdig) engine.</span></span> <span data-ttu-id="56b25-129">Weitere Informationen zu bestimmten Tags und Formatierungskonventionen finden Sie unter [Docs Markdown Reference](/contribute/markdown-reference).</span><span class="sxs-lookup"><span data-stu-id="56b25-129">For more information on specific tags and formatting conventions, see [Docs Markdown reference](/contribute/markdown-reference).</span></span>

## <a name="file-paths"></a><span data-ttu-id="56b25-130">Dateipfade</span><span class="sxs-lookup"><span data-stu-id="56b25-130">File Paths</span></span>

<span data-ttu-id="56b25-131">Wenn Sie relative Pfade verwenden und Links zu anderen Dokumentenmappen erstellen, ist es wichtig, einen gültigen Dateipfad für Hyperlinks in Ihrer Dokumentation festzulegen.</span><span class="sxs-lookup"><span data-stu-id="56b25-131">When using relative paths and creating links to other docsets, it is important to set a valid file path for hyperlinks in your documentation.</span></span> <span data-ttu-id="56b25-132">Ihr Build ist auf GitHub nur erfolgreich, wenn der Dateipfad korrekt oder gültig ist.</span><span class="sxs-lookup"><span data-stu-id="56b25-132">Your build succeeds on GitHub only if the file path is correct or valid.</span></span>
 
<span data-ttu-id="56b25-133">Weitere Informationen zu Hyperlinks und Dateipfaden finden Sie unter [Verwenden von Links in der Dokumentation.](/contribute/how-to-write-links)</span><span class="sxs-lookup"><span data-stu-id="56b25-133">For more information on hyperlinks and file paths, see [use links in documentation](/contribute/how-to-write-links).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56b25-134">So verweisen Sie auf einen Artikel, **der Teil des** Teams Plattform-Docset ist:</span><span class="sxs-lookup"><span data-stu-id="56b25-134">To reference an article that is **part of** the Teams platform docset:</span></span><br>
> <span data-ttu-id="56b25-135">&emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne vorangestellten Schrägstrich.</span><span class="sxs-lookup"><span data-stu-id="56b25-135">&emsp;&#x2714; Use a relative path without a leading forward slash.</span></span><br>
> <span data-ttu-id="56b25-136">&emsp;&#x2714; schließen Sie die Dateierweiterung Markdown ein.</span><span class="sxs-lookup"><span data-stu-id="56b25-136">&emsp;&#x2714; Include the Markdown file extension.</span></span><br>
><span data-ttu-id="56b25-137">Beispiel: **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-article.md** – > [Erstellen einer App für Microsoft Teams](../concepts/building-an-app.md)</span><span class="sxs-lookup"><span data-stu-id="56b25-137">Ex:  **parent directory/directory/path-to-article.md** —> [Building an app for Microsoft Teams](../concepts/building-an-app.md)</span></span> <br><br>
> <span data-ttu-id="56b25-138">So verweisen Sie auf einen Microsoft Docs-Bibliotheksartikel, der nicht Teil des Teams Plattform-Docsets **ist:**</span><span class="sxs-lookup"><span data-stu-id="56b25-138">To reference a Microsoft Docs library article that **is not part of** the Teams platform docset:</span></span><br>
> <span data-ttu-id="56b25-139">&emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.</span><span class="sxs-lookup"><span data-stu-id="56b25-139">&emsp;&#x2714; Use a relative path that begins with a forward slash.</span></span><br>
> <span data-ttu-id="56b25-140">&emsp;&#x2714; Dateierweiterung nicht einschließen.</span><span class="sxs-lookup"><span data-stu-id="56b25-140">&emsp;&#x2714; Do not include the file extension.</span></span> <br> <span data-ttu-id="56b25-141">Beispiel: **/docset/address-to-file-location** - > [Verwenden der Microsoft Graph-API zum Arbeiten mit Microsoft Teams](/graph/api/resources/teams-api-overview)</span><span class="sxs-lookup"><span data-stu-id="56b25-141">Ex:  **/docset/address-to-file-location** —> [Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)</span></span><br><br>
> <span data-ttu-id="56b25-142">Um auf eine Seite außerhalb der Microsoft Docs-Bibliothek zu verweisen, z. B. GitHub, verwenden Sie den vollständigen `https` Dateipfad.</span><span class="sxs-lookup"><span data-stu-id="56b25-142">To reference a page outside of the Microsoft Docs library, such as GitHub, use the full `https` file path.</span></span><br>

## <a name="code-samples-and-snippets"></a><span data-ttu-id="56b25-143">Codebeispiele und Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="56b25-143">Code Samples and Snippets</span></span>

<span data-ttu-id="56b25-144">Codebeispiele spielen eine wichtige Rolle bei der effektiven Verwendung von APIs und SDKs.</span><span class="sxs-lookup"><span data-stu-id="56b25-144">Code samples play an important role to use APIs and SDKs effectively.</span></span> <span data-ttu-id="56b25-145">Gut dargestellte Codebeispiele können deutlich vermitteln, wie alles funktioniert, als beschreibende Text- und Anleitungsinformationen allein.</span><span class="sxs-lookup"><span data-stu-id="56b25-145">Well presented code samples can communicate how things work more clearly than descriptive text and instructional information alone.</span></span> <span data-ttu-id="56b25-146">Ihre Codebeispiele müssen präzise, präzise, gut dokumentiert und leserfreundlicher sein.</span><span class="sxs-lookup"><span data-stu-id="56b25-146">Your code samples must be accurate, concise, well documented, and reader friendly.</span></span> <span data-ttu-id="56b25-147">Code, der leicht zu lesen ist, muss leicht verständlich sein, testen, debuggen, verwalten, ändern und erweitern.</span><span class="sxs-lookup"><span data-stu-id="56b25-147">Code that is easy to read must be easy to understand, test, debug, maintain, modify, and extend.</span></span> <span data-ttu-id="56b25-148">Weitere Informationen finden Sie unter ["Einfügen von Code in Dokumente".](/contribute/code-in-docs)</span><span class="sxs-lookup"><span data-stu-id="56b25-148">For more information, see [how to include code in docs](/contribute/code-in-docs).</span></span>

## <a name="see-also"></a><span data-ttu-id="56b25-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="56b25-149">See also</span></span>

* [<span data-ttu-id="56b25-150">Microsoft-Dokumente</span><span class="sxs-lookup"><span data-stu-id="56b25-150">Microsoft Docs</span></span>](/)
* [<span data-ttu-id="56b25-151">Leitfaden für Mitwirkende</span><span class="sxs-lookup"><span data-stu-id="56b25-151">contributors guide</span></span>](/contribute)
* [<span data-ttu-id="56b25-152">Schnellstart für Dokumentstil und Sprache</span><span class="sxs-lookup"><span data-stu-id="56b25-152">Docs style and voice quick start</span></span>](/contribute/style-quick-start)
* [<span data-ttu-id="56b25-153">Neuesten Stand: Quellcodelesbarkeit Tipps</span><span class="sxs-lookup"><span data-stu-id="56b25-153">Cutting Edge : Source Code Readability Tips</span></span>](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [<span data-ttu-id="56b25-154">Teams Dokumentation</span><span class="sxs-lookup"><span data-stu-id="56b25-154">Teams documentation</span></span>](/microsoftteams/platform/overview)
* [<span data-ttu-id="56b25-155">GitHub</span><span class="sxs-lookup"><span data-stu-id="56b25-155">GitHub</span></span>](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)


## <a name="next-step"></a><span data-ttu-id="56b25-156">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="56b25-156">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56b25-157">Abrufen von Microsoft Docs-Updates und den neuesten Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="56b25-157">Get Microsoft Docs updates and the latest announcements</span></span>](/teamblog)
