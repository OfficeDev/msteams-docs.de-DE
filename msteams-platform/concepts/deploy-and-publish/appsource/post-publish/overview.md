---
title: Nach Veröffentlichung
description: Vorgehensweisen nach dem Veröffentlichen der APP
keywords: Update Zertifikat für Teams nach Veröffentlichung
ms.openlocfilehash: 05e4ea47bbf81967ccf086230bf0ad8c633f6e0b
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674176"
---
# <a name="maintain-and-support-your-published-app"></a>Verwalten und unterstützen Ihrer veröffentlichten App 

Nachdem Ihre APP genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erweitern, indem Sie die APP-Zertifizierung erreichen oder eine Download Schaltfläche Ihrer Website hinzufügen.

## <a name="application-certificate"></a>Anwendungszertifikat

Microsoft stellt ein [Anwendungs Zertifizierungsprogramm](./application-certification.md) bereit, das Ihre APP-Informationen kompiliert und auf der [Seite Microsoft Teams-App-Sicherheit und-Kompatibilität](https://aka.ms/AppCertification)präsentiert. Diese Informationen sollen Administratoren dabei helfen, Apps auszuwählen, die für Ihre Organisation sicher sind.

## <a name="add-a-download-button-to-your-product-site"></a>Hinzufügen einer Schaltfläche zum herunterladen zu ihrer Produkt Website

Wenn Ihre APP im Microsoft Teams Store gespeichert ist, können Sie einen Link für Ihre Website generieren, der Teams startet und eine Zustimmung und ein Installationsdialogfeld für Benutzer zum Hinzufügen der APP anzeigt.
Das Format lautet: `https://teams.microsoft.com/l/app/<appId>` wobei die ID die GUID ist, die Sie im übermittelten Manifest deklarieren.
Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.

## <a name="updating-your-existing-teams-app"></a>Aktualisieren der vorhandenen Teams-App

* Verwenden Sie nicht die Schaltfläche *neue APP hinzufügen* , um Ihre APP erneut zu übermitteln. Verwenden Sie stattdessen die Kachel für Ihre APP auf der Registerkarte Übersicht.
* Die im aktualisierten Manifest enthaltene-ID sollte mit einer erhöhten Versionsnummer im aktuellen Manifest identisch sein.
* Erhöhen Sie die Versionsnummer in ihrem Manifest.

### <a name="when-does-updating-your-app-trigger-the-user-consent-flow"></a>Wann löst die Aktualisierung Ihrer APP den Benutzer Zustimmungs Fluss aus?

Wenn ein Benutzer Ihre Anwendung installiert eines der ersten Schritte, die Sie ausführen, ist die Zustimmung, der APP die Berechtigung für den Zugriff auf die Dienste und Informationen zu erteilen, die die APP für Ihre Aufgabe benötigt. Wenn Sie Ihre APP aktualisieren, kann dies das Zustimmungs Verhalten erneut auslösen, insbesondere dann, wenn Sie eine oder mehrere der folgenden Änderungen vorgenommen haben:

* Hinzufügen einer neuen Funktion zu einer APP, beispielsweise Hinzufügen eines bot zu einer nur-Tab-app.
* Ändern des Berechtigungs Arrays im Manifest.
* Erhöhen Sie Ihre APP-Versionsnummer in ihrem Manifest.
