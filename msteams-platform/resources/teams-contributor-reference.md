---
title: Beitrag zur Microsoft Teams Dokumentation
description: Schritte zum Erstellen und Veröffentlichen Teams Dokumentation
author: laujan
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: 52253bb096857e2cb883295c8ae6b58518506d9a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566229"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Beitrag zur Microsoft Teams Dokumentation

[Teams Dokumentation](/microsoftteams/platform/overview) ist Teil der technischen [Dokumentationsbibliothek von Microsoft Docs.](https://docs.microsoft.com/) Der Inhalt ist in Gruppen organisiert, die als Docsets bezeichnet werden und jeweils eine Gruppe verwandter Dokumente darstellen, die als eine einzelne Entität verwaltet werden. Artikel im gleichen Docset haben nach *Docs <span></span> .microsoft.com* dieselbe URL-Pfaderweiterung.  `/docs.microsoft.com/microsoftteams/...`Der Anfang des Teams docset-Dateipfad ist z. B. der Anfang. Teams Artikel werden in [Der MarkDown-Syntax](#markdown-reference) geschrieben und auf [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)gehostet.

## <a name="set-up-your-workspace"></a>Einrichten Ihres Arbeitsbereichs

> [!div class="checklist"]
>
> * Installieren Sie [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Installieren Sie [Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Installieren Sie [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) direkt aus dem VS Code Marketplace.
<br>&emsp;&emsp; Oder

> [!div class="checklist"]
>
> * Installieren sie von VS Code:

   1. Wählen Sie das **Symbol Erweiterungen** auf der Seitenaktivitätsleiste aus, oder verwenden Sie den Befehl **Ansicht => Erweiterungen** (Strg+Umschalt+X) und suchen Sie nach dem *Docs Authoring Pack* (Microsoft).
   1. Wählen Sie die **Schaltfläche Installieren** aus.
   1. Sobald die Installation abgeschlossen ist, wechselt die **Schaltfläche Installieren** zur Schaltfläche Getriebe **verwalten.**

## <a name="review-the-microsoft-docs-contributors-guide"></a>Lesen Sie das Microsoft Docs Contributors Guide

Das [Teilnehmerhandbuch](/contribute) bietet Anweisungen zum Erstellen, Veröffentlichen und Aktualisieren technischer Inhalte auf der Microsoft Docs-Plattform.

## <a name="microsoft-writing-style-and-content-guides"></a>Microsoft-Schrift-, Stil- und Inhaltshandbücher

* **[Microsoft Writing Style Guide](/style-guide/welcome)**. Erwägen Sie, diese Online-Anleitung zum Favoritenmenü Ihres **Browsers** hinzuzufügen. Es ist eine umfassende Ressource für das heutige technische Schreiben und spiegelt Microsofts modernen Ansatz in Bezug auf Sprache und Stil wider.

* **[Schreiben von Entwicklerinhalten](/style-guide/developer-content/)**. Teams-spezifische Inhalte richten sich an ein Entwicklerpublikum mit einem grundlegenden Verständnis von Programmierkonzepten und -prozessen. Es ist wichtig, dass Sie klare, technisch genaue Informationen auf überzeugende Weise bereitstellen und gleichzeitig den Ton und Stil von Microsoft beibehalten.

* **[Schritt-für-Schritt-Anleitungen](/style-guide/procedures-instructions/writing-step-by-step-instructions)**. Angewandte und interaktive Erlebnisse sind eine hervorragende Möglichkeit für Entwickler, sich über Microsoft-Produkte und -Technologien zu informieren. Komplexe oder einfache Verfahren in einem progressiven Format zu präsentieren, ist natürlich und benutzerfreundlich.

## <a name="markdown-reference"></a>MarkDown-Referenz

 Microsoft Docs-Seiten werden in MarkDown-Syntax geschrieben und über ein [Markdig-Modul](https://github.com/lunet-io/markdig) analysiert. Weitere Informationen finden Sie *unter* [Docs Markdown-Referenz](/contribute/markdown-reference) für bestimmte Tags und Formatierungskonventionen.

## <a name="file-paths"></a>Dateipfade

Das Festlegen eines gültigen Dateipfads für Hyperlinks in der Dokumentation kann eine Herausforderung darstellen, insbesondere wenn Sie relative Pfade verwenden und Links zu anderen Dokumenten erstellen.  Ihr Build wird auf GitHub nicht erfolgreich sein, wenn der Dateipfad falsch oder ungültig ist.

Weitere Informationen zu Hyperlinks und Dateipfaden finden Sie unter Verwenden von [Links in der Dokumentation](/contribute/how-to-write-links).

>[!IMPORTANT]
> So verweisen Sie auf einen Artikel, *der Teil des* Teams Plattform-Docset ist:<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad ohne einen führenden Schrägstrich.<br>
> &emsp;&#x2714; Die Markdown-Dateierweiterung einschließen.<br>
>Ex:  **übergeordnetes Verzeichnis/Verzeichnis/Pfad-zu-article.md** —> `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> So verweisen Sie auf einen Microsoft Docs-Bibliotheksartikel, der nicht Teil des Teams-Plattformdokumentsatz *ist:*<br>
> &emsp;&#x2714; Verwenden Sie einen relativen Pfad, der mit einem Schrägstrich beginnt.<br>
> &emsp;&#x2714; Die Dateierweiterung nicht einschließen. <br> Ex:  **/docset/address-to-file-location** —> `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`<br><br>
> Um auf eine Seite außerhalb der Microsoft Docs-Bibliothek zu verweisen, z. B. GitHub, verwenden Sie den vollständigen `https` Dateipfad.<br>

## <a name="code-samples-and-snippets"></a>Codebeispiele und Ausschnitte

Codebeispiele spielen eine wichtige Rolle bei der erfolgreichen Verwendung von APIs und SDKs. Gut präsentierte Codebeispiele können klarer kommunizieren, wie Die Dinge funktionieren, als beschreibender Text und Lehrinformationen allein. Ihre Codebeispiele sollten genau, prägnant, gut dokumentiert und vor allem leserfreundlich sein. Code, der leicht zu lesen ist, ist auch leicht zu verstehen, zu testen, zu debuggen, zu warten, zu ändern und zu erweitern. Weitere Informationen finden Sie unter [So fügen Sie Code in Dokumente](/contribute/code-in-docs)ein.

## <a name="see-also"></a>Siehe auch

* [Docs Stil und Stimme Schnellstart](/contribute/style-quick-start)
* [Cutting Edge : Source Code Readability Tipps](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Abrufen von Microsoft Docs-Updates und den neuesten Ankündigungen](/teamblog)
