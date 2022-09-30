---
title: Häufig gestellte Fragen
author: MuyangAmigo
description: In diesem Modul finden Sie häufig gestellte Fragen zum Teams-Toolkit mit Visual Studio Code
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 6a6c6599ff036cf7b81dd30b00e5608db3dc4cc2
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243375"
---
# <a name="faq-for-teams-toolkit"></a>Häufig gestellte Fragen zum Teams-Toolkit

Die häufig gestellten Fragen (FAQ) finden Sie in allen Abschnitten des Teams-Toolkits für Visual Studio Code.

Häufig gestellte Fragen zur [Bereitstellung von Cloudressourcen mithilfe des Teams-Toolkits](provision.md)

<br>

<details>

<summary><b>Wie kann ich Fehler beheben?</b></summary>

Wenn Sie Fehler mit dem Teams-Toolkit in Visual Studio Code erhalten, können Sie **hilfe** zu der Fehlerbenachrichtigung auswählen, um zum zugehörigen Dokument zu wechseln. Wenn Sie TeamsFx CLI verwenden, befindet sich am Ende der Fehlermeldung ein Hyperlink, der auf das Hilfedokument verweist. Sie können auch direkt das [Hilfedokument zur Bereitstellung](https://aka.ms/teamsfx-arm-help) anzeigen.

<br>

</details>

<details>

<summary><b>Wie kann ich während der Bereitstellung zu einem anderen Azure-Abonnement wechseln?</b></summary>

1. Wechseln Sie das Abonnement im aktuellen Konto oder melden Sie sich ab und wählen Sie ein neues Abonnement aus.
2. Wenn Sie die aktuelle Umgebung bereits bereitgestellt haben, müssen Sie eine neue Umgebung erstellen und die Bereitstellung durchführen, da ARM das Verschieben von Ressourcen nicht unterstützt.
3. Wenn Sie die aktuelle Umgebung nicht bereitgestellt haben, können Sie die Bereitstellung direkt auslösen.

<br>

</details>

<details>

<summary><b>Wie kann ich die Ressourcengruppe während der Bereitstellung ändern?</b></summary>

Vor der Bereitstellung werden Sie gefragt, ob Sie eine neue Ressourcengruppe erstellen oder eine vorhandene verwenden möchten. Sie können in diesem Schritt einen neuen Ressourcengruppennamen angeben oder einen vorhandenen auswählen.

<br>

</details>

<details>

<summary><b>Wie kann ich eine Sharepoint-basierte Anwendung bereitstellen?</b></summary>

Sie können [SharePoint-basierte Anwendungen bereitstellen](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4).

> [!NOTE]
> Derzeit verfügt die Erstellung von Teams-Apps mit Sharepoint-Framework mit Teams Toolkit nicht über eine direkte Integration mit Azure, die Inhalte im Dokument gelten nicht für SPFx-basierte Apps.

<br>

</details>
