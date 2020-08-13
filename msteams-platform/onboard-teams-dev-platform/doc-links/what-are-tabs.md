---
title: Was sind benutzerdefinierte Registerkarten in Microsoft Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: f338387e658733981c16b36ed2a05c15132fc87c
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652001"
---
# <a name="what-are-tabs"></a>Was sind Registerkarten?

Mithilfe von Registerkarten können Sie webbasierten Inhalt in Microsoft Teams einbetten. Es handelt sich um einfache iFrames, die auf in Ihrem App-Manifest deklarierte Domänen zeigen und Teil eines Team Kanals, Gruppenchats oder einer persönlichen APP sein können. *Weitere Informationen finden Sie unter* [Teams JavaScript Client SDK](/javascript/api/overview/msteams-client).

> [!NOTE]
> In Chrome 80 werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt. Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen. *Siehe* [SameSite-Cookie-Attribut (2020 Update)](../../resources/samesite-cookie-update.md).

Es gibt zwei Arten von Registerkarten in Microsoft Teams: Kanal/Gruppe und persönliche Registerkarten. Eine Kanal-Gruppe-Registerkarte bietet Inhalte für Kanäle und Gruppenchats und ist eine hervorragende Möglichkeit zum Erstellen von kollaborativen Räumen um dedizierte webbasierte Inhalte. Persönliche Registerkarten, zusammen mit personenbezogenen Bots, gehören zu persönlichen apps und sind für Interaktionen mit einem einzelnen Benutzer ausgelegt. Sie können für einfachen Zugriff an der linken Navigationsleiste fixiert werden.

## <a name="user-scenarios"></a>Benutzerszenarien

**Szenario:** Bereitstelleneiner vorhandenen webbasierten Ressource in Microsoft Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-APP, die Benutzern eine Informations-Unternehmenswebsite zur Verfügung stellt.

**Szenario:** Hinzufügen von Support Seiten zu einem Teams-bot oder einer Messaging Erweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten, die Webseiteninhalte für Benutzer bereitstellen und Ihnen helfen.

**Szenario:** Bereitstellen des Zugriffs auf Elemente, mit denen Ihre Benutzer regelmäßig für kooperativen Dialog und Zusammenarbeit interagieren. \
**Beispiel:** Sie erstellen eine Kanal-Gruppe-Registerkarte mit einer tiefen Verknüpfung mit einzelnen Elementen.

## <a name="how-do-tabs-work"></a>Wie funktionieren Registerkarten?

Eine benutzerdefinierte Registerkarte wird im App-Manifest des App-Pakets deklariert. Für jede Webseite, die als Registerkarte in Ihrer APP enthalten sein soll, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie das Microsoft [Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client) zu Ihrer Seite hinzufügen und nach dem Laden der Seite anrufen `microsoftTeams.initialize()` . Dadurch wird Microsoft Teams mitgeteilt, dass Sie Ihre Seite anzeigen, Ihnen Zugriff auf Teams-spezifische Informationen ermöglichen (beispielsweise, wenn der Team-Client das dunkle Design ausführt) und Ihnen die Möglichkeit geben, basierend auf den Ergebnissen Maßnahmen zu ergreifen.

Unabhängig davon, ob Sie die Registerkarte innerhalb des Kanals/der Gruppe oder des persönlichen Bereichs verfügbar machen möchten, müssen Sie auf Ihrer Registerkarte eine iframed HTML- [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) präsentieren. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in ihrem Manifest durch die `contentUrl` -Eigenschaft im `staticTabs` Array festgelegt. Die Inhalte Ihrer Registerkarte sind für alle Benutzer gleich.

Für Channel/Group-Registerkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, mit der Ihre Benutzer ihre Inhaltsseiten-URL konfigurieren können, normalerweise mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass die Registerkarte Kanal/Gruppe mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können die Benutzer die Registerkarte so konfigurieren, dass Sie die Umgebung nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder eine Registerkarte konfigurieren, wird der Registerkarte, die in der Microsoft Teams-Benutzeroberfläche angezeigt wird, eine URL zugeordnet. Durch das Konfigurieren einer Registerkarte werden einfach zusätzliche Parameter zu dieser URL hinzugefügt. Wenn Sie beispielsweise die Registerkarte Azure DevOps Board hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden soll. Die URL der Konfigurationsseite wird durch die  `configurationUrl` -Eigenschaft im `configurableTabs` Array in Ihrem App-Manifest angegeben.

Sie können maximal eine Kanal/Gruppen-Registerkarte und bis zu 16 persönliche Registerkarten pro APP haben.

## <a name="lesser-known-tab-features"></a>Weniger bekannte registerkartenfunktionen

* Wenn einer APP, die auch einen bot enthält, eine Registerkarte hinzugefügt wird, wird der bot auch dem Team hinzugefügt.
* Sensibilisierung für die Azure-Active Directory-ID des aktuellen Benutzers.
* Gebietsschema Awareness für den Benutzer, um die Sprache anzugeben (beispielsweise `en-us` ).
* SSO-Funktion, falls unterstützt.
* Möglichkeit, Bots oder App-Benachrichtigungen zu verwenden, um einen tiefen Link zur Registerkarte oder zu einer unter Entität innerhalb des Diensts zu erstellen (beispielsweise eine einzelne Arbeitsaufgabe).
* Die Möglichkeit, ein Aufgabenmodul über Links in einer Registerkarte zu öffnen.
* Verwenden Sie SharePoint-Webparts auf der Registerkarte.

## <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, `setSettings()` muss die Konfiguration über einen Wert für die `websiteUrl` Eigenschaft verfügen (siehe unten). Persönliche Registerkarten sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar. Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze veröffentlicht. Zur Vorbereitung des Updates sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.

## <a name="learn-more"></a>Weitere Informationen

* [Planen Ihrer APP](../../concepts/extensibility-points.md)
* [Erstellen Ihrer APP](../../concepts/building-an-app.md)
* [Bereitstellen Ihrer APP](../../concepts/deploy-and-publish/overview.md)
