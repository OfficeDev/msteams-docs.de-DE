---
title: Integrieren von Web-Apps
author: Rajeshwari-v
description: Ein Überblick über die Integration von Webanwendungen und Gerätefunktionen mit der Teams-Anwendung.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
keywords: Power Plattform Power Apps People Picker Deep Link Virtueller Agent Assistent Share-to-Teams
ms.openlocfilehash: dc31644fca25aeca12b7e5f3095ebae53a3c02ac
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757668"
---
# <a name="integrate-web-apps"></a>Integrieren von Web-Apps

Durch die Integration der Funktionen einer bestehenden Webanwendung in die Microsoft Teams-Plattform können Sie die Benutzererfahrung verbessern. Achten Sie darauf, die [Microsoft Teams-Designrichtlinien](~/concepts/design/understand-use-cases.md) zu befolgen, um native Apps für Microsoft Teams zu erstellen.
Dieses Dokument gibt einen Überblick über die Voraussetzungen für die Integration von Webanwendungen in Teams, die Power-Plattform zur Erstellung von Power-Apps, Power Virtual Agents, Virtual Assistant, App-Vorlagen, Shift-Konnektoren, Moodle LMS, das Erstellen einer Share-to-Teams-Schaltfläche für Ihre Website, das Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint, das Erstellen von Deep Links und die Integration von Gerätefunktionen.

## <a name="prerequisites"></a>Voraussetzungen

Um eine wirksame Integration zu erreichen, sollten Sie die folgenden Voraussetzungen besser verstehen:

* Fähigkeiten der Teams.
* SharePoint-Anforderungen für die Datei- und Datenspeicherung.
* API-Anforderungen.
* Authentifizierung.
* Tiefe Verknüpfung Ihrer Anwendung mit Teams.
* Ordnen Sie die Anwendungsfälle Ihrer App zu Funktionen der Microsoft Teams-Plattform zu.
* Bestimmen Sie die Einstiegspunkte für Ihre App, z. B. persönliche Nutzung, Zusammenarbeit oder beides.

## <a name="low-code-platforms"></a>Low-Code-Plattformen

Low-Code-Plattformen bieten einen intuitiven Ansatz für die Softwareentwicklung und erfordern wenig oder gar keine Codierung, um Anwendungen und Prozesse zu erstellen. Sie können benutzerdefinierte Apps ganz einfach mit Low-Code-Plattformen erstellen. Diese Plattformen bestehen aus einer grafischen Benutzeroberfläche, Connectors für Back-End-Dienste und einem integrierten App-Lebenszyklusverwaltungssystem zum Erstellen, Debuggen, Bereitstellen und Verwalten von Anwendungen. Microsoft bietet die folgenden innovativen Gateways, um schnell Teams-kompatible Anwendungen mit niedrigen Code-Attributen zu erstellen:

* Microsoft Power-Plattform
* App-Vorlagen für Microsoft Teams

## <a name="microsoft-power-platform"></a>Microsoft Power-Plattform

Die Microsoft Power-Plattform vereint vier robuste Microsoft-Technologien, wie Power BI, Power Apps, Power Automate und Power Virtual Agents, in einer leistungsstarken Anwendungsplattform. Mit diesen Technologien können Sie Lösungen erstellen, Prozesse automatisieren, Daten analysieren und virtuelle Agents in einer einheitlichen und integrierten Umgebung erstellen.

>[!NOTE]
>Sie dürfen mit Microsoft Power Platform erstellte Apps nicht im Teams App Store veröffentlichen. Microsoft Power Platform-Apps können nur im App Store einer Organisation veröffentlicht werden.

### <a name="power-apps"></a>Power Apps

Mit Power Apps können Sie Geschäftsanwendungen erstellen, die mit Ihren Geschäftsdaten verbunden sind und auf die Bedürfnisse Ihres Unternehmens zugeschnitten sind. Power Apps ermöglicht eine breite Palette von Anwendungsszenarien, um geschäftliche Herausforderungen durch Canvas-Anwendungen zu lösen. Nachdem Sie die Anwendung erstellt haben, können Sie sie aus dem Power Apps Maker Portal exportieren und in Microsoft Teams einbetten.

### <a name="power-virtual-agents"></a>Power Virtual Agents

Power Virtual Agent ist eine codefreie, geführte grafische Schnittstellenlösung. Es basiert auf der Microsoft Power Platform und dem Bot Framework. Es ermöglicht jedem Mitglied Ihres Teams, umfangreiche Konversations-Chatbots zu erstellen und zu verwalten, die problemlos in die Teams-Plattform integriert werden können. Sie können intelligente virtuelle Agenten für Teams entwerfen, entwickeln und veröffentlichen, ohne dass Sie eine Entwicklungsumgebung einrichten, einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren müssen.

### <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten

Virtual Assistant ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die volle Kontrolle über die Benutzererfahrung, das Branding und die erforderlichen Daten behalten.

## <a name="app-templates"></a>App-Vorlagen

Sie können App-Vorlagen verwenden, um maßgeschneiderte Apps zu erstellen, die Ihren organisatorischen Anforderungen entsprechen. Dies sind produktionsreife Anwendungen für Microsoft Teams, die von der Community betrieben werden, Open-Source sind und auf GitHub zur Verfügung stehen. Jede Vorlage enthält detaillierte Anweisungen für die Bereitstellung und Installation der Anwendung in Ihrem Unternehmen. Es handelt sich um eine gebrauchsfertige Anwendung, die Sie installieren und sofort nutzen können.

