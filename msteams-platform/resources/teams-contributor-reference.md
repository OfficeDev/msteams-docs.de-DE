---
title: Mitwirken an der Teams-Dokumentation
description: Erfahren Sie mehr über die Schritte zum Erstellen und Veröffentlichen der Teams-Dokumentation
author: surbhigupta
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: contributor-guide
ms.openlocfilehash: 4a0c522b5e9d4bcf99ee884de41b1d75846b004a
ms.sourcegitcommit: 377a4b712b50a211851aeecc1029414939945390
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68044665"
---
# <a name="contribute-to-teams-documentation"></a>Mitwirken an der Teams-Dokumentation

Die Teams-Dokumentation ist Teil der Technischen Dokumentationsbibliothek **von Microsoft Learn** . Der Inhalt ist in Gruppen unterteilt, die als Docsets bezeichnet werden und jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden. Artikel im selben Dokument haben die gleiche URL-Pfaderweiterung nach `learn.microsoft.com`. `/learn.microsoft.com/microsoftteams/...` Beispielsweise ist der Anfang des Teams-Dokumentdateipfads. Teams-Artikel werden in Markdown-Syntax geschrieben und auf GitHub gehostet.

## <a name="set-up-your-workspace"></a>Einrichten Ihres Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren Sie [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren sie [Microsoft Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Installieren Sie [docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt aus dem VS Code Marketplace.
<br>&emsp;&emsp; Oder
> [!div class="checklist"]
>
> * Installieren in VS Code:

   1. Wählen Sie das **Symbol "Erweiterungen"** auf der seitenseitigen Aktivitätsleiste aus, oder verwenden Sie den Befehl **"Ansicht => Erweiterungen** " oder STRG+UMSCHALT+X, und suchen Sie nach **dem Dokumenterstellungspaket**.
   1. Wählen Sie **Installieren** aus.
   1. Nach der Installation ändert sich die **Schaltfläche "Installieren** " in die Schaltfläche "Zahnrad **verwalten** ".

## <a name="review-the-microsoft-docs-contributor-guide"></a>Lesen Sie den Leitfaden für Microsoft-Dokumentation-Mitwirkende

Der Leitfaden für Mitwirkende enthält eine Anleitung zum Erstellen, Veröffentlichen und Aktualisieren technischer Inhalte auf der **Microsoft Learn-Plattform** .

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft Writing-, Style- und Inhaltshandbücher

* **[Microsoft Writing Style Guide](/style-guide/welcome)**: Microsoft Writing Style Guide ist eine umfassende Ressource für technisches Schreiben und spiegelt den modernen Ansatz von Microsoft für Sprache und Stil wider. Für eine einfache Referenz fügen Sie diesen Onlineleitfaden zum **Favoritenmenü** Ihres Browsers hinzu.

* **[Schreiben von Entwicklerinhalten](/style-guide/developer-content/)**: Teams-spezifische Inhalte richten sich an ein Entwicklerpublikum mit einem grundlegenden Verständnis von Programmierkonzepten und -prozessen. Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und dabei den Ton und Stil von Microsoft beibehalten.

* **[Schrittweise Anleitungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)** schreiben: Angewendete und interaktive Erfahrungen sind eine großartige Möglichkeit für Entwickler, sich über Microsoft-Produkte und -Technologien zu informieren. Die Darstellung komplexer oder einfacher Verfahren in einem progressiven Format ist natürlich und benutzerfreundlich.

## <a name="markdown-reference"></a>MarkDown-Referenz

**Microsoft Learn-Seiten** werden in **MarkDown-Syntax** geschrieben und über ein [Markdig-Modul](https://github.com/lunet-io/markdig) analysiert. Weitere Informationen zu bestimmten Tags und Formatierungskonventionen finden Sie in der [Referenz zu Docs Markdown](/contribute/markdown-reference).

## <a name="file-paths"></a>Dateipfade

Wenn Sie relative Pfade verwenden und Links zu anderen Dokumentenmappen erstellen, ist es wichtig, einen gültigen Dateipfad für Links in Ihrer Dokumentation festzulegen. Ihr Build ist auf GitHub nur dann erfolgreich, wenn der Dateipfad korrekt oder gültig ist.

Weitere Informationen zu Links und Dateipfaden finden [Sie unter "Verwenden von Links in der Dokumentation"](/contribute/how-to-write-links).

> [!IMPORTANT]
> So verweisen Sie auf einen Artikel, **der Teil des** Teams-Plattformdokuments ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne vorangestellten Schrägstrich.<br>
> &emsp;&#x2714; Die Dateierweiterung Markdown einschließen.<br>
>Beispiel:  **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-article.md** –> [Erstellen einer App für Microsoft Teams](../concepts/building-an-app.md) <br><br>
> So verweisen Sie auf einen Microsoft Learn-Artikel, **der nicht Teil des** Teams-Plattformdokuments ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; Schließen Sie die Dateierweiterung nicht ein. <br>
> Beispiel: **/docset/address-to-file-location** –> [Verwenden der Microsoft Graph-API für die Zusammenarbeit mit Microsoft Teams](/graph/api/resources/teams-api-overview)<br><br>
> Um auf eine Seite außerhalb von Microsoft Learn zu verweisen, z. B. GitHub, verwenden Sie den vollständigen `https` Dateipfad.<br>

## <a name="code-samples-and-snippets"></a>Codebeispiele und Codeausschnitte

Codebeispiele spielen eine wichtige Rolle, um APIs und SDKs effektiv zu verwenden. Gut dargestellte Codebeispiele können kommunizieren, wie die Dinge besser funktionieren als nur beschreibender Text und Anweisungsinformationen. Ihre Codebeispiele müssen genau, prägnant, gut dokumentiert und leserfreundlich sein. Leicht lesbarer Code muss leicht zu verstehen, zu testen, zu debuggen, zu warten, zu ändern und zu erweitern sein. Weitere Informationen finden Sie unter [Einschließen von Code in einen Artikel](/contribute/code-in-docs).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abrufen von Microsoft Learn-Updates und den neuesten Ankündigungen](/teamblog)

## <a name="see-also"></a>Siehe auch

* [Microsoft Learn](/)
* [Leitfaden für Microsoft Learn-Dokumentationsmitwirkende](/contribute)
* [Microsoft Learn- und Sprachschnellstart](/contribute/style-quick-start)
* [Aktuelles: Tipps zur Lesbarkeit von Quellcode](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [Teams-Dokumentation](/microsoftteams/platform/overview)
* [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)
