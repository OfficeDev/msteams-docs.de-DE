---
title: Was sind benutzerdefinierte Registerkarten in Teams?
author: surbhigupta
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Teams-Plattform
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 792604c7763628ce0d45b332064e23c14e94aeb2
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069191"
---
# <a name="microsoft-teams-tabs"></a>Registerkarten für Microsoft Teams

Registerkarten sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind. Es handelt sich um einfache HTML-<\> iframe-Tags, die auf Domänen verweisen, die im App-Manifest deklariert sind und als Teil eines Kanals innerhalb eines Teams, gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden können. Sie können benutzerdefinierte Registerkarten in Ihre App einschließen, um Ihre eigenen Webinhalte in Teams einzubetten, oder Teams-spezifische Funktionen zu Ihren Webinhalten hinzufügen. Weitere Informationen finden Sie unter [Teams JavaScript-Client-SDK.](/javascript/api/overview/msteams-client)

Es gibt zwei Arten von Registerkarten in Teams : Kanal/Gruppe und persönlich. Kanal-/Gruppenregisterkarten liefern Inhalte an Kanäle und Gruppenchats und sind eine hervorragende Möglichkeit zum Erstellen von Bereichen für die Zusammenarbeit rund um dedizierte webbasierte Inhalte. Persönliche Registerkarten sowie persönliche Bots sind Teil persönlicher Apps und sind auf einen einzelnen Benutzer beschränkt. Sie können für einen einfachen Zugriff an die linke Navigationsleiste angeheftet werden.

## <a name="tab-features"></a>Registerkartenfeatures

> [!div class="checklist"]
>
> * Wenn eine Registerkarte zu einer App hinzugefügt wird, die auch über einen Bot verfügt, wird der Bot auch dem Team hinzugefügt.
> * Bewusstsein für Azure Active Directory (Azure AD)-ID des aktuellen Benutzers.
> * Gebietsschemabewusstsein für den Benutzer, um die Sprache anzugeben, z. B. `en-us` . 
> * SSO-Funktion (Single Sign-On), falls unterstützt.
> * Möglichkeit, Bots oder App-Benachrichtigungen für deep-Links zur Registerkarte oder zu einer Unterentität innerhalb des Diensts zu verwenden, z. B. zu einer einzelnen Arbeitsaufgabe.
> * Die Möglichkeit, ein Aufgabenmodul über Links auf einer Registerkarte zu öffnen.
> * Wiederverwendung von SharePoint-Webparts auf der Registerkarte.

## <a name="tabs-user-scenarios"></a>Registerkartenbenutzerszenarien

**Szenario:** Bringen Sie eine vorhandene webbasierte Ressource in Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-App, die Benutzern eine informationsbezogene Unternehmenswebsite anzeigt.

**Szenario:** Hinzufügen von Supportseiten zu einem Teams Bot oder einer Messaging-Erweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten, die Benutzern Webseiteninhalte *bereitstellen* und *ihnen helfen.*

**Szenario:** Bieten Sie Zugriff auf Elemente, mit denen Ihre Benutzer regelmäßig für einen dialogbasierten Dialog und die Zusammenarbeit interagieren. \
**Beispiel:** Sie erstellen eine Kanal-/Gruppenregisterkarte mit deep-Links zu einzelnen Elementen.

## <a name="understand-how-tabs-work"></a>Grundlegendes zur Funktionsweise von Registerkarten

