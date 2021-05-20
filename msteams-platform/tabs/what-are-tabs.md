---
title: Was sind benutzerdefinierte Registerkarten in Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Teams-Plattform
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 19c51d5c30f938dc5368b28b69ffeb29330887b4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566593"
---
# <a name="microsoft-teams-tabs"></a>Registerkarten für Microsoft Teams

Tabs sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind. Es handelt sich um einfache HTML-<\> iframe-Tags, die auf Domänen verweisen, die im App-Manifest deklariert sind, und können als Teil eines Kanals innerhalb eines Teams, Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden. Sie können benutzerdefinierte Registerkarten in Ihre App einschließen, um Ihre eigenen Webinhalte in Teams einzubetten oder Ihren Webinhalten Teams-spezifische Funktionen hinzuzufügen. Weitere Informationen finden Sie [unter Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client).

Es gibt zwei Arten von Registerkarten in Teams verfügbar: Kanal/Gruppe und persönliche. Kanal-/Gruppenregisterkarten liefern Inhalte für Kanäle und Gruppenchats und sind eine hervorragende Möglichkeit, kollaborative Räume rund um dedizierte webbasierte Inhalte zu erstellen. Persönliche Tabs, zusammen mit persönlich bestückten Bots, sind Teil persönlicher Apps und werden auf einen einzelnen Benutzer beschränkt. Sie können für einen einfachen Zugriff an die linke Navigationsleiste gepinnt werden.

## <a name="tab-features"></a>Tab-Funktionen

> [!div class="checklist"]
>
> * Wenn eine Registerkarte zu einer App hinzugefügt wird, die auch einen Bot hat, wird der Bot auch dem Team hinzugefügt.
> * Bekanntwerden der Azure Active Directory (Azure AD)-ID des aktuellen Benutzers.
> * Lokales für den Benutzer, die Sprache anzugeben, d. h. `en-us` . 
> * SSO-Funktion (Single Sign-On), sofern unterstützt.
> * Möglichkeit, Bots oder App-Benachrichtigungen zu verwenden, um eine Tiefe der Verknüpfung mit der Registerkarte oder einer Untereinheit innerhalb des Dienstes herzustellen, z. B. einer einzelnen Arbeitsaufgabe.
> * Die Möglichkeit, ein Taskmodul über Links innerhalb einer Registerkarte zu öffnen.
> * Wiederverwendung von SharePoint Webparts innerhalb der Registerkarte.

## <a name="tabs-user-scenarios"></a>Registerkarten-Benutzerszenarien

**Szenario:** Bringen Sie eine vorhandene webbasierte Ressource in Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-App, die Benutzern eine informationsgebende Unternehmenswebsite darstellt.

**Szenario:** Hinzufügen von Supportseiten zu einem Teams Bot oder einer Messagingerweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten, die Benutzern Webseiteninhalte *bereitstellen* und *ihnen helfen.*

**Szenario:** Bieten Sie Zugriff auf Elemente, mit denen Ihre Benutzer regelmäßig interagieren, um einen kooperativen Dialog und eine zusammenarbeite Zusammenarbeit zu ermöglichen. \
**Beispiel:** Sie erstellen eine Kanal-/Gruppenregisterkarte mit tiefer Verknüpfung mit einzelnen Elementen.

## <a name="understand-how-tabs-work"></a>Verstehen der Funktionsweise von Registerkarten

Eine benutzerdefinierte Registerkarte wird im App-Manifest Ihres App-Pakets deklariert. Für jede Webseite, die Als Registerkarte in Ihre App aufgenommen werden soll, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie das [Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) zu Ihrer Seite hinzufügen und nach dem `microsoftTeams.initialize()` Laden der Seite aufrufen. Auf diese Weise werden Teams aufgefordert, Ihre Seite anzuzeigen, Ihnen Zugriff auf Teams-spezifische Informationen zu geben (z. B. wenn der Teams Client das *dunkle Design* ausführt), und Ihnen ermöglichen, basierend auf den Ergebnissen Maßnahmen zu ergreifen.

Unabhängig davon, ob Sie Ihre Registerkarte innerhalb des Kanals/der Gruppe oder des persönlichen Bereichs verfügbar machen möchten, müssen Sie eine <\> iframe-HTML-Inhaltsseite auf Ihrer Registerkarte anzeigen. [](~/tabs/how-to/create-tab-pages/content-page.md) Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams App-Manifest durch die `contentUrl` Eigenschaft im `staticTabs` Array festgelegt. Der Inhalt Ihrer Registerkarte ist für alle Benutzer gleich.

Für Kanal-/Gruppenregisterkarten müssen Sie außerdem eine zusätzliche Konfigurationsseite erstellen, mit der Benutzer ihre Inhaltsseiten-URL konfigurieren können, in der Regel mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass Ihre Kanal-/Gruppenregisterkarte mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können Ihre Benutzer die Registerkarte konfigurieren, sodass Sie die Benutzeroberfläche nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die in der Teams-Benutzeroberfläche angezeigt wird, eine URL zugeordnet. Wenn Sie eine Registerkarte konfigurieren, werden dieser URL einfach zusätzliche Parameter hinzugefügt. Wenn Sie beispielsweise die Registerkarte Azure Boards hinzufügen, können Sie auf der Konfigurationsseite auswählen, welche Platine die Registerkarte geladen werden soll. Die URL der Konfigurationsseite wird durch die  `configurationUrl` Eigenschaft im Array im `configurableTabs` App-Manifest angegeben.

Sie können mehrere Kanäle oder Gruppenregisterkarten und bis zu sechzehn persönliche Registerkarten pro App haben.

## <a name="mobile-considerations"></a>Mobile Überlegungen

Wenn Sie festlegen, dass Ihr Kanal oder die Registerkarte Gruppe auf Teams mobilen Clients angezeigt wird, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` haben. Um eine optimale Benutzererfahrung zu gewährleisten, müssen Sie beim Erstellen Ihrer Registerkarten die [Anleitung für Registerkarten auf Mobilgeräten](~/tabs/design/tabs-mobile.md) befolgen. Apps, [die über den Teams Store verteilt](~/concepts/deploy-and-publish/appsource/publish.md) werden, verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps ist wie folgt:

| **App-Fähigkeit** | **Verhalten, wenn die App genehmigt ist** | **Verhalten, wenn die App nicht genehmigt ist** |
| --- | --- | --- |
| **Persönliche Registerkarten** | App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams Client geöffnet. | Die App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Kanal- und Gruppenregisterkarten** | Die Registerkarte wird im Teams Client mit `contentUrl` geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mithilfe von `websiteUrl` geöffnet. |

> [!NOTE]
>
> Das Standardverhalten von Apps ist nur anwendbar, wenn es über den Teams Store verteilt wird. Standardmäßig werden alle Registerkarten im Teams Client geöffnet.
> Um eine Evaluierung Ihrer App auf mobile Freundlichkeit zu initiieren, wenden Sie sich an teamsubm@microsoft.com mit Ihren App-Details.

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](../concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren Eines QR- oder Barcode-Scanners](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integration von Standortfunktionen](../concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkartenanforderungen](~/tabs/how-to/tab-requirements.md)