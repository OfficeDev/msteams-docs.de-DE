---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Was tun, nachdem Sie Ihre App veröffentlicht haben
ms.topic: how-to
keywords: Updateupdateupdateupdatemanifest für Teams nach der Veröffentlichung
ms.openlocfilehash: 8644db5e329e15d77062553eda4a41a36b2740ee
ms.sourcegitcommit: e78c9f51c4538212c53bb6c6a45a09d994896f09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2021
ms.locfileid: "51585834"
---
# <a name="maintain-and-support-your-published-app"></a>Verwalten und Unterstützen Ihrer veröffentlichten App 

Nachdem Ihre App genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erhöhen, indem Sie das Microsoft 365 App Compliance Program abschließen oder eine Downloadschaltfläche auf Ihrer Website hinzufügen.

## <a name="microsoft-365-certified"></a>Microsoft 365 Certified

Das [Microsoft 365 App Compliance Program](./application-certification.md)ist ein dreistufiger Ansatz für die Sicherheit und Compliance von Apps. Jede Ebene baut auf der nächsten auf – und bietet ein mehrschichtiges Programm, das den Anforderungen Ihres Kunden entspricht. Weitere Informationen zur Sicherheits- und Compliancehaltung von Teams-Apps finden Sie auf der Seite ["Compliance".](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps)

## <a name="add-a-download-button-to-your-product-site"></a>Hinzufügen einer Downloadschaltfläche zu Ihrer Produktwebsite

Wenn Sich Ihre App im globalen Microsoft Teams Store befindet, können Sie einen Link für Ihre Website generieren, der Teams startet und ein Zustimmungs- und Installationsdialogfeld für Benutzer zum Hinzufügen der App zeigt.
Das Format ist:  `https://teams.microsoft.com/l/app/<appId>` dabei ist appID die GUID, die sie im übermittelten Manifest deklarieren.
Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.

## <a name="updating-your-existing-teams-app"></a>Aktualisieren Ihrer vorhandenen Teams-App

* Verwenden Sie nicht die *Schaltfläche Neue App hinzufügen,* um Ihre App erneut zu übermitteln. Verwenden Sie stattdessen die Kachel für Ihre App auf der Registerkarte Übersicht.
* Die appId im aktualisierten Manifest sollte mit der im aktuellen Manifest identisch sein, mit einer inkrementierten Versionsnummer.
* Erhöhen Sie Ihre Versionsnummer im Manifest, wenn Sie Änderungen an Ihrer Übermittlung vornehmen, einschließlich des App-Namens oder metadaten im Manifest.
* Aktualisierte Übermittlungen sind erforderlich, um einen neuen Überprüfungs- und Überprüfungsprozess durchlaufen zu können.

## <a name="app-updates-and-the-user-consent-flow"></a>App-Updates und der Benutzer-Zustimmungsfluss

Wenn ein Benutzer Ihre Anwendung installiert, ist eine der ersten Aufgaben die Zustimmung, der App die Berechtigung zum Zugriff auf die Dienste und Informationen zu erteilen, die die App benötigt, um ihre Aufgabe zu erfüllen. In den meisten Fällen wird die neue Version nach Abschluss eines App-Updates automatisch für Endbenutzer angezeigt. Es gibt jedoch einige Updates für das [Teams-App-Manifest,](../../../../resources/schema/manifest-schema.md) für die die Benutzerakzeptanz erforderlich ist und dieses Zustimmungsverhalten erneut auslösen kann:

 >[!div class="checklist"]
>
> * Ein Bot wird hinzugefügt oder entfernt.
> * Der eindeutige Wert eines vorhandenen `botId` Bots wird geändert.
> * Der boolesche Wert eines `isNotificationOnly` vorhandenen Bots wird geändert.
> * Der oder der boolesche Wert eines vorhandenen `supportsFiles` `supportsCalling` Bots wird geändert.
> * Eine Messagingerweiterung `composeExtensions` wird hinzugefügt oder entfernt.
> * Es wird ein neuer Connector hinzugefügt.
> * Eine neue statische oder persönliche Registerkarte wird hinzugefügt.
> * Eine neue konfigurierbare Gruppe oder Kanalregisterkarte wird hinzugefügt.
> * Die Darin enthaltenen `webApplicationInfo` Eigenschaften werden geändert. Für Änderungen `webApplicationInfo` an ist die Zustimmung nur im Bereich Teams erforderlich.

### <a name="images-of-user-consent-flow"></a>Bilder des Benutzer-Zustimmungsflusses:

**Einrichten eines Connectors** – Dieser Bildschirm wird nur für Teams-Benutzer angezeigt.

![Einrichten eines Konnektordiagramms für den Zustimmungsfluss](../../../../assets/images/connector-teams-consentflow.png)

**Benutzer-Zustimmungsfluss–** Dieser Bildschirm ist sowohl für persönliche als auch für Gruppenbereiche üblich. Aktivieren Sie hier das **Kontrollkästchen Zustimmung im** Namen Ihrer Organisation, und wählen Sie Akzeptieren **aus.**

![Berechtigungsdiagramm](../../../../assets/images/user-consent-flow.png)
