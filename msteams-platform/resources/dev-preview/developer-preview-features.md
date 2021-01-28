---
title: Features im öffentlichen Developer Preview
description: Details zu den Features in der öffentlichen Microsoft Teams-Developer Preview
ms.topic: reference
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: 3275ef7ac0d4ba052f417f6e852f48e2fdf267f5
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014355"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features im öffentlichen Developer Preview für Microsoft Teams

Die Entwicklervorschau enthält die folgenden neuen Features:

## <a name="tabs-single-sign-on-sso"></a>Einmaliges Anmelden (Single Sign-On, SSO)

Sie können jetzt einmaliges Anmelden [(Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um sich über das JavaScript SDK von Teams über eine Webinhaltsseite anzumelden und einen Benutzer auf desktop- und mobilen Geräten zu authentifizieren. Einer der Vorteile ist, dass sich ein Benutzer nie anmelden muss. und nachdem sie der App mithilfe ihres Profils zugestimmt haben: Sie werden automatisch bei ihrer Registerkarte (einschließlich Mobilgerät) angemeldet.

Unsere Entwicklervorschau ist in Manifestversionen 1.5 und höher verfügbar. Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen. Wir bieten jedoch eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="calls-and-online-meeting-bots"></a>Anrufe und Online-Besprechungsbots

Durch das Hinzufügen von [Microsoft Graph-APIs für](/graph/api/resources/communications-api-overview?view=graph-rest-beta)Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt mithilfe von Sprache und Video auf vielfältige Weise mit Benutzern interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videostreams in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.

Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Anrufen und Onlinebesprechungsbots hinzugefügt, beginnend mit der [Übersicht.](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

## <a name="image-enlarge-support"></a>Unterstützung für Bildgröße

Bots können jetzt angeben, welche In adaptiven Karten in Teams freigegebenen Bilder vergrößert werden dürfen. Dies ist hilfreich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Anleitungen über Bots, die für Benutzer andernfalls schwer zu lesen sein könnten. Um ein Bild erweiterbar zu machen, kennzeichnen Sie es `allowExpand: true` wie unten dargestellt.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Dadurch rendert der Web-/Desktopclient von Teams ein Element beim Zeigen auf das Bild, damit der Benutzer das Bild erweitern kann.

