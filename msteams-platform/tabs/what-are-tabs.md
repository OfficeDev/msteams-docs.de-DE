---
title: Was sind benutzerdefinierte Registerkarten in Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Teams Plattform
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 06454530ab2d0b7e993120f6696f3507a7352bf3
ms.sourcegitcommit: 25c02757fe207cdff916ba63aa215f88e24e1d6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2021
ms.locfileid: "52667412"
---
# <a name="microsoft-teams-tabs"></a>Registerkarten für Microsoft Teams

Registerkarten sind Teams, die in die Microsoft Teams. Es handelt sich um einfache HTML-<-iframe-Tags, die auf im App-Manifest deklarierte Domänen verweisen und als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden \> können. Sie können benutzerdefinierte Registerkarten in Ihre App einbinden, um eigene Webinhalte in Teams einzubetten oder Teams Webinhalten spezifische Funktionen hinzuzufügen. Weitere Informationen finden Sie unter [Teams JavaScript client SDK](/javascript/api/overview/msteams-client).

Es gibt zwei Arten von Registerkarten, die in Teams verfügbar sind: Kanal/Gruppe und persönlich. Kanal-/Gruppenregisterkarten liefern Inhalte an Kanäle und Gruppenchats und stellen eine hervorragende Möglichkeit zum Erstellen von gemeinsamen Räumen für dedizierte webbasierte Inhalte zur Verfügung. Persönliche Registerkarten sind zusammen mit persönlichen Bots Teil von persönlichen Apps und sind auf einen einzelnen Benutzer begrenzt. Sie können für einen einfachen Zugriff an die linke Navigationsleiste angeheftet werden.

## <a name="tab-features"></a>Registerkartenfeatures

> [!div class="checklist"]
>
> * Wenn einer App, die auch über einen Bot verfügt, eine Registerkarte hinzugefügt wird, wird auch der Bot dem Team hinzugefügt.
> * Bekanntheit Azure Active Directory (Azure AD)-ID des aktuellen Benutzers.
> * Locale awareness for the user to indicate language, d. h. `en-us` . 
> * Einmaliges Anmelden (Single Sign-On, SSO)-Funktion, sofern unterstützt.
> * Möglichkeit, Bots oder App-Benachrichtigungen zu verwenden, um eine tiefe Verknüpfung zur Registerkarte oder zu einer Unterentität innerhalb des Diensts zu erstellen, z. B. eine einzelne Arbeitsaufgabe.
> * Die Möglichkeit, ein Aufgabenmodul über Links innerhalb einer Registerkarte zu öffnen.
> * Wiederverwendung SharePoint Webparts auf der Registerkarte.

## <a name="tabs-user-scenarios"></a>Registerkartenbenutzerszenarien

**Szenario:** Bring an existing web-based resource inside Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Teams App, die benutzern eine informationselle Unternehmenswebsite präsentiert.

**Szenario:** Hinzufügen von Supportseiten zu Teams oder Messagingerweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten,  die *Informationen zu Webseiteninhalten* bereitstellen und Benutzern helfen.

**Szenario:** Bieten Sie Zugriff auf Elemente, mit denen Ihre Benutzer regelmäßig interagieren, um einen kooperativen Dialog und eine zusammenarbeit zu ermöglichen. \
**Beispiel:** Sie erstellen eine Kanal-/Gruppenregisterkarte mit einer tiefen Verknüpfung mit einzelnen Elementen.

## <a name="understand-how-tabs-work"></a>Verstehen der Funktionsweise von Registerkarten

