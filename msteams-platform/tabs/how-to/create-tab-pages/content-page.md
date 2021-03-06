---
title: Erstellen einer Inhaltsseite
author: laujan
description: Erstellen einer Inhaltsseite
keywords: teams tabs group channel configurable static
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 619ca1079fcdb5a44eec2fa63d6687a0eb65cd4d
ms.sourcegitcommit: 9cfbc44912980a33d2d7c7c85739aeea6ccb41de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "50479872"
---
# <a name="create-a-content-page-for-your-tab"></a>Erstellen einer Inhaltsseite für Ihre Registerkarte

Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird. In der Regel sind diese Teil von:

* Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.
* Eine benutzerdefinierte Kanal-/Gruppenregisterkarte – Nachdem der Benutzer die Registerkarte im entsprechenden Kontext anheftet und konfiguriert hat, wird die Inhaltsseite angezeigt.
* Ein [Aufgabenmodul:](~/task-modules-and-cards/what-are-task-modules.md) Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten. Die Seite wird im modalen Popup gerendert.

Dieser Artikel ist speziell für die Verwendung von Inhaltsseiten als Registerkarten. Der Großteil der hier gezeigten Anleitungen würde jedoch unabhängig davon gelten, wie die Inhaltsseite dem Endbenutzer präsentiert wird.

## <a name="tab-content-and-style-guidelines"></a>Richtlinien für Registerkarteninhalte und -stile

Das übergeordnete Ziel Ihrer Registerkarte sollte es sein, Zugriff auf aussagekräftige und ansprechende Inhalte zu bieten, die einen praktischen und offensichtlichen Zweck haben. Dies bedeutet nicht, dass Sie auf einen ansprechenden Stil verzichten sollten, aber Sie sollten sich auf die Minimierung von Unübersichtlichkeit konzentrieren, indem Sie Das Tabdesign sauber, intuitiv und inhalteverdingend gestalten. Informationen [zu Inhalten und Unterhaltungen finden](~/tabs/design/tabs.md) Sie unter Gleichzeitige Verwendung von Registerkarten und Anleitungen zum [Genehmigungsprozess für Microsoft Teams-Apps](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)

## <a name="integrate-your-code-with-teams"></a>Integrieren von Code in Teams

Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) und einen Aufruf nach dem Laden `microsoftTeams.initialize()` der Seite hinzufügen. So kommunizieren Ihre Seite und der Teams-Client:

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
...
</head>

<body>
...
    <script>
    microsoftTeams.initialize();
    </script>
...
</body>
```

## <a name="accessing-additional-content"></a>Zugreifen auf zusätzliche Inhalte

### <a name="using-the-sdk-to-interact-with-teams"></a>Verwenden des SDK für die Interaktion mit Teams

Das [JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) des Teams-Clients bietet viele zusätzliche Funktionen, die Sie bei der Entwicklung Ihrer Inhaltsseite möglicherweise hilfreich finden.

### <a name="deep-links"></a>Deep-Links

Sie können tiefe Links zu Entitäten in Teams erstellen. In der Regel werden diese zum Erstellen von Links verwendet, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere [Informationen finden Sie unter Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul ist eine modale Popuperfahrung, die Sie von Ihrer Registerkarte aus auslösen können. In der Regel möchten Sie auf einer Inhaltsseite ihren Benutzer nicht durch mehrere Seiten navigieren. Stattdessen verwenden Sie Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zum anderen Zeitpunkt, zu dem Sie dem Benutzer zusätzliche Informationen präsentieren müssen, zu präsentieren. Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden. Vollständige Informationen finden Sie unter Verwenden [von Aufgabenmodulen in](~/task-modules-and-cards/task-modules/task-modules-tabs.md) Registerkarten.

### <a name="valid-domains"></a>Gültige Domänen

Stellen Sie sicher, dass alle in Ihren Registerkarten verwendeten URL-Domänen im `validDomains` Array in Ihrem Manifest enthalten [sind.](~/concepts/build-and-test/apps-package.md) Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifestschemareferenz. Beachten Sie jedoch, dass die Kernfunktionalität Ihrer Registerkarte in Teams und nicht außerhalb von Teams vorhanden ist.

## <a name="reorder-static-personal-tabs"></a>Neu anordnen von statischen persönlichen Registerkarten

Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen. Insbesondere kann ein Entwickler  die Registerkarte Botchat, die immer an die erste Position festgelegt ist, an eine beliebige Stelle in der Persönlichen App-Registerkartenkopfzeile verschieben. Wir haben zwei reservierte Tab-EntityId-Schlüsselwörter deklariert, *Unterhaltungen* und *über*.

Wenn Sie einen Bot  mit einem persönlichen Bereich erstellen, wird er standardmäßig an der ersten Registerkartenposition in einer persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie dem Manifest ein statisches Tab-Objekt mit dem reservierten Schlüsselwort *Unterhaltungen hinzufügen.* Die *Registerkarte* Unterhaltung wird im Web oder Desktop angezeigt, je nach der Stelle, an der Sie die *Registerkarte* Unterhaltung im Array `staticTabs` hinzufügen. 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

## <a name="show-a-native-loading-indicator"></a>Anzeigen eines systemeigenen Ladeindikators

Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie [](../../../resources/schema/manifest-schema.md#showloadingindicator) eine systemeigene Ladeanzeige überall dort bereitstellen, wo Ihre Webinhalte in [](removal-page.md) Teams geladen werden, z. B. Registerkarteninhaltsseite, [](#integrate-your-code-with-teams)Konfigurationsseite, [](configuration-page.md) [Entfernungsseite](../../../task-modules-and-cards/task-modules/task-modules-tabs.md)und Aufgabenmodule in Registerkarten .

> [!NOTE]
> 1. Die systemeigene Ladeanzeige wird auf mobilen Geräten noch nicht unterstützt.
> 2. Wenn Sie im App-Manifest angeben, müssen alle Registerkartenkonfigurations-, Inhalts- und Entfernungsseiten sowie alle iframebasierten Aufgabenmodule dem obligatorischen Protokoll folgen, das unten  `"showLoadingIndicator : true`  aufgeführt ist:


1. Um den Ladeindikator zu zeigen, fügen Sie `"showLoadingIndicator": true` dem Manifest hinzu. 
2. Denken Sie daran, `microsoftTeams.initialize();` auf zu rufen.
3. **Optional**. Wenn Sie bereit sind, auf den Bildschirm zu drucken und den Rest des Anwendungsinhalts verzögert laden möchten, können Sie die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`
4. **Obligatorisch**. Rufen Sie schließlich Teams auf, um zu benachrichtigen, dass Ihre App `microsoftTeams.appInitialization.notifySuccess()` erfolgreich geladen wurde. Teams blendet dann ggf. die Ladeanzeige aus. Wenn nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass für Ihre App ein Zeitsprung aufgetreten ist und ein Fehlerbildschirm mit einer  `notifySuccess`  Wiederholungsoption angezeigt wird.
5. Wenn ihre Anwendung nicht geladen werden kann, können Sie Teams über `microsoftTeams.appInitialization.notifyFailure(reason);` einen Fehler in Verbindung mit dem Server rufen. Dem Benutzer wird dann ein Fehlerbildschirm angezeigt:

```typescript
``
/* List of failure reasons */
export const enum FailedReason {
    AuthFailed = "AuthFailed",
    Timeout = "Timeout",
    Other = "Other"
}
```
>
