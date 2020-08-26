---
title: Erste Schritte mit App Studio für Microsoft Teams
description: Erste Schritte beim Erstellen von tollen apps in Microsoft Teams mit App Studio
keywords: Erste Schritte-App Studio Teams
ms.date: 03/20/2019
ms.openlocfilehash: b8bae38ae2a3044d87389b4bd5ee3d5a7d1e029d
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874877"
---
# <a name="quickly-develop-apps-with-app-studio-for-microsoft-teams"></a>Schnelles Entwickeln von apps mit App Studio für Microsoft Teams

App Studio erleichtert das Erstellen oder integrieren eigener Microsoft Teams-apps, unabhängig davon, ob Sie benutzerdefinierte Apps für Ihre Enterprise-oder SaaS-Anwendungen für Teams auf der ganzen Welt entwickeln, indem Sie die Erstellung des Manifests und Pakets für Ihre APP optimieren und nützliche Tools wie den Kartenherausgeber und eine Reaktions Steuerungs Bibliothek bereitstellen.

## <a name="installing-app-studio"></a>Installieren von App Studio

App Studio ist eine Teams-APP, die im Microsoft Teams Store zu finden ist. Befolgter Link zum direkten Download: [App Studio](https://aka.ms/InstallTeamsAppStudio) (Sie können die APP auch im App Store finden).

Suchen Sie im Store nach App Studio.

![Store-Eintrag für App Studio](~/assets/images/get-started/storeteamsappstudio.png)

Wählen Sie die Kachel App Studio aus, um die APP-Installationsseite zu öffnen:

![Konfigurieren von App Studio](~/assets/images/get-started/teamsappstudioconfiguration.png)

Wählen Sie *install*aus.

![App Studio](~/assets/images/get-started/teamsappstudio.png)

Wenn Sie sich in App Studio befinden, klicken Sie auf die Registerkarte *Manifest-Editor* , auf der Sie entweder eine vorhandene App importieren oder eine neue APP erstellen können.

## <a name="app-studio-features"></a>App Studio-Features

### <a name="conversation"></a>Unterhaltung

Hier können Sie sehen, welche [Karten Sie in App Studio](#card-editor) wie in Microsoft Teams erstellen, wenn Sie Sie testen, indem Sie Sie an sich selbst senden.

### <a name="manifest-editor"></a>Manifest-Editor

Wie bereits erwähnt, ist der wichtigste Teil eines Microsoft Teams-App-Pakets die Datei manifest.js. Diese Datei, die dem Microsoft Teams- [App-Schema](~/resources/schema/manifest-schema.md)entsprechen muss, enthält Metadaten, mit denen Microsoft Teams Ihre APP den Benutzern korrekt präsentieren kann.

Die Registerkarte Manifest-Editor in App Studio vereinfacht die Erstellung des Manifests, sodass Sie die APP beschreiben, ihre Symbole hochladen, App-Funktionen hinzufügen und eine ZIP-Datei erstellen können, die problemlos in Teams zum Testen hochgeladen oder für andere Benutzer verteilt werden kann. Beachten Sie, dass APP Studio keinen Funktionscode für Ihre APP erstellt oder Ihre APP hostet. Ihre APP muss bereits gehostet sein und unter der im Manifest für den App-Upload-Prozess aufgeführten URL ausgeführt werden, damit eine funktionierende App entsteht.

#### <a name="details"></a>Details

Der Abschnitt "Details" des Manifest-Editors definiert die allgemeine Beschreibung der APP, die Sie erstellen. Dies umfasst beispielsweise den Namen, die Beschreibung und das visuelle Branding von apps. Sie können automatisch eine GUID für Ihre APP generieren und URLs für Ihre Datenschutzerklärung und Nutzungsbedingungen bereitstellen.

#### <a name="capabilities"></a>Funktionen

Im Bereich "capabilities" des Manifest-Editors werden die Funktionen der APP definiert, und es werden Details zu diesen Funktionen aufgelistet.

##### <a name="tabs"></a>Registerkarten

* **Team Registerkarten.** Eine Team-Registerkarte wird Teil eines Kanals und bietet schnellen Zugriff auf Team Informationen und-Ressourcen. Beispielsweise enthält die Registerkarte Planer für einen Kanal einen einzelnen Plan; die Power BI-Registerkarte wird einem bestimmten Bericht zugeordnet. Benutzer können einen Drilldown zum relevanten Kontext ausführen, aber Sie sollten nicht außerhalb der Registerkarte navigieren können. Die Power BI-Registerkarte aktiviert beispielsweise nicht die Navigation zu anderen Power BI-Berichten, aber Sie aktiviert die Schaltfläche " *Gehe zu Website* ", mit der der Bericht in der Haupt Power BI-Website gestartet wird.

  Für Team Registerkarten müssen Sie eine *Konfigurations-URL* angeben, um Optionen zu präsentieren und Informationen zu sammeln, damit Benutzer den Inhalt und die Erfahrung ihrer Registerkarte anpassen können. Diese iframed HTML-Seite wird angezeigt, wenn ein Benutzer die Registerkarte zunächst einem Kanal hinzufügt.

  Sie müssen auch alle weiteren Domänen bereitstellen, von denen die Registerkarte zu laden erwartet oder mit der eine Verknüpfung hergestellt werden soll.

* **Persönliche Registerkarten.** In diesem Abschnitt können Sie eine Gruppe von RegisterkartenDefinieren, die standardmäßig in der persönlichen App-Umgebung angezeigt werden (d. h. die Benutzerfreundlichkeit, die ein Benutzer mit ihrer App außerhalb des Kontexts eines Teams oder Kanals hat). Geben Sie in diesem Abschnitt den Registerkartennamen, einen eindeutigen Bezeichner, die URL, die auf die Benutzeroberfläche zeigt, die in Microsoft Teams angezeigt werden soll, und optional die URL an, die verwendet werden soll, wenn ein Benutzer die Registerkarte in einem Browser anzeigen möchte. Stellen Sie wie bei Microsoft Teams-Registerkarten alle weiteren Domänen bereit, von denen die Registerkarte erwartet, von zu laden oder eine Verknüpfung mit zu erstellen.

##### <a name="bots"></a>Bots

In diesem Abschnitt können Sie Ihrer APP einen [Unterhaltungs bot](~/bots/what-are-bots.md) hinzufügen. Wenn Sie bereits einen bot mit bot-Framework registriert haben, können Sie diesen bot hinzufügen, indem Sie auf *Einrichten* und den Namen des bot, bot Framework-ID und die Bereiche definieren, in denen der bot funktionieren wird.

Wenn Sie noch keinen bot mit dem bot-Framework registriert haben, klicken Sie auf *registrieren* , um eine neue zu erstellen. Wenn Sie die Registrierung Ihres bot abgeschlossen haben, kehren Sie zu diesem Abschnitt des Manifest-Editors zurück, um den Namen und die bot Framework-ID einzugeben.

Nachdem Sie die Informationen zu Ihrem bot bereitgestellt haben, können Sie nun optional eine Liste mit Befehlen definieren, die ihr bot Benutzern vorschlagen kann. Fügen Sie den Namen des Befehls, eine Beschreibung des Befehls, der seine Syntax und Argumente angibt, und den Bereich (s), auf den dieser Befehl angewendet werden soll.

Beachten Sie, dass, wenn Sie Ihren bot so definiert haben, dass er nur einen Bereich unterstützt, die für den nicht unterstützten Bereich angegebenen Befehle ignoriert werden. Sie können die Bereiche, die ihr bot unterstützt, jederzeit bearbeiten.

##### <a name="connectors"></a>Connectors

In diesem Abschnitt können Sie Ihrer APP einen Konnektor hinzufügen. Wenn Sie bereits einen Office 365-Connector registriert haben, wählen Sie *Einrichten* aus, und geben Sie den Namen und die ID des Connectors ein. Wenn Sie möchten, dass ein neuer Connector in Ihrem Browser zum Connector Developer Dashboard geleitet wird, klicken Sie auf *registrieren* .

##### <a name="messaging-extensions"></a>Messaging-Erweiterungen

[Messaging Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) sind eine leistungsstarke Möglichkeit für Benutzer, mit ihrer app in Microsoft Teams zu interagieren. Benutzer können Informationen von Ihrem Dienst Abfragen und diese Informationen in Form von Karten direkt in den Kanal oder Chat Unterhaltung Posten.

Messaging-Erweiterungen werden von bot-Framework-Bots betrieben, sodass Sie einen konfigurierten bot für den Betrieb benötigen. Wenn Sie über den Namen und die bot Framework-ID des bot verfügen, den Sie für die Messaging Erweiterung angeben möchten, geben Sie ihn ein. Klicken Sie andernfalls auf *registrieren* , um einen zu erstellen, und geben Sie die Informationen danach ein. Wählen Sie aus, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann.

Nachdem Sie den zugrunde liegenden bot konfiguriert haben, definieren Sie die Befehle und Parameter, die die Messaging Erweiterung annehmen kann.

Jeder Befehl erfordert einen Titel und eine ID. Der Befehl kann optional eine Beschreibung für den Benutzer enthalten. Jeder Befehl kann bis zu fünf Parameter unterstützen, die jeweils Folgendes erfordern:

* Der Name des Parameters, wie er im Microsoft Teams-Client angezeigt wird und in der Benutzeranforderung enthalten ist.
* Ein benutzerfreundlicher Titel
* Eine optionale Beschreibung

#### <a name="test-and-distribute"></a>Testen und verteilen

Nachdem Sie die Definition Ihrer Anwendung abgeschlossen haben, können Sie im Abschnitt Test and Distribute die Definition Ihrer APP als ZIP-Datei exportieren, die dann zum Testen freigegeben und in den Teams-Client hochgeladen werden kann. Durch Klicken auf Exportieren wird die ZIP-Datei als *appname.zip* im standardmäßigen Downloadverzeichnis heruntergeladen.

##### <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer APP in Microsoft Teams
Auf Ihrer Project-Startseite können Sie Ihre APP in ein Team hochladen, Ihre APP für Benutzer in Ihrer Organisation an den benutzerdefinierten APP-Speicher des Unternehmens übermitteln oder Ihre APP an die APP-Quelle für alle Microsoft Teams-Benutzer senden. Ihr IT-Administrator prüft diese Übermittlungen. Sie können zur Seite *veröffentlichen* zurückkehren, um den Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre APP von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. In diesem Fall können Sie auch Aktualisierungen an Ihre APP übermitteln oder derzeit aktive Übermittlungen kündigen.

### <a name="card-editor"></a>Karten-Editor

Eine Karte ist ein Container für kurze oder verwandte Informationen. Microsoft Teams unterstützt Karten, die mehrere Eigenschaften und Anlagen aufweisen können. Karten stellen eine wichtige Möglichkeit dar, dass Bots und Connectors umsetzbare Informationen an Benutzer weiterleiten. 

Um diesen Prozess einfacher und fehleranfälliger zu machen, können Sie mit der Registerkarte Karten-Editor Hero-Karten oder thumbnailkarten mithilfe eines Formulars erstellen und die resultierende Karte (genau so wie ein Benutzer Sie sehen würde) über einen bot überprüfen und testen. Außerdem wird der entsprechende JSON-, C#-oder Node.js-Code für die Karte bereitgestellt, die Sie in den Quellcode Ihrer APP kopieren/einfügen können.

Wenn Sie bereits über eine Karte verfügen, die Sie innerhalb von Teams überprüfen möchten, können Sie die JSON für diese Karte in die Registerkarte JSON unter *Karteninfo hinzufügen* einfügen und an sich selbst senden, um zu sehen, wie Sie in einem Chat aussieht.

### <a name="react-control-library"></a>Reaktions Steuerungs Bibliothek

>[!Note]
> Diese Reaktions Steuerungs Bibliothek wird in Zukunft veraltet sein. Verwenden Sie die [Fluent-UI reagiere-Steuerung als Alternative](https://microsoft.github.io/fluent-ui-react/) (ehemals Stardust UI).

Das Erstellen einer APP, die den Best Practices von Teams folgt, ist eine hervorragende Möglichkeit, um Ihrer APP ein Aussehen und Verhalten zu verleihen, das nahtlos mit der Clientumgebung von Teams in zusammen passt. Die Benutzeroberflächen-Steuerelemente, die Sie verwenden, sind wichtig, um dieses Ende zu erreichen. Um die Erstellung einer konsistenten Benutzeroberfläche zu vereinfachen, bietet App Studio verschiedene Kategorien von UI-Steuerelementen, die den Entwurfsprinzipien von Teams entsprechen.

Beispiele für die Steuerelemente und die entsprechenden reaktionskomponenten werden bereitgestellt und können beim Erstellen Ihrer APP verwendet werden.

#### <a name="controls"></a>Steuerelemente

Zu den Steuerelementen gehören:

* Schaltflächen
* DropDowns
* Kontrollkästchen
* Optionsfelder
* Schaltet
* Text Bereiche
* Links
* Registerkarten
* Tabellen
* Symbole
