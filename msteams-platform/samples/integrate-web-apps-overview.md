---
title: Integrieren von Web-Apps
author: Rajeshwari-v
description: Eine Übersicht über die Integration von Webanwendungen und Gerätefunktionen in Microsoft Teams App.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
keywords: power platform power apps people picker deep link virtual agent assistant share-to-Teams
ms.openlocfilehash: 8fe6b41f129497d439d9cf5ef391c800d6ddea0e
ms.sourcegitcommit: f892125106adb6731a20127f15d6e92f279127c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2022
ms.locfileid: "64685590"
---
# <a name="integrate-web-apps"></a>Integrieren von Web-Apps

Sie können eine erweiterte Benutzererfahrung bereitstellen, indem Sie die Features einer vorhandenen Webanwendung in Microsoft Teams Plattform integrieren. Achten Sie darauf, [Teams Designrichtlinien](~/concepts/design/understand-use-cases.md) zu befolgen, damit Ihre App Teams nativ ist.
Dieses Dokument enthält eine Übersicht über die Voraussetzungen für die Integration von Webanwendungen in Teams, Power Platform zum Erstellen von Power-Apps, Power Virtual Agents, Virtual Assistant, App-Vorlagen, Umschaltconnectors, Moodle LMS, Erstellen einer Schaltfläche "Teilen zu Teams" für Ihre Website und Hinzufügen eines Microsoft Teams  registerkarte in SharePoint, Erstellen von Deep-Links und Integrieren von Gerätefunktionen.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie für eine effektive Integration sicher, dass Sie die folgenden Voraussetzungen besser verstehen:

* Teams Funktionen.
* SharePoint Anforderungen für die Datei- und Datenspeicherung.
* API-Anforderungen.
* Authentifizierung.
* Deep-Verknüpfung Ihrer App mit Teams.
* Ordnen Sie die Anwendungsfälle Ihrer App Teams Plattformfunktionen zu.
* Bestimmen Sie die Einstiegspunkte Ihrer App, z. B. persönliche Verwendung, Zusammenarbeit oder beides.

## <a name="low-code-platforms"></a>Low-Code-Plattformen

Low-Code-Plattformen bieten einen intuitiven Ansatz für die Softwareentwicklung und erfordern nur wenig oder gar keine Codierung, um Anwendungen und Prozesse zu erstellen. Sie können benutzerdefinierte Apps auf einfache Weise mit Low-Code-Plattformen erstellen. Diese Plattformen bestehen aus einer visuellen Schnittstelle, Connectors für Back-End-Dienste und einem integrierten App-Lebenszyklusverwaltungssystem zum Erstellen, Debuggen, Bereitstellen und Verwalten von Anwendungen. Microsoft stellt die folgenden innovativen Gateways bereit, um schnell Teams-kompatible Apps mit niedrigen Codeattributen zu erstellen:

* Microsoft Power Platform
* Microsoft Teams App-Vorlagen

## <a name="microsoft-power-platform"></a>Microsoft Power Platform

Die Microsoft Power-Plattform kombiniert vier robuste Microsoft-Technologien wie Power BI, Power Apps, Power Automate und Power Virtual Agents in einer leistungsstarken Anwendungsplattform. Mit diesen Technologien können Sie Lösungen erstellen, Prozesse automatisieren, Daten analysieren und virtuelle Agents in einer einheitlichen und integrierten Umgebung erstellen.

>[!NOTE]
>Sie dürfen Microsoft Power Platform nicht verwenden, um Apps zu erstellen, die im Teams App Store veröffentlicht werden sollen. Microsoft Power Platform-Apps können nur im App Store einer Organisation veröffentlicht werden.

### <a name="power-apps"></a>Power-Apps

Mit Power Apps können Sie Geschäfts-Apps erstellen, die eine Verbindung mit Ihren Geschäftsdaten herstellen und auf die Anforderungen Ihrer Organisation zugeschnitten sind. Power Apps ermöglichen eine Vielzahl von App-Szenarien, um geschäftliche Herausforderungen mit Canvas-Apps zu lösen. Nachdem Sie die App erstellt haben, können Sie sie aus dem Power Apps Maker-Portal exportieren und in Microsoft Teams einbetten.

### <a name="power-virtual-agents"></a>Power Virtual Agents

Power Virtual Agent ist eine codelose, geführte grafische Benutzeroberflächenlösung. Es basiert auf der Microsoft Power Platform und dem Bot Framework. Es ermöglicht jedem Mitglied Ihres Teams, umfangreiche Conversational Chatbots zu erstellen und zu pflegen, die sich problemlos in die Teams-Plattform integrieren lassen. Sie können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten, einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren zu müssen.

### <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten

Virtual Assistant ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die volle Kontrolle über die Benutzererfahrung, das Branding der Organisation und die erforderlichen Daten behalten.

## <a name="app-templates"></a>App-Vorlagen

Sie können die App-Vorlage verwenden, um benutzerdefinierte Apps zu erstellen, die ihren Anforderungen ihrer Organisation entsprechen. Dies sind produktionsbereite Apps für Microsoft Teams, die communitygesteuert, open-source und auf GitHub verfügbar sind. Jede Vorlage enthält detaillierte Anweisungen zum Bereitstellen und Installieren der App für Ihre Organisation. Es bietet eine sofort einsatzbereite Anwendung, die Sie sofort installieren und verwenden können.

## <a name="teams-shifts-work-force-management-connectors"></a>Teams Shifts Work Force Management Connectors

