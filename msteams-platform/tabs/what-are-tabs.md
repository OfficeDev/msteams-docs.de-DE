---
title: Was sind benutzerdefinierte Registerkarten in Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Teams-Plattform
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 7e256423ad713b81f9d4bc3760c33903ef91b179
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231666"
---
# <a name="what-are-microsoft-teams-tabs"></a>Was sind Microsoft Teams-Registerkarten?

Registerkarten sind in Microsoft Teams eingebettete Teams- aware Webseiten. Es handelt sich um einfache HTML-<-iframe-Tags, die auf im App-Manifest deklarierte Domänen verweisen und als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden \> können. Sie können benutzerdefinierte Registerkarten in Ihre App integrieren, um Ihre eigenen Webinhalte in Teams einzubetten oder Teams-spezifische Funktionen zu Ihren Webinhalten hinzuzufügen. *Weitere Informationen* [finden Sie im JavaScript-Client-SDK für Teams.](/javascript/api/overview/msteams-client)

> [!NOTE]
> Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und legt standardmäßig Cookierichtlinien fest. Es wird empfohlen, dass Sie die beabsichtigte Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen. *Siehe* [SameSite cookie attribute (2020 update)](../resources/samesite-cookie-update.md).

Es gibt zwei Arten von Registerkarten in Teams: Kanal/Gruppe und persönlich. Kanal-/Gruppenregisterkarten liefern Inhalte an Kanäle und Gruppenchats und stellen eine hervorragende Möglichkeit zum Erstellen von Gemeinsamen Räumen für dedizierte webbasierte Inhalte zur Verfügung. Persönliche Registerkarten sind zusammen mit persönlichen Bots Teil von persönlichen Apps und sind auf einen einzelnen Benutzer begrenzt. Sie können für einfachen Zugriff an die linke Navigationsleiste angeheftet werden.

## <a name="lesser-known-tab-features"></a>Weniger bekannte Registerkartenfeatures

> [!div class="checklist"]
>
> * Wenn eine Registerkarte zu einer App hinzugefügt wird, die auch über einen Bot verfügt, wird der Bot auch dem Team hinzugefügt.
> * Bewusstsein der Azure Active Directory (Azure AD)-ID des aktuellen Benutzers.
> * Locale awareness for the user to indicate language, d. h. `en-us` . 
> * Funktion für einmaliges Anmelden (Single Sign-On, SSO), sofern unterstützt.
> * Möglichkeit zur Verwendung von Bots oder App-Benachrichtigungen, um einen Deep-Link zur Registerkarte oder zu einer Unterentität innerhalb des Diensts zu verwenden, z. B. eine einzelne Arbeitsaufgabe.
> * Die Möglichkeit, ein Aufgabenmodul über Links auf einer Registerkarte zu öffnen.
> * Wiederverwendung von SharePoint-Webparts auf der Registerkarte.

## <a name="tabs-user-scenarios"></a>Benutzerszenarien für Registerkarten

**Szenario:** Bringen Sie eine vorhandene webbasierte Ressource in Teams mit. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-App, die Benutzern eine Unternehmenswebsite mit Informationen zur Verfügung stellt.

**Szenario:** Hinzufügen von Supportseiten zu einem Teams-Bot oder einer Messaging-Erweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten, die Informationen *und* Hilfe *zu* Webseiteninhalten für Benutzer bereitstellen.

**Szenario:** Bereitstellen des Zugriffs auf Elemente, mit denen Ihre Benutzer regelmäßig interagieren, um einen kooperativen Dialog und eine zusammenarbeit zu ermöglichen. \
**Beispiel:** Sie erstellen eine Kanal-/Gruppenregisterkarte mit einer tiefen Verknüpfung zu einzelnen Elementen.

## <a name="how-do-tabs-work"></a>Wie funktionieren Registerkarten?

Eine benutzerdefinierte Registerkarte wird im App-Manifest Ihres App-Pakets deklariert. Für jede Webseite, die sie als Registerkarte in Ihre App einfügen möchten, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie das [JavaScript-Client-SDK](/javascript/api/overview/msteams-client) für Teams zu Ihrer Seite hinzufügen und nach dem `microsoftTeams.initialize()` Laden der Seite aufrufen. Auf diese Weise wird Teams an die Anzeige Ihrer Seite informiert, Sie erhalten Zugriff auf Teams-spezifische Informationen (z. B. wenn der Teams-Client das dunkle Design *verwendet),* und Sie können basierend auf den Ergebnissen Maßnahmen ergreifen.

Unabhängig davon, ob Sie Ihre Registerkarte im Kanal-/Gruppenbereich oder im persönlichen Bereich verfügbar machen möchten, müssen Sie eine <iframe-HTML-Inhaltsseite \> auf Ihrer Registerkarte präsentieren. [](~/tabs/how-to/create-tab-pages/content-page.md) Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams-App-Manifest durch die `contentUrl` Eigenschaft im Array `staticTabs` festgelegt. Der Inhalt Ihrer Registerkarte ist für alle Benutzer identisch.

Für Kanal-/Gruppenregisterkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, auf der Benutzer die URL Ihrer Inhaltsseite konfigurieren können, in der Regel mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass Ihre Kanal-/Gruppenregisterkarte mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können Die Benutzer die Registerkarte konfigurieren, sodass Sie die Benutzererfahrung nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die auf der Benutzeroberfläche von Teams angezeigt wird, eine URL zugeordnet. Beim Konfigurieren einer Registerkarte werden einfach zusätzliche Parameter zu dieser URL hinzugefügt. Wenn Sie beispielsweise die Registerkarte "Azure Boards" hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden wird. Die URL der Konfigurationsseite wird durch die Eigenschaft  `configurationUrl` im Array in Ihrem `configurableTabs` App-Manifest angegeben.

Sie können maximal eine (1) Kanal-/Gruppenregisterkarte und bis zu 16 (16) persönliche Registerkarten pro App verwenden.

## <a name="mobile-clients"></a>Mobile Clients

Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration `setSettings()` einen Wert für die Eigenschaft `websiteUrl` haben. Um eine optimale Benutzererfahrung zu gewährleisten, müssen Sie beim Erstellen ihrer Registerkarten die Anleitungen für Registerkarten [auf mobilen](~/tabs/design/tabs-mobile.md) Geräten befolgen. Apps, die [über Appsource verteilt](~/concepts/deploy-and-publish/appsource/publish.md) werden, verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps lautet wie folgt:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wurde** | **Verhalten, wenn die App nicht genehmigt ist** |
| --- | --- | --- |
| **Statische Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams-Client geöffnet. | Die App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Konfigurierbare Registerkarten** | Die Registerkarte wird im Teams-Client mit `contentUrl` geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mit `websiteUrl` geöffnet. |


>[!NOTE]
>
>- Das Standardverhalten der Apps gilt nur, wenn sie über den Teams Store (AppSource) verteilt werden. Es gibt keinen Genehmigungsprozess für Apps, die über andere [Verteilungsmethoden verteilt werden.](~/concepts/deploy-and-publish/overview.md) Standardmäßig werden alle Registerkarten im Teams-Client geöffnet.
>- Um eine Auswertung Ihrer App für mobile Geräte zu initiieren, wenden Sie sich an teamsubm@microsoft.com Ihre App-Details.

> [!div class="nextstepaction"]
> [Weitere Informationen: Anfordern von Geräteberechtigungen](../concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
