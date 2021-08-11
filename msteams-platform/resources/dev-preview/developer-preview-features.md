---
title: Features in der Öffentlichen Entwicklervorschau
description: Details zu den Features in der Microsoft Teams Public Developer Preview
ms.topic: reference
localization_priority: Normal
keywords: Teams– Vorschau für Entwicklerfeatures
ms.openlocfilehash: f24f95245707097cb5fc79c041582efb5e1f11ef29877855003baf3707842c4c
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57704396"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a>Features in der Öffentlichen Entwicklervorschau für Microsoft Teams

> [!NOTE]
> Diese Seite wird im Juni 2021 veraltet sein. Informationen zu den für die Entwicklervorschau verfügbaren Features finden Sie unter ["Neuigkeiten".](~/whats-new.md)

Die Entwicklervorschau umfasst die folgenden neuen Features:

## <a name="app-customization"></a>App-Anpassung

Sie können jetzt einen ausgewählten Satz von Eigenschaften definieren, den ein Teams Administrator basierend auf den Anforderungen seiner Organisation anpassen oder neu ein Branding durchführen kann. Weitere Informationen finden Sie unter [App-Anpassungsfeature.](~/concepts/design/design-teams-app-overview.md)

## <a name="tabs-single-sign-on-sso"></a>Registerkarten für einmaliges Anmelden (Single Sign-On, SSO)

Sie können jetzt [einmaliges Anmelden (Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um einen Benutzer auf dem Desktop und auf mobilgeräten mithilfe des Teams JavaScript SDK von einer Webinhaltsseite aus anzumelden und zu authentifizieren. Einer der Vorteile besteht darin, dass sich ein Benutzer nie anmelden muss. und nachdem sie der App mit ihrem Profil zugestimmt haben, werden sie automatisch bei ihrer Registerkarte angemeldet (einschließlich mobilgeräte).

Unsere Entwicklervorschau ist in den Manifestversionen 1.5 und höher verfügbar. Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen, aber wir bieten eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.

## <a name="calls-and-online-meeting-bots"></a>Anrufe und Onlinebesprechungs-Bots

Durch die Hinzufügung von [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)können Microsoft Teams Apps jetzt mit Benutzern auf vielfältige Weise mitHilfe von Sprache und Video interagieren. Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videodatenströme in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.

Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Bots für Anrufe und Onlinebesprechungen hinzugefügt, beginnend mit der [Übersicht.](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)


## <a name="image-enlarge-support"></a>Unterstützung für bild vergrößerte Bilder

Bots können jetzt angeben, welche Bilder in adaptiven Karten in Teams vergrößert werden dürfen. Dies ist nützlich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Handbücher über Bots, die andernfalls für Benutzer schwer zu lesen sein können. Um ein Bild erweiterbar zu machen, kennzeichnen Sie es einfach `allowExpand: true` wie unten dargestellt.

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
Dies führt dazu, dass Teams Web-/Desktopclient ein Element rendert, wenn der Mauszeiger auf das Bild gezeigt wird, damit der Benutzer das Bild erweitern kann.
