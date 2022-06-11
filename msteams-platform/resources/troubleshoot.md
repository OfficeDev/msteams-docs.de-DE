---
title: Problembehandlung für Ihre App
description: Behandeln von Problemen oder Fehlern beim Erstellen von Apps für Microsoft Teams
keywords: Problembehandlung bei der Entwicklung von Teams-Apps
localization_priority: Normal
ms.topic: troubleshooting
ms.date: 07/09/2018
ms.openlocfilehash: 76a1a4d45757dff36d45c73f1ea5f2791fbe2e02
ms.sourcegitcommit: 12510f34b00bfdd0b0e92d35c8dbe6ea1f6f0be2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2022
ms.locfileid: "66032823"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Problembehandlung für Ihre Microsoft Teams-App

## <a name="troubleshooting-tabs"></a>Problembehandlung bei Registerkarten

### <a name="accessing-the-devtools"></a>Zugreifen auf die DevTools

Sie können [DevTools im Teams-Client](~/tabs/how-to/developer-tools.md) öffnen, um eine ähnliche Erfahrung wie das Drücken von F12 (auf Windows) oder Command-Option-I (unter MacOS) in einem Browser zu erhalten.

### <a name="blank-tab-screen"></a>Leerer Registerkartenbildschirm

Wenn Ihr Inhalt in der Registerkartenansicht nicht angezeigt wird, könnte dies folgende Aktionen sein:

