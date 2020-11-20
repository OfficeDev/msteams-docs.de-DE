---
title: Beitrag zur Microsoft Teams-Dokumentation
description: Schritte zum Erstellen und Veröffentlichen von Microsoft Teams-Dokumentation
author: laujan
ms.author: lajanuar
ms.topic: contributor-guide
ms.openlocfilehash: 18aae61a674cf9c4c94831f22149cd4b9e7ebeda
ms.sourcegitcommit: 43e1be9d9e3651ce73a8d2139e44d75550a0ca60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "49366896"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Beitrag zur Microsoft Teams-Dokumentation

[Teams-Dokumentation](/microsoftteams/platform/overview) ist Bestandteil der technischen Dokumentationsbibliothek von [Microsoft docs](https://docs.microsoft.com/) . Der Inhalt ist in Gruppen mit dem Namen docsets organisiert, die jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden. Artikel in derselben DokSet haben dieselbe URL-Pfaderweiterung nach *docs <span></span> . Microsoft.com*.  Ist beispielsweise  `/docs.microsoft.com/microsoftteams/...`   der Anfang des Dateipfads für Teams DokSet. Microsoft Teams-Artikel sind in der Syntax für den  [Abschlag](#markdown-reference) geschrieben und auf [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)gehostet.

## <a name="set-up-your-workspace"></a>Einrichten Ihres Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren Sie [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren Sie [Visual Studio-Code](https://code.visualstudio.com/) (vs-Code).
> * Installieren von [docs-Erstellungspaket](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt über den vs-Code-Marktplatz
<br>&emsp;&emsp; oder

> [!div class="checklist"]
>
> * Installieren im vs-Code:

   1. Klicken Sie auf der Seite Aktivitäts Leiste auf das **Symbol Erweiterungen** , oder verwenden Sie den Befehl **View => Extensions** (STRG + UMSCHALT + X), und suchen Sie nach dem *Dokument Erstellungspaket* (Microsoft).
   1. Klicken Sie auf die Schaltfläche **Installieren** .
   1. Nachdem die Installation abgeschlossen ist, ändert sich die Schaltfläche " **Installieren** " in die Schaltfläche "Zahnrad **Verwalten** ".

## <a name="review-the-microsoft-docs-contributors-guide"></a>Lesen des Microsoft docs-Handbuchs für Mitwirkende

Der [Leitfaden für mitwirk](/contribute) Ende bietet Anleitungen zum Erstellen, veröffentlichen und aktualisieren technischer Inhalte auf der Microsoft docs-Plattform. *Siehe auch* [Text & Tabellenformatvorlage und sprach-Schnellstart](/contribute/style-quick-start) .

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft-Schriftarten, Formatvorlagen und Inhalts Handbücher

* **[Microsoft Writing Style Guide](/style-guide/welcome)**. Fügen Sie dieses Online Handbuch in das Menü **Favoriten** Ihres Browsers ein. Es handelt sich um eine umfassende Ressource für das technische Schreiben von heute und spiegelt das moderne Konzept von Microsoft für Sprache und Stil wider.

* **[Schreiben von Entwickler Inhalten](/style-guide/developer-content/)**. Der Microsoft Teams-spezifische Inhalt richtet sich an ein Entwickler Publikum mit einem grundlegenden Verständnis von Programmierkonzepten und-Prozessen. Es ist wichtig, dass Sie klare, technisch präzise Informationen auf eine überzeugende Art und Weise bereitstellen und dabei den Ton und das Format von Microsoft beibehalten.

* **[Schreiben Schritt-für-Schritt-Anleitungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)**. Angewandte und interaktive Erfahrungen sind eine hervorragende Möglichkeit für Entwickler, sich über Microsoft-Produkte und-Technologien zu informieren. Die Darstellung komplexer oder einfacher Prozeduren im progressiven Format ist natürlich und benutzerfreundlich.

## <a name="markdown-reference"></a>Referenz zum Abschlag

 Microsoft docs-Seiten werden in der Abzugs Syntax geschrieben und durch ein [Markdig](https://github.com/lunet-io/markdig) -Modul analysiert. Weitere *Informationen finden Sie unter* [docs-Referenz](/contribute/markdown-reference) für bestimmte Tags und Formatierungskonventionen.

## <a name="file-paths"></a>Dateipfade

Das Festlegen eines gültigen Dateipfads für Hyperlinks in der Dokumentation kann eine Herausforderung sein, insbesondere bei der Verwendung relativer Pfade und dem Erstellen von Links zu anderen docsets.  Ihr Build wird auf GitHub nicht erfolgreich ausgeführt, wenn der Dateipfad falsch oder ungültig ist.

Weitere Informationen zu Hyperlinks und Dateipfaden finden Sie *unter* [Use Links in Documentation](/contribute/how-to-write-links).

>[!IMPORTANT]
> So verweisen Sie auf einen Artikel, der Teil der Microsoft Teams *-* Plattform DokSet ist:<br>
> &emsp;&#x2714; einen relativen Pfad ohne vorangestellten Schrägstrich verwenden.<br>
> &emsp;&#x2714; die Dateierweiterung "ablegen" hinzufügen.<br>
>Ex:  **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-Artikel. MD** – > `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> So verweisen Sie auf einen Microsoft docs-Bibliotheks Artikel, der *nicht Teil* der Teams-Platt Form DokSet ist:<br>
> &emsp;&#x2714; verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; nicht die Dateierweiterung enthalten. <br> Ex:  **/docset/Address-to-File-Location** – > `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`<br><br>
> Wenn Sie auf eine Seite außerhalb der Microsoft docs-Bibliothek wie GitHub verweisen möchten, verwenden Sie den vollständigen `https` Dateipfad.<br>

## <a name="code-samples-and-snippets"></a>Code Beispiele und Codeausschnitte

Code Beispiele spielen eine wichtige Rolle bei der erfolgreichen Verwendung von APIs und SDKs durch Entwickler. Durch gut dargestellte Codebeispiele kann kommuniziert werden, wie die Dinge klarer funktionieren als beschreibenden Text und nur für Lehr Informationen. Ihre Codebeispiele sollten genau, prägnant, gut dokumentiert und vor allem leserfreundlich sein. Leicht lesbarer Code ist ebenfalls leicht verständlich, testen, Debuggen, warten, ändern und erweitern. *Weitere Informationen finden Sie unter* [How to include Code in docs](/contribute/code-in-docs). Tipps zur Lesbarkeit finden Sie *unter* [Cutting Edge: Tipps zur Quell Code Lesbarkeit](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Abrufen von Microsoft docs-Updates und den neuesten Ankündigungen](/teamblog)