Teams Shifts Work Force Management-Connectors sind produktionsbereite, Open Source- und Community-gesteuerte Integrationen. Sie bieten eine nahtlose Erfahrung und einen schnellen Prozess für die digitale Transformation von Mitarbeitern in Service und Produktion mit Teams Schichten.

## <a name="install-moodle-lms"></a>Installieren von Moodle LMS

Moodle ist ein beliebtes Open Source Learning Management System (LMS). Es ist jetzt in Microsoft Teams integriert. Diese Integration hilft Lehrkräften und Lehrern, an Moodle-Kursen zusammenzuarbeiten, Fragen zu Noten und Aufgaben zu stellen und mit Benachrichtigungen direkt innerhalb Teams auf dem Laufenden zu bleiben.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Erstellen einer Schaltfläche zum Teilen in Teams für Ihre Website

Websites von Drittanbietern können das Startprogrammskript verwenden, um "Freigeben" in Teams Schaltflächen auf ihren Webseiten einzubetten. Wenn Sie die Schaltfläche auswählen, wird die Schaltfläche "Freigeben" gestartet, um Teams Oberfläche in einem Popupfenster zu Teams. Auf diese Weise können Sie einen Link direkt für eine beliebige Person oder Microsoft Teams Kanal freigeben, ohne den Kontext zu wechseln.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Hinzufügen einer Microsoft Teams Registerkarte in SharePoint

Sie können eine umfassende Integrationserfahrung zwischen Microsoft Teams und SharePoint erhalten, indem Sie eine Microsoft Teams Registerkarte in SharePoint als SPFx-Webpart hinzufügen.

## <a name="create-deep-link"></a>Erstellen eines Deep-Links

Sie können Deep-Links zu den Entitäten in Teams erstellen. Sie können Links zu Informationen und Features in Teams erstellen. Diese Deep-Links navigieren zu Inhalten und Informationen auf Ihrer Registerkarte. Sie können Deep-Links verwenden, um Ihre App mit Teams zu verknüpfen, wenn sie mehrere Teile einer App miteinander verknüpfen, um eine systemeigenere Teams zu ermöglichen.

## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die an den integrierten Erfahrungen von Erstanbietern ausgerichtet sind. Die erweiterte Teams-Plattform ermöglicht Es Partnern, auf die systemeigenen Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort mit dedizierten APIs zuzugreifen und diese zu integrieren, die im JavaScript-Client-SDK Microsoft Teams verfügbar sind.

## <a name="integrate-people-picker"></a>Integration der Personenauswahl

Sie können das Teams systemeigene Personenauswahl-Steuerelement integrieren, mit dem Benutzer Personen in der Web-App suchen und auswählen können.

## <a name="integrate-teams-in-your-external-app"></a>Integrieren Teams in Ihre externe App

Sie können Ihre eigenen Erfahrungen in Microsoft Teams einbetten, indem Sie Teams Apps erstellen. Wenn Sie dieses Modell *umkehren* und Teams oder andere Kommunikationsfunktionen in Ihre eigene externe App-Umgebung integrieren möchten, lesen Sie [Azure Communication Services](/azure/communication-services/overview). Azure Communication Services sind cloudbasierte Dienste mit REST-APIs und Clientbibliotheks-SDKs, die Ihnen helfen, die Kommunikation in Ihre eigenen benutzerdefinierten Anwendungen zu integrieren. Sie können generische oder Teams-Webkomponenten im Stil von React zum Aufrufen und Chatten mit Hilfe der [Benutzeroberflächenbibliothek](https://azure.github.io/communication-ui-library/) einbetten.

Azure Communication Services-Anwendungen können öffentliche Vorschaufunktionen verwenden, um [mit Teams zu arbeiten](/azure/communication-services/concepts/teams-interop) und Ihrer benutzerdefinierten Anwendung die anonyme Teilnahme an Teams Besprechungen zu ermöglichen. Sie können beispielsweise Videoanrufe in eine Mobile Banking-Anwendung integrieren und Endbenutzern ermöglichen, sich mithilfe von Microsoft Teams virtuell mit Bankmitarbeitern zu treffen.

Sie können auch Microsoft 365 Identität integrieren, um externe Anwendungen zu erstellen, die Video- und PSTN-Anrufe im Namen eines Teams Benutzers einbetten. Wenn Sie in der Vergangenheit [Skype for Business SDKs](/skype-sdk/appsdk/skypeappsdk) verwendet haben, werden diese Funktionen als Teil Azure Communication Services als Ersatz empfohlen.

## <a name="see-also"></a>Siehe auch

* [Zuordnen der Anwendungsfälle Ihrer App zu Teams Plattformfunktionen](~/concepts/design/map-use-cases.md)
* [Ermitteln der Einstiegspunkte Ihrer App](~/concepts/extensibility-points.md)
* [Überlegungen zur Microsoft Teams-Integration](~/samples/integrating-web-apps.md)
* [Erstellen benutzerdefinierter Apps mit geringem Code für Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Hinzufügen eines Power Virtual Agent-Chatbots](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
* [Erstellen eines virtuellen Assistenten](~/samples/virtual-assistant.md)
* [App-Vorlagen für Microsoft Teams](~/samples/app-templates.md)
* [Produktionsbereite Schichtverbinder](~/samples/shifts-wfm-connectors.md)
* [Installieren von Moodle LMS](~/resources/moodleinstructions.md)
* [Freigeben für Teams aus Web-Apps](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)
* [Erstellen von Deep-Links](~/concepts/build-and-test/deep-links.md)
* [Gerätefunktionen](~/concepts/device-capabilities/device-capabilities-overview.md)
* [Steuerelement „Personenauswahl“](~/concepts/device-capabilities/people-picker-capability.md)