* Ihre Inhalte können nicht in einem `<iframe>`angezeigt werden.
* die Inhaltsdomäne nicht in der Liste ["validDomains](~/resources/schema/manifest-schema.md#validdomains) " im Manifest enthalten ist.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>Die Schaltfläche "Speichern" ist im Dialogfeld "Einstellungen" nicht aktiviert.

Rufen Sie unbedingt auf, `microsoftTeams.settings.setValidityState(true)` sobald der Benutzer alle erforderlichen Daten auf der Einstellungsseite eingegeben oder ausgewählt hat, um die Schaltfläche "Speichern" zu aktivieren.

### <a name="the-tab-settings-cant-be-saved-on-selecting-save"></a>Die Registerkarteneinstellungen können nicht gespeichert werden, wenn Sie "Speichern" auswählen.

Wenn Sie beim Hinzufügen einer Registerkarte " **Speichern"** auswählen, aber eine Fehlermeldung erhalten, die anzeigt, dass die Einstellungen nicht gespeichert werden können, kann das Problem eine von zwei Klassen von Problemen sein:

* **Die Erfolgsmeldung zum Speichern wurde nie empfangen**: Wenn ein Speicherhandler mit `microsoftTeams.settings.registerOnSaveHandler(handler)`registriert wurde, muss der Rückruf aufrufen `saveEvent.notifySuccess()`.

  * Wenn der Rückruf nicht innerhalb von 30 Sekunden aufgerufen `saveEvent.notifySuccess()` wird oder stattdessen aufruft `saveEvent.notifyFailure(reason)` , wird dieser Fehler angezeigt.
  * Wenn kein Speicherhandler registriert wurde, wird der `saveEvent.notifySuccess()` Aufruf automatisch ausgeführt, wenn der Benutzer " **Speichern**" auswählt.

* **Die bereitgestellten Einstellungen waren ungültig**: Der andere Grund, warum die Einstellungen möglicherweise nicht gespeichert werden, ist, ob der Aufruf `microsoftTeams.setSettings(settings)` eines ungültigen Einstellungsobjekts oder der Aufruf überhaupt nicht erfolgt ist. Weitere Informationen finden Sie im nächsten Abschnitt, Allgemeine Probleme mit dem Einstellungsobjekt.

### <a name="common-problems-with-the-settings-object"></a>Häufige Probleme mit dem Einstellungsobjekt

* `settings.entityId` fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl` fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl` oder die optional `settings.removeUrl`sind oder `settings.websiteUrl` angegeben, aber nicht gültig sind. Die URLs müssen HTTPS verwenden und müssen entweder dieselbe Domäne wie die Einstellungsseite sein oder in der Liste des Manifests `validDomains` angegeben sein.

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Der Benutzer kann nicht authentifiziert oder Ihr Authentifizierungsanbieter auf der Registerkarte angezeigt werden.

Sofern Sie keine automatische Authentifizierung durchführen, müssen Sie den Authentifizierungsprozess befolgen, der vom [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) bereitgestellt wird.

> [!NOTE]
>Wir verlangen, dass der gesamte Authentifizierungsfluss in Ihrer Domäne beginnt und endet, die im `validDomains` Objekt in Ihrem Manifest aufgeführt sein muss.

Weitere Informationen zur Authentifizierung finden Sie unter [Authentifizieren eines Benutzers](~/concepts/authentication/authentication.md).

### <a name="static-tabs-not-showing-up"></a>Statische Registerkarten werden nicht angezeigt

Es gibt ein bekanntes Problem, bei dem beim Aktualisieren einer vorhandenen Bot-App mit einer neuen oder aktualisierten statischen Registerkarte diese Registerkartenänderung beim Zugriff auf die App aus einer persönlichen Chatunterhaltung nicht angezeigt wird.  Um die Änderung anzuzeigen, sollten Sie einen neuen Benutzer oder eine neue Testinstanz testen oder über das Apps-Flyout auf den Bot zugreifen.

## <a name="troubleshooting-bots"></a>Problembehandlung bei Bots

### <a name="cant-add-my-bot"></a>Mein Bot kann nicht hinzugefügt werden.

Apps müssen vom Office 365 Mandantenadministrator aktiviert werden, damit sie von Endbenutzern geladen werden können. In einigen Fällen sind dem Office 365 Mandanten möglicherweise mehrere SKUs zugeordnet, und damit Bots in allen SKUs funktionieren, müssen sie in allen SKUs aktiviert sein. Weitere Informationen finden [Sie unter "Vorbereiten Ihres Office 365 Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md)".

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Bot kann nicht als Mitglied eines Teams hinzugefügt werden

Bots müssen zuerst in ein Team hochgeladen werden, bevor in einem Kanal dieses Teams darauf zugegriffen werden kann. Weitere Informationen zu diesem Vorgang finden Sie unter [Hochladen Ihrer App in einem Team](~/concepts/deploy-and-publish/apps-upload.md).

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>Mein Bot erhält meine Nachricht nicht in einem Kanal

Bots in Kanälen empfangen Nachrichten nur, wenn sie explizit @mentioned werden, auch wenn Sie auf eine vorherige Bot-Nachricht antworten. Die einzige Ausnahme, in der der Botname in einer Nachricht möglicherweise nicht angezeigt wird, ist, wenn der Bot eine `imBack` Aktion als Ergebnis einer CardAction empfängt, die er ursprünglich gesendet hat.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>Mein Bot versteht meine Befehle in einem Kanal nicht

Da Bots in Kanälen Nachrichten nur empfangen, wenn sie @mentioned sind, enthalten alle Nachrichten, die Ihr Bot in einem Kanal empfängt, diese @mention in das Textfeld. Es empfiehlt sich, den Botnamen selbst aus allen eingehenden Textnachrichten zu entfernen, bevor Sie ihn an Ihre Analyselogik übergeben. Lesen Sie [Erwähnungen](../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions) , um Tipps zur Behandlung dieses Falls zu erfahren.

## <a name="issues-with-packaging-and-uploading"></a>Probleme beim Packen und Hochladen

### <a name="error-while-reading-manifestjson"></a>Fehler beim Lesen von manifest.json

Die meisten Manifestfehler geben einen Hinweis darauf, welches feld fehlt oder welches ungültig ist. Wenn die JSON-Datei jedoch überhaupt nicht als JSON gelesen werden kann, wird diese generische Fehlermeldung verwendet.

Häufige Gründe für Manifestlesefehler:

* Ungültiger JSON-Code. Verwenden Sie eine IDE wie [Visual Studio Code](https://code.visualstudio.com) oder [Visual Studio](https://www.visualstudio.com/vs/), die die JSON-Syntax automatisch überprüft.
* Codierungsprobleme. Verwenden Sie UTF-8 für die Datei *manifest.json* . Andere Codierungen, insbesondere mit der BOM, sind möglicherweise nicht lesbar.
* Falsch formatiertes .zip-Paket. Die Datei *manifest.json* muss sich auf der obersten Ebene der .zip Datei befinden. Beachten Sie, dass die Standardmäßige Mac-Dateikomprimierung die *Datei manifest.json* möglicherweise in einem Unterverzeichnis platziert, das in Microsoft Teams nicht ordnungsgemäß geladen wird.

### <a name="another-extension-with-same-id-exists"></a>Eine weitere Erweiterung mit derselben ID ist vorhanden.

Wenn Sie versuchen, ein aktualisiertes Paket mit derselben ID erneut hochzuladen, wählen Sie das Symbol **"Ersetzen"** am Ende der Tabellenzeile der Registerkarte statt der Schaltfläche **"Hochladen**" aus.

Wenn Sie ein aktualisiertes Paket nicht erneut hochladen, stellen Sie sicher, dass die ID eindeutig ist.
