---
title: Hochladen Ihrer benutzerdefinierten app in Microsoft Teams
description: Beschreibt, wie Sie Ihre APP in Microsoft Teams hochladen
keywords: Upload von Teams-apps
ms.openlocfilehash: 6fbcd7a81c113d25a26ee6db15865929a53def0d
ms.sourcegitcommit: 560bf433129c16888135879e2703dbdeb38ec99f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "48397708"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a>Hochladen eines App-Pakets in Microsoft Teams

Um Ihre APP-Erfahrung in Microsoft Teams zu testen, müssen Sie Ihre APP in Teams hochladen. Durch Hochladen wird die APP dem ausgewählten Team hinzugefügt, und Sie und Ihre Teammitglieder können wie Endbenutzer mit ihr interagieren.

> [!NOTE]
> Beim Hochladen eines aktualisierten Pakets für eine vorhandene App mit einem bot werden im Fenster Unterhaltungen möglicherweise keine Registerkarten Änderungen angezeigt. Es ist besser, über das Apps-Fly-Out darauf zuzugreifen oder auf eine saubere Testumgebung zu testen.

## <a name="create-your-upload-package"></a>Erstellen des Upload-Pakets

Für die Entwicklung als auch für AppSource (ehemals Office Store)-Übermittlung müssen Sie ein uploadable-Paket erstellen, das die Informationen zum Beschreiben Ihrer Benutzeroberfläche enthält. Das Paket, eine ZIP-Datei, enthält das Anwendungsmanifest und die Symbole, die Ihre Benutzeroberfläche eindeutig definieren.

Informationen zum Erstellen eines Upload-Pakets finden Sie unter [Erstellen des Pakets für Ihre Microsoft Teams-App](../build-and-test/apps-package.md).

Wenn Ihr Paket erstellt wurde, können Sie es jetzt in ein Team hochladen. Sobald hochgeladen, steht sie für alle Benutzer im ausgewählten Team und nur für die Benutzer dieses Teams zur Verfügung.

## <a name="load-your-package-into-teams"></a>Laden Ihres Pakets in Microsoft Teams

Sie können Ihr Paket testen, indem Sie es in Teams hochladen.

> [!NOTE]
> Damit das Hochladen funktioniert, muss Ihr mandantenadministrator zunächst das [Hochladen von Apps aktivieren](/microsoftteams/admin-settings).

Es gibt zwei Möglichkeiten, Ihre APP in Microsoft Teams hochzuladen:

* Verwenden des Stores
* Verwenden der Registerkarte "Apps"

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a>Laden Sie Ihr Paket mit dem Store in ein Team oder eine Unterhaltung hoch.

1. Wählen Sie in der unteren linken Ecke von Microsoft Teams das Symbol Store aus. Wählen Sie auf der Seite Store die Option "benutzerdefinierte App hochladen" aus.

  ![Team anzeigen](../../assets/images/store-upload-a-custom-app2.png)

2. Navigieren Sie im Dialogfeld *Öffnen* zu dem Paket, das Sie hochladen möchten, und wählen Sie *Öffnen*aus.

   ![Menü hinzufügen](../../assets/images/NewappAddmenudropdown.png)

Das hochgeladene Paket sollte jetzt für die Verwendung in der im Zustimmungsdialogfeld angegebenen Gruppe oder Unterhaltung zur Verfügung stehen. Wenn Ihre APP nicht angezeigt wird, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die APP-, bot-und Messaging-Erweiterungen. Wenn die APP nicht für Unterhaltungen ausgelegt ist, wird diese Option nicht angezeigt.

>[!NOTE]
> Apps in Unterhaltungen befinden sich derzeit in der [Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md), und die Option wird nicht angezeigt, wenn Teams nicht in diesem Modus ausgeführt werden.

