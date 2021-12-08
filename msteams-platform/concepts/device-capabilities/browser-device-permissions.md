---
title: Geräteberechtigungen für den Browser
keywords: Berechtigungen für Teams-Apps-Funktionen
description: Sicheres Zurücksetzen der Geräteberechtigungsunterstützung für Apps in unserem Webclient
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: df0b45af341d936496b3b4cd4314f47f62f2bd3d
ms.sourcegitcommit: a01d22a29e13e19331936e332ab7fbe6ffb1d718
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2021
ms.locfileid: "61348349"
---
# <a name="device-permissions-for-the-browser"></a>Geräteberechtigungen für den Browser

> [!NOTE]
> Das neueste Update zur Behandlung von Geräteberechtigungen im Browser ist derzeit nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar. Dieses Update wird bis zum 1. Februar 2022 allgemein verfügbar sein.


Teams App, die Geräteberechtigungen benötigt, z. B. Kamera- oder Mikrofonzugriff, müssen Benutzer jetzt manuell Berechtigungen pro App-Ebene im Webbrowser erteilen. Zuvor hat der Browser behandelt, wie Zugriffsberechtigungen erteilt werden, aber jetzt werden diese Berechtigungen in Microsoft Teams behandelt. Dies hat Auswirkungen auf die Art und Weise, wie Sie Ihre Anwendung entwerfen und ob sie diese Berechtigungen im Browser benötigen.

## <a name="enable-apps-device-permissions"></a>Aktivieren der Geräteberechtigungen der App
Wenn Ihre Teams App im [Anwendungsmanifest](native-device-permissions.md#specify-permissions) deklariert hat, dass sie Geräteberechtigungen benötigt, wird die **App-Berechtigungsoption** für die Benutzer angezeigt, um die Geräteberechtigungen der App zu aktivieren. Die **App-Berechtigungsoption** ist in den folgenden Funktionen verfügbar: 

* **Dialogfelder für persönliche Apps und Aufgabenmodul:** Die **App-Berechtigungsoption** ist in der oberen rechten Ecke der Seite verfügbar.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

* **Registerkarten für Chats, Kanäle oder Besprechungen:** Die **App-Berechtigungsoption** ist in der Dropdownliste der Registerkarte verfügbar. ![ Dropdownmenü "App-Berechtigungen"](../../assets/images/tabs/drop-downapppermissions.png)

Nachdem die **App-Berechtigungsoption** ausgewählt wurde, wird ein Popup angezeigt, in dem der Benutzer die Berechtigungsschaltfläche aktivieren kann.

Ein Benutzer muss diese Berechtigungen im Browser aktivieren, damit diese Berechtigungen wirksam werden. Nachdem der Benutzer die Geräteberechtigungen der App im Browser geändert hat, wird er aufgefordert, die Anwendung in Teams neu zu laden.

> [!IMPORTANT]
> Sie müssen die Benutzer darauf aufmerksam machen, wohin sie gehen müssen, um diese **App-Berechtigungen** in Microsoft Teams zu aktivieren.

## <a name="recommendation"></a>Empfehlung
Teams App, die Geräteberechtigungen im Browser erfordert, müssen Den Benutzern Anweisungen anzeigen, wo sie diese Berechtigungen auf der Teams Benutzeroberfläche finden und aktivieren können. Abhängig vom Kontext, in dem Ihre Anwendung ausgeführt wird, müssen Sie sicherstellen, dass Ihre Anweisungen den Benutzer darauf hinweisen, den Speicherort für den Zugriff auf diese Berechtigungen zu korrigieren, da sie sich für persönliche Apps, Aufgabenmoduldialogfelder, Registerkarten in Chats und Kanäle oder Besprechungen unterscheiden.

</br>
<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | Node.js |
|----------------|-----------------|--------------|
| Registerkartengeräteberechtigungen für Browser | Der Beispielcode veranschaulicht, wie die Geräteberechtigungen für den Browser angezeigt werden. | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |


## <a name="see-also"></a>Siehe auch

* [Übersicht über die Gerätefunktionen](device-capabilities-overview.md)
* [Geräteberechtigungen anfordern](native-device-permissions.md)
