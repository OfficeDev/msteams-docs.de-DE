---
title: Microsoft Teams-Entwicklerdokumentation – Glossar
description: Erfahren Sie mehr über die allgemeinen Begriffe, Bedeutungen und Definitionen, die in der Microsoft Teams-Entwicklerdokumentation verwendet werden.
ms.localizationpriority: high
ms.topic: reference
ms.openlocfilehash: 74717387d83e32e240a21b83d87a89bcb4591145
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791440"
---
# <a name="glossary"></a>Glossar

Allgemeine Begriffe und Definitionen, die in der Microsoft Teams-Entwicklerdokumentation verwendet werden.

## <a name="a"></a>Ein

| Begriff | Definition |
| --- | --- |
| [Aktionsbefehl](../messaging-extensions/how-to/action-commands/define-action-command.md) | Eine Art von Nachrichtenerweiterungs-App, die ein Popup verwendet, um Informationen zu sammeln oder anzuzeigen. <br>**Siehe auch**: [Nachrichtenerweiterung](#m);[Suchbefehle](#s) |
| [Adaptive Karten](../task-modules-and-cards/what-are-cards.md) | Ein umsetzbarer Inhaltsausschnitt, der einer Unterhaltung von einem Bot oder einer Nachrichtenerweiterung hinzugefügt wird. Verwenden Sie Text, Grafiken und Schaltflächen mit diesen Karten für eine umfassende Kommunikation. |
| [App-Katalog](../toolkit/publish.md) | Eine Website, die SharePoint- und Office-Apps für die interne Verwendung einer Organisation speichert. <br>**Weitere Informationen unter**: [SPFx](#s) |
| [App-Manifest](../resources/schema/manifest-schema.md) | Das Teams App-Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird. Das Manifest muss dem [Manifestschema](https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json) entsprechen. |
| [App-Paket](../concepts/build-and-test/apps-package.md) | Ein Teams-App-Paket ist eine ZIP-Datei, die die App-Manifestdatei, das Farbsymbol und das Gliederungssymbol enthält. |
| [App-Berechtigung](../concepts/device-capabilities/browser-device-permissions.md#enable-apps-device-permissions) | Eine Option in einer Teams-App zum Aktivieren von Geräteberechtigungen. Sie ist nur verfügbar, wenn die Manifestdatei der App deklariert, dass die App Geräteberechtigungen benötigt. <br> **Siehe auch**: [Geräteberechtigungen](#d) |
| [App-Bereich](../concepts/design/understand-use-cases.md#app-scope) | Ein Bereich in Teams, in dem Personen Ihre App verwenden können. Apps können einen oder mehrere Bereiche haben, darunter Privat, Kanäle, Chats und Besprechungen. Eine Teams-App kann bereichsübergreifend vorhanden sein. |
| Anwendungsleiste | Eine Anwendungsleiste, die sich auf der unteren Leiste einer mobilen Teams-App befindet. Sie sammelt alle Apps, die geöffnet sind, aber derzeit nicht verwendet werden oder deaktiviert sind. <br>**Weitere Informationen unter**: [Teams Mobile](#t) |
| [Azure-Ressource](../toolkit/provision.md) | Ein über Azure verfügbarer Dienst, den Ihre Teams-App für die Azure-Bereitstellung verwenden kann. Dabei kann es sich um Speicherkonten, Web-Apps, Datenbanken und vieles mehr handeln. |
| [Azure Active Directory](../tabs/how-to/authentication/auth-tab-aad.md) | Der cloudbasierte Identitäts- und Zugriffsverwaltungsdienst von Microsoft. Sie hilft authentifizierten Benutzern beim Zugriff auf interne und externe Ressourcen. |
| [Authentifizierung](../concepts/authentication/authentication.md) | Der Prozess zum Überprüfen der Identität eines Benutzers für den Zugriff auf Ihre App. <br> **Weitere Informationen**: [Identitätsanbieter](#i); [SSO](#s) |
| [Authentifizierungsfluss](../concepts/authentication/authentication.md) | Die Art und Weise, wie sich ein Benutzer bei Ihrer App authentifiziert. Für Teams-Apps wird die Verwendung des einmaligen Anmeldens (Single Sign On, SSO) mit Azure Active Directory (AAD) empfohlen, eine Alternative besteht darin, einen OAuth-Drittanbieter zu verwenden.|

## <a name="b"></a>B

| Begriff | Definition |
| --- | --- |
| [Blazor](../get-started/get-started-overview.md) | A free and open-source web framework that enables developers to create web apps using C# and HTML. It's being developed by Microsoft. |
| [Bicep](../toolkit/provision.md) | Eine deklarative Sprache, was bedeutet, dass die Elemente in beliebiger Reihenfolge erscheinen können. Im Gegensatz zu imperativen Sprachen hat die Reihenfolge der Elemente keinen Einfluss darauf, wie die Bereitstellung verarbeitet wird. |
| [Bot](../bots/what-are-bots.md): | Ein Bot ist eine App, die programmierte wiederholte Aufgaben ausführt. <br> **Weitere Informationen unter**: [Unterhaltungsbot](#c); [Chat-Bot](#c) |
| [Bot-Emulator](../bots/how-to/debug/locally-with-an-ide.md#use-the-bot-emulator) | Eine Desktop-Anwendung, mit der Sie Bots entweder lokal oder remote testen und debuggen können. |
| [Bot Framework](../bots/bot-features.md) | Ein umfangreiches SDK zum Erstellen von Bots mit C#, Java, Python und JavaScript. Wenn Sie einen Bot haben, der auf dem Bot Framework basiert, können Sie ihn so ändern, dass er in Teams funktioniert. |

## <a name="c"></a>C

| Begriff | Definition |
| --- | --- |
| [Bot aufrufen](../bots/calls-and-meetings/calls-meetings-bots-overview.md) | Ein Bot, der an Audio- oder Videoanrufen und Online-Besprechungen teilnimmt. <br> **Weitere Informationen unter**: [Chat-Bot](#c); [Besprechungsbot](#m) |
| [Funktionalität](../toolkit/add-capability.md) | Ein Teams Feature, das Sie in Ihre App für die Interaktion mit App-Benutzern integrieren können. Eine App-Funktion wird verwendet, um Teams an Ihre App-Anforderungen anzupassen. Eine App kann über eine oder mehrere Kernfunktionen verfügen, z. B. Registerkarte, Bot und Nachrichtenerweiterung. <br>**Weitere Informationen unter**: [Gerätefunktion](#d); [Medienfunktion](#m) |
| [Chat-Bot](../bots/how-to/conversations/conversation-basics.md) | Ein Bot wird auch als Chatbot oder Unterhaltungsbot bezeichnet. Es handelt sich um eine App, die einfache und sich wiederholende Aufgaben für Benutzern ausführt, z. B. Kundendienst- oder Supportmitarbeiter. <br> **Weitere Informationen unter**: [Unterhaltungs-Bot](#c) |
| Kanal | Ein zentraler Ort, an dem ein Team Nachrichten, Tools und Dateien gemeinsam nutzen kann. Sie können einen Kanal für Teamarbeit und Kommunikation verwenden. <br>**Weitere Informationen unter**: [Unterhaltung](#c) |
| [Geheimer Clientschlüssel](../bots/how-to/authentication/add-authentication.md) | Eine geheime Zeichenfolge, die die Anwendung verwendet, um ihre Identität beim Anfordern eines Tokens nachzuweisen. Es kann auch als Anwendungskennwort bezeichnet werden.|
| [Cloudressourcen](../toolkit/add-resource.md) | Ein Dienst, der in der Cloud über das Internet verfügbar ist und von Ihrer Teams-App verwendet werden kann. Dabei kann es sich um Speicherkonten, Web-Apps, Datenbanken und vieles mehr handeln. |
| [Apps für die Zusammenarbeit](../concepts/extensibility-points.md) | Eine App mit Funktionen, mit denen ein Benutzer in einem kollaborativen Arbeitsbereich mit anderen Benutzern arbeiten kann. <br> **Weitere Informationen unter**: [Eigenständige App](#s) |
| [Verfassen-Erweiterung](../resources/schema/manifest-schema.md#composeextensions) | Eine Eigenschaft im App-Manifest (`composeExtensions`), die auf die Nachrichtenerweiterungsfunktion verweist. Es wird verwendet, wenn sich Ihre Erweiterung entweder authentifizieren oder konfigurieren muss, um fortzufahren. <br>**Weitere Informationen**: [App-Manifest](#a); [Nachrichtenerweiterung](#m) |
| [CommandBox](../resources/schema/manifest-schema.md) | Ein Kontexttyp im App-Manifest (`commandBox`), den Sie konfigurieren können, um eine Nachrichtenerweiterung über das Teams-Befehlsfeld aufzurufen. |
| [Connector](../webhooks-and-connectors/what-are-webhooks-and-connectors.md) | Damit können Benutzer den Empfang von Benachrichtigungen und Nachrichten von den Webdiensten abonnieren. Connectors machen den HTTPS-Endpunkt für den Dienst verfügbar, um Nachrichten in Teams-Kanälen zu posten, in der Regel in Form von Karten. <br> **Weitere Informationen unter**: [Webhook](#w) |
| Unterhaltung | Eine Reihe von Nachrichten, die zwischen Ihrer Microsoft Teams-App (Registerkarte oder Bot) und einem oder mehreren Benutzern gesendet werden. Eine Unterhaltung kann drei Bereiche haben: Kanal-, Privat- und Gruppen-Chat. <br>**Weitere Informationen unter**: [1:1-Chat](#o); [Gruppen-Chat](#g); [Kanal](#c) |
| [Unterhaltungs-Bot](../bots/how-to/conversations/conversation-messages.md) |  Er ermöglicht einem Benutzer, mithilfe von Text, interaktiven Karten und Aufgabenmodulen mit Ihrem Webdienst zu interagieren. <br>**Weitere Informationen unter** [Chat-Bot](#c) |

## <a name="d"></a>D

| Begriff | Definition |
| --- | --- |
| [Deep Linking](../concepts/build-and-test/deep-links.md) | In einer Teams-App können Sie Deep Links zu Informationen und Funktionen in Teams erstellen oder dem Benutzer helfen, zu Inhalten in Ihrer App zu navigieren. |
|[Verteidigungsministerium (DoD, Department of Defense)](../concepts/app-fundamentals-overview.md#government-community-cloud)| DoD-Umgebungen erfüllen die Richtlinien für Sicherheitsanforderungen des Us-Verteidigungsministeriums, DFARS -Ergänzung (Defense Federal Acquisition Regulations) und International Traffic in Arms Regulations (ITAR).|
| [Entwicklerportal für Teams](../concepts/build-and-test/teams-developer-portal.md) | Das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps. Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr. |
| [Developer Preview](../resources/dev-preview/developer-preview-intro.md) | Ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht freigegebene Features in Microsoft Teams bietet. Damit können Sie bevorstehende Features erkunden und testen, um eine potenzielle Einbindung in Ihre Microsoft Teams-App zu ermöglichen. |
| Bereitstellen | Ein Prozess zum Upload des Back-End- und Front-End-Codes für die Anwendung. Bei der Bereitstellung wird der Code für Ihre App in die Ressourcen kopiert, die Sie während der Bereitstellung erstellt haben. <br>**Weitere Informationen**: [Bereitstellung](#p) |
| [Gerätefunktionen](../concepts/device-capabilities/device-capabilities-overview.md) | Integrierte Geräte, z. B. Kamera, Mikrofon, Strichcodescanner, Fotogalerie auf Mobilgeräten oder Desktops. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in Microsoft Teams JavaScript-Client-SDK verfügbar sind. <br>**Weitere Informationen unter**: [Funktion](#c); [Medienfunktion](#m); [Standortfunktion](#l) |
| [Geräteberechtigung](../concepts/device-capabilities/browser-device-permissions.md) | Eine Teams App-Einstellung, die Sie in Ihrer App konfigurieren können. Sie verwenden diese, um die Berechtigung für Ihre App anzufordern, auf eine systemeigene Gerätefunktion zuzugreifen und diese zu nutzen. Sie können Geräteberechtigungen in Team- Einstellungen verwalten. <br>**Weitere Informationen unter**: [App-Berechtigungen](#a) |
| [Entwicklungsumgebung](../toolkit/TeamsFx-multi-env.md#create-new-environment) | Ein Entwicklungsumgebungstyp, den das Teams Toolkit standardmäßig erstellt. Es stellt Konfigurationen der Remote- oder Cloudumgebung dar. Ein Projekt kann mehrere Remoteumgebungen aufweisen. Mit Teams Toolkit können Sie Ihrem Projekt weitere Entwicklungsumgebungen hinzufügen. <br>**Weitere Informationen unter** [Umgebung](#e); [Lokale Umgebung](#l) |
| [DevTools](../tabs/how-to/developer-tools.md) | Die DevTools des Browsers werden verwendet, um Konsolenprotokolle anzuzeigen, Laufzeitnetzwerkanforderungen anzuzeigen oder zu ändern, Code (JavaScript) Haltepunkte hinzuzufügen und interaktives Debuggen für eine Teams App durchzuführen. Das Feature ist nur für Desktop- und Android-Clients verfügbar, nachdem die Entwicklervorschau aktiviert wurde. |
| [Dynamische Suche](../task-modules-and-cards/cards/dynamic-search.md#dynamic-typeahead-search) | Ein Suchfeature für adaptive Karten, das hilfreich ist, um Daten aus großen Datasets zu suchen und auszuwählen. Es hilft beim Herausfiltern der Auswahl, wenn der Benutzer die Suchzeichenfolge eingibt. <br>**Weitere Informationen unter**: [Statische Suche](#s) |

## <a name="e"></a>E

| Begriff | Definition |
| --- | --- |
| [E5-Entwicklerkonto](../toolkit/tools-prerequisites.md#accounts-to-build-your-teams-app) | E5-Entwicklerabonnement zum Erstellen von Apps zur Erweiterung von Microsoft 365. Es umfasst bis zu 25 Benutzerlizenzen, einschließlich des Administrators (nur für Entwicklungszwecke).  <br>**Weitere Informationen unter**: [Microsoft 365 Konto](#m) |
| [Einstiegspunkt](../concepts/app-fundamentals-overview.md) | Ein Zugriffspunkt, z. B. Team, Kanal und Chat, für eine Teams App, in der Benutzer Ihre App verwenden können. |
| [Umgebung](../toolkit/teamsfx-multi-env.md) | Ein Feature im Teams-Toolkit, mit dem Sie mehrere Entwicklungsumgebungen für Ihr App-Projekt erstellen und verwenden können. Es gibt zwei Entwicklungsumgebungen, die Teams Toolkit standardmäßig erstellt, lokale Umgebung und Entwicklungsumgebung. <br>**Weitere Informationen unter**: [Lokale Umgebung](#l); [Entwicklungsumgebung](#d) |

## <a name="f"></a>F

| Begriff | Definition |
| --- | --- |
| [Erste Ausführung](../concepts/design/design-teams-app-ui-templates.md)|Eine First-Run-Experience (FRE) ist die Einführung eines Benutzers in Ihr Produkt. Die FRE hilft Benutzern bei den ersten Schritten mit den Funktionen, Features und Vorteilen des Produkts und beeinflusst die Benutzer, wieder zurückzukommen und Ihr Produkt weiterhin zu verwenden.|

## <a name="g"></a>G

| Begriff | Definition |
| --- | --- |
|[Government Community Cloud (GCC)](../concepts/app-fundamentals-overview.md#government-community-cloud)| Die GCC-Umgebung bietet die Einhaltung der Bundesanforderungen für Clouddienste, einschließlich FedRAMP High, DFARS -Ergänzung (Defense Federal Acquisition Regulations, DFARS) und Anforderungen für Strafjustiz- und Bundessteuerinformationssysteme (CJI- und FTI-Datentypen).|
|[Government community cloud (GCC) High](../concepts/app-fundamentals-overview.md#government-community-cloud)|GCC High-Umgebungen erfüllen die Sicherheitsanforderungen des Verteidigungsministeriums (Department of Defense, DoD), DFARS (Defense Federal Acquisition Regulations Supplement) und International Traffic in Arms Regulations (ITAR).<br>**Siehe auch**: [Department of Defense (DoD)](#d)|
| [Graph-API](../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) | Eine RESTful-Web-API für Microsoft Graph, mit der Sie auf Microsoft Cloud-Dienstressourcen zugreifen können. <br>**Weitere Informationen unter**: [Microsoft Graph Explorer](#m) |
| [Gruppen-Chat](../resources/bot-v3/bot-conversations/bots-conversations.md) | Ein Chat-Feature, bei dem ein Benutzer mit einem Bot in einer Gruppeneinstellung chatten kann, indem er @mention verwendet, um den Bot aufzurufen. <br>**Weitere Informationen unter**: [1:1-Chat](#o); [Chat-Bot](#c) |

## <a name="i"></a>I

| Begriff | Definition |
| --- | --- |
| [Identitätsanbieter](../concepts/authentication/authentication.md) | Eine Entität, die Anmeldeinformationen speichert und dem Benutzer zur Verfügung stellt. Es ermöglicht benutzern auch, sich selbst zu registrieren.  <br>**Weitere Informationen unter**: [Authentifizierung](#a) |
| [Eingehender Webhook](../webhooks-and-connectors/how-to/add-incoming-webhook.md) | Eine externe App kann Inhalte in Teams-Kanälen freigeben. Diese Webhooks werden als Nachverfolgungs- und Benachrichtigungstools verwendet. <br>**Weitere Informationen unter**: [Webhook](#w); [Ausgehender Webhook](#o) |
| [In-Meeting-App-Umgebung](../apps-in-teams-meetings/teams-apps-in-meetings.md) | A stage of Teams meeting lifecycle. With the in-meeting app experience, you can engage participants during the meeting by using apps and the in-meeting dialog box. <br>**Weitere Informationen unter**: [Besprechungslebenszyklus](#m) |

## <a name="l"></a>L

| Begriff | Definition |
| --- | --- |
| [Verbreiten von Links](../messaging-extensions/how-to/link-unfurling.md) | Eine Funktion, die bei der Nachrichtenerweiterung und Besprechungen verwendet wird, um Links zu öffnen, die in einen Bereich zum Verfassen von Nachrichten eingefügt werden. Die Links werden erweitert, um zusätzliche Informationen zu dem Link in adaptiven Karten oder in der Besprechungsphasenansicht anzuzeigen. |
| [Lokale Umgebung](../toolkit/TeamsFx-multi-env.md#create-new-environment) | Eine standardmäßige Entwicklungsumgebung, die von Teams Toolkit erstellt wurde.  <br>**Weitere Informationen unter**: [Umgebung](#e); [Entwicklungsumgebung](#d) |
| [Lokale Workbench](../sbs-gs-spfx.yml) | Die Standardoption zum Ausführen und Debuggen einer Teams-App in Visual Studio Code, die mit SPFx erstellt wird. <br>**Weitere Informationen unter**: [Workbench](#w); [Teams Workbench](#t) |
| [Standortfunktion](../concepts/device-capabilities/location-capability.md) | A device capability that you can integrate with your app to know the geographical location of the app user for an enhanced collaborative experience. This feature is currently available only for Teams mobile clients only. <br>**Weitere Informationen unter**: [Funktion](#c); [Medienfunktion](#m); [Gerätefunktion](#d); [Teams Mobile](#t) |
| [Apps mit geringem Code](../samples/teams-low-code-solutions.md) | Eine benutzerdefinierte Teams-App, die mithilfe der Microsoft Power Platform von Grund auf neu erstellt wurde und wenig oder gar keine Codierung erfordert und schnell entwickelt und bereitgestellt werden kann. |

## <a name="m"></a>M

| Begriff | Definition |
| --- | --- |
| [Medienfunktion](../concepts/device-capabilities/media-capabilities.md) | Systemeigene Gerätefunktionen wie Kamera und Mikrofon, die Sie in Ihre Teams App integrieren können. <br>**Weitere Informationen unter**: [Funktion](#c); [Gerätefunktion](#d) |
| [Besprechungsbot](../bots/calls-and-meetings/calls-meetings-bots-overview.md) | Bots, die mit Teams-Anrufen und Besprechungen interagieren, verwenden Sprach-, Video- und Bildschirmfreigabe in Echtzeit. <br>**Weitere Informationen unter**: [Anruf-Bot](#c); [Chat-Bot](#c) |
| [Der Besprechungslebenszyklus](../apps-in-teams-meetings/teams-apps-in-meetings.md) | Es umfasst App-Erfahrungen vor der Besprechung, während sowie nach der Besprechung. Sie können Registerkarten, Bots und Nachrichtenerweiterungen in jeder Phase des Besprechungslebenszyklus integrieren. <br>**Weitere Informationen unter**: [Besprechungserfahrung](#i) |
| [Besprechungsphase](../sbs-meetings-stage-view.yml) | Ein Feature der Besprechungserweiterungs-App. Es handelt sich um einen freigegebenen Bereich, auf den alle Teilnehmer während der Besprechung zugriffen können. Es hilft Teilnehmern, in Echtzeit mit App-Inhalten zu interagieren und zusammenzuarbeiten. <br>**Weitere Informationen unter**: [Phasenansicht](#s) |
| [Nachrichtenerweiterung](../messaging-extensions/what-are-messaging-extensions.md) | Message extensions are shortcuts for inserting app content or acting on a message. You can use a message extension without navigating away from the conversation. <br>**Weitere Informationen unter**: [Suchbefehle](#s); [Aktionsbefehle](#a) |
| [Besprechungserweiterung](../apps-in-teams-meetings/design/designing-apps-in-meetings.md) | Eine App, die während des Besprechungslebenszyklus verwendet werden soll, um sie produktiver zu machen, wie z. B. Whiteboard, Dashboard und viele mehr. |
| [Microsoft 365 Konto](../toolkit/accounts.md#microsoft-365-developer-account-types) | Microsoft 365 Konto umfasst 25 Benutzerlizenzen, einschließlich des Administrators, nur für Entwicklungszwecke. |
| [Microsoft 365-Entwicklerprogramm](../toolkit/tools-prerequisites.md)| Das Microsoft 365-Entwicklerprogramm hilft Ihnen beim Erstellen von Apps, die Microsoft 365 erweitern. |
| [Microsoft Graph-Tester](../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) | The gateway to data and intelligence in Microsoft 365. It provides a unified programmability model that you can use to access data in Microsoft 365, Windows 10, and Enterprise Mobility + Security. |
| [Microsoft Teams](../overview.md) | Microsoft Teams ist eine Software für die Gruppenzusammenarbeit, die verwendet werden kann, um Teams bei der Remotearbeit zu unterstützen. |
| [Microsoft Teams-Plattform](../concepts/app-fundamentals-overview.md) | Die Microsoft Teams Entwicklerplattform erleichtert Entwicklern die Integration eigener Apps und Dienste in Teams. |
| [Microsoft Teams-Benutzeroberflächenbibliothek](../concepts/design/design-teams-app-ui-templates.md#microsoft-teams-ui-library) | Microsoft Teams Benutzeroberflächenbibliothek hilft Ihnen, einzelne Teams Benutzeroberflächenvorlagen und zugehörige Komponenten in Ihrem Browser anzuzeigen und zu testen. |
| [Microsoft Teams-Benutzeroberflächentoolkit](../concepts/design/design-teams-app-ui-templates.md#microsoft-teams-ui-library) | Microsoft Teams-Benutzeroberflächentoolkit enthält Komponenten und Muster, die speziell für die Erstellung Teams Apps entwickelt wurden. |

## <a name="o"></a>O

| Begriff | Definition |
| --- | --- |
| [Office 365-Connector](../webhooks-and-connectors/how-to/connectors-creating.md) | Sie können eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und diese als Teil einer Teams-App verpacken. Sie können Nachrichten in erster Linie mit Office 365 Connectorkarten senden und ihnen eine begrenzte Anzahl von Kartenaktionen hinzufügen. |
| [Ausgehender Webhook](../webhooks-and-connectors/how-to/add-outgoing-webhook.md) | Er fungiert als Bot und sucht mithilfe von @mention nach Nachrichten in Kanälen. Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten. <br>**Weitere Informationen unter**: [Webhook](#w); [Eingehender Webhook](#i) |
| [Outlook-Kanal](../m365-apps/extend-m365-teams-message-extension.md#add-an-outlook-channel-for-your-bot) | Eine Funktion der Teams-Nachrichtenerweiterungs-App, mit der die Benutzer von Microsoft Outlook aus interagieren können. |
| [1:1-Chat](../resources/bot-v3/bot-conversations/bots-conv-personal.md) | Ein Chattyp zwischen der persönlichen Bot-App von Teams und einem einzelnen Benutzer. <br>**Weitere Informationen unter**: [Gruppen-Chat](#g); [Chat-Bot](#c) |

## <a name="p"></a>P

| Begriff | Definition |
| --- | --- |
| [Personenauswahl](../task-modules-and-cards/cards/people-picker.md) | Ein systemeigenes Steuerelement in der Teams-Plattform zum Suchen und Auswählen von Personen, das in Web-Apps, adaptive Karten und vieles mehr integriert werden kann. |
| [Persönliche App](../concepts/design/personal-apps.md) | Eine persönliche App ist eine Teams Anwendung mit einem persönlichen Bereich. Der Schwerpunkt liegt auf Interaktionen mit einem einzelnen Benutzer. Es kann sich um einen 1:1-Unterhaltungs-Bot handeln, um Einzelgespräche mit einem Benutzer zu führen, oder um eine persönliche Registerkarte, die ein eingebettetes Weberlebnis bietet, oder beides. <br>**Weitere Informationen unter**: [Freigegebene App](#s) |
| [Power Virtual Agents](../bots/how-to/add-power-virtual-agents-bot-to-teams.md) | Eine codefreie grafische Oberflächenlösung, mit der jedes Mitglied Ihres Teams umfassende Chat-Bots für Unterhaltungen erstellen kann, die problemlos in die Teams-Plattform integriert werden können. |
| [Proaktive Nachrichten](../bots/how-to/conversations/send-proactive-messages.md) | Eine Von einem Bot gesendete Nachricht, die nicht als Reaktion auf eine Anforderung eines Benutzers gesendet wird, z. B. Willkommensnachrichten, Benachrichtigungen, geplante Nachrichten. |
| [Bestimmung](../toolkit/provision.md) | A process that creates resources in Azure and Microsoft 365 for your app, but no code (HTML, CSS, JavaScript, etc.) is copied to the resources. It's a prerequisite to deployment. <br>**Weitere Informationen unter**: [Bereitstellen](#d) |

## <a name="r"></a>R

| Begriff | Definition |
| --- | --- |
| [Begrenzung der Datenübertragungsrate](../bots/how-to/rate-limit.md) | Eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken, um sicherzustellen, dass die Anzahl der Nachrichten ausreichend ist und nicht als Spam angezeigt wird. |
| [Rollenbasierte Ansichten](../task-modules-and-cards/cards/universal-actions-for-adaptive-cards/user-specific-views.md) | Ein Feature von Registerkarten, bei der die Registerkartenerfahrung für Benutzer je nach Berechtigungsstufe unterschiedlich sein kann. |
| [RSC-Berechtigung](../graph-api/rsc/resource-specific-consent.md) | Die Berechtigungsfunktion für ressourcenspezifische Zustimmung (RSC) wird von Teambesitzern benötigt, damit eine Bot-App Nachrichten über Kanäle in einem Team empfangen kann, ohne @erwähnt zu werden. |

## <a name="s"></a>S

| Begriff | Definition |
| --- | --- |
| [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) | Eine Art von Nachrichtenerweiterungs-App, mit der Benutzer externe Systeme durchsuchen und das Suchergebnis mithilfe einer Karte in eine Nachricht einfügen können. <br>**Weitere Informationen unter**: [Nachrichtenerweiterungen](#m); [Aktionsbefehle](#a) |
| [Sequenzieller Workflow](../task-modules-and-cards/cards/universal-actions-for-adaptive-cards/sequential-workflows.md) | Ein Workflow, mit dem ein Bot basierend auf der Benutzerantwort eine Unterhaltung mit einem Benutzer durchführen kann. |
| [Freigegebene App](../concepts/extensibility-points.md#shared-app-experiences) | Eine App, die in einem Team, Kanal oder Chat vorhanden ist, in der Benutzer zusammenarbeiten und interagieren können. <br>**Weitere Informationen unter:** Persönliche App |
| [SharePoint Websitesammlung](../sbs-gs-spfx.yml) | A collection site for SharePoint apps. You need to have an administrator account for this site before you can deploy your SPFx-based app on the SharePoint site. <br>**Weitere Informationen unter**: SPFx |
| [Querladen](../toolkit/publish.md#publish-to-individual-scope-or-sideload-permission) | Ein Prozess, bei dem eine Teams-App auf den Teams-Client geladen wird, um sie in der Teams Umgebung zu testen, bevor sie verteilt wird. |
| [SidePanel](../sbs-meetings-sidepanel.yml) | Eine Funktion der Teams-Besprechungs-App, mit der Sie Erfahrungen in einer Besprechung anpassen können, die es Organisatoren und Referenten ermöglicht, unterschiedliche Ansichten und Aktionen zu haben. |
| [SPFx](../sbs-gs-spfx.yml) | SharePoint Framework (SPFx) ist ein Entwicklungsmodell zum Erstellen clientseitiger Lösungen für Microsoft Teams und SharePoint. |
| SSO | Akronym für Single Sign-On, eine Authentifizierungsmethode, bei der sich ein Benutzer nur einmal bei einem unabhängigen Dienst einer Softwareplattform (z. B. Microsoft 365) anmelden muss. Der Benutzer kann dann auf alle Dienste zugreifen, ohne sich erneut authentifizieren zu müssen. <br>**Weitere Informationen unter**: [Authentifizierung](#a) |
| [Phasenansicht](../sbs-meetings-stage-view.yml) | A user interface component that lets you render the content that is opened in full screen in Teams and pinned as a tab. It's invoked to surface web content within Teams. Note that it is *not* the same as meeting stage. <br>**Weitere Informationen unter**: [Besprechungsfreigabefenster](#m) |
| [Eigenständige App](../samples/integrating-web-apps.md) | Eine einzelne Seite oder eine große und komplexe App. Der Benutzer kann einige Aspekte davon in Teams verwenden. <br>**Weitere Informationen unter**: [Zusammenarbeits-AAP](#c) |
| [Statische Suche](../task-modules-and-cards/cards/dynamic-search.md) | Eine Methode der Schnelleingabesuche, mit der Benutzer nach vordefinierten Werten in der Payload der adaptiven Karten suchen können. <br>**Weitere Informationen unter**: [Dynamische Suche](#d) |
| [Richtlinien für die Store-Validierung](../concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) | Eine Reihe von Teams-spezifischen Richtlinien zum Überprüfen einer App, bevor sie an Teams Store übermittelt werden kann. <br>**Weitere Informationen unter**: [Teams Store](#t) |

## <a name="t"></a>T

| Begriff | Definition |
| --- | --- |
| [Tab](../tabs/what-are-tabs.md) | Registerkarten sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind, welche auf Domänen verweisen, die im Manifest deklariert sind. Sie können sie in einem Team, einem Gruppenchat oder einer persönlichen App hinzufügen. |
| [Registerkartenchat](../tabs/how-to/conversational-tabs.md) | Ein Registerkartentyp, mit dem ein Benutzer eine fokussierte Unterhaltungserfahrung auf dynamischen Registerkarten haben kann. |
| [Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md) | Eine Funktion der Teams-App zum Erstellen eines modalen Popups zum Abschließen von Aufgaben, Anzeigen von Videos oder Dashboards. |
| [Diskussionsthread](../tabs/design/tabs.md#thread-discussion) | Eine Unterhaltung, die in einem Kanal oder Chat zwischen Benutzern gepostet wird. <br>**Weitere Informationen unter** [Unterhaltung](#c); [Kanal](#c) |
| [Microsoft Teams](../overview.md) | Microsoft Teams is the ultimate message app for your organization. It's a workspace for real-time collaboration and communication, meetings, file and app sharing. |
| [Teams Toolkit](../toolkit/teams-toolkit-fundamentals.md) | Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen.  |
| [TeamsFx](../toolkit/teamsfx-cli.md) | TeamsFx is a text-based command line interface that accelerates Teams application development. It's also called TeamsFx CLI.|
| [TeamsFx SDK](../toolkit/teamsfx-sdk.md) | TeamsFx SDK ist im Gerüstprojekt mithilfe des TeamsFx-Toolkits oder der CLI vorkonfiguriert. |
| [TeamsJS-SDK](../tabs/how-to/using-teams-client-sdk.md) | Mit dem TeamsJS-SDK können Sie gehostete Erfahrungen in Teams erstellen. Ab TeamsJS v.2.0.0 können Sie Teams-Apps so erweitern, dass sie in Outlook und Office ausgeführt werden können. |
| [Teams Mobile](../concepts/design/plan-responsive-tabs-for-teams-mobile.md) | Microsoft Teams als mobile App verfügbar. |
| [Teams Store](../concepts/deploy-and-publish/appsource/publish.md) | Eine Store-Angebotsseite, die Apps für Benutzer an einem zentralen Ort bereitstellt. Die Apps sind nach Verwendung, Branche und anderem kategorisiert. Eine App muss Store Validierungsrichtlinien folgen und eine Genehmigung einholen, bevor sie benutzern über den Teams Store zur Verfügung steht.  <br>**Weitere Informationen unter**: [Store-Validierungsrichtlinien](#s) |
| [Teams Workbench](../sbs-gs-spfx.yml) | Eine Workbench in Visual Studio Code beim Erstellen für Teams Apps verwendet, die mit SPFx und Teams Toolkit erstellt wurden. <br>**Weitere Informationen unter**: [Workbench](#w); [Lokale Workbench](#l) |

## <a name="u"></a>U

| Begriff | Definition |
| --- | --- |
| [Benutzeroberflächenkomponenten](../concepts/design/design-teams-app-basic-ui-components.md) | Für Teams App-Entwicklung können Sie Fluent Benutzeroberflächenkomponenten verwenden, um Ihre App von Grund auf neu zu erstellen. |
| [Vorlagen für Benutzeroberflächen](../concepts/design/design-teams-app-ui-templates.md) | Für Teams App-Entwicklung können Sie Teams Benutzeroberflächenvorlagen verwenden, um Ihre Apps schnell zu entwerfen. |
| [Universal-Aktionen für adaptive Karten](../task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) | Eine Möglichkeit, die Adaptive Karten plattform- und anwendungsübergreifend zu implementieren. Sie verwenden einen Bot als allgemeines Back-End für die Behandlung von Aktionen. |

## <a name="v"></a>V

| Begriff | Definition |
| --- | --- |
| [Virtual Assistant](../samples/virtual-assistant.md) | Eine Microsoft Open Source-Vorlage, mit der Sie eine stabile Unterhaltungslösung erstellen können. |

## <a name="w"></a>W

| Begriff | Definition |
| --- | --- |
| [Website-URL](../tabs/design/tabs-mobile.md) | A property in the app manifest file (`websiteUrl`) that links the app to the website of the organization or landing page of the relevant product. It's a mandatory configuration for Teams mobile client. <br>**Weitere Informationen unter**: [App-Manifest](#a); [Teams Mobile](#t) |
| [Web-App](../samples/integrate-web-apps-overview.md) | Eine App, die auf einem Webserver ausgeführt wird. Sie kann in der Microsoft Teams-Plattform integriert werden. |
| [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md) | Ein Feature einer Teams-App, das verwendet wird, um sie in externe Apps zu integrieren. <br>**Weitere Informationen unter**: Eingehender Webhook; Ausgehender Webhook |
| [Webpart](../sbs-gs-spfx.yml) | Eine Benutzeroberflächenkomponente, die zum Erstellen einer Seite oder einer Website in einer Teams App verwendet wird, die mit Visual Studio Code und SharePoint-Framework erstellt wurde. <br>**Weitere Informationen unter**: [SPFx](#s) |
| [Workbench](../sbs-gs-spfx.yml) | Allgemeine Visual Studio Code-Benutzeroberfläche, die Benutzeroberflächenkomponenten wie Titelleiste, Panel und mehr umfasst. <br>**Weitere Informationen unter**: [Lokale Workbench](#l); [Teams Workbench](#t) |

## <a name="y"></a>v

| Begriff | Definition |
| --- | --- |
| [YoTeams](../get-started/get-started-overview.md) | Ein Entwicklungs-Toolkit zum Erstellen Microsoft Teams Anwendungen, die auf TypeScript und node.js basieren. |
