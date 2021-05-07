---
title: Features in der öffentlichen Developer Preview
description: Details zu den Features im Microsoft Teams Public Developer Preview
ms.topic: reference
localization_priority: Normal
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: 84683420a5c61bb1eb493f8191bfbcbe97f6fb46
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230904"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features in der öffentlichen Developer Preview für Microsoft Teams

> [!NOTE]
> Diese Seite ist im Juni 2021 veraltet. Informationen zu features available for developer preview finden Sie unter [What's new?](~/whats-new.md)

Die Entwicklervorschau enthält die folgenden neuen Features:

## <a name="app-customization"></a>App-Anpassung

Sie können jetzt einen ausgewählten Satz von Eigenschaften definieren, den ein Teams Administrator je nach Bedarf der Organisation anpassen oder neubranden kann. Weitere Informationen finden Sie unter [App-Anpassungsfeature](~/concepts/design/design-teams-app-overview.md).

## <a name="tabs-single-sign-on-sso"></a>Einmaliges Anmelden (Single Sign-On, SSO)

Sie können jetzt einmaliges Anmelden [(Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um sich über das Teams JavaScript SDK über eine Webinhaltsseite anzumelden und einen Benutzer auf Desktop- und Mobilgeräten zu authentifizieren. Einer der Vorteile ist, dass sich ein Benutzer niemals anmelden muss. und sobald sie der App mit ihrem Profil zugestimmt haben: Sie werden automatisch auf ihrer Registerkarte (einschließlich Mobile) angemeldet.

Unsere Entwicklervorschau ist in den Manifestversionen 1.5 und höher verfügbar. Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen. Wir bieten jedoch eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="calls-and-online-meeting-bots"></a>Anrufe und Online-Besprechungsbots

Durch das Hinzufügen von [Microsoft Graph-APIs](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)für Anrufe und Onlinebesprechungen können Microsoft Teams Apps jetzt mit Benutzern auf vielfältige Weise mithilfe von Sprach- und Videonachrichten interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videostreams in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.

Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Anrufen und Onlinebesprechungsbots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).


## <a name="image-enlarge-support"></a>Unterstützung für die Bild vergrößern

Bots können jetzt angeben, welche Bilder in adaptiven Karten in Teams vergrößert werden dürfen. Dies ist nützlich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Anleitungen über Bots, die für Benutzer andernfalls schwer zu lesen sind. Um ein Bild erweiterbar zu machen, kennzeichnen Sie es `allowExpand: true` wie unten gezeigt.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Dies hat zur Teams, dass der Web-/Desktopclient beim Zeigen auf das Bild ein Element rendert, damit der Benutzer das Bild erweitern kann.
