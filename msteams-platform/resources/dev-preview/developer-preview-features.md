---
title: Features in der öffentlichen Developer Preview
description: Details zu den Features in der öffentlichen Microsoft Teams-Developer Preview
ms.topic: reference
localization_priority: Normal
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: 38acccedacb86437f5e6c949b674c0a62bbbd63c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020618"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features in der öffentlichen Developer Preview für Microsoft Teams

Die Entwicklervorschau enthält die folgenden neuen Features:

## <a name="app-customization"></a>App-Anpassung

Sie können nun einen ausgewählten Satz von Eigenschaften definieren, den ein Teams-Administrator je nach Bedarf der Organisation anpassen oder neubranden kann. Weitere Informationen finden Sie unter [App-Anpassungsfeature](~/concepts/design/design-teams-app-overview.md).

## <a name="tabs-single-sign-on-sso"></a>Einmaliges Anmelden (Single Sign-On, SSO)

Sie können jetzt [einmaliges Anmelden (Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um sich über das Teams JavaScript SDK über eine Webinhaltsseite anzumelden und einen Benutzer auf Desktop- und Mobilgeräten zu authentifizieren. Einer der Vorteile ist, dass sich ein Benutzer niemals anmelden muss. und sobald sie der App mit ihrem Profil zugestimmt haben: Sie werden automatisch auf ihrer Registerkarte (einschließlich Mobile) angemeldet.

Unsere Entwicklervorschau ist in den Manifestversionen 1.5 und höher verfügbar. Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen, wir bieten jedoch eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="calls-and-online-meeting-bots"></a>Anrufe und Online-Besprechungsbots

Durch das Hinzufügen von [Microsoft Graph-APIs](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)für Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt auf vielfältige Weise mithilfe von Sprach- und Videonachrichten mit Benutzern interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videostreams in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.

Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Anrufen und Onlinebesprechungsbots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).


## <a name="image-enlarge-support"></a>Unterstützung für die Bild vergrößern

Bots können jetzt angeben, welche Bilder, die in adaptiven Karten in Teams freigegeben sind, vergrößert werden dürfen. Dies ist nützlich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Anleitungen über Bots, die für Benutzer andernfalls schwer zu lesen sind. Um ein Bild erweiterbar zu machen, kennzeichnen Sie es `allowExpand: true` wie unten gezeigt.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Dies hat zur Ursache, dass der Web-/Desktopclient von Teams ein Element beim Zeigen auf das Bild rendert, damit der Benutzer das Bild erweitern kann.

