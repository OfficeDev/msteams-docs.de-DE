---
title: Features in der Public Developer Preview
description: Beschreibt die Features in der öffentlichen Entwicklervorschau von Microsoft Teams
keywords: Entwicklerfeatures in Microsoft Teams Preview
ms.openlocfilehash: 7ed442072779917dcc5db3ebcb4afaac9db0407f
ms.sourcegitcommit: b9e8839858ea8e9e33fe5e20e14bbe86c75fd510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "44210701"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features in der Public Preview für Entwickler von Microsoft Teams

Die Entwicklervorschau umfasst die folgenden neuen Features:

## <a name="adaptive-cards-v12-support"></a>Adaptive Cards v 1.2-Unterstützung

Die Unterstützung für [Adaptive Karten v 1.2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) in Microsoft Teams steht nun der allgemeinen Öffentlichkeit zur Verfügung. [Medienelemente](https://adaptivecards.io/explorer/Media.html) werden jedoch derzeit in Adaptive Cards v 1.2 auf der Microsoft Teams-Plattform nicht unterstützt.

## <a name="tabs-single-sign-on-sso"></a>Registerkarten für einmaliges Anmelden (SSO)

Sie können jetzt [einmaliges Anmelden (Single Sign-on, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) für die Anmeldung und Authentifizierung eines Benutzers auf Desktop-und Mobilgeräten verwenden, indem Sie das Microsoft Teams-JavaScript-SDK über eine Webinhalts Seite verwenden. Einer der Vorteile besteht darin, dass sich ein Benutzer niemals anmelden muss; und nachdem Sie der App mithilfe Ihres Profils zugestimmt haben: Sie werden automatisch auf Ihrer Registerkarte (einschließlich Mobiltelefon) angemeldet.

Unsere Entwicklervorschau steht in Manifest-Versionen 1,5 und höher zur Verfügung. Unsere aktuelle Implementierung kann nur eine beschränkte Menge an Graph-APIs erhalten, aber wir bieten eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="personal-apps-static-tabs-and-1-1-bots-enabled-on-mobile"></a>Auf mobilen Geräten aktivierte persönliche Apps (statische Registerkarten und 1-1-Bots)

Installierte persönliche Apps (statische Tabs und 1-1-Bots) sind jetzt in der APP-Leiste auf mobilen Geräten verfügbar. Anleitungen zur Entwurfs Anleitung finden Sie unter [Design Guidelines for Mobile](~/tabs/design/tabs-mobile.md) . Apps können nur von einem Desktop-oder WebClient installiert werden, und es kann bis zu 4 Stunden dauern, bis Sie nach der Installation auf mobilen Geräten verfügbar sind.

Dies umfasst die Möglichkeit für einen System Administrator, eine APP über [App-Setup Richtlinien](/microsoftteams/teams-app-setup-policies)voranheften. Apps, die merken, werden in der APP-Schublade angezeigt.

## <a name="calls-and-online-meeting-bots"></a>Bots für Anrufe und Onlinebesprechungen

Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta)können Microsoft Teams-apps nun mithilfe von Sprach-und Videofunktionen auf vielfältige Weise mit Benutzern interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Echtzeit-Audio-und/oder-Videodatenströme für Anrufe und Besprechungen einschließlich Desktop-und App-Freigaben hinzufügen.

Wir haben einen neuen Abschnitt zum Erstellen und entwickeln von Anrufen und Online-Besprechungs-Bots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).
