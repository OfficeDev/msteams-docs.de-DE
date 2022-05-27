---
title: Geräteberechtigungen für den Browser
keywords: Teams Apps Funktionen Berechtigungen
description: Sichere Wiedereinführung der Unterstützung von Geräteberechtigungen für Apps in unserem Webclient
localization_priority: medium
ms.topic: how-to
ms.openlocfilehash: 0789715aebfd1db0c9d0100ccffb2ff213a10d1d
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756744"
---
# <a name="device-permissions-for-the-browser"></a>Geräteberechtigungen für den Browser

Teams App, für die Geräteberechtigungen erforderlich sind, z. B. Kamera- oder Mikrofonzugriff, müssen Benutzer die Berechtigung jetzt manuell auf App-Ebene im Webbrowser erteilen. Zuvor hat der Browser behandelt, wie Zugriffsberechtigungen gewährt werden, aber jetzt werden diese Berechtigungen in Microsoft Teams behandelt. Dies hat Auswirkungen darauf, wie Sie Ihre Anwendung entwerfen und ob sie diese Berechtigungen im Browser benötigen.

## <a name="enable-apps-device-permissions"></a>Aktivieren der Geräteberechtigungen der App

Wenn Ihre Teams-App im [Anwendungsmanifest](native-device-permissions.md#specify-permissions) deklariert hat, dass sie Geräteberechtigungen benötigt, wird die Option **App-Berechtigungen** für die Benutzer angezeigt, um die Geräteberechtigungen der App zu aktivieren. Die Option **App-Berechtigung** ist in den folgenden Funktionen verfügbar:

* **Dialogfelder für persönliche Apps und Aufgabenmodule**: Die Option **App-Berechtigungen** ist in der oberen rechten Ecke der Seite verfügbar.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

* **Chats-, Kanal- oder Besprechungsregisterkarten**: Die Option **App-Berechtigungen** ist in der Dropdownliste der Registerkarte verfügbar. ![Dropdownliste „App-Berechtigungen“](../../assets/images/tabs/drop-downapppermissions.png)

Nachdem die Option **App-Berechtigungen** ausgewählt wurde, wird ein Popup angezeigt, in dem der Benutzer die Berechtigungsschaltfläche aktivieren kann.

Ein Benutzer muss diese Berechtigungen im Browser aktivieren, damit diese Berechtigungen wirksam werden. Nachdem der Benutzer die Geräteberechtigungen der App im Browser geändert hat, wird er aufgefordert, die Anwendung in Teams neu zu laden.

> [!IMPORTANT]
> Sie müssen die Benutzer darauf hinweisen, wohin sie wechseln müssen, um diese **App-Berechtigungen** in Microsoft Teams zu aktivieren.

## <a name="recommendation"></a>Empfehlung

Teams App, für die Geräteberechtigungen im Browser erforderlich sind, müssen Benutzern Anweisungen zum Suchen und Aktivieren dieser Berechtigungen in der benutzeroberfläche Teams anzeigen. Je nach Kontext, in dem Ihre Anwendung ausgeführt wird, müssen Sie sicherstellen, dass die Anweisungen den Benutzer auf den richtigen Speicherort verweisen, um auf diese Berechtigungen zuzugreifen. Die Berechtigungen unterscheiden sich für persönliche Apps, Aufgabenmoduldialogfelder, Registerkarten in Chats und Kanäle oder Besprechungen.

</br>
<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | Node.js |
|----------------|-----------------|--------------|
| Registerkarten-Geräteberechtigungen für den Browser“ | Der Beispielcode veranschaulicht, wie die Geräteberechtigungen für den Browser angezeigt werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../sbs-tab-device-permissions.yml), um Registerkarten-Geräteberechtigungen in Microsoft Teams zu erteilen.

## <a name="see-also"></a>Siehe auch

* [Übersicht über Gerätefunktionen](device-capabilities-overview.md)
* [Geräteberechtigungen anfordern](native-device-permissions.md)
