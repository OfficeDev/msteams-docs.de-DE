---
title: Features in der Public Developer Preview
description: Details zu den Features in der Public Developer Preview von Microsoft Teams
keywords: Entwicklerfeatures in Microsoft Teams Preview
ms.openlocfilehash: 773e0334bddf45b7b86d31329b99607f3b70c534
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874842"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features in der Public Preview für Entwickler von Microsoft Teams

Die Entwicklervorschau umfasst die folgenden neuen Features:

## <a name="tabs-single-sign-on-sso"></a>Registerkarten für einmaliges Anmelden (SSO)

Sie können jetzt [einmaliges Anmelden (Single Sign-on, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) für die Anmeldung und Authentifizierung eines Benutzers auf Desktop-und Mobilgeräten verwenden, indem Sie das Microsoft Teams-JavaScript-SDK über eine Webinhalts Seite verwenden. Einer der Vorteile besteht darin, dass sich ein Benutzer niemals anmelden muss; und nachdem Sie der App mithilfe Ihres Profils zugestimmt haben: Sie werden automatisch auf Ihrer Registerkarte (einschließlich Mobiltelefon) angemeldet.

Unsere Entwicklervorschau steht in Manifest-Versionen 1,5 und höher zur Verfügung. Unsere aktuelle Implementierung kann nur eine beschränkte Menge an Graph-APIs erhalten, aber wir bieten eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="calls-and-online-meeting-bots"></a>Bots für Anrufe und Onlinebesprechungen

Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta)können Microsoft Teams-apps nun mithilfe von Sprach-und Videofunktionen auf vielfältige Weise mit Benutzern interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Echtzeit-Audio-und/oder-Videodatenströme für Anrufe und Besprechungen einschließlich Desktop-und App-Freigaben hinzufügen.

Wir haben einen neuen Abschnitt zum Erstellen und entwickeln von Anrufen und Online-Besprechungs-Bots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

## <a name="image-enlarge-support"></a>Unterstützung für Bildvergrößerung

Es ist nun möglich, dass Bots anzeigen, welche in Adaptive Cards in Microsoft Teams freigegebenen Bilder vergrößert werden dürfen. Dies ist nützlich für Szenarien wie das Freigeben detaillierter Schritt-für-Schritt-visueller Anleitungen über Bots, die andernfalls für Benutzer schwer lesbar sein können. Um ein Bild erweiterbar zu machen, markieren Sie es einfach `allowExpand: true` wie unten dargestellt.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Dadurch wird ein Element des Teams-Webservers/Desktop Clients auf dem Mauszeiger über dem Bild gerendert, damit der Benutzer das Bild erweitern kann.

