---
title: Erste Schritte mit App Studio für Microsoft Teams
description: In diesem Artikel erfahren Sie, wie Sie Ihre Apps mit App Studio für Microsoft Teams erstellen und verwalten und App Studio installieren.
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: ac036e6f62741a2d7de52ec2498d75c152929141
ms.sourcegitcommit: fb0942afb8be32d92df282dec03fbb3b13f8f303
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2022
ms.locfileid: "67264155"
---
# <a name="manage-your-apps-with-app-studio-for-microsoft-teams"></a>Verwalten Ihrer Apps mit App Studio für Microsoft Teams

> [!WARNING]
> **Testen Sie das Entwicklerportal**: App Studio hat sich weiterentwickelt. Konfigurieren, Verteilen und Verwalten Ihrer Teams-Apps mit dem neuen [Entwicklerportal](https://dev.teams.microsoft.com/). <br> App Studio ist ab dem 01. August 2022 veraltet.

Mit App Studio können Sie ganz einfach mit dem Erstellen oder Integrieren Ihrer eigenen Microsoft Teams-Apps beginnen, unabhängig davon, ob Sie benutzerdefinierte Apps für Ihr Unternehmen oder SaaS-Anwendungen für Teams auf der ganzen Welt entwickeln, indem Sie die Erstellung des Manifests und Pakets für Ihre App optimieren und nützliche Tools wie Karteneditor und eine React-Steuerelementbibliothek bereitstellen.

> [!IMPORTANT]
> App Studio ist derzeit in den folgenden Typen von Teams-Organisationen nicht verfügbar:
>
> * Government Community Cloud (GCC)
> * GCC High
> * DoD

## <a name="installing-app-studio"></a>Installieren von App Studio

App Studio ist eine Teams-App, die im Teams Store zu finden ist. Folgen Sie diesem Link, um [App Studio](https://aka.ms/InstallTeamsAppStudio) direkt herunterzuladen. Sie finden die App auch im App Store.

Suchen Sie im Store nach App Studio.

:::image type="content" source="../../assets/images/get-started/StoreTeamsAppStudio.png" alt-text="Store-Eintrag für App Studio":::

Wählen Sie die App Studio-Kachel aus, um die App-Installationsseite zu öffnen:

:::image type="content" source="../../assets/images/get-started/teamsAppStudioConfiguration.png" alt-text="Konfigurieren der App-Suite":::

Wählen Sie **Installieren**.

:::image type="content" source="../../assets/images/get-started/TeamsAppStudio.png" alt-text="App Studio":::

Sobald Sie sich in App Studio befinden, wählen Sie auf der Registerkarte " **Manifest-Editor** " aus, auf der Sie entweder eine vorhandene App importieren oder eine neue App erstellen können.

## <a name="app-studio-features"></a>App Studio-Features

In diesem Abschnitt werden Features wie Unterhaltung, Manifest-Editor, Details und Funktionen behandelt. Sie können Ihre Funktionen mithilfe von App-Anpassungen anpassen.

### <a name="conversation"></a>Unterhaltung

Hier können Sie sehen, wie die [in App Studio erstellten Karten](#card-editor) in Teams aussehen, indem Sie diese zum Test an sich selbst senden.

### <a name="manifest-editor"></a>Manifest-Editor

Wie bereits erwähnt, ist die manifest.json-Datei der wichtigste Teil eines Teams-App-Pakets. Diese Datei, die dem [Teams-App-Schema](~/resources/schema/manifest-schema.md) entsprechen muss, enthält Metadaten, mit denen Microsoft Teams Ihre App den Benutzern korrekt präsentieren kann.

Die Registerkarte "Manifest-Editor" in App Studio vereinfacht das Erstellen des Manifests, sodass Sie die App beschreiben, Ihre Symbole hochladen, App-Funktionen hinzufügen und eine .zip Datei erstellen können, die einfach in Teams hochgeladen werden kann, um sie zu testen oder für andere Benutzer zu verwenden. App Studio erzeugt keinen funktionalen Code für Ihre App oder hosten Ihre App. Ihre App muss bereits unter der im Manifest angegebenen URL gehostet und ausgeführt werden, damit der App-Upload-Vorgang zu einer funktionierenden App führt.

#### <a name="details"></a>Details

Im Detailabschnitt des Manifest-Editors wird die allgemeine Beschreibung der App definiert, die Sie erstellen. Dazu gehören beispielsweise der Name, die Beschreibung und das visuelle Branding der App. Sie können automatisch eine GUID für Ihre App generieren und URLs für Ihre Datenschutzerklärung und Nutzungsbedingungen bereitstellen.

#### <a name="capabilities"></a>Funktionen

Im Abschnitt "Funktionen" des Manifest-Editors werden die Funktionen der App definiert und Details zu den einzelnen Funktionen aufgelistet.

> [!NOTE]
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen können. Weitere Informationen finden Sie [unter Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).

##### <a name="tabs"></a>Registerkarten

* **Teamregisterkarten.** Eine Teamregisterkarte wird Teil eines Kanals und ermöglicht den schnellen Zugriff auf Teaminformationen und -ressourcen. Beispielsweise enthält die Registerkarte Planner einen einzelnen Plan für einen Kanal. Die Registerkarte Power BI wird einem bestimmten Bericht zugeordnet. Benutzer können einen Drilldown zum relevanten Kontext ausführen, sollten jedoch nicht außerhalb der Registerkarte navigieren können. Die Power BI-Registerkarte ermöglicht z. B. keine Navigation zu anderen Power BI-Berichten, aber sie aktiviert die Schaltfläche " *Zur Website wechseln* ", mit der der Bericht auf der Power BI-Hauptwebsite gestartet wird.

  Für Teamregisterkarten müssen Sie eine *Konfigurations-URL* angeben, um Optionen anzuzeigen und Informationen zu sammeln, damit Benutzer den Inhalt und die Erfahrung Ihrer Registerkarte anpassen können. Diese iframed-HTML-Seite wird angezeigt, wenn ein Benutzer die Registerkarte zum ersten Mal einem Kanal hinzufügt.

  Sie müssen auch alle zusätzlichen Domänen angeben, von denen die Registerkarte erwartet, dass sie geladen werden oder mit denen sie verlinkt wird.

* **Persönliche Registerkarten.** Sie können eine Reihe von Registerkarten definieren, die standardmäßig in der persönlichen App-Umgebung angezeigt werden (Erfahrung, die ein Benutzer mit Ihrer App außerhalb des Kontexts eines Teams oder Kanals hat). Geben Sie in diesem Abschnitt den Registerkartennamen an, ein eindeutiger Bezeichner, die URL, die auf die Benutzeroberfläche verweist und in Teams angezeigt werden soll, und optional die URL, die verwendet werden soll, wenn ein Benutzer die Registerkarte in einem Browser anzeigen möchte. Stellen Sie mit Teams-Registerkarten alle zusätzlichen Domänen bereit, von denen die Registerkarte erwartet, dass sie von der Registerkarte geladen wird, oder verknüpfen Sie sie.

##### <a name="bots"></a>Bots

In diesem Abschnitt können Sie Ihrer App einen [Unterhaltungs-Bot](~/bots/what-are-bots.md) hinzufügen. Wenn Sie bereits einen Bot bei Bot Framework registriert haben, können Sie diesen Bot hinzufügen, indem Sie auf " *Einrichten* " klicken und den Namen des Bots, die Bot Framework-ID, angeben und die Bereiche definieren, in denen der Bot arbeitet.

Wenn Sie noch keinen Bot beim Bot Framework registriert haben, wählen Sie **"Registrieren"** aus, um einen neuen bot zu erstellen. Wenn Sie mit der Registrierung Ihres Bots fertig sind, kehren Sie zu diesem Abschnitt des Manifest-Editors zurück, um dessen Namen und Bot Framework-ID einzugeben.

Nachdem Sie die Informationen Ihres Bots bereitgestellt haben, können Sie jetzt optional eine Liste von Befehlen definieren, die Ihr Bot Benutzern vorschlagen kann. Fügen Sie den Namen des Befehls, eine Beschreibung des Befehls, der seine Syntax und Argumente angibt, und die Bereiche hinzu, auf die dieser Befehl angewendet werden soll.

> [!NOTE]
> Wenn Sie Ihren Bot so definiert haben, dass er nur einen Bereich unterstützt, werden die für den nicht unterstützten Bereich angegebenen Befehle ignoriert. Sie können die vom Bot unterstützten Bereiche jederzeit bearbeiten.

##### <a name="connectors"></a>Connectors

In diesem Abschnitt können Sie Ihrer App einen Connector hinzufügen. Wenn Sie bereits einen Office 365-Connector registriert haben, wählen Sie **Einrichten** und geben Sie den Namen und die ID des Konnektors ein. Wenn Sie einen neuen Connector verwenden möchten, wählen Sie **"Registrieren"** aus, um zum Connector-Entwicklerdashboard in Ihrem Browser weitergeleitet zu werden.

##### <a name="message-extensions"></a>Nachrichtenerweiterungen

[Nachrichtenerweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) sind eine leistungsstarke Möglichkeit für Benutzer, mit Ihrer App in Teams zu interagieren. Benutzer können Informationen von Ihrem Dienst abfragen und diese Informationen in Form von Karten direkt im Kanal oder in der Chat-Unterhaltung veröffentlichen.

Nachrichtenerweiterungen werden von Bot Framework-Bots unterstützt, sodass sie einen konfigurierten Bot für den Betrieb benötigen. Wenn Sie den Namen und die Bot Framework-ID des Bots haben, den Sie mit der Nachrichtenerweiterung betreiben möchten, geben Sie ihn ein. Wählen Sie andernfalls **"Registrieren"** aus, um eine zu erstellen, und geben Sie anschließend die Informationen ein. Wählen Sie aus, ob die Konfiguration einer Nachrichtenerweiterung vom Benutzer aktualisiert werden kann.

Nachdem Sie den zugrunde liegenden Bot konfiguriert haben, definieren Sie die Befehle und Parameter, die die Nachrichtenerweiterung akzeptieren kann.

Jeder Befehl erfordert einen Titel und eine ID. Der Befehl kann optional eine Beschreibung für den Benutzer enthalten. Jeder Befehl kann bis zu fünf Parameter unterstützen, für die jeweils Folgendes erforderlich ist:

* Der Name des Parameters, wie er im Teams-Client angezeigt wird und in der Benutzeranforderung enthalten ist.
* Ein benutzerfreundlicher Titel.
* Eine optionale Beschreibung.

> [!NOTE]
> Informationen zum Erstellen einer Nachrichtenerweiterung mit app studio finden [Sie unter Erstellen einer Nachrichtenerweiterung mit app studio](~/resources/create-messaging-extension-using-appstudio.md).

#### <a name="test-and-distribute"></a>Testen und Verteilen

Nachdem Sie die Definition Ihrer Anwendung abgeschlossen haben, können Sie im Abschnitt "Testen und Verteilen" die Definition Ihrer App als ZIP-Datei exportieren, die dann freigegeben und zum Testen in den Teams-Client hochgeladen werden kann. Wenn Sie auf "Exportieren" klicken, wird die Zip-Datei als *appname.zip* in Ihr Standard-Download-Verzeichnis heruntergeladen.

##### <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

Auf Ihrer Projekthomepage können Sie Ihre App in ein Team hochladen, Ihre App für Benutzer in Ihrer Organisation an den benutzerdefinierten App Store Ihres Unternehmens senden oder Ihre App für alle Teambenutzer an App Source senden. Ihr IT-Administrator überprüft diese Übermittlungen. Sie können zur Seite *Veröffentlichen* zurückkehren, um Ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App einreichen oder derzeit aktive Übermittlungen abbrechen.

### <a name="card-editor"></a>Karten-Editor

Bei einer Karte handelt es sich um einen Container für kurze oder verknüpfte Informationen. Teams unterstützt Karten, die mehrere Eigenschaften und Anlagen aufweisen können. Karten sind eine wichtige Methode, mit der Bots und Konnektoren verwertbare Informationen an Benutzer weitergeben.

Um diesen Vorgang einfacher und weniger fehleranfällig zu machen, können Sie auf der Registerkarte "Karten-Editor" Herokarten oder Miniaturansichtenkarten mithilfe eines Formulars erstellen und die resultierende Karte (genau so, wie sie einem Benutzer angezeigt wird) über einen Bot überprüfen und testen. Er enthält auch den entsprechenden JSON-, C#- oder Node.js-Code für die Karte, die Sie in den Quellcode Ihrer App kopieren/einfügen können.

Wenn Sie bereits über eine Karte verfügen, die Sie in Teams überprüfen möchten, können Sie den JSON für diese Karte in die Registerkarte JSON unter *Karteninformationen hinzufügen* einfügen und an sich selbst senden, um zu sehen, wie er in einem Chat aussieht.

### <a name="react-control-library"></a>React-Steuerelementbibliothek

>[!Note]
> Diese React Steuerelementbibliothek wird in Zukunft nicht mehr unterstützt. Erwägen Sie die Verwendung der [Fluent-UI-React-Steuerelemente als alternative,](https://microsoft.github.io/fluent-ui-react/) zuvor stardust ui.

Das Erstellen einer App, die Teams‘ Bewährte Methoden befolgt, ist eine hervorragende Möglichkeit, Ihrer App ein Erscheinungsbild zu verleihen, das sich nahtlos in die Kundenerfahrung in Teams einfügt. Die von Ihnen verwendeten UI-Steuerelemente sind entscheidend, um dieses Ziel zu erreichen. Um die Erstellung einer konsistenten Benutzeroberfläche zu vereinfachen, stellt App Studio mehrere Kategorien von UI-Steuerelementen bereit, die den Entwurfsprinzipien von Teams entsprechen.

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

## <a name="app-studio-to-developer-portal"></a>App Studio zum Entwicklerportal

App Studio ist veraltet, Sie können das Entwicklerportal verwenden. Die folgende Tabelle enthält die detaillierten Informationen zu den im Entwicklerportal unterstützten Features:

| Features | App-Studio | Entwicklerportal |
| --- | --- | --- |
| App-Analysen* | ❌ | ✔️ |
| App-Funktionen– Bots | ✔️ | ✔️ |
| App-Funktionen–Connectors | ✔️ | ✔️ |
| App-Funktionen– Messaging-Erweiterung | ✔️ | ✔️ |
| App-Funktionen– Besprechungserweiterung | ❌ | ✔️ |
| App-Funktionen – Persönliche Apps | ✔️ | ✔️ |
| App-Funktionen – Registerkarten | ✔️ | ✔️ |
| App-Umgebungen | ❌ | ✔️ |
| App-Sprachen | ✔️ | ✔️ |
| App-Manifestvorschau und -download | ✔️ | ✔️ |
| App-Pläne und Preise | ❌ | ✔️ |
| App-Veröffentlichung | ✔️ | ✔️ |
| App-Berechtigungen | ❌ | ✔️ |
| Teilen von Apps mit Mitentwicklern | ❌ | ✔️ |
| App-Überprüfung | ✔️ | ✔️ |
| Erstellen einer neuen App | ✔️ | ✔️ |
| Übermitteln eines ZIP-Pakets | ✔️ | ✔️ |

\**App-Analysen werden in Kürze für GA verfügbar sein.*

## <a name="see-also"></a>Siehe auch

[Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md)
