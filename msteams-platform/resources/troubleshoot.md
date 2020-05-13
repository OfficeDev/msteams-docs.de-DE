---
title: Problembehandlung bei Ihrer APP
description: Behandeln von Problemen oder Fehlern beim Erstellen von Apps für Microsoft Teams
keywords: Microsoft Teams-apps-Entwicklung-Problembehandlung
ms.date: 07/09/2018
ms.openlocfilehash: 5f6c8b2d5496d1c49ea35b069c16f4ede507f5e1
ms.sourcegitcommit: b9e8839858ea8e9e33fe5e20e14bbe86c75fd510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "44210708"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Problembehandlung für Ihre Microsoft Teams-App

## <a name="troubleshooting-tabs"></a>Problem Behandlungs Registerkarten

### <a name="accessing-the-devtools"></a>Zugreifen auf das devtools

Sie können [devtools im Teams-Client](~/tabs/how-to/developer-tools.md) öffnen, um eine ähnliche Erfahrung wie das Drücken von F12 (unter Windows) oder Command-Option-I (auf MacOS) in einem Browser zu erreichen.

### <a name="blank-tab-screen"></a>Leerer Registerkarten Bildschirm

Wenn Ihre Inhalte nicht in der Registerkartenansicht angezeigt werden, kann dies wie folgt lauten:

