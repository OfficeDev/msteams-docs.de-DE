---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Was Sie sich überlegen sollten, sobald Ihr Store im Teams und AppSource aufgeführt ist.
ms.topic: conceptual
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 8e4656ea7ca9f373123026a50ecb837d1a64e3fa
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230917"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Verwalten Der veröffentlichten Microsoft Teams App

Wenn Ihre App im Microsoft Teams aufgeführt ist, überlegen Sie, wie Sie die App in Zukunft verwalten und Downloads und Nutzung erhöhen.

## <a name="publish-updates-to-your-app"></a>Veröffentlichen von Updates für Ihre App

Sie können Änderungen an Ihrer App (z. B. neue Features oder sogar Metadaten) im Partner Center übermitteln. Diese Änderungen erfordern einen neuen Überprüfungsprozess.

Stellen Sie beim Veröffentlichen von Updates Folgendes sicher:

* Ändern Sie ihre App-ID nicht.
* Erhöhen Sie die Versionsnummer Ihrer App.
* Wählen Sie im Partner Center keine Option **Neue App hinzufügen aus, um** das Update zu tun. Wechseln Sie stattdessen zur Seite Ihrer App.

### <a name="app-updates-requiring-user-consent"></a>App-Updates, die die Zustimmung des Benutzers erfordern

Wenn ein Benutzer Ihre App installiert, muss er der App die Berechtigung zum Zugriff auf die Dienste und Informationen erteilen, die die App zum Funktionieren benötigt. In den meisten Fällen müssen Benutzer dies nur einmal tun, und neue Versionen Ihrer App werden automatisch installiert.

Wenn Sie jedoch eine der folgenden Änderungen an Ihrer App vornehmen, müssen Ihre vorhandenen Benutzer eine andere Berechtigungsanforderung akzeptieren, um das Update zu installieren:

* Hinzufügen oder Entfernen eines Bots.
* Ändern Sie die Bot-ID.
* Ändern sie die Konfiguration der one-way-Benachrichtigung eines Bots.
* Ändern sie die Unterstützung eines Bots für das Hochladen und Herunterladen von Dateien.
* Hinzufügen oder Entfernen einer Messagingerweiterung.
* Fügen Sie eine persönliche Registerkarte hinzu.
* Fügen Sie einen Kanal und eine Gruppenregisterkarte hinzu.
* Fügen Sie einen Connector hinzu.
* Ändern von Konfigurationen im Zusammenhang mit Azure Active Directory (Azure AD)-App-Registrierung. Weitere Informationen finden Sie unter [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="fix-issues-with-your-published-app"></a>Beheben von Problemen mit ihrer veröffentlichten App

Microsoft führt tägliche Automatisierungstests für Apps durch, die im Teams sind. Wenn Probleme mit Ihrer App identifiziert werden, wenden wir uns an Sie mit einem detaillierten Bericht darüber, wie Sie die Probleme und Empfehlungen reproduzieren, um sie zu beheben. Wenn Sie die Probleme innerhalb einer angegebenen Zeitachse nicht beheben können, wird Ihr App-Eintrag möglicherweise aus dem Store entfernt.

## <a name="promote-your-app-on-another-site"></a>Bewerben Ihrer App auf einer anderen Website

Wenn Ihre App im Teams aufgeführt ist, können Sie einen Link erstellen, der Teams startet und ein Dialogfeld zum Installieren Der App anzeigt. Sie können diesen Link beispielsweise mit einer Downloadschaltfläche auf der Marketingseite Ihres Produkts hinzufügen.

Erstellen Sie den Link mit der folgenden URL, die mit Ihrer App-ID angefügt ist: `https://teams.microsoft.com/l/app/<your-app-id>` .

## <a name="complete-microsoft-365-certification"></a>Vollständige Microsoft 365 Zertifizierung

[Microsoft 365 Zertifizierung](/microsoft-365-app-certification/docs/certification) bietet die Garantie, dass Daten und Datenschutz angemessen gesichert und geschützt werden, wenn ein Drittanbieter-Office-App oder -Add-In in Ihrem Microsoft 365 installiert wird. Die Zertifizierung bestätigt, dass Ihre App mit Microsoft-Technologien kompatibel, mit bewährten Methoden für die Cloud-App-Sicherheit kompatibel und von Microsoft unterstützt wird.

## <a name="see-also"></a>Siehe auch

[Monetarisieren Sie Ihre App über den Microsoft Commercial Marketplace](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
