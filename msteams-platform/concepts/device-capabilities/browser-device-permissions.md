---
title: Geräteberechtigungen für den Browser
keywords: Berechtigungen für Teams-Apps-Funktionen
description: Sicheres Zurücksetzen der Geräteberechtigungsunterstützung für Apps in unserem Webclient
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: b2e83ca784e5459edfd80a3862610ebab2f8df30
ms.sourcegitcommit: ce956267b620f807e15e6d2df7afa022ffacc22f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2021
ms.locfileid: "60496239"
---
# <a name="device-permissions-for-the-browser"></a>Geräteberechtigungen für den Browser

> [!NOTE]
> Die Änderung der Behandlung von Geräteberechtigungen im Browser ist derzeit nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar. Diese Änderung wird bis zum 21. Januar 2022 allgemein verfügbar sein.

Anwendungen, für die Geräteberechtigungen erforderlich sind , z. B. Kamera- oder Mikrofonzugriff, erfordern jetzt, dass Benutzer die Zustimmung auf App-Ebene im Webbrowser manuell erteilen. Zuvor hat der Browser behandelt, wie diese Berechtigungen erteilt wurden, aber jetzt werden diese Berechtigungen in Microsoft Teams behandelt. Dies hat Auswirkungen auf die Art und Weise, wie Sie Ihre Anwendung entwerfen, wenn diese Berechtigungen im Browser benötigen.

## <a name="change-in-behavior"></a>Verhaltensänderung
Wenn Ihre Anwendung deklariert hat, dass sie Geräteberechtigungen im [Anwendungsmanifest](native-device-permissions.md)benötigt, wird Benutzern die Option "App-Berechtigungen" angezeigt, mit der sie die Geräteberechtigungen einer App aktivieren können. Die Option "App-Berechtigungen" finden Sie in persönlichen Apps, Dialogfeldern des Aufgabenmoduls und Registerkarten in Chats, Kanälen oder Besprechungen.

### <a name="personal-apps-and-task-module-dialogs"></a>Dialogfelder für persönliche Apps und Aufgabenmodul
Die Einstellung "App-Berechtigungen" befindet sich oben rechts.
<img src="../../assets/images/tabs/apppermissions.png" alt="App permissions button" width="800"/>

### <a name="chat-channel-or-meeting-tabs"></a>Registerkarten für Chat, Kanal oder Besprechung
Die Einstellung "App-Berechtigungen" finden Sie im Dropdownmenü der Registerkarte.
![Dropdownmenü "App-Berechtigungen"](../../assets/images/tabs/drop-downapppermissions.png)

Ein Benutzer muss diese Berechtigungen im Browser aktivieren, damit diese Berechtigungen wirksam werden. Sobald ein Benutzer die Geräteberechtigungen einer App im Browser ändert, wird er aufgefordert, die Anwendung in Teams neu zu laden. Es ist wichtig, dass Sie die Benutzer darauf aufmerksam machen, wohin sie gehen müssen, um diese Berechtigungen in Microsoft Teams zu aktivieren.

## <a name="recommendation"></a>Empfehlung
Microsoft Teams Anwendungen, die Geräteberechtigungen im Browser erfordern, werden Benutzern Anweisungen dazu angezeigt, wo sie diese Berechtigungen in der Teams Benutzeroberfläche finden und aktivieren können. Abhängig vom Kontext, in dem Ihre Anwendung ausgeführt wird, müssen Sie sicherstellen, dass Ihre Anweisungen den Benutzer darauf hinweisen, den Speicherort für den Zugriff auf diese Berechtigungen zu korrigieren, da sie sich für persönliche Apps, Aufgabenmoduldialogfelder und Registerkarten in Chats, Kanälen oder Besprechungen unterscheiden.

<img src="../../assets/images/tabs/enable-access.png" alt="Enable camera access" width="800"/>

## <a name="see-also"></a>Siehe auch

* [Übersicht über die Gerätefunktionen](device-capabilities-overview.md)
* [Geräteberechtigungen anfordern](native-device-permissions.md)