Sie können eine der folgenden Methoden zum Erstellen von Registerkarten verwenden:
* [Deklarieren einer benutzerdefinierten Registerkarte im App-Manifest](#declare-custom-tab-in-app-manifest)
* [Verwenden einer adaptiven Karte zum Erstellen von Registerkarten](#use-adaptive-card-to-build-tabs)

### <a name="declare-custom-tab-in-app-manifest"></a>Deklarieren einer benutzerdefinierten Registerkarte im App-Manifest

Eine benutzerdefinierte Registerkarte wird im App-Manifest Ihres App-Pakets deklariert. Für jede Webseite, die Sie als Registerkarte in Ihre App einfügen möchten, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie der Seite das [Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) hinzufügen und nach dem `microsoftTeams.initialize()` Laden der Seite aufrufen. Auf diese Weise wird Teams aufgefordert, Ihre Seite anzuzeigen, Ihnen Zugriff auf Teams-spezifische Informationen zu gewähren (z. B. wenn der Teams Client das *dunkle Design* ausführt), und Ihnen die Möglichkeit geben, basierend auf den Ergebnissen Maßnahmen zu ergreifen.

Unabhängig davon, ob Sie Ihre Registerkarte innerhalb des Kanals/der Gruppe oder im persönlichen Bereich verfügbar machen möchten, müssen Sie auf Ihrer Registerkarte eine <\> iframe-HTML-Inhaltsseite anzeigen. [](~/tabs/how-to/create-tab-pages/content-page.md) Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams App-Manifest durch die `contentUrl` Eigenschaft im `staticTabs` Array festgelegt. Der Inhalt Ihrer Registerkarte ist für alle Benutzer identisch.

Für Kanal-/Gruppenregisterkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, die Es Benutzern ermöglicht, die URL der Inhaltsseite zu konfigurieren, in der Regel mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass Ihre Kanal-/Gruppenregisterkarte mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können Ihre Benutzer die Registerkarte konfigurieren, sodass Sie die Benutzeroberfläche nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die auf der Teams Benutzeroberfläche angezeigt wird, eine URL zugeordnet. Durch das Konfigurieren einer Registerkarte werden dieser URL einfach zusätzliche Parameter hinzugefügt. Wenn Sie beispielsweise die Registerkarte Azure Boards hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte geladen wird. Die URL der Konfigurationsseite wird durch die  `configurationUrl` Eigenschaft im Array in Ihrem `configurableTabs` App-Manifest angegeben.

Sie können über mehrere Kanäle oder Gruppenregisterkarten und bis zu 16 persönliche Registerkarten pro App verfügen.


### <a name="use-adaptive-card-to-build-tabs"></a>Verwenden einer adaptiven Karte zum Erstellen von Registerkarten

Bei der Entwicklung einer Registerkarte mithilfe der herkömmlichen Methode müssen Sie Dinge berücksichtigen, z. B. HTML, CSS-Überlegungen zum Verhalten, langsame Ladezeiten, iFrame-Einschränkungen, Serverwartung und Kosten usw. Adaptive Kartenregisterkarten sind eine neue Möglichkeit zum Erstellen von Registerkarten in Teams. Anstatt Webinhalte in einen iframe einzubetten, können Sie adaptive Karten auf einer Registerkarte rendern. Während das Front-End als adaptive Karte gerendert wird, wird das Back-End von einem Bot unterstützt. Der Bot ist dafür verantwortlich, Anforderungen zu akzeptieren und mit der zu rendernden adaptiven Karte entsprechend zu antworten.

## <a name="mobile-clients"></a>Mobile Clients

Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Clients anzeigen möchten, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` aufweisen. Um eine optimale Benutzererfahrung zu gewährleisten, müssen Sie beim Erstellen ihrer Registerkarten die [Anleitungen für Registerkarten auf mobilgeräten](~/tabs/design/tabs-mobile.md) befolgen. Apps, [die über den Teams Store verteilt werden,](~/concepts/deploy-and-publish/appsource/publish.md) verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps lautet wie folgt:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wurde** | **Verhalten, wenn die App nicht genehmigt wurde** |
| --- | --- | --- |
| **Persönliche Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams Client geöffnet. | Die App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Kanal- und Gruppenregisterkarten** | Die Registerkarte wird im Teams Client mit `contentUrl` geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mit `websiteUrl` geöffnet. |

> [!NOTE]
> [Apps, die zur Veröffentlichung auf Teams an AppSource übermittelt](../concepts/deploy-and-publish/overview.md#publish-to-appsource) werden, werden automatisch auf die Reaktionsfähigkeit mobiler Geräte ausgewertet. Wenden Sie sich bei Abfragen an teamsubm@microsoft.com.
> Für alle [Apps, die nicht über AppSource verteilt werden,](../concepts/deploy-and-publish/overview.md)werden die Registerkarten standardmäßig in einer In-App-Webansicht innerhalb der Teams Clients geöffnet, und es ist kein separater Genehmigungsprozess erforderlich.
> 
> Das Standardverhalten von Apps gilt nur, wenn sie über den Teams Store verteilt werden. Standardmäßig werden alle Registerkarten im Teams Client geöffnet.
> Wenden Sie sich an teamsubm@microsoft.com mit Ihren App-Details, um eine Bewertung Der Benutzerfreundlichkeit Ihrer App zu initiieren.

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](../concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren eines QR- oder Strichcodescanners](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integration von Standortfunktionen](../concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkartenanforderungen](~/tabs/how-to/tab-requirements.md)
