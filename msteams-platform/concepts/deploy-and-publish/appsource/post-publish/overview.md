---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Verwalten Sie Ihre veröffentlichte Microsoft Teams-App. Analysieren Sie die App-Nutzung, veröffentlichen Sie Updates, bewerben Sie Ihre App, schließen Sie die Microsoft 365-Zertifizierung ab.
ms.topic: conceptual
ms.localizationpriority: high
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 77b17cb837312bca5b253fbd99fba2d0503f1744
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560470"
---
# <a name="maintain-your-published-microsoft-teams-app"></a>Unterhalt Ihrer veröffentlichte Microsoft Teams-App

Wenn Ihre App im Microsoft Teams-Store gelistet ist, sollten Sie sich Gedanken darüber machen, wie Sie die App in Zukunft pflegen und die Downloads und die Nutzung steigern können.

## <a name="analyze-app-usage"></a>Analysieren der App-Nutzung

Sie können Ihre App-Nutzung im [Teams App-Nutzungsbericht](/office/dev/store/teams-apps-usage) im Partner Center nachverfolgen. Zu den Metriken gehören aktive monatliche, tägliche und wöchentliche Benutzer sowie Aufbewahrungs- und Intensitätsdiagramme, mit denen Sie Änderungen und Nutzungshäufigkeit nachverfolgen können.

Bei Daten für neu veröffentlichte Apps dauert es etwa eine Woche, bis sie im Bericht angezeigt werden.

## <a name="publish-updates-to-your-app"></a>Veröffentlichen von Updates für Ihre App

> [!NOTE]
> Teams Store hat sich weiterentwickelt:
>
> Zuvor wurden die Links durch Auswählen des Ellipsensymbols auf der App-Kachel kopiert. Bei der aktualisierten Teams-Storeerfahrung haben Sie über die Registerkarte „Details“ der Apps Zugriff auf diese. Dieses Update wird ab dem 01. März 2022 allgemein verfügbar sein (GA).

Sie können Änderungen an Ihrer App (z. B. neue Features oder sogar Metadaten) in Partner Center übermitteln. Diese Änderungen erfordern einen neuen Überprüfungsprozess.

Stellen Sie beim Veröffentlichen von Updates Folgendes sicher:

* Ändern Sie Ihre App-ID nicht.
* Erhöhen Sie die Versionsnummer Ihrer App.
* In Partner Center, don't select **Add a new app** to do the update. Go to your app's page instead.

### <a name="app-updates-requiring-user-consent"></a>App-Updates, die eine Zustimmung des Benutzers erfordern

Wenn ein Benutzer Ihre App installiert, muss er der App die Berechtigung erteilen, auf die Dienste und Informationen zuzugreifen, die die App für die Funktion benötigt. In den meisten Fällen müssen Benutzer dies einmal tun, und eine neue Version Ihrer App wird automatisch installiert.
Wenn Sie jedoch eine der folgenden Änderungen an Ihrer App vornehmen, müssen Ihre vorhandenen Benutzer eine andere Berechtigungsanforderung akzeptieren, um das Update zu installieren:

* Sie fügen einen Bot hinzu bzw. entfernen einen.
* Sie ändern die Bot-ID.
* Sie ändern die Konfiguration der unidirektionalen Benachrichtigung eines Bots.
* Sie ändern Sie Unterstützung eines Bots für das Hochladen und Herunterladen von Dateien.
* Fügen Sie eine Nachrichtenerweiterung hinzu oder entfernen Sie sie.
* Sie fügen eine persönliche Registerkarte hinzu.
* Sie fügen eine Kanal- und Gruppen-Registerkarte hinzu.
* Sie fügen einen Connector hinzu.
* Modify configurations related to your Microsoft Azure Active Directory (Azure AD) app registration. For more information, see [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="fix-issues-with-your-published-app"></a>Beheben von Problemen mit Ihrer veröffentlichten App

Microsoft führt tägliche Automatisierungstests für Apps aus, die im Teams-Store aufgelistet sind. Wenn Probleme mit Ihrer App identifiziert werden, kontaktieren wir Sie mit einem detaillierten Bericht über die Reproduzierbarkeit der Probleme und Empfehlungen zu deren Behebung. Wenn Sie die Probleme nicht innerhalb einer bestimmten Zeitspanne beheben können, wird Ihr App-Eintrag möglicherweise aus dem Store entfernt.

## <a name="promote-your-app-on-another-site"></a>Bewerben Ihrer App auf einer anderen Website

Wenn Ihre App im Teams-Store aufgelistet ist, können Sie einen Link erstellen, der Teams startet und ein Dialogfeld zum Installieren Ihrer App anzeigt. Sie können diesen Link z. B. mit einer Downloadschaltfläche auf der Marketingseite Ihres Produkts einfügen.

Erstellen Sie den Link mithilfe der folgenden URL, an die Ihre App-ID angefügt ist: `https://teams.microsoft.com/l/app/<your-app-id>`.

## <a name="complete-microsoft-365-certification"></a>Durchführen einer Microsoft 365-Zertifizierung

Eine [Microsoft 365-Zertifizierung](/microsoft-365-app-certification/docs/certification) bietet die Sicherheit, dass Daten und der Datenschutz angemessen gesichert und geschützt sind, wenn eine Office-Anwendung oder ein Add-In eines Drittanbieters in Ihrem Microsoft 365-Ökosystem installiert wird. Die Zertifizierung bestätigt, dass Ihre App mit Microsoft-Technologien kompatibel ist, den bewährten Cloud App Security-Verfahren entspricht und von Microsoft unterstützt wird.

## <a name="stop-app-distribution"></a>Beenden der App-Verteilung

Sie können eine App aus dem [kommerziellen Microsoft Marketplace](/azure/marketplace/overview) entfernen, um deren Entdeckung und Verwendung zu verhindern.

Führen Sie die folgenden Schritte aus, um die Verteilung einer App nach der Veröffentlichung zu stoppen:

1. Wählen Sie auf der Seite **Produktübersicht** die Option **Verkauf beenden** aus. Es entfernt die App aus der Microsoft AppSource.
1. Um die Aufhebung der Auflistung der App zu initiieren, wählen Sie auf **Partner Center** die Seite **Übersicht** und dann **Verkauf beenden** aus.

Nachdem Sie die Verteilung einer App beendet haben, können Sie sie weiterhin im Partner Center mit dem Status **Nicht verfügbar** sehen. Wenn Sie sich entscheiden, die App erneut aufzulisten, befolgen Sie die Anweisungen zum [Veröffentlichen Ihrer App im Microsoft Teams Store](../publish.md).

## <a name="see-also"></a>Siehe auch

[Monetarisieren Sie Ihre App über den Microsoft Commercial Marketplace](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
