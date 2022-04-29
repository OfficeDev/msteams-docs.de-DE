---
title: Debuggen von Hintergrundprozessen
author: zyxiaoyuer
description: Funktion von Visual Studio Code und Teams-Toolkit während des lokalen Debuggens
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: a3259c46927547b98700f76f704c6c5cb222a74d
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104014"
---
# <a name="debug-background-process"></a>Debuggen von Hintergrundprozessen

Der lokale Debugworkflow umfasst die Dateien `.vscode/launch.json` und `.vscode/tasks.json`, um den Debugger in Visual Studio Code zu konfigurieren, dann startet Visual Studio Code die Debugger und Microsoft Edge oder Chrome-Debugger startet wie folgt eine neue Browserinstanz:

1. Die Datei `launch.json` konfiguriert den Debugger in Visual Studio Code.

2. Visual Studio Code führt den Verbund **preLaunchTask**, **Überprüfung vor dem Debuggen und alle Starten** in der Datei `.vscode/tasks.json` aus.

3. Visual Studio Code startet dann die in den Verbundkonfigurationen angegebenen Debugger, z. B. **An Bot anfügen**, **An Back-End anfügen**, **An Front-End anfügen** und **Bot starten**.

4.  Der Microsoft Edge- oder Chrome-Debugger startet eine neue Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients.

## <a name="prerequisites"></a>Voraussetzungen

Das Teams-Toolkit überprüft während des Debugprozesses die folgenden Voraussetzungen:

* Node.js, gilt für die folgenden Projekttypen:

  |Projekttyp|Node.js LTS-Version|
  |----------|--------------------------------|
  |Registerkarte ohne Azure Functions | 10, 12, **14 (empfohlen)**, 16 |
  |Registerkarte mit Azure Functions | 10, 12, **14 (empfohlen)**|
  |Bot |  10, 12, **14 (empfohlen)**, 16|
  |Nachrichtenerweiterung | 10, 12, **14 (empfohlen)**, 16 |

   
* Microsoft 365 Konto mit gültigen Anmeldeinformationen, das Teams-Toolkit fordert Sie auf, sich bei dem Microsoft 365-Konto anzumelden, wenn Sie sich nicht bereits angemeldet haben.

* Das Hochladen oder Querladen benutzerdefinierter Apps für Ihren Entwicklermandanten ist aktiviert, wenn dies nicht der Fall ist, wird das lokale Debuggen beendet.

* Ngrok Binary Version 2.3 gilt für Bot- und Nachrichtenerweiterungen. Wenn Ngrok nicht installiert ist oder die Version nicht der Anforderung entspricht, installiert das Teams Toolkit das Ngrok NPM-Paket `ngrok@4.2.2` in `~/.fx/bin/ngrok`. Die Ngrok-Binärdatei wird vom Ngrok-NPM-Paket in `/.fx/bin/ngrok/node modules/ngrok/bin`verwaltet.

* Azure Functions Core Tools, Version 3. Wenn Azure Functions Core Tools nicht installiert ist oder die Version nicht der Anforderung entspricht, installiert das Teams-Toolkit das Azure Functions Core Tools-NPM-Paket „azure-functions-core-tools@3“ für **Windows** und für **macOs** in `~/.fx/bin/func`. Das Azure Functions Core Tools-NPM-Paket in  `~/.fx/bin/func/node_modules/azure-functions-core-tools/bin` verwaltet die Azure Functions Core Tools-Binärdatei. Bei Linux wird das lokale Debuggen beendet.

* .NET Core SDK-Version, die für Azure Functions gilt. Wenn .NET Core SDK nicht installiert ist oder die Version nicht der Anforderung entspricht, installiert das Teams-Toolkit .NET Core SDK für Windows und MacOS in `~/.fx/bin/dotnet`. Bei Linux wird das lokale Debuggen beendet.

  In der folgenden Tabelle sind die .NET Core-Versionen aufgeführt:

  | Plattform  | Software|
  | --- | --- |
  |Windows, MacOs (x64) und Linux | **3.1 (empfohlen)**, 5.0, 6.0 |
  |macOs (arm64) |6.0 |

* Entwicklungszertifikat. Wenn das Entwicklungszertifikat für localhost nicht für die Registerkarte in Windows oder macOS installiert ist, werden Sie vom Teams-Toolkit aufgefordert, es zu installieren.

* Azure Functions-Bindungserweiterungen, die in `api/extensions.csproj` definiert sind. Wenn Azure Functions-Bindungserweiterungen nicht installiert sind, installiert das Teams-Toolkit Azure Functions-Bindungserweiterungen.

* NPM-Pakete, die für die Registerkarten-App, Bot-App, Nachrichtenerweiterungs-App und Azure Functions gelten. Wenn NPM nicht installiert ist, installiert das Teams-Toolkit alle NPM-Pakete.

