---
title: Was sind benutzerdefinierte Registerkarten in Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Teams-Plattform
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: af6d0a87fbbb87ae4abf09a2ff53319299f452df
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449220"
---
# <a name="what-are-microsoft-teams-tabs"></a>Was sind Microsoft Teams-Registerkarten?

Registerkarten sind in Microsoft Teams eingebettete Webseiten, die teams-entsprechen. Es handelt sich um einfache HTML-<-iframe-Tags, die auf im App-Manifest deklarierte Domänen verweisen und als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden \> können. Sie können benutzerdefinierte Registerkarten in Ihre App einbinden, um eigene Webinhalte in Teams einzubetten oder Teams-spezifische Funktionen zu Ihren Webinhalten hinzuzufügen. *Weitere Informationen* [finden Sie unter Teams JavaScript client SDK](/javascript/api/overview/msteams-client).

> [!NOTE]
> Chrome 80, das anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und setzt standardmäßig Cookierichtlinien auf. Es wird empfohlen, dass Sie die beabsichtigte Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Weitere Informationen* [finden Sie unter SameSite cookie attribute (2020 update)](../resources/samesite-cookie-update.md).

Es gibt zwei Arten von Registerkarten, die in Teams verfügbar sind: Kanal/Gruppe und persönlich. Kanal-/Gruppenregisterkarten liefern Inhalte an Kanäle und Gruppenchats und stellen eine hervorragende Möglichkeit zum Erstellen von gemeinsamen Räumen für dedizierte webbasierte Inhalte zur Verfügung. Persönliche Registerkarten sind zusammen mit persönlichen Bots Teil von persönlichen Apps und sind auf einen einzelnen Benutzer begrenzt. Sie können für einen einfachen Zugriff an die linke Navigationsleiste angeheftet werden.

## <a name="lesser-known-tab-features"></a>Weniger bekannte Registerkartenfeatures

> [!div class="checklist"]
>
> * Wenn einer App, die auch über einen Bot verfügt, eine Registerkarte hinzugefügt wird, wird auch der Bot dem Team hinzugefügt.
> * Bekanntheit der Azure Active Directory (Azure AD)-ID des aktuellen Benutzers.
> * Locale awareness for the user to indicate language, d. h. `en-us` . 
> * Einmaliges Anmelden (Single Sign-On, SSO)-Funktion, sofern unterstützt.
> * Möglichkeit, Bots oder App-Benachrichtigungen zu verwenden, um eine tiefe Verknüpfung zur Registerkarte oder zu einer Unterentität innerhalb des Diensts zu erstellen, z. B. eine einzelne Arbeitsaufgabe.
> * Die Möglichkeit, ein Aufgabenmodul über Links innerhalb einer Registerkarte zu öffnen.
> * Wiederverwendung von SharePoint-Webparts auf der Registerkarte.

## <a name="tabs-user-scenarios"></a>Registerkartenbenutzerszenarien

**Szenario:** Bring an existing web-based resource inside Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-App, die Benutzern eine informationselle Unternehmenswebsite bietet.

**Szenario:** Hinzufügen von Supportseiten zu einem Teams-Bot oder einer Messagingerweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten,  die *Informationen zu Webseiteninhalten* bereitstellen und Benutzern helfen.

**Szenario:** Bieten Sie Zugriff auf Elemente, mit denen Ihre Benutzer regelmäßig interagieren, um einen kooperativen Dialog und eine zusammenarbeit zu ermöglichen. \
**Beispiel:** Sie erstellen eine Kanal-/Gruppenregisterkarte mit einer tiefen Verknüpfung mit einzelnen Elementen.

## <a name="how-do-tabs-work"></a>Wie funktionieren Registerkarten?

Eine benutzerdefinierte Registerkarte wird im App-Manifest Ihres App-Pakets deklariert. Für jede Webseite, die Sie als Registerkarte in Ihrer App einfügen möchten, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie der Seite das [Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) hinzufügen und nach dem Laden `microsoftTeams.initialize()` der Seite aufrufen. Auf diese Weise wird Teams zum Anzeigen Ihrer Seite, zum Zugriff auf teamsspezifische Informationen (z. B. wenn der Teams-Client das dunkle Design *ausgeführt)* und Ihnen ermöglichen, Aktionen basierend auf den Ergebnissen zu ergreifen.

Unabhängig davon, ob Sie Ihre Registerkarte im Kanal-/Gruppen- oder persönlichen Bereich verfügbar machen möchten, müssen Sie auf Ihrer Registerkarte eine <\> iframe-HTML-Inhaltsseite [](~/tabs/how-to/create-tab-pages/content-page.md) präsentieren. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams-App-Manifest durch die `contentUrl` Eigenschaft im Array `staticTabs` festgelegt. Der Inhalt Ihrer Registerkarte ist für alle Benutzer identisch.

Für Kanal-/Gruppenregisterkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, auf der Benutzer die URL ihrer Inhaltsseite konfigurieren können, in der Regel mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass Ihre Kanal-/Gruppenregisterkarte mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können Ihre Benutzer die Registerkarte konfigurieren, sodass Sie die Benutzererfahrung nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die auf der Benutzeroberfläche von Teams angezeigt wird, eine URL zugeordnet. Wenn Sie eine Registerkarte konfigurieren, fügen Sie einfach zusätzliche Parameter zu dieser URL hinzu. Wenn Sie beispielsweise die Registerkarte Azure Boards hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden soll. Die URL der Konfigurationsseite wird durch die  `configurationUrl` Eigenschaft im Array im `configurableTabs` App-Manifest angegeben.

Sie können maximal eine (1) Kanal-/Gruppenregisterkarte und bis zu sechzehn (16) persönliche Registerkarten pro App verwenden.

## <a name="mobile-clients"></a>Mobile Clients

Wenn Sie den Kanal oder die Registerkarte "Gruppe" auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration `setSettings()` einen Wert für die Eigenschaft `websiteUrl` haben. Um eine optimale Benutzererfahrung sicherzustellen, müssen Sie beim Erstellen Ihrer Registerkarten die Anleitungen für Registerkarten auf [Mobilgeräten](~/tabs/design/tabs-mobile.md) befolgen. Apps, die [über Appsource verteilt](~/concepts/deploy-and-publish/appsource/publish.md) werden, verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps lautet wie folgt:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wird** | **Verhalten, wenn die App nicht genehmigt wurde** |
| --- | --- | --- |
| **Statische Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams-Client geöffnet. | App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Konfigurierbare Registerkarten** | Die Registerkarte wird im Teams-Client mit `contentUrl` geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mit `websiteUrl` geöffnet. |


>[!NOTE]
>
>- Das Standardverhalten der Apps gilt nur, wenn sie über den Teams Store (AppSource) verteilt werden. Es gibt keinen Genehmigungsprozess für Apps, die über andere [Verteilungsmethoden verteilt werden.](~/concepts/deploy-and-publish/overview.md) Standardmäßig werden alle Registerkarten im Teams-Client geöffnet.
>- Um eine Auswertung Ihrer App für die Mobile-Freundlichkeit zu initiieren, wenden Sie sich an teamsubm@microsoft.com Ihre App-Details.

> [!div class="nextstepaction"]
> [Weitere Informationen: Anfordern von Geräteberechtigungen](../concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von QR- oder Barcodescannerfunktionen in Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von Standortfunktionen in Teams](../concepts/device-capabilities/location-capability.md)
