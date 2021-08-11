---
title: Problembehandlung für Ihre App
description: Behandeln von Problemen oder Fehlern beim Erstellen von Apps für Microsoft Teams
keywords: Problembehandlung bei der Entwicklung von Teams-Apps
localization_priority: Normal
ms.topic: troubleshooting
ms.date: 07/09/2018
ms.openlocfilehash: 9688f2023707ca4eb3e7de6b52d3395a4cba47fd36dd29599dc4ead590368b95
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708037"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Problembehandlung für Ihre Microsoft Teams-App

## <a name="troubleshooting-tabs"></a>Problembehandlung bei Registerkarten

### <a name="accessing-the-devtools"></a>Zugreifen auf die DevTools

Sie können [DevTools im Teams-Client](~/tabs/how-to/developer-tools.md) öffnen, um eine ähnliche Erfahrung wie das Drücken von F12 (auf Windows) oder Command-Option-I (unter MacOS) in einem Browser zu erhalten.

### <a name="blank-tab-screen"></a>Leerer Registerkartenbildschirm

Wenn Ihre Inhalte in der Registerkartenansicht nicht angezeigt werden, kann dies folgendermaßen sein:

* Ihre Inhalte können nicht in einer angezeigt `<iframe>` werden.
* Die Inhaltsdomäne befindet sich nicht in der [Liste "validDomains"](~/resources/schema/manifest-schema.md#validdomains) im Manifest.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>Die Schaltfläche "Speichern" ist im Dialogfeld "Einstellungen" nicht aktiviert.

Rufen Sie auf, `microsoftTeams.settings.setValidityState(true)` sobald der Benutzer alle erforderlichen Daten auf der Einstellungsseite eingegeben oder ausgewählt hat, um die Schaltfläche "Speichern" zu aktivieren.

### <a name="after-selecting-the-save-button-the-tab-settings-cannot-be-saved"></a>Nachdem Sie die Schaltfläche "Speichern" ausgewählt haben, können die Registerkarteneinstellungen nicht gespeichert werden.

Wenn Sie beim Hinzufügen einer Registerkarte auf die Schaltflächen zum Speichern klicken, aber eine Fehlermeldung angezeigt wird, die angibt, dass die Einstellungen nicht gespeichert werden können, kann das Problem eine von zwei Problemklassen sein:

* Die Nachricht zum Speichern des Erfolgs wurde nie empfangen. Wenn ein Speicherhandler registriert `microsoftTeams.settings.registerOnSaveHandler(handler)` wurde, muss der Rückruf `saveEvent.notifySuccess()` aufrufen. Wenn der Rückruf dies nicht innerhalb von 30 Sekunden aufruft oder `saveEvent.notifyFailure(reason)` stattdessen aufruft, wird dieser Fehler angezeigt.

* Wenn kein Speicherhandler registriert wurde, erfolgt der `saveEvent.notifySuccess()` Aufruf automatisch, sobald der Benutzer die Schaltfläche zum Speichern auswählt.

* Die bereitgestellten Einstellungen waren ungültig. Der andere Grund, warum die Einstellungen möglicherweise nicht gespeichert werden, ist, wenn der Aufruf `microsoftTeams.setSettings(settings)` ein ungültiges Einstellungsobjekt bereitgestellt hat oder der Aufruf überhaupt nicht erfolgt ist. Weitere Informationen finden Sie im nächsten Abschnitt, häufig auftretende Probleme mit dem Einstellungsobjekt.

### <a name="common-problems-with-the-settings-object"></a>Häufige Probleme mit dem Einstellungsobjekt

* `settings.entityId` fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl` fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl` oder optional `settings.removeUrl` oder `settings.websiteUrl` bereitgestellt, aber nicht gültig. Die URLs müssen HTTPS verwenden und müssen entweder die gleiche Domäne wie die Einstellungsseite sein oder in der Manifestliste angegeben `validDomains` sein.

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Kann den Benutzer nicht authentifizieren oder Ihren Authentifizierungsanbieter auf ihrer Registerkarte anzeigen

Wenn Sie keine automatische Authentifizierung durchführen, müssen Sie den Authentifizierungsprozess befolgen, der vom [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client.md)bereitgestellt wird.

> [!NOTE]
>Es ist erforderlich, dass der gesamte Authentifizierungsfluss in Ihrer Domäne beginnt und endet, die im Objekt in Ihrem Manifest aufgeführt werden `validDomains` muss.

Weitere Informationen zur Authentifizierung finden Sie unter ["Authentifizieren eines Benutzers".](~/concepts/authentication/authentication.md)

### <a name="static-tabs-not-showing-up"></a>Statische Registerkarten werden nicht angezeigt

Es gibt ein bekanntes Problem, bei dem beim Aktualisieren einer vorhandenen Bot-App mit einer neuen oder aktualisierten statischen Registerkarte diese Registerkartenänderung beim Zugriff auf die App aus einer persönlichen Chatunterhaltung nicht angezeigt wird.  Um die Änderung anzuzeigen, sollten Sie mit einem neuen Benutzer oder einer testinstanz testen oder über das App-Flyout auf den Bot zugreifen.

## <a name="troubleshooting-bots"></a>Problembehandlung für Bots

### <a name="cant-add-my-bot"></a>Mein Bot kann nicht hinzugefügt werden

Apps müssen vom Office 365 Mandantenadministrator aktiviert sein, damit sie von Endbenutzern geladen werden können. Beachten Sie, dass dem Office 365 Mandanten in einigen Fällen möglicherweise mehrere SKUs zugeordnet sind. Damit Bots in einem beliebigen Element funktionieren, müssen sie in allen SKUs aktiviert sein. Weitere Informationen finden Sie unter [Vorbereiten Ihres Office 365 Mandanten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Bot kann nicht als Mitglied eines Teams hinzugefügt werden

Bots müssen zuerst in ein Team hochgeladen werden, bevor sie innerhalb eines Kanals dieses Teams zugänglich sind. Weitere Informationen zu diesem Vorgang finden Sie [unter "Hochladen Ihrer App in einem Team".](~/concepts/deploy-and-publish/apps-upload.md)

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>Mein Bot erhält meine Nachricht nicht in einem Kanal

Bots in Kanälen empfangen Nachrichten nur, wenn sie explizit @mentioned werden, auch wenn Sie auf eine vorherige Bot-Nachricht antworten. Die einzige Ausnahme, bei der der Botname in einer Nachricht möglicherweise nicht angezeigt wird, ist, wenn der Bot eine `imBack` Aktion als Ergebnis einer CardAction empfängt, die er ursprünglich gesendet hat.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>Mein Bot versteht meine Befehle nicht, wenn er sich in einem Kanal befindet

Da Bots in Kanälen Nachrichten nur empfangen, wenn sie @mentioned sind, enthalten alle Nachrichten, die Ihr Bot in einem Kanal empfängt, die @mention im Textfeld. Es ist eine bewährte Methode, den Botnamen selbst aus allen eingehenden Textnachrichten zu entfernen, bevor Sie an Ihre Analyselogik übergeben werden. In [den Erwähnungen](../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions) finden Sie Tipps zum Umgang mit diesem Fall.

## <a name="issues-with-packaging-and-uploading"></a>Probleme beim Packen und Hochladen

### <a name="error-while-reading-manifestjson"></a>Fehler beim Lesen von manifest.json

Die meisten Manifestfehler geben einen Hinweis darauf, welches Feld fehlt oder ungültig ist. Wenn die JSON-Datei jedoch überhaupt nicht als JSON gelesen werden kann, wird diese generische Fehlermeldung verwendet.

Häufige Ursachen für Fehler beim Lesen von Manifesten:

* Ungültiger JSON-Code. Verwenden Sie eine IDE wie [Visual Studio Code](https://code.visualstudio.com) oder [Visual Studio,](https://www.visualstudio.com/vs/) die die JSON-Syntax automatisch überprüft.
* Codierungsprobleme. Verwenden Sie UTF-8 für die *manifest.json-Datei.* Andere Codierungen, insbesondere mit der BOM, sind möglicherweise nicht lesbar.
* Falsch formatiertes .zip-Paket. Die *manifest.js* on-Datei muss sich auf der obersten Ebene der .zip-Datei befinden. Beachten Sie, dass die standardmäßige Mac-Dateikomprimierung die *manifest.js* möglicherweise in einem Unterverzeichnis platziert, das in Microsoft Teams nicht ordnungsgemäß geladen wird.

### <a name="another-extension-with-same-id-exists"></a>Eine weitere Erweiterung mit derselben ID ist vorhanden.

Wenn Sie versuchen, ein aktualisiertes Paket mit derselben ID erneut hochzuladen, wählen Sie das Symbol **"Ersetzen"** am Ende der Tabellenzeile der Registerkarte anstelle der **Schaltfläche Hochladen** aus.

Wenn Sie kein aktualisiertes Paket erneut hochladen, stellen Sie sicher, dass die ID eindeutig ist.