Sie können eine der folgenden Methoden verwenden, um Registerkarten zu erstellen:
* [Deklarieren einer benutzerdefinierten Registerkarte im App-Manifest](#declare-custom-tab-in-app-manifest)
* [Erstellen von Registerkarten mithilfe der adaptiven Karte](#use-adaptive-card-to-build-tabs)

### <a name="declare-custom-tab-in-app-manifest"></a>Deklarieren einer benutzerdefinierten Registerkarte im App-Manifest

Eine benutzerdefinierte Registerkarte wird im App-Manifest Ihres App-Pakets deklariert. Für jede Webseite, die Sie als Registerkarte in Ihrer App einfügen möchten, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie der Seite das [Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) hinzufügen und nach dem Laden `microsoftTeams.initialize()` der Seite aufrufen. Auf diese Weise erhalten Teams informationen, dass Sie Ihre Seite anzeigen sollen, Ihnen Zugriff auf Teams-spezifische Informationen geben (z. B. wenn der Teams-Client das dunkle Design *verwendet),* und Sie können basierend auf den Ergebnissen Maßnahmen ergreifen.

Unabhängig davon, ob Sie Ihre Registerkarte im Kanal-/Gruppen- oder persönlichen Bereich verfügbar machen möchten, müssen Sie auf Ihrer Registerkarte eine <\> iframe-HTML-Inhaltsseite [](~/tabs/how-to/create-tab-pages/content-page.md) präsentieren. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams-App-Manifest durch die `contentUrl` Eigenschaft im Array `staticTabs` festgelegt. Der Inhalt Ihrer Registerkarte ist für alle Benutzer identisch.

Für Kanal-/Gruppenregisterkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, auf der Benutzer die URL ihrer Inhaltsseite konfigurieren können, in der Regel mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass Ihre Kanal-/Gruppenregisterkarte mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können Ihre Benutzer die Registerkarte konfigurieren, sodass Sie die Benutzererfahrung nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die in der Benutzeroberfläche angezeigt wird, Teams zugeordnet. Wenn Sie eine Registerkarte konfigurieren, fügen Sie einfach zusätzliche Parameter zu dieser URL hinzu. Wenn Sie beispielsweise die Registerkarte Azure Boards hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden soll. Die URL der Konfigurationsseite wird durch die  `configurationUrl` Eigenschaft im Array im `configurableTabs` App-Manifest angegeben.

Sie können über mehrere Kanäle oder Gruppenregisterkarten und bis zu 16 persönliche Registerkarten pro App verfügen.


### <a name="use-adaptive-card-to-build-tabs"></a>Erstellen von Registerkarten mithilfe der adaptiven Karte

Bei der Entwicklung einer Registerkarte mit der herkömmlichen Methode müssen Sie Dinge berücksichtigen, z. B. HTML, CSS-Überlegungen, um systemeigene, langsame Ladezeiten, iFrame-Einschränkungen, Serverwartung und -kosten zu berücksichtigen und so weiter. Adaptive Kartenregisterkarten sind eine neue Möglichkeit zum Erstellen von Registerkarten in Teams. Anstatt Webinhalte in einen iframe einzubetten, können Sie adaptive Karte auf einer Registerkarte rendern. Während das Front-End als adaptive Karte gerendert wird, wird das Back-End von einem Bot unterstützt. Der Bot ist dafür verantwortlich, Anforderungen zu akzeptieren und entsprechend mit der adaptiven Karte zu reagieren, die gerendert werden soll.

## <a name="mobile-clients"></a>Mobile Clients

Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf mobilen Clients Teams, muss die Konfiguration einen `setSettings()` Wert für die Eigenschaft `websiteUrl` haben. Um eine optimale Benutzererfahrung sicherzustellen, müssen Sie beim Erstellen Ihrer Registerkarten die Anleitungen für Registerkarten auf [Mobilgeräten](~/tabs/design/tabs-mobile.md) befolgen. Apps, [die über den Teams verteilt werden,](~/concepts/deploy-and-publish/appsource/publish.md) verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps lautet wie folgt:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wird** | **Verhalten, wenn die App nicht genehmigt wurde** |
| --- | --- | --- |
| **Persönliche Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams geöffnet. | App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Kanal- und Gruppenregisterkarten** | Die Registerkarte wird im Teams client mit `contentUrl` geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams mit `websiteUrl` geöffnet. |

> [!NOTE]
> [Apps, die an die AppSource](../concepts/deploy-and-publish/overview.md#publish-to-appsource) zur Veröffentlichung auf Teams werden automatisch auf mobile Reaktionsfähigkeit ausgewertet. Für alle Abfragen erreichen Sie die teamsubm@microsoft.com.
> Für alle Apps, die nicht über [appSource](../concepts/deploy-and-publish/overview.md)verteilt werden, werden die Registerkarten standardmäßig in einer In-App-Webview innerhalb der Teams-Clients geöffnet, und es ist kein separater Genehmigungsprozess erforderlich.
> 
> Das Standardverhalten von Apps gilt nur, wenn sie über den Teams werden. Standardmäßig werden alle Registerkarten im Client Teams geöffnet.
> Um eine Auswertung Ihrer App für die Mobile-Freundlichkeit zu initiieren, wenden Sie sich an teamsubm@microsoft.com Ihre App-Details.

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](../concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren eines QR- oder Barcodescanners](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integration von Standortfunktionen](../concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkartenanforderungen](~/tabs/how-to/tab-requirements.md)
