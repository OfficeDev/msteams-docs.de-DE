---
title: Microsoft Teams-Entwicklerdokumentation – Glossar
description: Glossar für Microsoft Teams Entwicklerdokumentation
ms.localizationpriority: medium
ms.topic: reference
keywords: Microsoft Teams Entwicklerdefinition
ms.openlocfilehash: 0858d0cfb246e99871c02f81c82c1eaa30bb6edf
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059831"
---
# <a name="glossary"></a>Glossar

Allgemeine Begriffe und Definitionen, die in Teams Entwicklerdokumentation verwendet werden.
<br>
<br>
<details>
<summary>Ein</summary>

| Begriff | Definition |
| --- | --- |
| Aktionsbefehl | Aktionsbefehle werden verwendet, um benutzern ein modales Popup anzuzeigen, um Informationen zu sammeln oder anzuzeigen. <br>**Siehe auch**: Messaging-Erweiterung; Suchbefehle |
| Adaptive Karte | Eine adaptive Karte ist ein Aktionen erfordernder Inhaltsausschnitt, den Sie einer Unterhaltung über einen Bot oder eine Messaging-Erweiterung hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen ermöglichen diese Karten eine umfassende Kommunikation mit Ihrer Zielgruppe. |
| App-Katalog | Der App-Katalog wird verwendet, um die Apps für SharePoint und Office für die interne Verwendung unserer Organisation zu speichern. |
| App-Manifest | Das Teams App-Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird. Ihr Manifest muss dem schema gehosteten https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json entsprechen. |
| App-Paket | Ein Teams App-Paket ist eine ZIP-Datei mit der App-Manifestdatei und App-Symbolen – Farbsymbol und Gliederungssymbol. |
| App-Berechtigungen | Mit der App-Berechtigungsoption in Teams können Sie die Geräteberechtigungen der App für Ihre App aktivieren. Sie ist nur verfügbar, wenn die Manifestdatei der App deklariert, dass die App Geräteberechtigungen benötigt. <br> **Siehe auch:** Geräteberechtigungen |
| App-Bereich | Der App-Bereich bestimmt, wie Ihre App mit Ihren Benutzern interagiert. Eine App kann einen persönlichen, Kanal- oder Teambereich haben. Eine Teams App kann bereichsübergreifend vorhanden sein. |
| App-Studio | App Studio ist eine App, um mit dem Erstellen oder Integrieren Ihrer eigenen Microsoft Teams-Apps zu beginnen. Sie wurde nun zum Entwicklerportal weiterentwickelt. <br> **Siehe auch**: Entwicklerportal |
| Azure-Ressource | Ein Dienst, der über Azure verfügbar ist, den Ihre Teams-App für die Azure-Bereitstellung verwenden kann. Dabei kann es sich um Speicherkonten, Web-Apps, Datenbanken und vieles mehr handeln. |
| Azure Active Directory | Azure Active Directory (Azure AD) ist der cloudbasierte Identitäts- und Zugriffsverwaltungsdienst von Microsoft. Es hilft authentifizierten Benutzern, auf interne und externe Azure-Ressourcen zuzugreifen. |
| Authentifizierung | Die Authentifizierung ist ein Prozess zum Autorisieren des Benutzerzugriffs für die Nutzung Ihrer App. Dies kann mithilfe von Microsoft Graph-APIs oder der webbasierten Authentifizierung erfolgen. <br> **Siehe auch**: Identitätsanbieter |
| Authentifizierungsfluss | In Teams gibt es zwei verschiedene Authentifizierungsflüsse, um einen Benutzer für die Verwendung einer App zu authentifizieren: webbasierte Authentifizierung und OAuthPrompt-Fluss. |
|
</details>
<br>
<details>
<summary>B</summary>

| Begriff | Definition |
| --- | --- |
| Aufzungsmesser | Dies ist ein kostenloses und Open-Source-Webframework, mit dem Entwickler Web-Apps mit C# und HTML erstellen können. Sie können interaktive Web-Benutzeroberflächen mit C# anstelle von JavaScript erstellen. Mischungs-Apps bestehen aus wiederverwendbaren Web-UI-Komponenten, die mit C#, HTML und CSS implementiert werden. Es wird von Microsoft entwickelt. |
| Bizeps | Bicep ist eine deklarative Sprache, was bedeutet, dass die Elemente in beliebiger Reihenfolge angezeigt werden können. Im Gegensatz zu imperativen Sprachen wirkt sich die Reihenfolge der Elemente nicht auf die Verarbeitung der Bereitstellung aus. |
| Bot | Ein Bot ist eine App, die programmierte wiederholte Aufgaben ausführt. <br> **Siehe auch**: Unterhaltungsbot; Chat-Bot |
| Bot-Emulator | Bot Framework Emulator ist eine Desktopanwendung, mit der Sie Bots lokal oder remote testen und debuggen können. |
| Bot Framework | Das Bot Framework ist ein umfangreiches SDK, das zum Erstellen von Bots mit C#, Java, Python und JavaScript verwendet wird. Wenn Sie bereits über einen Bot verfügen, der auf bot Framework basiert, können Sie ihn einfach so ändern, dass er in Teams funktioniert. |
</details>
<br>
<details>
<summary>C</summary>

| Begriff | Definition |
| --- | --- |
| Bot aufrufen | Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt. <br> **Siehe auch**: Chat-Bot; Besprechungsbot |
| Funktion | Das Feature einer Teams-App wird als Funktion bezeichnet. Eine App kann über eine oder mehrere Kernfunktionen verfügen, z. B. Registerkarte, Bot, Messaging-Erweiterungen. <br>**Siehe auch:** Gerätefunktion; Medienfunktion |
| Chat-Bot | Ein Bot wird auch als Chatbot oder Unterhaltungs-Bot bezeichnet. Es handelt sich um eine App, die einfache und sich wiederholende Aufgaben von Benutzern wie Kundendienst oder Supportmitarbeitern ausführt. <br> **Siehe auch**: Unterhaltungs-Bot. |
| Kanal | Ein Kanal ist ein einzelner Ort für ein Team zum Freigeben von Nachrichten, Tools und Dateien. In Teams erfolgt Teamarbeit und Kommunikation in Kanälen.  |
| Geheimer Clientschlüssel | Der geheime Clientschlüssel/das Kennwort oder ein öffentliches oder privates Schlüsselpaar, bei dem es sich um ein Zertifikat handelt. Dies ist für systemeigene Apps nicht erforderlich. <br> **Siehe auch**: Bot |
| Cloudressourcen | Ein Dienst, der über das Internet in der Cloud verfügbar ist, den Ihre Teams-App verwenden kann. Dabei kann es sich um Speicherkonten, Web-Apps, Datenbanken und vieles mehr handeln. |
| Zusammenarbeits-App |  <br> **Siehe auch**: Eigenständige App |
| Connectors |  <br> **Siehe auch**: Webhooks |
| Unterhaltung | Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams Bot und einem oder mehreren Benutzern gesendet werden. Eine Unterhaltung kann drei Bereiche haben: Kanal-, persönliche und Gruppenchat. <br>**Siehe auch:** Einzelchat; Gruppenchat |
| Unterhaltungsbot |  Unterhaltungs-Bots ermöglichen Benutzern die Interaktion mit Ihrem Webdienst mithilfe von Text, interaktiven Karten und Aufgabenmodulen. <br>**See aso** Chat-Bot |