* Bot- und Nachrichtenerweiterung, das Teams Toolkit startet Ngrok, um einen HTTP-Tunnel für Bot- und Nachrichtenerweiterung zu erstellen

* Verfügbare Ports, wenn Registerkarten-, Bot-, Nachrichtenerweiterungs- und Azure Functions-Ports nicht verfügbar sind, wird das lokale Debuggen beendet.

  In der folgenden Tabelle sind die Ports aufgeführt, die für Komponenten verfügbar sind:

  | Komponente  | Port |
  | --- | --- |
  | Tab | 53000 |
  | Bot- oder Nachrichtenerweiterung | 3978 |
  | Knoteninspektor für Bot- oder Nachrichtenerweiterung | 9239 |
  | Azure Functions | 7071 |
  | Knoteninspektor für Azure Functions | 9229 |


<!-- The following table lists the limitations if the required software is unavailable for debugging:

|Project type|Installation| Limitation|
|----------|--------------------------------|-----|
|Tab without Azure functions | Node.js LTS versions 10, 12, **14 (recommended)**, 16 | The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Tab with Azure functions | Node.js LTS versions 10, 12, **14 (recommended)** |The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Bot | Node.js LTS versions 10, 12, **14 (recommended)**, 16|The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Message extension | Node.js LTS versions 10, 12, **14 (recommended)**, 16 |The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Sign in to Microsoft 365 account | Microsoft 365 credentials |Teams toolkit prompts you to sign in to Microsoft 365 account, if you haven't signed in. |
|Bot, message extension | Ngrok version 2.3| • If Ngrok isn't installed or the version doesn't match the requirement, the Teams toolkit installs Ngrok NPM package `ngrok@4.2.2` in `~/.fx/bin/ngrok`. </br> • The Ngrok binary is managed by Ngrok NPM package in `/.fx/bin/ngrok/node modules/ngrok/bin`.|
|Azure functions | Azure Functions Core Tools version 3| • If Azure Functions Core Tools isn't installed or the version doesn't match the requirement, the Teams toolkit installs Azure Functions Core Tools NPM package, azure-functions-core-tools@3 for **Windows** and for **macOs** in  `~/.fx/bin/func`. </br> • The Azure Functions Core Tools NPM package in  `~/.fx/bin/func/node_modules/azure-functions-core-tools/bin` manages Azure Functions Core Tools binary. For Linux, the local debug terminates.|
|Azure functions |.NET Core SDK version|• If .NET Core SDK isn't installed or the version  doesn't match the requirement, the toolkit installs .NET Core SDK for Windows and macOS in `~/.fx/bin/dotnet`.</br> • For Linux, the local debug terminates.|
|Azure functions | Azure functions binding extensions defined in `api/extensions.csproj`| If Azure functions binding extensions isn't installed, the toolkit installs Azure functions binding extensions.|
|NPM packages| NPM packages for tab app, bot app, message extension app, and Azure functions|If NPM isn't installed, the toolkit installs all NPM packages.|
|Bot and message extension | Ngrok |Toolkit starts Ngrok to create a HTTP tunnel for bot and message extension. |

> [!NOTE]
> If tab, bot, message extension, and Azure functions ports are unavailable, the local debug terminates.

Use the following .NET Core versions:

| Platform  | Software|
| --- | --- |
|Windows, macOs (x64), Linux | **3.1 (recommended)**, 5.0, 6.0 |
|macOs (arm64) |6.0 |


> [!NOTE]
> If the development certificate for localhost isn't installed for tab in Windows or macOS, the Teams toolkit prompts you to install it.</br> -->


Wenn Sie **Start Debugging (F5)** auswählen, zeigt der Ausgabekanal des Teams-Toolkits den Fortschritt und das Ergebnis an, nachdem die Voraussetzungen überprüft wurden.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/prerequisites-debugcheck.png" alt-text="Voraussetzungen":::

## <a name="register-and-configure-your-teams-app"></a>Registrieren und Konfigurieren Ihrer Teams-App

Im Einrichtungsprozess bereitet das Teams-Toolkit die folgenden Registrierungen und Konfigurationen für Ihre Teams-App vor:

