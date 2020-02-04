---
title: Features in der Public Developer Preview
description: Beschreibt die Features in der öffentlichen Entwicklervorschau von Microsoft Teams
keywords: Entwicklerfeatures in Microsoft Teams Preview
ms.openlocfilehash: abec097d9f3b6fb48a4a50cb26d73cf811151149
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674111"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features in der Public Preview für Entwickler von Microsoft Teams

Die Entwicklervorschau umfasst die folgenden neuen Features:

## <a name="mention-support-in-adaptive-cards"></a>Erwähnung der Unterstützung in adaptiven Karten

Sie können nun @ Mentions in einem adaptiven Kartentext für Bots und Messaging-Erweiterungs Antworten hinzufügen. @ Mentions in Cards beruhen auf der gleichen Benachrichtigungslogik und der gleichen Darstellung wie die von regulären erwähnten Meldungen. Beachten Sie, dass kartenbasierte Erwähnungen nur heute in den Webservern und Desktop Clients unterstützt werden, wobei die Unterstützung für die Wiedergabe in mobilen Clients in Kürze verfügbar ist.

## <a name="adaptive-12-support"></a>Adaptive 1,2-Unterstützung

Microsoft Teams unterstützt jetzt die [Adaptive Version 1,2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) in der Entwicklervorschau. Beachten Sie, dass [Medienelemente](https://adaptivecards.io/explorer/Media.html) noch nicht unterstützt werden.

## <a name="tabs-single-sign-on"></a>Registerkarten für einmaliges Anmelden

Sie können jetzt [einmaliges Anmelden (Single Sign-on, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) für die Anmeldung und Authentifizierung eines Benutzers auf Desktop-und Mobilgeräten verwenden, indem Sie das Microsoft Teams-JavaScript-SDK über eine Webinhalts Seite verwenden. Einer der Vorteile besteht darin, dass sich ein Benutzer niemals anmelden muss; und nachdem Sie der App mithilfe Ihres Profils zugestimmt haben: Sie werden automatisch auf Ihrer Registerkarte (einschließlich Mobiltelefon) angemeldet.

Unsere Entwicklervorschau steht in Manifest-Versionen 1,5 und höher zur Verfügung. Unsere aktuelle Implementierung kann nur eine beschränkte Menge an Graph-APIs erhalten, aber wir bieten eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="personal-apps-static-tabs-and-1-1-bots-enabled-on-mobile"></a>Auf mobilen Geräten aktivierte persönliche Apps (statische Registerkarten und 1-1-Bots)

Installierte persönliche Apps (statische Tabs und 1-1-Bots) sind jetzt in der APP-Leiste auf mobilen Geräten verfügbar. Anleitungen zur Entwurfs Anleitung finden Sie unter [Design Guidelines for Mobile](~/tabs/design/tabs-mobile.md) . Apps können nur von einem Desktop-oder WebClient installiert werden, und es kann bis zu 4 Stunden dauern, bis Sie nach der Installation auf mobilen Geräten verfügbar sind.

Dies umfasst die Möglichkeit für einen System Administrator, eine APP über [App-Setup Richtlinien](/microsoftteams/teams-app-setup-policies)voranheften. Apps, die merken, werden in der APP-Schublade angezeigt.

## <a name="calls-and-online-meeting-bots"></a>Bots für Anrufe und Onlinebesprechungen

Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta)können Microsoft Teams-apps nun mithilfe von Sprach-und Videofunktionen auf vielfältige Weise mit Benutzern interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Echtzeit-Audio-und/oder-Videodatenströme für Anrufe und Besprechungen einschließlich Desktop-und App-Freigaben hinzufügen.

Wir haben einen neuen Abschnitt zum Erstellen und entwickeln von Anrufen und Online-Besprechungs-Bots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).