![Beispiel für bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a>Hochladen des Pakets mithilfe der Registerkarte "Apps" in ein Team

1. Wählen Sie im Ziel Team *Weitere Optionen* (**&#8943;**) aus, und wählen Sie *Team verwalten*aus.

   > [!NOTE]
   > Sie müssen der Teambesitzer sein, oder der Besitzer muss zulassen, dass Benutzer die entsprechenden App-Typen hinzufügen, damit diese Funktion angezeigt wird.

2. Wählen Sie die Registerkarte Apps aus, und wählen Sie dann *eine benutzerdefinierte App* in der rechten oberen Ecke Hochladen aus.

   ![Einstiegspfad hochladen](../../assets/images/UploadACustomApp.png)

3. Navigieren Sie zu Ihrem ZIP-Paket auf Ihrem Computer, und wählen Sie es aus.

4. Nach einer kurzen Pause wird Ihre hochgeladene app in der Liste angezeigt.

   ![Beispiel für bot in der Liste der hochgeladenen Bots](../../assets/images/botinlist.jpg)

Wenn Ihre APP nicht lädt, ist der häufigste Grund ein Fehler im Manifest, insbesondere IDs für die APP-, bot-und Messaging-Erweiterungen.

## <a name="accessing-your-uploaded-configurable-tab"></a>Zugreifen auf die konfigurierbare Registerkarte "hochgeladen"

Wenn die APP Registerkarten enthält, können Benutzer Sie an jede Unterhaltung oder einen Team Kanal mit dem standardmäßigen Tab Gallery Flow anheften:

1. Wechseln Sie zu einem Kanal im Team. Klicken Sie *+* auf der rechten Seite der vorhandenen Registerkarten auf (*Registerkarte hinzufügen*).

2. Wählen Sie in der angezeigten Galerie die Registerkarte aus.

3. Akzeptieren Sie die Zustimmungsaufforderung.

4. Konfigurieren Sie die Registerkarte über die [Konfigurationsseite](../../tabs/how-to/create-tab-pages/configuration-page.md) , und wählen Sie *Speichern*aus.

  ![Das Dialogfeld "Register hinzufügen" mit einem Katalog verfügbarer Registerkarten](../../assets/images/tab_gallery.png)

## <a name="accessing-your-uploaded-bot"></a>Zugriff auf Ihren hochgeladenen bot

Wenn Sie einem Team einen bot hinzufügen, sollte er je nach der Bereichsdefinition des bot von jedem Benutzer in diesem Team innerhalb und außerhalb der Team Kanäle verwendet werden. Ihnen und anderen Teammitgliedern wird ein Beitrag im allgemeinen Kanal angezeigt, der angibt, dass der bot dem Team hinzugefügt wurde.

Für einen Teams-fähigen bot können Sie zunächst Ihren bot aufrufen, indem Sie @mentioning den Namen des bot, der AutoVervollständigen sollte.

Um direkte Chats mit Ihrem bot zu testen, können Sie entweder über das App-Home darauf zugreifen, es in einem Kanal @Mention oder im **neuen Chat** Fenster danach suchen.

Wenn Sie Ihren bot zu einer Unterhaltung hinzufügen, um direkte Chats mit Ihrem bot zu testen, können Sie ihn in einer Unterhaltung @Mention oder im **neuen Chat** Fenster suchen.

## <a name="accessing-your-uploaded-connector"></a>Zugreifen auf Ihren hochgeladenen Connector

Wenn die APP im Team oder in der Unterhaltung geladen ist, können Benutzer einen Connector mit dem standardmäßigen Konnektoren-Katalog Ablauf einrichten:

1. Wechseln Sie zu einem Kanal im Team. Wählen Sie *Weitere Optionen* (*&#8943;*) aus, und wählen Sie *Connectors*aus.

2. Wählen Sie den Verbinder im Abschnitt **quer geladene** unten aus.

3. Konfigurieren Sie den Connector über die [Konfigurationsseite](../../webhooks-and-connectors/how-to/connectors-creating.md) , und wählen Sie *Speichern*aus.

  ![Das DialogfeldRegister hinzufügen mit einem Katalog verfügbarer Registerkarten.](../../assets/images/connector_gallery.png)

## <a name="accessing-your-uploaded-messaging-extension"></a>Zugriff auf Ihre hochgeladene Messaging Erweiterung

Eine hochgeladene App mit einer Messaging Erweiterung wird automatisch im Menü *Weitere Optionen* (*&#8943;*) im Feld Verfassen angezeigt.

![Messaging-Erweiterungen](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="removing-or-updating-your-app"></a>Entfernen oder Aktualisieren Ihrer APP

Wenn Sie Ihre APP entfernen möchten, wählen Sie in der Liste Teams-Bots anzeigen neben dem APP-Namen das Papierkorbsymbol aus.

Wenn Sie Manifestinformationen ändern, müssen Sie zuerst die APP entfernen und dann das aktualisierte Paket hinzufügen (pro [Laden Ihres Pakets in ein Team](#load-your-package-into-teams)). Beachten Sie, dass für Codeänderungen in Ihrem Dienst im Allgemeinen keine erneute Hochladung des Manifests erforderlich ist, es sei denn, für diese Änderungen sind Manifeste Aktualisierungen erforderlich (beispielsweise Änderungen an der URL oder an der Microsoft App-ID für den bot).

> [!NOTE]
> Es gibt keine Möglichkeit, einen bot vollständig aus dem persönlichen Kontext zu entfernen. Wenn der bot entfernt und erneut hinzugefügt wird, wird die zusätzliche Kommunikation mit dem bot an die vorherige Unterhaltung angefügt.

## <a name="troubleshooting-notes"></a>Problembehandlung bei Notizen

* Wenn das Manifest nicht lädt, überprüfen Sie bitte, ob Sie alle Anweisungen unter [Erstellen des Pakets](../../concepts/build-and-test/apps-package.md) befolgt und Ihr Manifest anhand des [Schemas](../../resources/schema/manifest-schema.md)überprüft haben.

