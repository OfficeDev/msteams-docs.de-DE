---
title: Was sind benutzerdefinierte Registerkarten in Microsoft Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: v-laujan
ms.openlocfilehash: 7560a9a7d19ca0182b2f5f45b304a96a0f2dddd4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674528"
---
# <a name="what-are-microsoft-teams-custom-tabs"></a>Was sind benutzerdefinierte Microsoft Teams-Registerkarten?

Registerkarten sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind. Sie können als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder als persönliche App für einen einzelnen Benutzer hinzugefügt werden. Als Teil ihrer App können Sie benutzerdefinierte Registerkarten hinzufügen, um Ihre eigenen Webinhalte in Microsoft Teams einzubetten und mit dem [JavaScript-Client-SDK von Teams](/javascript/api/overview/msteams-client)Ihrem Webinhalt Teams-spezifische Funktionen hinzuzufügen.

> [!NOTE]
> In Chrome 80, das für die Veröffentlichung Anfang 2020 vorgesehen ist, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt. Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen. *Siehe* [SameSite-Cookie-Attribut (2020 Update)](../resources/samesite-cookie-update.md).

Es gibt zwei Arten von Registerkarten in Microsoft Teams – Kanal/Gruppe und persönlich. Eine Kanal-Gruppe-Registerkarte bietet Inhalte für Kanäle und Gruppenchats und ist eine hervorragende Möglichkeit zum Erstellen von kollaborativen Räumen um dedizierte webbasierte Inhalte. Persönliche Registerkarten, zusammen mit personenbezogenen Bots, gehören zu persönlichen apps und sind für einen einzelnen Benutzer ausgelegt. Sie können für einfachen Zugriff an der linken Navigationsleiste fixiert werden.

## <a name="tabs-user-scenarios"></a>Benutzerszenarien für Registerkarten

**Szenario:** Bereitstelleneiner vorhandenen webbasierten Ressource in Microsoft Teams. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-APP, die Benutzern eine Informations-Unternehmenswebsite zur Verfügung stellt.

**Szenario:** Hinzufügen von Support Seiten zu einem Teams-bot oder einer Messaging Erweiterung. \
**Beispiel:** Sie erstellen persönliche Registerkarten, die Webseiteninhalte für Benutzer bereitstellen und Ihnen helfen.

**Szenario:** Bereitstellen des Zugriffs auf Elemente, mit denen Ihre Benutzer regelmäßig für kooperativen Dialog und Zusammenarbeit interagieren. \
**Beispiel:** Sie erstellen eine Kanal-Gruppe-Registerkarte mit einer tiefen Verknüpfung mit einzelnen Elementen.

## <a name="how-do-tabs-work"></a>Wie funktionieren Registerkarten?

Eine benutzerdefinierte Registerkarte wird im App-Manifest des App-Pakets deklariert. Für jede Webseite, die als Registerkarte in Ihrer APP enthalten sein soll, definieren Sie eine URL und einen Bereich. Darüber hinaus müssen Sie das Microsoft [Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client) zu Ihrer Seite hinzu `microsoftTeams.initialize()` fügen und nach dem Laden der Seite anrufen. Dadurch wird Microsoft Teams mitgeteilt, dass Sie Ihre Seite anzeigen, Ihnen Zugriff auf Teams-spezifische Informationen ermöglichen (beispielsweise, wenn der Team-Client das dunkle Design ausführt) und Ihnen die Möglichkeit geben, basierend auf den Ergebnissen Maßnahmen zu ergreifen.

Unabhängig davon, ob Sie die Registerkarte innerhalb des Kanals/der Gruppe oder des persönlichen Bereichs verfügbar machen möchten, müssen Sie auf Ihrer Registerkarte eine iframed HTML- [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) präsentieren. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in ihrem Manifest durch die `contentUrl` -Eigenschaft im `staticTabs` Array festgelegt. Die Inhalte Ihrer Registerkarte sind für alle Benutzer gleich.

Für Channel/Group-Registerkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, mit der Ihre Benutzer ihre Inhaltsseiten-URL konfigurieren können, normalerweise mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass die Registerkarte Kanal/Gruppe mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können die Benutzer die Registerkarte so konfigurieren, dass Sie die Umgebung nach Bedarf anpassen können. Wenn Sie beispielsweise die Registerkarte Azure DevOps Board hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden soll. Die URL der Konfigurationsseite wird durch die `configurationUrl` -Eigenschaft im `configurableTabs` Array in Ihrem App-Manifest angegeben.

Sie können maximal eine (1) Kanal/Gruppen-Registerkarte und bis zu sechzehn (16) persönliche Registerkarten pro APP haben.

## <a name="mobile-clients"></a>Mobile Clients

Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, muss `setSettings()` die Konfiguration über einen Wert für die `websiteUrl` Eigenschaft verfügen (siehe unten). Persönliche Registerkarten sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar. Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze veröffentlicht. Zur Vorbereitung des Updates sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.
