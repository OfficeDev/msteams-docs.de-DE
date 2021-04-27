---
title: Beitragen zur Microsoft Teams-Dokumentation
description: Schritte zum Erstellen und Veröffentlichen der Teams-Dokumentation
author: laujan
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: a6742b8b994cc3752df923db75a3d7d77cbebd83
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019671"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Beitragen zur Microsoft Teams-Dokumentation

[Die Teams-Dokumentation](/microsoftteams/platform/overview) ist Teil der [technischen Dokumentationsbibliothek von Microsoft Docs.](https://docs.microsoft.com/) Der Inhalt ist in Gruppen mit dem Namen docsets organisiert, die jeweils eine Gruppe verwandter Dokumente darstellen, die als einzelne Entität verwaltet werden. Artikel im gleichen docset haben die gleiche URL-Pfaderweiterung nach *docs <span></span> .microsoft.com*.  Beispielsweise ist  `/docs.microsoft.com/microsoftteams/...`   der Anfang des Dateipfads Teams docset. #A0 werden in [der #A1](#markdown-reference) geschrieben und auf [GitHub gehostet.](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)

## <a name="set-up-your-workspace"></a>Einrichten ihres Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren [sie Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren [Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Installieren [des Dokumenterstellungspakets](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt im VS Code Marketplace
<br>&emsp;&emsp; oder

> [!div class="checklist"]
>
> * Installieren in VS Code:

   1. Wählen Sie **das Symbol** Erweiterungen auf der seitenseitigen Aktivitätsleiste aus, oder verwenden Sie den Befehl View = **> Extensions** (STRG+Umschalt+X), und suchen Sie nach dem *Dokumenterstellungspaket* (Microsoft).
   1. Wählen Sie die **Schaltfläche Installieren** aus.
   1. Sobald die Installation abgeschlossen ist, wird die Schaltfläche **Installieren** auf die Schaltfläche **Zahnrad** verwalten geändert.

## <a name="review-the-microsoft-docs-contributors-guide"></a>Überprüfen des Microsoft Docs Contributors Guide

Das [Mitwirkendehandbuch bietet](/contribute) Eine Anleitung zum Erstellen, Veröffentlichen und Aktualisieren von technischen Inhalten auf der Microsoft Docs-Plattform. *Weitere Informationen finden Sie* [unter , Docs style and voice quick start](/contribute/style-quick-start) .

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft Writing, Style, and Content Guides

* **[Microsoft Writing Style Guide](/style-guide/welcome)**. Erwägen Sie das Hinzufügen dieses Onlineleitfadens zum **Menü Favoriten Ihres** Browsers. Es ist eine umfassende Ressource für das heutige technische Schreiben und spiegelt den modernen Ansatz von Microsoft für Sprache und Stil wider.

* **[Schreiben von Entwicklerinhalten](/style-guide/developer-content/)**. Teams-spezifische Inhalte richten sich an eine Entwicklerpublikum mit grundlegendem Verständnis von Programmierkonzepten und -prozessen. Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und dabei den Ton und stil von Microsoft beibehalten.

* **[Schrittweises Schreiben von Anweisungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)**. Angewandte und interaktive Erfahrungen sind eine hervorragende Möglichkeit für Entwickler, mehr über Microsoft-Produkte und -Technologien zu erfahren. Komplexe oder einfache Prozeduren in einem progressiven Format zu präsentieren, ist natürlich und benutzerfreundlich.

## <a name="markdown-reference"></a>MarkDown-Referenz

 Microsoft #A0 werden in der MarkDown-Syntax geschrieben und über ein [#A1](https://github.com/lunet-io/markdig) analysiert. Informationen *zu bestimmten* [Tags und Formatierungskonventionen](/contribute/markdown-reference) finden Sie unter Docs Markdown reference.

## <a name="file-paths"></a>Dateipfade

Das Festlegen eines gültigen Dateipfads für Hyperlinks in Der Dokumentation kann eine Herausforderung darstellen, insbesondere bei der Verwendung relativer Pfade und beim Erstellen von Links zu anderen Dokumenten.  Ihr Build ist auf GitHub nicht erfolgreich, wenn der Dateipfad falsch oder ungültig ist.

Weitere Informationen zu Hyperlinks und Dateipfaden finden Sie *unter* [Verwenden von Links in der Dokumentation](/contribute/how-to-write-links).

>[!IMPORTANT]
> So verweisen Sie auf einen Artikel, der *Teil des* Teams-Plattform-Docsets ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne führenden Schrägstrich.<br>
> &emsp;&#x2714; Schließen Sie die Dateierweiterung Markdown ein.<br>
>Beispiel:  **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-Article.md** -> `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> So verweisen Sie auf einen Microsoft Docs-Bibliotheksartikel, der nicht Teil *des* Teams-Plattform-Docsets ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; Schließen Sie die Dateierweiterung nicht ein. <br> Ex:  **/docset/address-to-file-location** –> `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`<br><br>
> Verwenden Sie den vollständigen Dateipfad, um auf eine Seite außerhalb der Microsoft Docs-Bibliothek zu verweisen, z. `https` B. GitHub.<br>

## <a name="code-samples-and-snippets"></a>Codebeispiele und Codeausschnitte

Codebeispiele spielen eine wichtige Rolle bei der erfolgreichen Verwendung von APIs und SDKs durch Entwickler. Gut dargestellte Codebeispiele können vermitteln, wie die Dinge besser funktionieren als beschreibender Text und Anweisungen allein. Ihre Codebeispiele sollten präzise, präzise, gut dokumentiert und vor allem leserfreundlich sein. Leicht lesbarer Code ist auch leicht zu verstehen, zu testen, zu debuggen, zu warten, zu ändern und zu erweitern. *Weitere Informationen* [finden Sie unter How to include code in docs](/contribute/code-in-docs). Tipps zur Lesbarkeit finden Sie *auch* [unter Cutting Edge : Source Code Readability Tips](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Herunterladen von Microsoft Docs-Updates und den neuesten Ankündigungen](/teamblog)
