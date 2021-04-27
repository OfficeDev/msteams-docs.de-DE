---
title: Problembehandlung für Ihre App
description: Behandeln von Problemen oder Fehlern beim Erstellen von Apps für Microsoft Teams
keywords: Problembehandlung bei der Entwicklung von Teams-Apps
localization_priority: Normal
ms.topic: troubleshooting
ms.date: 07/09/2018
ms.openlocfilehash: ce45a75869e8b6694cd84c10f8fac1f9bd55bad4
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020429"
---
# <a name="troubleshoot-your-microsoft-teams-app"></a>Problembehandlung für Ihre Microsoft Teams-App

## <a name="troubleshooting-tabs"></a>Problembehandlung bei Registerkarten

### <a name="accessing-the-devtools"></a>Zugreifen auf devTools

Sie können [DevTools](~/tabs/how-to/developer-tools.md) im Teams-Client öffnen, um eine ähnliche Erfahrung wie das Drücken von F12 (unter Windows) oder Command-Option-I (unter MacOS) in einem Browser zu erhalten.

### <a name="blank-tab-screen"></a>Leerer Registerkartenbildschirm

Wenn Ihre Inhalte nicht in der Registerkartenansicht angezeigt werden, kann es sich um:

* Ihre Inhalte können nicht in einer angezeigt `<iframe>` werden.
* die Inhaltsdomäne befindet sich nicht in der [Liste validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifest.

### <a name="the-save-button-isnt-enabled-on-the-settings-dialog"></a>Die Schaltfläche Speichern ist im Dialogfeld Einstellungen nicht aktiviert.

Rufen Sie unbedingt auf, sobald der Benutzer eingaben oder alle erforderlichen Daten auf ihrer Einstellungsseite ausgewählt `microsoftTeams.settings.setValidityState(true)` hat, um die Schaltfläche speichern zu aktivieren.

### <a name="after-selecting-the-save-button-the-tab-settings-cannot-be-saved"></a>Nachdem Sie die Schaltfläche Speichern ausgewählt haben, können die Registerkarteneinstellungen nicht gespeichert werden.

Wenn Sie beim Hinzufügen einer Registerkarte auf die Schaltflächen speichern klicken, aber eine Fehlermeldung angezeigt wird, die angibt, dass die Einstellungen nicht gespeichert werden können, kann das Problem eine von zwei Klassen von Problemen sein:

* Die Erfolgsnachricht zum Speichern wurde nie empfangen. Wenn ein Speicherhandler mit registriert `microsoftTeams.settings.registerOnSaveHandler(handler)` wurde, muss der Rückruf `saveEvent.notifySuccess()` aufrufen. Wenn der Rückruf dies nicht innerhalb von 30 Sekunden aufruft oder stattdessen aufruft, wird `saveEvent.notifyFailure(reason)` dieser Fehler angezeigt.

* Wenn kein Speicherhandler registriert wurde, wird der Aufruf automatisch sofort ausgeführt, nachdem der Benutzer `saveEvent.notifySuccess()` die Schaltfläche Speichern ausgewählt hat.

* Die bereitgestellten Einstellungen waren ungültig. Der andere Grund, warum die Einstellungen möglicherweise nicht gespeichert werden, ist, wenn der Aufruf ein ungültiges Einstellungsobjekt bereitgestellt hat oder der Aufruf überhaupt `microsoftTeams.setSettings(settings)` nicht erfolgt ist. Weitere Informationen finden Sie im nächsten Abschnitt Allgemeine Probleme mit dem Settings-Objekt.

### <a name="common-problems-with-the-settings-object"></a>Häufige Probleme mit dem Einstellungsobjekt

* `settings.entityId` fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl` fehlt. Dieses Feld ist obligatorisch.
* `settings.contentUrl` oder optional `settings.removeUrl` oder `settings.websiteUrl` werden bereitgestellt, aber nicht gültig. Die URLs müssen HTTPS verwenden und müssen entweder dieselbe Domäne wie die Einstellungsseite sein oder in der Liste des Manifests angegeben `validDomains` sein.

### <a name="cant-authenticate-the-user-or-display-your-auth-provider-in-your-tab"></a>Der Benutzer kann nicht authentifiziert werden oder der Authentifizierungsanbieter kann nicht auf Ihrer Registerkarte angezeigt werden.

Wenn Sie keine automatische Authentifizierung verwenden, müssen Sie den Authentifizierungsprozess befolgen, der vom [Microsoft Teams JavaScript-Client-SDK bereitgestellt wird.](/javascript/api/overview/msteams-client.md)

> [!NOTE]
>Wir benötigen den Authentifizierungsfluss, um ihre Domäne zu starten und zu beenden, die im Objekt `validDomains` in Ihrem Manifest aufgeführt werden muss.

Weitere Informationen zur Authentifizierung finden Sie unter [Authenticate a user](~/concepts/authentication/authentication.md).

### <a name="static-tabs-not-showing-up"></a>Statische Registerkarten werden nicht angezeigt

Es gibt ein bekanntes Problem, bei dem das Aktualisieren einer vorhandenen Bot-App mit einer neuen oder aktualisierten statischen Registerkarte beim Zugriff auf die App aus einer persönlichen Chat-Unterhaltung nicht angezeigt wird.  Um die Änderung zu sehen, sollten Sie einen neuen Benutzer oder eine neue Testinstanz testen oder über das Flyout Apps auf den Bot zugreifen.

## <a name="troubleshooting-bots"></a>Problembehandlung bei Bots

### <a name="cant-add-my-bot"></a>Mein Bot kann nicht hinzugefügt werden

Apps müssen vom Office 365-Mandantenadministrator aktiviert sein, damit sie von Endbenutzern geladen werden können. Beachten Sie, dass dem Office 365-Mandanten in einigen Fällen möglicherweise mehrere SKUs zugeordnet sind, und damit Bots in einem Beliebigen funktionieren, müssen sie in allen SKUs aktiviert sein. Weitere Informationen finden Sie unter [Prepare your Office 365 tenant.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

### <a name="cant-add-bot-as-a-member-of-a-team"></a>Bot kann nicht als Teammitglied hinzugefügt werden

Bots müssen zuerst in ein Team hochgeladen werden, bevor innerhalb eines beliebigen Kanals dieses Teams darauf zugegriffen werden kann. Weitere Informationen zu diesem Prozess finden Sie unter Hochladen Ihrer [App in](~/concepts/deploy-and-publish/apps-upload.md) einem Team.

### <a name="my-bot-doesnt-get-my-message-in-a-channel"></a>My bot doesn't get my message in a channel

Bots in Kanälen empfangen Nachrichten nur, wenn sie explizit @mentioned werden, auch wenn Sie auf eine vorherige Botnachricht antworten. Die einzige Ausnahme, in der der Botname in einer Nachricht möglicherweise nicht angezeigt wird, ist, wenn der Bot eine Aktion als Ergebnis einer cardAction empfängt, die `imBack` er ursprünglich gesendet hat.

### <a name="my-bot-doesnt-understand-my-commands-when-in-a-channel"></a>My bot doesn't understand my commands when in a channel

Da Bots in Kanälen nachrichten nur empfangen, wenn sie @mentioned, enthalten alle Nachrichten, die Ihr Bot in einem Kanal empfängt, @mention im Textfeld enthalten. Es ist eine bewährte Methode, den Botnamen selbst aus allen eingehenden Textnachrichten zu löschen, bevor Sie an Ihre Analyselogik übergeben. Lesen [Sie Erwähnungen](../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions) für Tipps, wie Sie diesen Fall behandeln.

## <a name="issues-with-packaging-and-uploading"></a>Probleme beim Packen und Hochladen

### <a name="error-while-reading-manifestjson"></a>Fehler beim Lesen manifest.jsein

Die meisten Manifestfehler geben einen Hinweis darauf, welches bestimmte Feld fehlt oder ungültig ist. Wenn die JSON-Datei jedoch überhaupt nicht als JSON gelesen werden kann, wird diese allgemeine Fehlermeldung verwendet.

Häufige Gründe für Fehler beim Lesen von Manifesten:

* Ungültiger JSON-Fehler. Verwenden Sie eine IDE, [Visual Studio Code](https://code.visualstudio.com) [oder](https://www.visualstudio.com/vs/) Visual Studio, die die #A0 automatisch überprüft.
* Codierungsprobleme. Verwenden Sie UTF-8 fürmanifest.js *on-Datei.* Andere Codierungen, insbesondere mit der Bom, sind möglicherweise nicht lesbar.
* Falsch formatiertes ZIP-Paket. Die *manifest.json-Datei* muss auf der obersten Ebene der ZIP-Datei sein. Beachten Sie, dass die Standardmäßige Mac-Dateikomprimierung dasmanifest.js *in* einem Unterverzeichnis platzieren kann, das in Microsoft Teams nicht ordnungsgemäß geladen wird.

### <a name="another-extension-with-same-id-exists"></a>Eine weitere Erweiterung mit derselben ID ist vorhanden.

Wenn Sie versuchen, ein aktualisiertes Paket mit derselben ID  erneut hochzuladen, wählen Sie das Symbol Ersetzen am Ende der Tabellenzeile der Registerkarte anstelle der Schaltfläche **Hochladen** aus.

Wenn Sie ein aktualisiertes Paket nicht erneut hochladen, stellen Sie sicher, dass die ID eindeutig ist.
