---
title: Erste Schritte mit App Studio für Microsoft Teams
description: Erste Schritte zum Erstellen von großartigen Apps in Microsoft Teams mit App Studio
keywords: Erste Schritte mit App Studio-Teams
ms.topic: overview
ms.openlocfilehash: d275e78909fe35a6032bf67cb7454396f3dbd7af
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696304"
---
# <a name="quickly-develop-apps-with-app-studio-for-microsoft-teams"></a>Entwickeln Sie schnell Apps mit App Studio für Microsoft Teams

Mit App Studio können Sie ganz einfach mit dem Erstellen oder Integrieren Ihrer eigenen Microsoft Teams-Apps beginnen, unabhängig davon, ob Sie benutzerdefinierte Apps für Ihr Unternehmen oder SaaS-Anwendungen für Teams auf der ganzen Welt entwickeln, indem Sie die Erstellung des Manifests und Pakets für Ihre App optimieren und nützliche Tools wie Karteneditor und eine React-Steuerelementbibliothek bereitstellen.

## <a name="installing-app-studio"></a>Installieren von App Studio

App Studio ist eine Teams-App und verfügbar im Teams Store. Folgen Sie diesem Link zum direkten Download: [App Studio](https://aka.ms/InstallTeamsAppStudio) (Sie finden die App auch im App Store).

Suchen Sie im Store nach App Studio.

![Store-Eintrag für App Studio](~/assets/images/get-started/storeteamsappstudio.png)

Wählen Sie die App Studio-Kachel aus, um die App-Installationsseite zu öffnen:

![Konfigurieren der App-Suite](~/assets/images/get-started/teamsappstudioconfiguration.png)

Wählen Sie *Installieren*.

![App Studio](~/assets/images/get-started/teamsappstudio.png)

Klicken Sie in App Studio auf die Registerkarte *Manifest-Editor*, auf der Sie entweder eine vorhandene App importieren oder eine neue App erstellen können.

## <a name="app-studio-features"></a>App Studio-Features

In diesem Abschnitt werden Features wie Unterhaltung, Manifesteditor, Details und Funktionen behandelt. Sie können Ihre Funktionen mithilfe von App-Anpassungen anpassen.

### <a name="conversation"></a>Unterhaltung

Hier können Sie sehen, wie die [in App Studio erstellten Karten](#card-editor) in Teams aussehen, indem Sie diese zum Test an sich selbst senden.

### <a name="manifest-editor"></a>Manifest-Editor

Wie bereits erwähnt, ist der wichtigste Teil eines Microsoft Teams-App-Pakets dessen Datei "manifest.json". Diese Datei, die dem [Team-App-Schema](~/resources/schema/manifest-schema.md) entsprechen muss, enthält Metadaten, mit denen Teams Ihre App den Benutzern korrekt präsentieren können.

Die Registerkarte Manifest-Editor in App Studio vereinfacht das Erstellen des Manifests. Auf diese Weise können Sie die App beschreiben, Ihre Symbole hochladen, App-Funktionen hinzufügen und eine ZIP-Datei erstellen, die zum Testen einfach in Teams hochgeladen oder an andere verteilt werden kann. Beachten Sie, dass App Studio keinen Funktionscode für Ihre App erstellt oder Ihre App hostet. Ihre App muss bereits unter der im Manifest angegebenen URL gehostet und ausgeführt werden, damit der App-Upload-Vorgang zu einer funktionierenden App führt.

#### <a name="details"></a>Details

Der Detailabschnitt des Manifest-Editors definiert die allgemeine Beschreibung der App, die Sie erstellen. Dazu gehören beispielsweise der Name, die Beschreibung und das visuelle Branding der App. Sie können automatisch eine GUID für Ihre App generieren und URLs für Ihre Datenschutzerklärung und Nutzungsbedingungen bereitstellen.

#### <a name="capabilities"></a>Funktionen

Im Abschnitt "Funktionen" des Manifest-Editors werden die Funktionen der App definiert und Details zu den einzelnen Funktionen aufgelistet.

> [!NOTE]
> Die App-Anpassungsfunktion ist derzeit nur in der Entwicklervorschau verfügbar.
> 
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).


##### <a name="tabs"></a>Registerkarten

* **Teamregisterkarten.** Eine Teamregisterkarte wird Teil eines Kanals und ermöglicht den schnellen Zugriff auf Teaminformationen und -ressourcen. Beispielsweise enthält die Registerkarte Planner einen einzelnen Plan für einen Kanal. Die Registerkarte Power BI wird einem bestimmten Bericht zugeordnet. Benutzer können einen Drilldown zum relevanten Kontext durchführen, sollten jedoch nicht in der Lage sein, außerhalb der Registerkarte zu navigieren. Auf der Registerkarte Power BI wird beispielsweise nicht die Navigation zu anderen Power BI-Berichten aktiviert, sondern die Schaltfläche *Zur Website wechseln*, mit welcher der Bericht auf der Power BI-Hauptwebsite gestartet wird.

  Für Teamregisterkarten müssen Sie eine *Konfigurations-URL* angeben, um Optionen anzuzeigen und Informationen zu sammeln, damit Benutzer den Inhalt und die Erfahrung Ihrer Registerkarte anpassen können. Diese iframed-HTML-Seite wird angezeigt, wenn ein Benutzer die Registerkarte zum ersten Mal einem Kanal hinzufügt.

  Sie müssen auch alle zusätzlichen Domänen angeben, von denen die Registerkarte erwartet, dass sie geladen werden oder mit denen sie verlinkt wird.

* **Persönliche Registerkarten.** In diesem Abschnitt können Sie eine Reihe von Registerkarten definieren, die standardmäßig in der persönlichen App-Erfahrung angezeigt werden (d. h. Die Erfahrung, die ein Benutzer mit Ihrer App außerhalb des Kontexts eines Teams oder Kanals hat). Geben Sie in diesem Abschnitt den Registerkartennamen an, ein eindeutiger Bezeichner, die URL, die auf die Benutzeroberfläche verweist und in Teams angezeigt werden soll, und optional die URL, die verwendet werden soll, wenn ein Benutzer die Registerkarte in einem Browser anzeigen möchte. Geben Sie wie bei Teams-Registerkarten üblich alle zusätzlichen Domänen an, von denen die Registerkarte voraussichtlich geladen oder verlinkt wird.

##### <a name="bots"></a>Bots

In diesem Abschnitt können Sie Ihrer App einen [Unterhaltungs-Bot](~/bots/what-are-bots.md) hinzufügen. Wenn Sie bereits einen Bot bei Bot Framework registriert haben, können Sie diesen Bot hinzufügen, indem Sie auf *Einrichten* klicken, den Bot-Namen und die Bot Framework-ID angeben und die Bereiche definieren, in denen der Bot arbeiten soll.

Wenn Sie noch keinen Bot beim Bot Framework registriert haben, klicken Sie auf *Registrieren*, um einen neuen Bot zu erstellen. Wenn Sie mit der Registrierung Ihres Bots fertig sind, kehren Sie zu diesem Abschnitt des Manifest-Editors zurück, um dessen Namen und Bot Framework-ID einzugeben.

Nachdem Sie die Informationen Ihres Bots bereitgestellt haben, können Sie nun optional eine Liste von Befehlen definieren, die Ihr Bot Benutzern vorschlagen kann. Fügen Sie den Befehlsnamen, eine Befehlsbeschreibung mit Angaben zu dessen Syntax und Argumenten sowie die Bereiche hinzu, für die dieser Befehl gelten soll.

Beachten Sie, dass Befehle, die für den nicht unterstützten Bereich angegeben wurden, ignoriert werden, wenn Sie Ihren Bot so definiert haben, dass er nur einen Bereich unterstützt. Sie können die vom Bot unterstützten Bereiche jederzeit bearbeiten.

##### <a name="connectors"></a>Connectors

In diesem Abschnitt können Sie Ihrer App einen Connector hinzufügen. Wenn Sie bereits einen Office 365-Connector registriert haben, wählen Sie *Einrichten* und geben Sie den Namen und die ID des Konnektors ein. Wenn Sie einen neuen Konnektor möchten, klicken Sie auf *Registrieren*, um zum Connector Developer Dashboard in Ihrem Browser zu gelangen.

> [!NOTE]
> Mithilfe der App-Anpassung können Administratoren das Aussehen und Die-Gefühl der Apps ändern, die über Bots, Messagingerweiterungen, Registerkarten und Connectors geladen werden. Wenn der Teams-Administrator beispielsweise den Namen einer App von *Contoso* in *Contoso Agent* anpasst, wird die App benutzern mit dem neuen Namen *Contoso Agent* angezeigt. Beim Hinzufügen eines Connectors zu einem Chat wird in der Liste der Connectors jedoch weiterhin der Name der App als *Contoso angezeigt.*


##### <a name="messaging-extensions"></a>Messaging-Erweiterungen

[Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) bieten Benutzern eine leistungsstarke Möglichkeit, mit Ihrer App in Microsoft Teams zu agieren. Benutzer können Informationen von Ihrem Dienst abfragen und diese Informationen in Form von Karten direkt im Kanal oder in der Chat-Unterhaltung veröffentlichen.

Messaging-Erweiterungen werden von Bot Framework-Bots unterstützt, sodass für den Betrieb ein konfigurierter Bot erforderlich ist. Wenn über Sie den Namen und die Bot Framework-ID des Bots verfügen, für den Sie die Messaging-Erweiterung aktivieren möchten, geben Sie ihn ein. Andernfalls klicken Sie auf *Registrieren*, um den Namen zu erstellen, und geben Sie anschließend die Informationen ein. Wählen Sie aus, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann.

Nachdem Sie den zugrunde liegenden Bot konfiguriert haben, definieren Sie die Befehle und Parameter, welche die Messaging-Erweiterung akzeptieren soll.

Jeder Befehl erfordert einen Titel und eine ID. Der Befehl kann optional eine Beschreibung für den Benutzer enthalten. Jeder Befehl kann bis zu fünf Parameter unterstützen, für die jeweils Folgendes erforderlich ist:

* Der Name des Parameters, wie er im Teams-Client angezeigt wird und in der Benutzeranforderung enthalten ist
* Ein benutzerfreundlicher Titel
* Eine optionale Beschreibung.

> [!NOTE]
> Informationen zum Erstellen einer Messagingerweiterung mithilfe von App Studio finden Sie unter [Create messaging extension using app studio](~/resources/create-messaging-extension-using-appstudio.md).

#### <a name="test-and-distribute"></a>Testen und Verteilen

Nachdem Sie Ihre App definiert haben, können Sie im Abschnitt "Testen und Verteilen" die Definition Ihrer Anwendung als Zip-Datei exportieren, die dann freigegeben und zum Testen in den Teams-Client hochgeladen werden kann. Wenn Sie auf "Exportieren" klicken, wird die Zip-Datei als *appname.zip* in Ihr Standard-Download-Verzeichnis heruntergeladen.

##### <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams
Auf Ihrer Projekthomepage können Sie Ihre App in ein Team hochladen, Ihre App für Benutzer in Ihrer Organisation an den benutzerdefinierten App Store Ihres Unternehmens senden oder Ihre App für alle Teambenutzer an App Source senden. Ihr IT-Administrator wird diese Übermittlungen überprüfen. Sie können zur Seite *Veröffentlichen* zurückkehren, um Ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App einreichen oder derzeit aktive Übermittlungen abbrechen.

### <a name="card-editor"></a>Karten-Editor

Bei einer Karte handelt es sich um einen Container für kurze oder verknüpfte Informationen. Microsoft Teams unterstützt Karten, die mehrere Eigenschaften und Anhänge haben können. Karten sind eine wichtige Methode, mit der Bots und Konnektoren verwertbare Informationen an Benutzer weitergeben. 

Um diesen Vorgang zu vereinfachen und weniger fehleranfällig zu machen, können Sie auf der Registerkarte Karten-Editor mithilfe eines Formulars Hero-Karten oder Miniaturkarten erstellen und die letztendliche Karte (genau so, wie ein Benutzer sie sehen würde) mit einem Bot überprüfen und testen. Er enthält auch den entsprechenden JSON-, C#- oder Node.js-Code für die Karte, die Sie in den Quellcode Ihrer App kopieren/einfügen können.

Wenn Sie bereits über eine Karte verfügen, die Sie in Teams überprüfen möchten, können Sie den JSON für diese Karte in die Registerkarte JSON unter *Karteninformationen hinzufügen* einfügen und an sich selbst senden, um zu sehen, wie er in einem Chat aussieht.

### <a name="react-control-library"></a>React-Steuerelementbibliothek

>[!Note]
> Diese React-Steuerelementbibliothek wird in Zukunft nicht mehr angezeigt. Erwägen Sie die Verwendung der [Fluent-UI-Reaktionssteuerung als Alternative](https://microsoft.github.io/fluent-ui-react/) (früher Stardust UI).

Das Erstellen einer App, die Teams‘ Bewährte Methoden befolgt, ist eine hervorragende Möglichkeit, Ihrer App ein Erscheinungsbild zu verleihen, das sich nahtlos in die Kundenerfahrung in Teams einfügt. Die von Ihnen verwendeten UI-Steuerelemente sind entscheidend, um dieses Ziel zu erreichen. Um das Erstellen einer konsistenten Benutzeroberfläche zu vereinfachen, bietet App Studio verschiedene Kategorien von Steuerelementen für die Benutzeroberfläche, die den Entwurfsprinzipien von Teams entsprechen.

Beispiele für die Steuerelemente und die entsprechenden React-Komponenten werden bereitgestellt und können beim Erstellen Ihrer App verwendet werden.

#### <a name="controls"></a>Steuerelemente

Steuerelemente enthalten:

* Schaltflächen
* Dropdowns
* Kontrollkästchen
* Optionsschaltflächen
* Umschalttasten
* Textbereiche
* Links
* Registerkarten
* Tabellen
* Symbole