* Ihre Inhalte können nicht in einer angezeigt werden `<iframe>` .
* die inhaltsdomäne befindet sich nicht in der [validDomains](~/resources/schema/manifest-schema.md#validdomains) -Liste im Manifest.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>Die Schaltfläche "Speichern" ist im Dialogfeld "Einstellungen" nicht aktiviert.

Stellen Sie sicher, dass Sie einen Anruf tätigen, `microsoftTeams.settings.setValidityState(true)` nachdem der Benutzereingaben vorgenommen oder alle erforderlichen Daten auf der Seite mit den Einstellungen ausgewählt hat, um die Schaltfläche Speichern zu aktivieren.

### <a name="after-selecting-the-save-button-the-tab-settings-cannot-be-saved"></a>Nachdem Sie die Schaltfläche Speichern ausgewählt haben, können die Registerkarteneinstellungen nicht gespeichert werden.

Wenn Sie beim Hinzufügen einer Registerkarte auf die Schaltfläche Speichern klicken, aber eine Fehlermeldung angezeigt wird, die besagt, dass die Einstellungen nicht gespeichert werden können, kann das Problem eine von zwei Problemen sein:

* Die Nachricht zum Speichern des Erfolgs wurde nie empfangen. Wenn ein Speicher Handler mit registriert wurde `microsoftTeams.settings.registerOnSaveHandler(handler)` , muss der Rückruf aufrufen `saveEvent.notifySuccess()` . Wenn der Rückruf dies nicht innerhalb von 30 Sekunden oder stattdessen Aufrufe aufruft `saveEvent.notifyFailure(reason)` , wird dieser Fehler angezeigt.

* Wenn kein Speicher Handler registriert wurde, `saveEvent.notifySuccess()` wird der Anruf automatisch sofort ausgeführt, sobald der Benutzer die Schaltfläche Speichern auswählt.

* Die bereitgestellten Einstellungen waren ungültig. Der andere Grund, warum die Einstellungen möglicherweise nicht gespeichert werden, ist, ob der Aufruf zur `microsoftTeams.setSettings(settings)` Bereitstellungeines ungültiges Settings-Objekts oder überhaupt nicht erfolgt ist. Im nächsten Abschnitt finden Sie häufige Probleme mit dem Settings-Objekt.

### <a name="common-problems-with-the-settings-object"></a>Häufige Probleme mit dem Settings-Objekt

* `settings.entityId`fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl`fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl`oder optional `settings.removeUrl` , oder `settings.websiteUrl` werden bereitgestellt, sind jedoch ungültig. Die URLs müssen HTTPS verwenden und müssen entweder dieselbe Domäne wie die Seite "Einstellungen" oder in der Liste des Manifests angegeben sein `validDomains` .

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Der Benutzer kann nicht authentifiziert werden, oder der Authentifizierungsanbieter wird auf der Registerkarte angezeigt.

Wenn Sie keine automatische Authentifizierung durchführen, müssen Sie dem Authentifizierungsprozess folgen, der vom [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client.md)bereitgestellt wird.

> [!NOTE]
>Wir fordern, dass der gesamte Authentifizierungs Fluss in Ihrer Domäne beginnt und endet, die im `validDomains` Objekt in ihrem Manifest aufgeführt werden muss.

Weitere Informationen zur Authentifizierung finden Sie unter [Authentifizieren eines Benutzers](~/concepts/authentication/authentication.md).

### <a name="static-tabs-not-showing-up"></a>Statische Registerkarten werden nicht angezeigt

Es gibt ein bekanntes Problem, bei dem beim Aktualisieren einer vorhandenen bot-App mit einer neuen oder aktualisierten statischen Registerkarte die Registerkarten Änderung beim Zugriff auf die APP aus einer persönlichen Chat Unterhaltung nicht angezeigt wird.  Um die Änderung anzuzeigen, sollten Sie einen neuen Benutzer oder eine Testinstanz testen oder über das App-Flyout auf den bot zugreifen.

## <a name="troubleshooting-bots"></a>Problembehandlung bei Bots

### <a name="cant-add-my-bot"></a>Mein bot kann nicht hinzugefügt werden

Apps müssen vom Office 365 mandantenadministrator aktiviert sein, damit Sie von Endbenutzern geladen werden können. Beachten Sie, dass in einigen Fällen dem Office 365-Mandanten möglicherweise mehrere SKUs zugeordnet sind und dass Bots in allen SKUs aktiviert werden müssen. Weitere Informationen finden Sie unter [Vorbereiten des Office 365 Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md) .

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Bot kann nicht als Mitglied eines Teams hinzugefügt werden

Bots müssen zuerst in ein Team hochgeladen werden, bevor Sie innerhalb eines beliebigen Kanals dieses Teams zugänglich sind. Weitere Informationen zu diesem Prozess finden Sie unter [Hochladen Ihrer APP in einem Team](~/concepts/deploy-and-publish/apps-upload.md) .

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>Mein bot erhält meine Nachricht nicht in einem Kanal

Bots in Kanälen empfangen Nachrichten nur dann, wenn Sie explizit @mentioned werden, selbst wenn Sie auf eine vorherige bot-Nachricht antworten. Die einzige Ausnahme, bei der der Bot-Name in einer Nachricht möglicherweise nicht angezeigt wird, ist, wenn der bot eine `imBack` Aktion als Ergebnis einer von ihm ursprünglich gesendeten Karte erhält.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>Mein bot versteht meine Befehle nicht, wenn Sie sich in einem Kanal befinden.

Da Bots in Kanälen nur Nachrichten empfangen, wenn Sie @mentioned sind, enthalten alle Nachrichten, die ihr bot in einem Kanal erhält, diese @mention in das Textfeld. Es ist eine bewährte Methode, den bot-Namen selbst aus allen eingehenden Textnachrichten zu entfernen, bevor Sie an die Analyselogik übergeben werden. Überprüfen Sie [Erwähnungen](../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions) für Tipps zur Behandlung dieses Falls.

## <a name="issues-with-packaging-and-uploading"></a>Probleme beim Verpacken und hochladen

### <a name="error-while-reading-manifestjson"></a>Fehler beim Lesen von Manifest. JSON

Die meisten manifestfehler bieten einen Hinweis darauf, was ein bestimmtes Feld fehlt oder ungültig ist. Wenn die JSON-Datei jedoch überhaupt nicht als JSON gelesen werden kann, wird diese generische Fehlermeldung verwendet.

Häufige Gründe für Fehler beim Lesen von Manifesten:

* Ungültige JSON. Verwenden Sie eine IDE wie [Visual Studio Code](https://code.visualstudio.com) oder [Visual Studio](https://www.visualstudio.com/vs/) , die die JSON-Syntax automatisch überprüft.
* Codierungsprobleme. Verwenden Sie UTF-8 für die Datei *Manifest. JSON* . Andere Codierungen, insbesondere mit der Stückliste, sind möglicherweise nicht lesbar.
* Ungültiges ZIP-Paket. Die Datei " *Manifest. JSON* " muss sich auf der obersten Ebene der ZIP-Datei befinden. Beachten Sie, dass die standardmäßige Mac-Dateikomprimierung das *Manifest. JSON* in einem Unterverzeichnis platzieren kann, das in Microsoft Teams nicht ordnungsgemäß laden wird.

### <a name="another-extension-with-same-id-exists"></a>Eine andere Erweiterung mit derselben ID ist vorhanden.

Wenn Sie versuchen, ein aktualisiertes Paket mit derselben ID erneut hochzuladen, wählen Sie das Symbol **ersetzen** am Ende der Tabellenzeile der Registerkarte anstelle der Schaltfläche **hochladen** aus.

Wenn Sie kein aktualisiertes Paket erneut hochladen, stellen Sie sicher, dass die ID eindeutig ist.