## <a name="install-moodle-lms"></a>Installieren von Moodle LMS

Moodle ist ein beliebtes Open-Source-Lernmanagementsystem (LMS). Es ist jetzt in Microsoft Teams integriert. Mit dieser Integration können Pädagogen und Lehrer in Moodle-Kursen zusammenarbeiten, Fragen zu Noten und Aufgaben stellen und mit Benachrichtigungen direkt in Teams auf dem Laufenden bleiben.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Erstellen einer Schaltfläche zum Teilen in Teams für Ihre Website

Websites von Drittanbietern können das Launcher-Skript verwenden, um Schaltflächen für die Weitergabe an Teams in ihre Webseiten einzubetten. Wenn Sie die Schaltfläche auswählen, wird die Funktion Für Teams freigeben in einem Popup-Fenster geöffnet. So können Sie einen Link direkt an eine beliebige Person oder einen Microsoft Teams-Kanal weitergeben, ohne den Kontext zu wechseln.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint

Sie können eine vielfältig nutzbare Integration zwischen Microsoft Teams und Sharepoint erhalten, indem Sie eine Microsoft Teams-Registerkarte in SharePoint als SPFx-Webpart hinzufügen.

## <a name="create-deep-link"></a>Deep Link erstellen

Sie können Deep Links zu den Entitäten in Teams erstellen. Sie können Links zu Informationen und Features in Teams erstellen. Diese Deep Links navigieren zu Inhalten und Informationen innerhalb Ihrer Registerkarte. Sie können Deep Links verwenden, um Ihre App mit Teams zu verknüpfen, da sie mehrere Teile einer App für ein nativeres Teams-Erlebnis miteinander verbinden.

## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an integrierten First-Party-Erfahrungen ausrichten. Die erweiterte Teams-Plattform ermöglicht Partnern den Zugriff auf und die Integration von nativen Gerätefunktionen wie Kamera, QR- oder Barcode-Scanner, Fotogalerie, Mikrofon und Standort mithilfe spezieller APIs, die im Microsoft Teams JavaScript Client SDK verfügbar sind.

## <a name="integrate-people-picker"></a>Integration der Personenauswahl

Sie können das native People-Picker-Steuerelement von Teams integrieren, mit dem Benutzer in der Web-Applikation Personen suchen und auswählen können.

## <a name="integrate-teams-in-your-external-app"></a>Integrieren Sie Teams in Ihre externe Anwendung

Sie können Ihre eigenen Erfahrungen in Microsoft Teams einbetten, indem Sie Teams-Anwendungen erstellen. Wenn Sie dieses Modell *umkehren* und Teams oder andere Kommunikationsfunktionen in Ihre eigene externe App integrieren möchten, lesen Sie [Azure Communication Services](/azure/communication-services/overview). Azure Communication Services sind Cloud-basierte Dienste mit REST-APIs und SDKs für Client-Bibliotheken, mit denen Sie die Kommunikation in Ihre eigenen benutzerdefinierten Anwendungen integrieren können. Sie können generische oder im Teams-Stil formatierte React-Webkomponenten für Anrufe und Chats mithilfe der [UI-Bibliothek](https://azure.github.io/communication-ui-library/) einbetten.

Azure Communication Services Anwendungen können öffentliche Vorschaufunktionen verwenden, um [mit Teams zu zusammenarbeiten](/azure/communication-services/concepts/teams-interop) und Ihrer benutzerdefinierten Anwendung zu ermöglichen, anonym an Teams-Besprechungen teilzunehmen. So können Sie beispielsweise Videogespräche in eine mobile Bankanwendung integrieren und Endbenutzern ermöglichen, sich mit Hilfe von Microsoft Teams virtuell mit Bankmitarbeitern zu treffen.

Sie können auch die Microsoft 365-Identität integrieren, um externe Anwendungen zu erstellen, die Video- und PSTN-Anrufe im Namen eines Benutzers von Teams einbetten. Wenn Sie [Skype for Business SDKs](/skype-sdk/appsdk/skypeappsdk) in der Vergangenheit verwendet haben, werden diese Funktionen als Teil Azure Communication Services als Ersatz empfohlen.

## <a name="see-also"></a>Siehe auch

* [Zuordnung der Anwendungsfälle Ihrer Anwendung zu den Funktionen der Teams-Plattform](~/concepts/design/map-use-cases.md)
* [Bestimmen Sie die Einstiegspunkte für Ihre Anwendung](~/concepts/extensibility-points.md)
* [Überlegungen zur Microsoft Teams-Integration](~/samples/integrating-web-apps.md)
* [Erstellen von benutzerdefinierten Low-Code-Anwendungen für Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Hinzufügen eines Power Virtual Agent-Chatbots](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
* [Virtuellen Assistenten erstellen](~/samples/virtual-assistant.md)
* [App-Vorlagen für Microsoft Teams](~/samples/app-templates.md)
* [Produktionsfertige Schaltsteckverbinder](~/samples/shifts-wfm-connectors.md)
* [Installieren von Moodle LMS](~/resources/moodleinstructions.md)
* [Von Web-Apps für Teams freigeben](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)
* [Erstellen von Deep-Links](~/concepts/build-and-test/deep-links.md)
* [Gerätefunktionen](~/concepts/device-capabilities/device-capabilities-overview.md)
* [Steuerelement „Personenauswahl“](~/concepts/device-capabilities/people-picker-capability.md)