1. [Registriert und konfiguriert Azure AD-Anwendung](#registers-and-configures-azure-ad-application): Teams-Toolkit registriert und konfiguriert Ihre Azure AD-Anwendung.

1. [Registriert und konfiguriert Bot](#registers-and-configures-bot): Teams-Toolkit registriert und konfiguriert Ihren Bot für die Registerkarten- oder Nachrichtenerweiterungs-App.

1. [Registriert und konfiguriert Teams-App](#registers-and-configures-teams-app): Teams-Toolkit registriert und konfiguriert Ihre Teams-App.

### <a name="registers-and-configures-azure-ad-application"></a>Registriert und konfiguriert Azure AD-Anwendung

1. Registriert eine Azure AD-Anwendung.

1. Erstellt einen geheimen Clientschlüssel.

1. Macht eine API verfügbar.

    a. Konfiguriert den Anwendungs-ID-URI. Für Registerkarte, `api://localhost/{appId}`. Für Bot- oder Nachrichtenerweiterung,  `api://botid-{botid}`.

    b. Fügt einen Bereich mit dem Namen `access_as_user` hinzu. Aktiviert es für **Administratoren und Benutzer**.


4. Konfiguriert API-Berechtigungen. Fügt **User.Read** die Microsoft Graph-Berechtigung hinzu.

    In der folgenden Tabelle ist die Konfiguration der Authentifizierung wie folgt aufgeführt:
    
      | Projekttyp | Umleitungs-URIs für das Web | Umleitungs-URIs für eine einseitige Anwendung |
      | --- | --- | --- |
      | Tab | `https://localhost:53000/auth-end.html` | `https://localhost:53000/auth-end.html?clientId={appId>}` |
      | Bot- oder Nachrichtenerweiterung | `https://ngrok.io/auth-end.html` | – |

    In der folgenden Tabelle sind die Konfigurationen der Microsoft 365-Clientanwendung mit den Client-IDs aufgeführt:
    
      | Microsoft 365-Clientanwendung |  Client-ID  |
      | --- | --- |
      | Teams-Desktop, Mobil | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
      | Teams-Web | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
      | Office.com | 4345a7b9-9a63-4910-a426-35363201d503 |
      | Office.com | 4765445b-32c6-49b0-83e6-1d93765276ca |
      | Office-Desktop | 0ec893e0-5785-4de6-99da-4ed124e5296c |
      | Outlook Desktop | d3590ed6-52b3-4102-aeff-aad2292ab01c |
      | Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
      | Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |
    
### <a name="registers-and-configures-bot"></a>Registriert und konfiguriert den Bot 

Für Registerkarten-App oder Nachrichtenerweiterungs-App:

1. Registriert eine Azure AD-Anwendung.

1. Erstellt einen geheimen Clientschlüssel für die Azure AD-Anwendung.

1. Registriert einen Bot in [Microsoft Bot Framework](https://dev.botframework.com/) mithilfe der Azure AD-Anwendung.

1. Fügt Microsoft Teams-Kanal hinzu.

1. Konfiguriert den Messaging-Endpunkt als `https://{ngrokTunnelId}.ngrok.io/api/messages`.

### <a name="registers-and-configures-teams-app"></a>Registriert und konfiguriert Teams-App

Registriert eine Teams-App in [Entwickler](https://dev.teams.microsoft.com/home) mithilfe der Manifestvorlage in `templates/appPackage/manifest.template.json`.

Nach dem Registrieren und Konfigurieren der App werden lokale Debugdateien generiert.

## <a name="take-a-tour-of-your-app-source-code"></a>Machen Sie einen Rundgang durch den Quellcode Ihrer App

Sie können die Projektordner und -dateien im Explorer-Bereich von Visual Studio Code anzeigen, nachdem das Teams-Toolkit Ihre App registriert und konfiguriert hat. In der folgenden Tabelle sind die lokalen Debugdateien und die Konfigurationstypen aufgeführt:

| Ordnername| Inhalt| Debugkonfigurationstyp |
| --- | --- | --- |
|  `.fx/configs/config.local.json` | Lokale Debugkonfigurationsdatei | Die Werte jeder Konfiguration werden während des lokalen Debuggens generiert und gespeichert. |
|  `templates/appPackage/manifest.template.json` | Teams-App-Manifestvorlagendatei für lokales Debuggen | Die Platzhalter in der Datei werden während des lokalen Debuggens aufgelöst. |
|  `tabs/.env.teams.local`  | Umgebungsvariablendatei für Registerkarte  | Die Werte jeder Umgebungsvariable werden während des lokalen Debuggens generiert und gespeichert. |
|  `bot/.env.teamsfx.local` | Umgebungsvariablendatei für Bot- und Nachrichtenerweiterung| Die Werte jeder Umgebungsvariable werden während des lokalen Debuggens generiert und gespeichert. |
| `api/.env.teamsfx.local`  | Umgebungsvariablendatei für Azure Functions | Die Werte jeder Umgebungsvariable werden während des lokalen Debuggens generiert und gespeichert. |

## <a name="see-also"></a>Siehe auch

[Debuggen Ihrer Teams-App mithilfe des Teams-Toolkits](debug-local.md)
