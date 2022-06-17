---
title: Mitwirken an der Teams-Dokumentation
description: Erfahren Sie mehr über die Schritte zum Erstellen und Veröffentlichen Teams Dokumentation
author: surbhigupta
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: contributor-guide
ms.openlocfilehash: 165f5df18395d329aa2f383d2f07e6f7ff3afdcf
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143081"
---
# <a name="contribute-to-teams-documentation"></a>Mitwirken an der Teams-Dokumentation

Teams Dokumentation ist Teil der **Microsoft-Dokumentation** Technischen Dokumentationsbibliothek. Der Inhalt ist in Gruppen unterteilt, die als Docsets bezeichnet werden und jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden. Artikel im selben Dokument weisen nach docs.microsoft.com die gleiche URL-Pfaderweiterung **auf**. `/docs.microsoft.com/microsoftteams/...` Beispielsweise ist der Anfang des Teams Docset-Dateipfads. Teams Artikel werden in Markdown-Syntax geschrieben und auf GitHub gehostet.

## <a name="set-up-your-workspace"></a>Einrichten Ihres Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren Sie [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren sie [Microsoft Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Installieren Sie [docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt aus dem VS Code Marketplace.
<br>&emsp;&emsp; Oder
> [!div class="checklist"]
>
> * Installieren sie innerhalb VS Code:

   1. Wählen Sie das **Symbol "Erweiterungen"** auf der seitenseitigen Aktivitätsleiste aus, oder verwenden Sie den Befehl **"Ansicht => Erweiterungen**" oder STRG+UMSCHALT+X, und suchen Sie nach **Microsoft-Dokumentation Authoring Pack**.
   1. Wählen Sie **Installieren** aus.
   1. Nach der Installation ändert sich die **Schaltfläche "Installieren** " in die Schaltfläche "Zahnrad **verwalten** ".

## <a name="review-the-microsoft-docs-contributors-guide"></a>Lesen Sie den Leitfaden für Microsoft-Dokumentation-Mitwirkende

Der Leitfaden für Mitwirkende enthält eine Anleitung zum Erstellen, Veröffentlichen und Aktualisieren technischer Inhalte auf der **Microsoft-Dokumentation** Plattform.

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft Writing-, Style- und Inhaltshandbücher

* **[Microsoft Writing Style Guide](/style-guide/welcome)**: Microsoft Writing Style Guide ist eine umfassende Ressource für technisches Schreiben und spiegelt den modernen Ansatz von Microsoft für Sprache und Stil wider. Für eine einfache Referenz fügen Sie diesen Onlineleitfaden zum **Favoritenmenü** Ihres Browsers hinzu.

* **[Schreiben von Entwicklerinhalten](/style-guide/developer-content/)**: Teams bestimmte Inhalte richtet sich an ein Entwicklerpublikum mit einem grundlegenden Verständnis von Programmierkonzepten und -prozessen. Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und dabei den Ton und Stil von Microsoft beibehalten.

* **[Schrittweise Anleitungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)** schreiben: Angewendete und interaktive Erfahrungen sind eine großartige Möglichkeit für Entwickler, sich über Microsoft-Produkte und -Technologien zu informieren. Die Darstellung komplexer oder einfacher Verfahren in einem progressiven Format ist natürlich und benutzerfreundlich.

## <a name="markdown-reference"></a>MarkDown-Referenz

**Microsoft-Dokumentation** Seiten werden in **MarkDown-Syntax** geschrieben und über ein [Markdig-Modul](https://github.com/lunet-io/markdig) analysiert. Weitere Informationen zu bestimmten Tags und Formatierungskonventionen finden Sie in der [Referenz zu Docs Markdown](/contribute/markdown-reference).

## <a name="file-paths"></a>Dateipfade

Wenn Sie relative Pfade verwenden und Links zu anderen Dokumentenmappen erstellen, ist es wichtig, einen gültigen Dateipfad für Links in Ihrer Dokumentation festzulegen. Der Build ist auf GitHub nur erfolgreich, wenn der Dateipfad korrekt oder gültig ist.

Weitere Informationen zu Links und Dateipfaden finden [Sie unter "Verwenden von Links in der Dokumentation"](/contribute/how-to-write-links).

> [!IMPORTANT]
> So verweisen Sie auf einen Artikel, **der Teil des** Teams-Plattformdokuments ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne vorangestellten Schrägstrich.<br>
> &emsp;&#x2714; Die Dateierweiterung Markdown einschließen.<br>
>Beispiel: **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-article.md** –> [Erstellen einer App für Microsoft Teams](../concepts/building-an-app.md) <br><br>
> So verweisen Sie auf einen Microsoft-Dokumentation **Bibliotheksartikel, der nicht Teil des** Teams-Plattformdokuments ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; Schließen Sie die Dateierweiterung nicht ein. <br>
> Beispiel: **/docset/address-to-file-location** –> [Verwenden der Microsoft Graph-API zum Arbeiten mit Microsoft Teams](/graph/api/resources/teams-api-overview)<br><br>
> Verwenden Sie den vollständigen `https` Dateipfad, um auf eine Seite außerhalb der Microsoft-Dokumentation Bibliothek zu verweisen, z. B. GitHub.<br>

## <a name="code-samples-and-snippets"></a>Codebeispiele und Codeausschnitte

Codebeispiele spielen eine wichtige Rolle, um APIs und SDKs effektiv zu verwenden. Gut dargestellte Codebeispiele können kommunizieren, wie die Dinge besser funktionieren als nur beschreibender Text und Anweisungsinformationen. Ihre Codebeispiele müssen genau, prägnant, gut dokumentiert und leserfreundlich sein. Leicht lesbarer Code muss leicht zu verstehen, zu testen, zu debuggen, zu warten, zu ändern und zu erweitern sein. Weitere Informationen finden Sie unter [Einschließen von Code in Dokumente](/contribute/code-in-docs).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abrufen Microsoft-Dokumentation Updates und der neuesten Ankündigungen](/teamblog)

## <a name="see-also"></a>Siehe auch

* [Microsoft-Dokumentation](/)
* [Leitfaden für Mitwirkende](/contribute)
* [Dokumentformat und Sprachschnellstart](/contribute/style-quick-start)
* [Aktuelles: Tipps zur Lesbarkeit von Quellcode](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [Teams Dokumentation](/microsoftteams/platform/overview)
* [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)
