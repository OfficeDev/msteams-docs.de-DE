---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Was Sie denken sollten, sobald Ihr Store im Teams Store und in AppSource aufgeführt ist.
ms.topic: conceptual
ms.localizationpriority: medium
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: cfbfc1cb1796bcdcf1946c87756e3fa2285eff69
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453579"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Unterhalt Ihrer veröffentlichte Microsoft Teams-App

Nachdem Ihre App im Microsoft Teams Store aufgeführt ist, überlegen Sie, wie Sie die App in Zukunft verwalten und Downloads und Nutzung erhöhen.

## <a name="analyze-app-usage"></a>Analysieren der App-Nutzung

Sie können Ihre App-Nutzung im [Bericht Teams App-Nutzung](/office/dev/store/teams-apps-usage) im Partner Center nachverfolgen. Zu den Metriken gehören aktive monatliche, tägliche und wöchentliche Benutzer sowie Aufbewahrungs- und Intensitätsdiagramme, mit denen Sie Änderungen und Nutzungshäufigkeit nachverfolgen können.

Bei Daten für neu veröffentlichte Apps dauert es etwa eine Woche, bis sie im Bericht angezeigt werden.

## <a name="publish-updates-to-your-app"></a>Veröffentlichen von Updates für Ihre App

> [!NOTE]
> Teams Store hat sich weiterentwickelt:
>
> Zuvor wurden die Links kopiert, indem Ellipsen auf der App-Kachel ausgewählt wurden. Mit der aktualisierten Teams Store-Erfahrung greifen Sie auf der Registerkarte "Details" der Apps auf dasselbe zu. Dieses Update wird bis zum 1. März 2022 allgemein verfügbar sein.

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
* Ändern Sie Konfigurationen im Zusammenhang mit ihrer Microsoft Azure Active Directory (Azure AD)-App-Registrierung. Weitere Informationen finden Sie unter [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="fix-issues-with-your-published-app"></a>Beheben von Problemen mit Ihrer veröffentlichten App

Microsoft führt tägliche Automatisierungstests für Apps aus, die im Teams Store aufgeführt sind. Wenn Probleme mit Ihrer App identifiziert werden, wenden wir uns an Sie mit einem detaillierten Bericht darüber, wie Sie die Probleme und Empfehlungen zur Behebung reproduzieren. Wenn Sie die Probleme nicht innerhalb einer angegebenen Zeitachse beheben können, wird Ihr App-Eintrag möglicherweise aus dem Store entfernt.

## <a name="promote-your-app-on-another-site"></a>Bewerben Ihrer App auf einer anderen Website

Wenn Ihre App im Teams Store aufgeführt ist, können Sie einen Link erstellen, der Teams startet und ein Dialogfeld zum Installieren Ihrer App anzeigt. Sie können diesen Link z. B. mit einer Downloadschaltfläche auf der Marketingseite Ihres Produkts einschließen.

Erstellen Sie den Link mithilfe der folgenden URL, die mit Ihrer App-ID angefügt wurde: `https://teams.microsoft.com/l/app/<your-app-id>`.

## <a name="complete-microsoft-365-certification"></a>Abschließen Microsoft 365 Zertifizierung

[Microsoft 365 Zertifizierung](/microsoft-365-app-certification/docs/certification) bietet Zusicherungen, dass Daten und Datenschutz angemessen gesichert und geschützt sind, wenn ein Office-App oder Add-In eines Drittanbieters in Ihrem Microsoft 365 Ökosystem installiert wird. Die Zertifizierung bestätigt, dass Ihre App mit Microsoft-Technologien kompatibel ist, den bewährten Methoden für cloudbasierte App-Sicherheit entspricht und von Microsoft unterstützt wird.

## <a name="see-also"></a>Siehe auch

[Monetarisieren Sie Ihre App über den Microsoft Commercial Marketplace](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
