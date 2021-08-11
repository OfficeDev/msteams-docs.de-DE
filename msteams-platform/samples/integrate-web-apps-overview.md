---
title: Integrieren von Web-Apps
author: Rajeshwari-v
description: Eine Übersicht über die Integration von Webanwendungen und Gerätefunktionen in Microsoft Teams App.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 125139abceb01218766dba1cd8d6c95850abd1272583e37e148aabebe68b778a
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707302"
---
# <a name="integrate-web-apps"></a>Integrieren von Web-Apps

Sie können eine erweiterte Benutzererfahrung bereitstellen, indem Sie die Features einer vorhandenen Webanwendung in Microsoft Teams Plattform integrieren. Stellen Sie sicher, [dass Sie Teams Entwurfsrichtlinien](~/concepts/design/understand-use-cases.md) befolgen, damit Ihre App für Teams systemeigen ist.
Dieses Dokument bietet einen Überblick über die Voraussetzungen für die Integration von Webanwendungen in Teams, Power-Plattform zum Erstellen von Power-Apps, Power Virtual Agents, Virtual Assistant, App-Vorlagen, Umschaltconnectors, Moodle LMS, erstellen einer Schaltfläche für Share-to-Teams für Ihre Website, Hinzufügen einer Microsoft Teams Registerkarte in SharePoint, Erstellen von Deep-Links und Integrieren von Gerätefunktionen.

## <a name="prerequisites"></a>Voraussetzungen   

Stellen Sie für eine effektive Integration sicher, dass Sie die folgenden Voraussetzungen besser verstehen:
* Teams Funktionen. 
* SharePoint Anforderungen für datei- und datenspeicherung.
* API-Anforderungen.
* Authentifizierung.
* Deep linking of your app with Teams.
* Ordnen Sie die Anwendungsfälle Ihrer App Teams Plattformfunktionen zu.
* Bestimmen Sie die Einstiegspunkte Ihrer App, z. B. persönliche Nutzung, Zusammenarbeit oder beides.

## <a name="low-code-platforms"></a>Plattformen mit wenig Code

Plattformen mit wenig Code bieten einen intuitiven Ansatz für die Softwareentwicklung und erfordern wenig oder gar keine Codierung, um Anwendungen und Prozesse zu erstellen. Sie können benutzerdefinierte Apps ganz einfach mit Plattformen mit wenig Code erstellen. Diese Plattformen bestehen aus einer visuellen Schnittstelle, Connectors zu Back-End-Diensten und einem integrierten App-Lebenszyklusverwaltungssystem zum Erstellen, Debuggen, Bereitstellen und Warten von Anwendungen. Microsoft bietet die folgenden innovative Gateways, um schnell Teams-kompatible Apps mithilfe von Attributen mit wenig Code zu erstellen:
* Microsoft Power-Plattform
* Microsoft Teams-App-Vorlagen

## <a name="microsoft-power-platform"></a>Microsoft Power-Plattform

Die Microsoft Power-Plattform kombiniert vier stabile Microsoft-Technologien wie Power BI, Power Apps, Power Automate und Power Virtual Agents in einer leistungsstarken Anwendungsplattform. Mit diesen Technologien können Sie Lösungen erstellen, Prozesse automatisieren, Daten analysieren und virtuelle Agents in einer einheitlichen und integrierten Umgebung erstellen.

### <a name="power-apps"></a>Power Apps

Mit Power Apps können Sie Geschäfts-Apps erstellen, die eine Verbindung zu Ihren Geschäftsdaten herstellen und auf die Anforderungen Ihrer Organisation zugeschnitten sind. Power Apps eine Vielzahl von App-Szenarien ermöglichen, um geschäftliche Herausforderungen durch Canvas-Apps zu lösen. Nach dem Erstellen der App können Sie sie aus dem Power Apps Herstellerportal exportieren und in Microsoft Teams einbetten.

### <a name="power-virtual-agents"></a>Power Virtual Agents

Power Virtual Agent ist eine codelose, geleitete grafische Schnittstellenlösung. Es basiert auf der Microsoft Power Platform und dem Bot Framework. Sie ermöglicht es jedem Mitglied Ihres Teams, umfassende Chat-Chatbots zu erstellen und zu verwalten, die sich problemlos in die Teams-Plattform integrieren lassen. Sie können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten, einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren zu müssen.

### <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten

Virtual Assistant ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die volle Kontrolle über die Benutzeroberfläche, das Branding der Organisation und die erforderlichen Daten behalten können. 

## <a name="app-templates"></a>App-Vorlagen

Sie können die App-Vorlage verwenden, um benutzerdefinierte Apps zu erstellen, die Ihren Organisatorischen Anforderungen entsprechen. Hierbei handelt es sich um produktionsbereite Apps für Microsoft Teams, die communitygesteuert, Open Source und auf GitHub verfügbar sind. Jede Vorlage enthält detaillierte Anweisungen zum Bereitstellen und Installieren der App für Ihre Organisation. Es bietet eine sofort einsatzbereite Anwendung, die Sie sofort installieren und verwenden können. 

## <a name="teams-shifts-work-force-management-connectors"></a>Teams Schichten von Work Force Management-Connectors

Teams Shifts Work Force Management Connectors sind produktionsbereite, Open Source- und communitygesteuerte Integrationen. Sie bieten eine nahtlose Erfahrung und einen schnellen Prozess für die digitale Transformation von Mitarbeitern in Service und Produktion mit Teams Schichten.

## <a name="install-moodle-lms"></a>Installieren von Moodle LMS

Moodle ist ein beliebtes Open-Source-Learning Management System (LMS). Es ist jetzt in Microsoft Teams integriert. Diese Integration hilft Lehrkräften und Lehrkräften, bei Moodle-Kursen zusammenzuarbeiten, Fragen zu Noten und Aufgaben zu stellen und mit Benachrichtigungen direkt innerhalb Teams auf dem Laufenden zu bleiben.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Erstellen einer Schaltfläche zum Teilen in Teams für Ihre Website

Websites von Drittanbietern können das Startprogrammskript verwenden, um "Freigeben" in Teams Schaltflächen auf ihren Webseiten einzubetten. Wenn Sie die Schaltfläche auswählen, wird die Freigabe gestartet, um die Benutzeroberfläche in einem Popupfenster Teams. Auf diese Weise können Sie einen Link direkt für jede Person oder Microsoft Teams Kanal freigeben, ohne den Kontext zu wechseln.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Hinzufügen einer Microsoft Teams Registerkarte in SharePoint

Sie erhalten eine umfassende Integration zwischen Microsoft Teams und SharePoint, indem Sie eine Microsoft Teams Registerkarte in SharePoint als SPFx Webpart hinzufügen. 

## <a name="create-deep-link"></a>Deep-Link erstellen

Sie können Deep-Links zu den Entitäten in Teams erstellen. Sie können Links zu Informationen und Features in Teams erstellen. Diese Deep-Links navigieren zu Inhalten und Informationen auf Ihrer Registerkarte. Sie können Deep-Links verwenden, um Ihre App mit Teams zu verknüpfen, da sie mehrere Teile einer App miteinander verknüpfen, um eine native Teams Zu bieten.

## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an den integrierten Erfahrungen von Erstanbietern orientieren. Die erweiterte Teams-Plattform ermöglicht Partnern den Zugriff auf und die Integration der systemeigenen Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort mithilfe dedizierter APIs, die in Microsoft Teams JavaScript-Client-SDK verfügbar sind. 

## <a name="see-also"></a>Weitere Informationen

* [Zuordnen der Anwendungsfälle Ihrer App zu Teams Plattformfunktionen](~/concepts/design/map-use-cases.md)
* [Ermitteln der Einstiegspunkte Ihrer App](~/concepts/extensibility-points.md)
* [Integrieren von Web-Apps](~/samples/integrating-web-apps.md)
* [Erstellen von benutzerdefinierten Apps mit wenig Code für Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Hinzufügen eines Power Virtual Agent-Chatbots](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
* [Erstellen eines virtuellen Assistenten](~/samples/virtual-assistant.md)
* [App-Vorlagen für Microsoft Teams](~/samples/app-templates.md)
* [Produktionsbereite Umschaltkonnektoren](~/samples/shifts-wfm-connectors.md)
* [Installieren von Moodle LMS](~/resources/moodleinstructions.md)
* [Erstellen einer Schaltfläche zum Teilen in Microsoft Teams](~/concepts/build-and-test/share-to-teams.md)
* [Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)
* [Erstellen von Deep-Links](~/concepts/build-and-test/deep-links.md)
* [Gerätefunktionen](~/concepts/device-capabilities/device-capabilities-overview.md)
