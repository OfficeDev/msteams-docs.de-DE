---
title: Nach Veröffentlichung
description: Vorgehensweisen nach dem Veröffentlichen der APP
keywords: Update-App-Update-Manifest für Teams nach Veröffentlichungs Update Zertifizierung
ms.openlocfilehash: 58e81688ab9a8b55d2b035fc9b43cb58dddb6133
ms.sourcegitcommit: 25afe104d10c9a6a2849decf5ec1d08969d827c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "48465915"
---
# <a name="maintain-and-support-your-published-app"></a>Verwalten und Unterstützen Ihrer veröffentlichten App 

Nachdem Ihre APP genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erweitern, indem Sie das Microsoft 365 App Compliance-Programm ausfüllen oder eine Download Schaltfläche auf Ihrer Website hinzufügen.

## <a name="microsoft-365-certified"></a>Microsoft 365 zertifiziert

Das [Microsoft 365 App Compliance-Programm](./application-certification.md)ist ein dreistufiger Ansatz für App-Sicherheit und-Compliance. Jede Schicht baut auf dem nächsten auf – bietet ein mehrstufiges Programm, um die Anforderungen Ihrer Kunden zu erfüllen. Weitere Informationen zur Sicherheit und Compliance-Haltung von Teams-apps finden Sie auf der [Seite "Kompatibilität"](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).

## <a name="add-a-download-button-to-your-product-site"></a>Hinzufügen einer Schaltfläche zum herunterladen zu ihrer Produkt Website

Wenn Ihre APP im Microsoft Teams Global Store installiert ist, können Sie einen Link für Ihre Website generieren, der Teams startet und eine Zustimmung und ein Installationsdialogfeld für Benutzer zur Verfügung stellt, um die APP hinzuzufügen.
Das Format lautet:  `https://teams.microsoft.com/l/app/<appId>` wobei die ID die GUID ist, die Sie im übermittelten Manifest deklarieren.
Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.

## <a name="updating-your-existing-teams-app"></a>Aktualisieren der vorhandenen Teams-App

* Verwenden Sie nicht die Schaltfläche *neue APP hinzufügen* , um Ihre APP erneut zu übermitteln. Verwenden Sie stattdessen die Kachel für Ihre APP auf der Registerkarte Übersicht.
* Die im aktualisierten Manifest enthaltene-ID sollte mit einer erhöhten Versionsnummer im aktuellen Manifest identisch sein.
* Erhöhen Sie die Versionsnummer im Manifest, wenn Sie Änderungen an ihrer Übermittlung einschließlich des App-namens oder aller Metadaten im Manifest vornehmen.
* Aktualisierte Übermittlungen sind erforderlich, um einem neuen Überprüfungs-und Validierungsprozess unterzogen zu werden.

## <a name="app-updates-and-the-user-consent-flow"></a>APP-Updates und der Benutzer Zustimmungs Fluss

Wenn ein Benutzer Ihre Anwendung installiert eines der ersten Schritte, die Sie ausführen, ist die Zustimmung, der APP die Berechtigung für den Zugriff auf die Dienste und Informationen zu erteilen, die die APP für Ihre Aufgabe benötigt. In den meisten Fällen wird, nachdem Sie ein App-Update abgeschlossen haben, die neue Version automatisch für Endbenutzer angezeigt. Es gibt jedoch einige Updates für das [Teams-App-Manifest](../../../../resources/schema/manifest-schema.md) , die eine Benutzerakzeptanz erfordern und das Zustimmungs Verhalten erneut auslösen können:

 >[!div class="checklist"]
>
> * Ein bot wurde hinzugefügt oder entfernt.
> * Der eindeutige Wert eines vorhandenen bot `botId` wurde geändert.
> * Der boolesche Wert eines vorhandenen bot `isNotificationOnly` wurde geändert.
> * Der boolesche Wert eines vorhandenen bot `supportsFiles` wurde geändert.
> * Eine Messaging Erweiterung ( `composeExtensions` ) wurde hinzugefügt oder entfernt.
> * Ein neuer Connector wurde hinzugefügt.
> * Eine neue Registerkarte statisch/persönlich wurde hinzugefügt.
> * Es wurde eine neue konfigurierbare Gruppe/Kanal-Registerkarte hinzugefügt.
> * Die `webApplicationInfo` Werte wurden geändert.
>
