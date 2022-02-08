---
title: Mitwirken an der Teams-Dokumentation
description: Schritte zum Erstellen und Veröffentlichen Teams Dokumentation
author: surbhigupta
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: contributor-guide
ms.openlocfilehash: 5ee1be71c0ba07612808dc8d1cfb766e2f40c36b
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435258"
---
# <a name="contribute-to-teams-documentation"></a>Mitwirken an der Teams-Dokumentation

Teams Dokumentation ist Teil der technischen **Dokumentationsbibliothek von Microsoft Docs**. Der Inhalt ist in Gruppen unterteilt, die als Docsets bezeichnet werden und jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden. Artikel im selben Dokumentsatz weisen nach docs.microsoft.com dieselbe URL-Pfaderweiterung **auf**. Ist beispielsweise `/docs.microsoft.com/microsoftteams/...` der Anfang des Teams Docset-Dateipfads. Teams Artikel werden in markdown-Syntax geschrieben und auf GitHub gehostet.

## <a name="set-up-your-workspace"></a>Einrichten des Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren Sie [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren sie [Microsoft Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Installieren Sie [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt aus dem VS Code Marketplace.
<br>&emsp;&emsp; Oder

> [!div class="checklist"]
>
> * Installation in VS Code:

   1. Wählen Sie das **Erweiterungssymbol** auf der Seitenaktivitätsleiste aus, oder verwenden Sie den Befehl **Ansicht => Erweiterungen** oder STRG+UMSCHALT+X, und suchen Sie nach **Microsoft Docs Authoring Pack**.
   1. Wählen Sie **Installieren** aus.
   1. Nach der Installation wird die Schaltfläche " **Install** " auf die Schaltfläche "Zahnrad **verwalten** " geändert.

## <a name="review-the-microsoft-docs-contributors-guide"></a>Überprüfen des Leitfadens für Mitwirkende zu Microsoft-Dokumenten

Der Leitfaden für Mitwirkende gibt die Richtung zum Erstellen, Veröffentlichen und Aktualisieren von technischen **Inhalten auf der Microsoft Docs-Plattform an** . 

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft Writing-, Style- und Inhaltshandbücher

* **[Microsoft Writing Style Guide](/style-guide/welcome)**: Microsoft Writing Style Guide ist eine umfassende Ressource für technisches Schreiben und spiegelt den modernen Ansatz von Microsoft für Sprache und Stil wider. Fügen Sie dieses Onlinehandbuch zum **Favoritenmenü** Ihres Browsers hinzu, um eine einfache Referenz zu finden.

* **[Schreiben von Entwicklerinhalten](/style-guide/developer-content/)**: Teams bestimmte Inhalte richten sich an eine Entwicklergruppe mit grundlegendem Verständnis von Programmierkonzepten und -prozessen. Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und gleichzeitig den Ton und Stil von Microsoft beibehalten.

* **[Schrittweise Anleitungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)**: Angewendete und interaktive Benutzeroberflächen sind eine großartige Möglichkeit für Entwickler, sich über Microsoft-Produkte und -Technologien zu informieren. Das Darstellen komplexer oder einfacher Prozeduren in einem progressiven Format ist natürlich und benutzerfreundlicher.

## <a name="markdown-reference"></a>MarkDown-Referenz

**Microsoft Docs-Seiten** werden in **MarkDown-Syntax** geschrieben und über ein [Markdig-Modul](https://github.com/lunet-io/markdig) analysiert. Weitere Informationen zu bestimmten Tags und Formatierungskonventionen finden Sie in der [Referenz zu Docs Markdown](/contribute/markdown-reference).

## <a name="file-paths"></a>Dateipfade

Wenn Sie relative Pfade verwenden und Links zu anderen Dokumentenmappen erstellen, ist es wichtig, einen gültigen Dateipfad für Hyperlinks in Ihrer Dokumentation festzulegen. Ihr Build ist auf GitHub nur erfolgreich, wenn der Dateipfad korrekt oder gültig ist.
 
Weitere Informationen zu Hyperlinks und Dateipfaden finden Sie unter ["Verwenden von Links" in der Dokumentation](/contribute/how-to-write-links).

> [!IMPORTANT]
> So verweisen Sie auf einen Artikel, **der Teil des** Teams Plattform-Docsets ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne vorangestellten Schrägstrich.<br>
> &emsp;&#x2714; Schließen Sie die Dateierweiterung Markdown ein.<br>
>Beispiel: **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-article.md** – > [Erstellen einer App für Microsoft Teams](../concepts/building-an-app.md) <br><br>
> So verweisen Sie auf einen Microsoft Docs-Bibliotheksartikel, **der nicht Teil des** Teams Plattform-Docsets ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; Dateierweiterung nicht einschließen. <br> Beispiel: **/docset/address-to-file-location** - > [Verwenden der Microsoft Graph-API zum Arbeiten mit Microsoft Teams](/graph/api/resources/teams-api-overview)<br><br>
> Um auf eine Seite außerhalb der Microsoft Docs-Bibliothek zu verweisen, z. B. GitHub, verwenden Sie den vollständigen `https` Dateipfad.<br>

## <a name="code-samples-and-snippets"></a>Codebeispiele und Codeausschnitte

Codebeispiele spielen eine wichtige Rolle bei der effektiven Verwendung von APIs und SDKs. Gut dargestellte Codebeispiele können deutlich vermitteln, wie alles funktioniert, als beschreibende Text- und Anleitungsinformationen allein. Ihre Codebeispiele müssen präzise, präzise, gut dokumentiert und leserfreundlicher sein. Code, der leicht zu lesen ist, muss leicht verständlich sein, testen, debuggen, verwalten, ändern und erweitern. Weitere Informationen finden Sie unter ["Einfügen von Code in Dokumente"](/contribute/code-in-docs).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abrufen von Microsoft Docs-Updates und den neuesten Ankündigungen](/teamblog)

## <a name="see-also"></a>Siehe auch

* [Microsoft-Dokumentation](/)
* [Leitfaden für Mitwirkende](/contribute)
* [Schnellstart für Dokumentstil und Sprache](/contribute/style-quick-start)
* [Neuesten Stand: Tipps zur Lesbarkeit von Quellcode](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [Teams-Dokumentation](/microsoftteams/platform/overview)
* [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)
