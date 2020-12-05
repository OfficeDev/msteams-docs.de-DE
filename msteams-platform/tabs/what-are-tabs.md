---
title: Was sind benutzerdefinierte Registerkarten in Microsoft Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: e89f07133f86b6c0700e6a71d8e53bf6d9831196
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576848"
---
# <a name="what-are-microsoft-teams-custom-tabs"></a>Was sind benutzerdefinierte Microsoft Teams-Registerkarten?

Registerkarten sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind. Es handelt sich um einfache HTML <IFRAME- \> Tags, die auf Domänen zeigen, die im App-Manifest deklariert werden und als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden können. Sie können benutzerdefinierte Registerkarten mit Ihrer APP einfügen, um Ihre eigenen Webinhalte in Microsoft Teams einzubetten oder Ihren Webinhalten Teams-spezifische Funktionen hinzuzufügen. *Weitere Informationen finden Sie unter* [Teams JavaScript Client SDK](/javascript/api/overview/msteams-client).

> [!NOTE]
> In Chrome 80, das für die Veröffentlichung Anfang 2020 vorgesehen ist, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt. Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen. *Siehe* [SameSite-Cookie-Attribut (2020 Update)](../resources/samesite-cookie-update.md).

In Microsoft Teams stehen zwei Arten von Registerkarten zur Verfügung: Kanal/Gruppe und persönlich. Kanäle/Gruppenregisterkarten liefern Inhalte zu Kanälen und Gruppenchats und sind eine großartige Möglichkeit zum Erstellen von kollaborativen Räumen um dedizierte webbasierte Inhalte. Persönliche Registerkarten, zusammen mit personenbezogenen Bots, gehören zu persönlichen apps und sind für einen einzelnen Benutzer ausgelegt. Sie können für einfachen Zugriff an der linken Navigationsleiste fixiert werden.

## <a name="lesser-known-tab-features"></a>Weniger bekannte registerkartenfunktionen

> [!div class="checklist"]
>
> * Wenn einer APP, die auch einen bot enthält, eine Registerkarte hinzugefügt wird, wird der bot ebenfalls dem Team hinzugefügt.
> * Bekanntheitsgrad der Azure Active Directory (Azure AD)-ID des aktuellen Benutzers.
> * Gebietsschema Awareness für den Benutzer, um die Sprache anzugeben, `en-us` also. 
> * SSO-Funktion (Single Sign-on, einmaliges Anmelden), falls unterstützt.
> * Möglichkeit, Bots oder App-Benachrichtigungen zu verwenden, um Deep Link zur Registerkarte oder zu einer unter Entität innerhalb des Diensts zu erstellen, beispielsweise ein einzelnes Arbeitselement.
> * Die Möglichkeit, ein Aufgabenmodul über Links in einer Registerkarte zu öffnen.
> * Wiederverwendung von SharePoint-Webparts auf der Registerkarte.

## <a name="tabs-user-scenarios"></a>Benutzerszenarien für Registerkarten

**Szenario:** Bereitstelleneiner vorhandenen webbasierten Ressource in Microsoft Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-APP, die Benutzern eine Informations-Unternehmenswebsite zur Verfügung stellt.

**Szenario:** Hinzufügen von Support Seiten zu einem Teams-bot oder einer Messaging Erweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten, *die Webseiten* Inhalte für Benutzer bereitstellen und *Ihnen helfen* .

**Szenario:** Bereitstellen des Zugriffs auf Elemente, mit denen Ihre Benutzer regelmäßig für kooperativen Dialog und Zusammenarbeit interagieren. \
**Beispiel:** Sie erstellen eine Kanal-Gruppe-Registerkarte mit einer tiefen Verknüpfung mit einzelnen Elementen.

## <a name="how-do-tabs-work"></a>Wie funktionieren Registerkarten?

Eine benutzerdefinierte Registerkarte wird im App-Manifest des App-Pakets deklariert. Für jede Webseite, die als Registerkarte in Ihrer APP enthalten sein soll, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie das Microsoft [Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client) zu Ihrer Seite hinzufügen und nach dem Laden der Seite anrufen `microsoftTeams.initialize()` . Dadurch wird Microsoft Teams mitgeteilt, dass Sie Ihre Seite anzeigen, Ihnen Zugriff auf Teams-spezifische Informationen ermöglichen (beispielsweise, wenn der Team-Client das *dunkle Design* ausführt) und Ihnen die Möglichkeit geben, basierend auf den Ergebnissen Maßnahmen zu ergreifen.

Unabhängig davon, ob Sie die Registerkarte innerhalb des Kanals/der Gruppe oder des persönlichen Bereichs verfügbar machen möchten, müssen Sie auf \> ihrer Registerkarte eine <IFRAME-HTML- [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) vorlegen. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams-App-Manifest durch die `contentUrl` -Eigenschaft im Array festgelegt `staticTabs` . Die Inhalte Ihrer Registerkarte sind für alle Benutzer gleich.

Für Channel/Group-Registerkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, mit der Benutzer ihre Inhaltsseiten-URL konfigurieren können, normalerweise mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass die Registerkarte Kanal/Gruppe mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können die Benutzer die Registerkarte konfigurieren, sodass Sie die Umgebung nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die in der Microsoft Teams-Benutzeroberfläche angezeigt wird, eine URL zugeordnet. Durch das Konfigurieren einer Registerkarte werden einfach zusätzliche Parameter zu dieser URL hinzugefügt. Wenn Sie beispielsweise die Registerkarte Azure Boards hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden soll. Die URL der Konfigurationsseite wird durch die  `configurationUrl` -Eigenschaft im `configurableTabs` Array in Ihrem App-Manifest angegeben.

Sie können maximal eine (1) Kanal/Gruppen-Registerkarte und bis zu sechzehn (16) persönliche Registerkarten pro APP haben.

## <a name="mobile-clients"></a>Mobile Clients

Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, `setSettings()` muss die Konfiguration einen Wert für die `websiteUrl` Eigenschaft besitzen. Um eine optimale Benutzerfreundlichkeit sicherzustellen, sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.

> [!div class="nextstepaction"]
> [Weitere Informationen: Anfordern von Geräte Berechtigungen](/concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
>[Weitere Informationen: Berechtigungen für Kamera und Bildergalerie](/concepts/device-capabilities/mobile-camera-image-permissions.md)