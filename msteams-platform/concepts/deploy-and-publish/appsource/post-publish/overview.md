---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Was Sie denken sollten, sobald Ihr Store im Teams Store und in AppSource aufgeführt ist.
ms.topic: conceptual
ms.localizationpriority: medium
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: ef4ccb10dbfecd10610ef30971ddd43285c0cb0e
ms.sourcegitcommit: c04a1a792773a9d5c61169c5702d94a8c478ad1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2021
ms.locfileid: "60260631"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Verwalten der veröffentlichten Microsoft Teams-App

Nachdem Ihre App im Microsoft Teams Store aufgeführt ist, überlegen Sie, wie Sie die App in Zukunft verwalten und Downloads und Nutzung erhöhen.

## <a name="publish-updates-to-your-app"></a>Veröffentlichen von Updates für Ihre App

Sie können Änderungen an Ihrer App (z. B. neue Features oder sogar Metadaten) im Partner Center übermitteln. Diese Änderungen erfordern einen neuen Überprüfungsprozess.

Stellen Sie beim Veröffentlichen von Updates Folgendes sicher:

* Ändern Sie ihre App-ID nicht.
* Erhöhen Sie die Versionsnummer Ihrer App.
* Wählen Sie im Partner Center keine **neue App** hinzufügen aus, um das Update durchführen zu können. Wechseln Sie stattdessen zur App-Seite.

### <a name="app-updates-requiring-user-consent"></a>App-Updates, die eine Zustimmung des Benutzers erfordern

Wenn ein Benutzer Ihre App installiert, muss er der App die Berechtigung erteilen, auf die Dienste und Informationen zuzugreifen, die die App für die Funktion benötigt. In den meisten Fällen müssen Benutzer dies einmal tun, und neue Versionen Ihrer App werden automatisch installiert.

Wenn Sie jedoch eine der folgenden Änderungen an Ihrer App vornehmen, müssen Ihre vorhandenen Benutzer eine andere Berechtigungsanforderung akzeptieren, um das Update zu installieren:

* Fügen Sie einen Bot hinzu oder entfernen Sie einen Bot.
* Ändern Sie die Bot-ID.
* Ändern der Unidirektionale Benachrichtigungskonfiguration eines Bots.
* Ändern der Unterstützung eines Bots für das Hochladen und Herunterladen von Dateien.
* Hinzufügen oder Entfernen einer Messaging-Erweiterung.
* Fügen Sie eine persönliche Registerkarte hinzu.
* Fügen Sie einen Kanal und eine Gruppenregisterkarte hinzu.
* Fügen Sie einen Connector hinzu.
* Ändern Sie Konfigurationen im Zusammenhang mit Ihrer Azure Active Directory (Azure AD)-App-Registrierung. Weitere Informationen finden Sie unter [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="fix-issues-with-your-published-app"></a>Beheben von Problemen mit Ihrer veröffentlichten App

Microsoft führt tägliche Automatisierungstests für Apps aus, die im Teams Store aufgeführt sind. Wenn Probleme mit Ihrer App identifiziert werden, wenden wir uns an Sie mit einem detaillierten Bericht darüber, wie Sie die Probleme und Empfehlungen zur Behebung reproduzieren. Wenn Sie die Probleme nicht innerhalb einer angegebenen Zeitachse beheben können, wird Ihr App-Eintrag möglicherweise aus dem Store entfernt.

## <a name="promote-your-app-on-another-site"></a>Bewerben Ihrer App auf einer anderen Website

Wenn Ihre App im Teams Store aufgeführt ist, können Sie einen Link erstellen, der Teams startet und ein Dialogfeld zum Installieren Ihrer App anzeigt. Sie können diesen Link z. B. mit einer Downloadschaltfläche auf der Marketingseite Ihres Produkts einschließen.

Erstellen Sie den Link mithilfe der folgenden URL, die mit Ihrer App-ID angefügt wurde: `https://teams.microsoft.com/l/app/<your-app-id>` .

## <a name="complete-microsoft-365-certification"></a>Abschließen Microsoft 365 Zertifizierung

[Microsoft 365 Zertifizierung](/microsoft-365-app-certification/docs/certification) bietet Zusicherungen, dass Daten und Datenschutz angemessen gesichert und geschützt sind, wenn ein Office-App oder Add-In eines Drittanbieters in Ihrem Microsoft 365-Ökosystem installiert wird. Die Zertifizierung bestätigt, dass Ihre App mit Microsoft-Technologien kompatibel ist, den bewährten Methoden für cloudbasierte App-Sicherheit entspricht und von Microsoft unterstützt wird.

## <a name="see-also"></a>Weitere Artikel

[Monetarisieren Sie Ihre App über den Microsoft Commercial Marketplace](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
