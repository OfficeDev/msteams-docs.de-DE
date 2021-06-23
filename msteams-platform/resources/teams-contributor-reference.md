---
title: Beitragen zu Microsoft Teams Dokumentation
description: Schritte zum Erstellen und Veröffentlichen Teams Dokumentation
author: surbhigupta
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: 33296219b9d42b2ca26eb3c44df5c6429f5259ce
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069156"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Beitragen zu Microsoft Teams Dokumentation

[Teams Dokumentation](/microsoftteams/platform/overview) ist Teil der technischen [Dokumentationsbibliothek von Microsoft Docs.](https://docs.microsoft.com) Der Inhalt ist in Gruppen unterteilt, die als Docsets bezeichnet werden und jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden. Artikel im selben Dokumentsatz weisen nach dokumenten *<span></span> .microsoft.com* die gleiche URL-Pfaderweiterung auf.  Ist beispielsweise `/docs.microsoft.com/microsoftteams/...` der Anfang des Teams Docset-Dateipfads. Teams Artikel werden in [der MarkDown-Syntax](#markdown-reference) geschrieben und auf [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)gehostet.

## <a name="set-up-your-workspace"></a>Einrichten des Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren Sie [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren Sie [Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Installieren Sie [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt aus dem VS Code Marketplace.
<br>&emsp;&emsp; Oder

> [!div class="checklist"]
>
> * Installieren von innerhalb VS Code:

   1. Wählen Sie das **Erweiterungssymbol** auf der Seitenaktivitätsleiste aus, oder verwenden Sie den Befehl **Ansicht => Erweiterungen** (STRG+UMSCHALT+X), und suchen Sie nach dem *Dokumenterstellungspaket* (Microsoft).
   1. Wählen Sie die Schaltfläche **"Installieren"** aus.
   1. Nach Abschluss der Installation wechselt die Schaltfläche **"Installieren"** zur Schaltfläche "Zahnrad **verwalten".**

## <a name="review-the-microsoft-docs-contributors-guide"></a>Überprüfen des Leitfadens für Mitwirkende zu Microsoft-Dokumenten

Der Leitfaden für [Mitwirkende](/contribute) bietet Anweisungen zum Erstellen, Veröffentlichen und Aktualisieren von technischen Inhalten auf der Microsoft Docs-Plattform.

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft Writing-, Style- und Inhaltshandbücher

* **[Microsoft Writing Style Guide](/style-guide/welcome)**. Erwägen Sie das Hinzufügen dieses Onlinehandbuchs zum **Favoritenmenü** Ihres Browsers. Es ist eine umfassende Ressource für das heutige technische Schreiben und spiegelt den modernen Ansatz von Microsoft für Sprache und Stil wider.

* **[Schreiben von Entwicklerinhalten.](/style-guide/developer-content/)** Teams-spezifischen Inhalte richten sich an eine Entwicklergruppe mit grundlegendem Verständnis von Programmierkonzepten und -prozessen. Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und gleichzeitig den Ton und Stil von Microsoft beibehalten.

* **[Schritt-für-Schritt-Anleitungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)** schreiben. Angewendete und interaktive Benutzeroberflächen sind eine großartige Möglichkeit für Entwickler, sich über Microsoft-Produkte und -Technologien zu informieren. Das Darstellen komplexer oder einfacher Prozeduren in einem progressiven Format ist natürlich und benutzerfreundlicher.

## <a name="markdown-reference"></a>MarkDown-Referenz

 Microsoft Docs-Seiten werden in MarkDown-Syntax geschrieben und über ein [Markdig-Modul](https://github.com/lunet-io/markdig) analysiert. Weitere Informationen zu bestimmten Tags und Formatierungskonventionen *finden* Sie in der Referenz zu [Docs Markdown.](/contribute/markdown-reference)

## <a name="file-paths"></a>Dateipfade

Das Festlegen eines gültigen Dateipfads für Hyperlinks in Ihrer Dokumentation kann eine Herausforderung sein, insbesondere bei der Verwendung relativer Pfade und beim Erstellen von Links zu anderen Dokumentenmappen.  Ihr Build ist auf GitHub nicht erfolgreich, wenn der Dateipfad falsch oder ungültig ist.

Weitere Informationen zu Hyperlinks und Dateipfaden finden Sie unter [Verwenden von Links in der Dokumentation.](/contribute/how-to-write-links)

>[!IMPORTANT]
> So verweisen Sie auf einen Artikel, *der Teil des* Teams-Plattform-Docsets ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne vorangestellten Schrägstrich.<br>
> &emsp;&#x2714; schließen Sie die Dateierweiterung Markdown ein.<br>
>Beispiel:  **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-article.md** -> `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> So verweisen Sie auf einen Microsoft Docs-Bibliotheksartikel, der nicht Teil des Teams Plattform-Docset *ist:*<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; Schließen Sie die Dateierweiterung nicht ein. <br> Beispiel:  **/docset/address-to-file-location** -> `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`<br><br>
> Um auf eine Seite außerhalb der Microsoft Docs-Bibliothek zu verweisen, z. B. GitHub, verwenden Sie den vollständigen `https` Dateipfad.<br>

## <a name="code-samples-and-snippets"></a>Codebeispiele und Codeausschnitte

Codebeispiele spielen eine wichtige Rolle bei der erfolgreichen Verwendung von APIs und SDKs für Entwickler. Gut dargestellte Codebeispiele können deutlich vermitteln, wie alles funktioniert, als beschreibende Text- und Anleitungsinformationen allein. Ihre Codebeispiele sollten präzise, präzise, gut dokumentiert und vor allem leserfreundlicher sein. Code, der leicht lesbar ist, ist auch leicht zu verstehen, zu testen, zu debuggen, zu verwalten, zu ändern und zu erweitern. Weitere Informationen finden Sie unter ["Einfügen von Code in Dokumente".](/contribute/code-in-docs)

## <a name="see-also"></a>Siehe auch

* [Schnellstart für Dokumentstil und Sprache](/contribute/style-quick-start)
* [Neuesten Stand: Quellcodelesbarkeit Tipps](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Abrufen von Microsoft Docs-Updates und den neuesten Ankündigungen](/teamblog)
