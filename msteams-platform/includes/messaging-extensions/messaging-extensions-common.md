## <a name="add-a-message-extension-to-your-app"></a>Hinzufügen einer Nachrichtenerweiterung zu Ihrer App

Eine Nachrichtenerweiterung ist ein in der Cloud gehosteter Dienst, der auf Benutzeranforderungen lauscht und mit strukturierten Daten, z. B. einer [Karte](~/task-modules-and-cards/what-are-cards.md), antwortet. Sie integrieren Ihren Dienst mit Microsoft Teams über Bot Framework-Objekte`Activity`. Unsere .NET- und Node.js-Erweiterungen für das Bot Builder SDK können Ihnen helfen, Ihrer App Nachrichtenerweiterungsfunktionen hinzuzufügen.

![Diagramm des Nachrichtenflusses für Nachrichtenerweiterungen](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrieren im Bot Framework

Wenn Sie dies noch nicht getan haben, müssen Sie zuerst einen Bot bei der Microsoft Bot Framework registrieren. Die Microsoft-App-ID und Rückrufendpunkte für Ihren Bot, wie dort definiert, werden in Ihrer Nachrichtenerweiterung verwendet, um Benutzeranfragen zu empfangen und zu beantworten. Denken Sie daran, den Microsoft Teams Kanal für Ihren Bot zu aktivieren.

Notieren Sie Ihre Bot-App-ID und ihr App-Kennwort. Sie müssen die App-ID in Ihrem App-Manifest angeben.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Wie bei Bots und Registerkarten aktualisieren Sie das [Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App, um die Eigenschaften der Nachrichtenerweiterung einzuschließen. Diese Eigenschaften steuern, wie Ihre Nachrichtenerweiterung im Microsoft Teams-Client angezeigt wird und wie sie sich verhält. Nachrichtenerweiterungen werden ab Version 1.0 des Manifests unterstützt.

#### <a name="declare-your-message-extension"></a>Deklarieren Der Nachrichtenerweiterung

Um eine Nachrichtenerweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur der obersten Ebene in Ihr Manifest mit der `composeExtensions` Eigenschaft ein. Derzeit sind Sie auf das Erstellen einer einzelnen Nachrichtenerweiterung für Ihre App beschränkt.

> [!NOTE]
> Das Manifest bezieht sich auf Nachrichtenerweiterungen als `composeExtensions`. Dies dient dazu, die Abwärtskompatibilität aufrechtzuerhalten.

Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App identisch sein. | Ja |
| `scopes` | Array, das angibt, ob diese Erweiterung hinzugefügt oder Bereichen (oder beiden) hinzugefügt `personal` `team` werden kann. | Ja |
| `canUpdateConfiguration` | Aktiviert **Einstellungen** Menüelement. | Nein |
| `commands` | Array von Befehlen, die diese Nachrichtenerweiterung unterstützt. Sie sind auf 10 Befehle beschränkt. | Ja |

#### <a name="define-commands"></a>Definieren von Befehlen

Ihre Nachrichtenerweiterung sollte einen Befehl deklarieren, der angezeigt wird, wenn der Benutzer Ihre App über die Schaltfläche " **Weitere Optionen** " (**&#8943;**) im Feld "Verfassen" auswählt.

![Screenshot der Liste der Nachrichtenerweiterungen in Teams](~/assets/images/compose-extensions/compose-extension-list.png)

Im App-Manifest ist ihr Befehlselement ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestmanifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl bewirkt. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Legen Sie den Befehlstyp fest. Mögliche Werte sind `query` und `action`. Wenn der Standardwert nicht vorhanden ist, wird er auf `query`festgelegt. | Nein | 1.4 |
| `initialRun` | Optionaler Parameter, der mit `query` Befehlen verwendet wird. Wenn " **true**" festgelegt ist, wird angegeben, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl in der Benutzeroberfläche wählt. | Nein | 1.0 |
| `fetchTask` | Optionaler Parameter, der mit `action` Befehlen verwendet wird. Auf **"true"** festgelegt, um die adaptive Karte oder Web-URL abzurufen, die im [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md) angezeigt werden soll. Dies wird verwendet, wenn die Eingaben für den `action` Befehl dynamisch sind, im Gegensatz zu einem statischen Satz von Parametern. Beachten Sie, dass die Liste der statischen Parameter für den Befehl ignoriert wird, wenn sie auf **"true** " festgelegt ist. | Nein | 1.4 |
| `parameters` | Statische Liste der Parameter für den Befehl. | Ja | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt die Zwecke oder das Beispiel des Werts, der bereitgestellt werden soll. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parametertitel oder Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Legen Sie den Typ der erforderlichen Eingabe fest. Mögliche Werte sind `text`, `textarea`, `number`, `date`, `time`. `toggle` Der Standardwert ist auf `text`. | Nein | 1.4 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Nachrichtenaktion verfügbar ist. Mögliche Werte sind `message`, `compose`oder `commandBox`. Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |
