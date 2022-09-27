---
title: Erstellen einer neuen Teams-App in Visual Studio
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie eine neue Teams-App mithilfe des Teams-Toolkits für Visual Studio erstellen.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 07/29/2022
ms.openlocfilehash: 12f0b74726aed8cdca50d9f5c078acd0f22cbeaa
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027455"
---
# <a name="create-new-teams-app-in-visual-studio"></a>Erstellen einer neuen Teams-App in Visual Studio

Das Teams-Toolkit stellt Microsoft Teams-App-Vorlagen in Visual Studio zum Erstellen der Teams-App bereit.  Sie können die Teams-App-Vorlage suchen und auswählen, die Sie benötigen, wenn Sie ein neues Projekt erstellen. Sie können Teams-App-Vorlagen zum Erstellen verwenden.

* Registerkarten-App
* Befehlsbot
* Benachrichtigungs-Bot
* Nachrichtenerweiterung

## <a name="prerequisites"></a>Voraussetzungen

| &nbsp; | Installieren | Zum Benutzen... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio, Version 17.3 | Sie können die Enterprise-Edition von Visual Studio und die "ASP.NET" Workload und Microsoft Teams-Entwicklungstools installieren. |
| &nbsp; | Teams Toolkit | Eine Visual Studio-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie die neueste Version. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort. |
 | &nbsp; | [Vorbereiten Ihres Microsoft 365-Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md) | Zugriff auf das Teams-Konto mit den entsprechenden Berechtigungen zum Installieren einer App. |

1. Wählen Sie beim Starten von Visual Studio im Abschnitt **"Erste Schritte**" die Option "**Neues Projekt erstellen**" aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project1.png" alt-text="Erstellen eines neuen Projekts von Anfang an":::

   Sie können ein neues Projekt auch direkt aus der Anwendung erstellen.

1. Wählen Sie das Menü **"Datei** " aus.
1. Wählen Sie  **"Neu**" aus.
1. Wählen Sie **"Projekt**" aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project2.png" alt-text="Erstellen eines neuen Projekts über das Menü &quot;Datei&quot;":::

1. Suchen Sie in der Liste nach der Microsoft **Teams-App** .
1. Wählen Sie **die Microsoft Teams-App aus**.
1. Wählen Sie **Weiter** aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app.png" alt-text="Suchen und Auswählen der Microsoft Teams-App":::

1. Wählen Sie **"Projektname** " aus, und geben Sie Ihren Projektnamen ein.
1. Wählen Sie **Erstellen** aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app-project-name.png" alt-text="Benennen Der Anwendung":::

1. Wählen Sie den **Teams-App-Typ** aus, den Sie erstellen möchten.
1. Wählen Sie **Erstellen** aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app-type.png" alt-text="Auswählen des Teams-App-Typs":::

## <a name="teams-app-templates-in-teams-toolkit-for-visual-studio"></a>Teams-App-Vorlagen im Teams-Toolkit für Visual Studio

Sie können Teams-App-Vorlagen sehen, die bereits im Teams-Toolkit für verschiedene Teams-App-Typen aufgefüllt wurden. In der folgenden Tabelle sind alle verfügbaren Vorlagen aufgeführt:

|Teams-App-Vorlage  |Beschreibung  |
|---------|---------|
|Benachrichtigungs-Bot     |Die Benachrichtigungs-Bot-App kann Benachrichtigungen an Ihren Teams-Client senden. Es gibt mehrere Möglichkeiten, die Benachrichtigung auszulösen. Lösen Sie z. B. die Benachrichtigung per HTTP-Anforderung oder nach Zeit aus. Sie können auch ausgelöste Benachrichtigungen basierend auf Ihrem Geschäftsszenario auswählen.         |
|Befehls-Bot     |Benutzer können einen Befehl eingeben, um mithilfe der Command Bot-App mit dem Bot zu interagieren.         |
|Tab     |Die Registerkarten-App zeigt eine Webseite in Teams an und ermöglicht einmaliges Anmelden mithilfe des Teams-Kontos.         |
|Nachrichtenerweiterung     |Die Nachrichtenerweiterungs-App implementiert einfache Features wie das Erstellen einer adaptiven Karte, die Suche nach Nugget-Paketen und das Erweitern von Links für die Domäne "dev.botframework.com".         |

> [!NOTE]
>Nachdem das Projekt erstellt wurde, wird das Teams-Toolkit automatisch "Erste Schritte" geöffnet. Sie können nun die Anweisungen in "Erste Schritte" sehen und sich die verschiedenen Features im Teams-Toolkit ansehen.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
