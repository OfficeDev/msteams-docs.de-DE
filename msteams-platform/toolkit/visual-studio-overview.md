---
title: Erstellen von Apps mit dem Teams Toolkit und Visual Studio
description: Erste Schritte beim Erstellen von großartigen benutzerdefinierten Apps direkt in Visual Studio mit dem Microsoft Teams Toolkit. Erfahren Sie, wie Sie Ihre App in Visual Studio konfigurieren, ihre App überprüfen und über Visual Studio und das Entwicklerportal veröffentlichen.
keywords: Visual Studio-Toolkit für Teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: johmil
ms.openlocfilehash: af4f4c1511460e79a99d437dbcc75e2c748d1506
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60888013"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Erstellen von Apps mit dem Teams Toolkit und Visual Studio

Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen. Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.

## <a name="prerequisites"></a>Voraussetzungen

1. [Aktivieren Sie die Entwicklervorschau.](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

2. Stellen Sie sicher, dass das **<span>ASP.NET-</span> und Webentwicklungsmodul** zu Ihrer Visual Studio Instanz hinzugefügt wurde. Weitere Informationen finden Sie unter [Ändern Visual Studio durch Hinzufügen oder Entfernen von Workloads und Komponenten.](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true)

![Visual Studio asp.net-Modul](../assets/images/visual-studio-web-dev-module.png)

## <a name="install-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Microsoft Teams Toolkit für Visual Studio steht im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit) oder direkt im Menü **"Erweiterungen"** in Visual Studio zum Download zur Verfügung.

## <a name="use-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Ausführen Ihrer App in Teams](#install-and-run-your-app-locally)
- [Validieren Ihrer App](#validate-your-app)
- [Veröffentlichen eigener Apps](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams Projekts

1. Starten Sie Visual Studio 2019.
2. Wählen Sie **"Neues Projekt erstellen"** aus.
3. Suchen Sie nach **Microsoft Teams App,** und wählen Sie **"Weiter"** aus.
4. Geben Sie im **Feld "Neues Projekt konfigurieren"** den **Namen Project,** **den Speicherort** und den **Projektmappennamen ein.**
5. Wählen Sie **"Weiter"** aus, um einen Namen für die App einzugeben.
6. Geben Sie im Bildschirm "Zusätzliche Informationen" einen **Anwendungs-** und **Entwickler- oder Firmennamen** für Ihre Teams-App ein.

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams App drei Komponenten:

- Der Microsoft Teams Client (Web, Desktop oder Mobil), auf dem Benutzer mit Ihrer App interagieren.
- Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden. Beispiel: HTML-Registerkarteninhalt oder eine adaptive Bot-Karte.
- Ein Teams-App-Paket besteht aus drei Dateien:

    > [!div class="checklist"]
    >
    > - Manifest.json
    > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen App- oder Organisations-App-Katalog angezeigt werden soll.
    > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige auf der Teams Aktivitätsleiste.

Wenn eine App installiert ist, analysiert der Teams Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter der sich die Dienste befinden.

> [!NOTE]
>Wenn dies noch nicht geschehen ist, müssen Sie sich bei Ihrem Microsoft 365 Konto anmelden, um den Entwicklungsprozess fortzusetzen.
>
> Wenn Sie nicht über ein Microsoft 365 Konto verfügen, können Sie sich für ein [Abonnement für Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist 90 Tage kostenlos und wird verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise oder Professional Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement,](https://aka.ms/MyVisualStudioBenefits)das für die Lebensdauer Ihres Visual Studio Abonnements aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements.](/office/developer-program/office-365-developer-program-get-started)

### <a name="configuration-steps"></a>Konfigurationsschritte 

1. Um Ihre App zu konfigurieren, wählen Sie das Menü **Project > TeamsFx > Konfigurieren für SSO...** aus.

Wenn Sie dazu aufgefordert werden, melden Sie sich bei Ihrem Microsoft-Konto an, das über einen M365-Mandanten verfügt.

## <a name="install-and-run-your-app-locally"></a>Lokales Installieren und Ausführen der App

Drücken Sie F5, um das Debuggen zu starten. Das Dialogfeld für die App-Installation wird im Teams Client angezeigt.

## <a name="validate-your-app"></a>Validieren Ihrer App

Mit **dem Menü Project > TeamsFx Validate > Teams Manifest** können Sie überprüfen, ob Ihr App-Paket gültig ist.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

Im [Teams Entwicklerportal](https://dev.teams.microsoft.com/home)können Sie Ihre App in ein Team hochladen, Ihre App an den benutzerdefinierten App Store Ihres Unternehmens für Benutzer in Ihrer Organisation übermitteln oder Ihre App für alle Teams Benutzer an app Source übermitteln.

- Ihr IT-Administrator wird diese Übermittlungen überprüfen.
- Sie können zur **Veröffentlichungsseite** zurückkehren, um ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App übermitteln oder alle derzeit aktiven Übermittlungen abbrechen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit Demerz](../get-started/first-app-blazor.md)
