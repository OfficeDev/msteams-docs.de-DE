## <a name="add-a-messaging-extension-to-your-app"></a>Hinzufügen einer Messaging-Erweiterung zu Ihrer App

Eine Messaging-Erweiterung ist ein in der Cloud gehosteter Dienst, der Benutzeranforderungen überwacht und mit strukturierten Daten wie z. B. einer [Karte](~/task-modules-and-cards/what-are-cards.md)antwortet. Sie integrieren Ihren Dienst mit Microsoft Teams über Bot `Activity` Framework-Objekte. Unsere .NET- und Node.js-Erweiterungen für das Bot Builder SDK können Ihnen helfen, Ihrer App Messaging-Erweiterungsfunktionen hinzuzufügen.

![Diagramm des Nachrichtenflusses für Messaging-Erweiterungen](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrieren im Bot Framework

Wenn sie dies noch nicht getan haben, müssen Sie zuerst einen Bot beim Microsoft Bot Framework registrieren. Die Dort definierten Microsoft-App-ID- und Rückrufendpunkte für Ihren Bot werden in Ihrer Messaging-Erweiterung verwendet, um Benutzeranforderungen zu empfangen und darauf zu reagieren. Denken Sie daran, den Microsoft Teams-Kanal für Ihren Bot zu aktivieren.

Notieren Sie Ihre Bot-App-ID und Ihr App-Kennwort. Sie müssen die App-ID in Ihrem App-Manifest angeben.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Wie bei Bots und Registerkarten aktualisieren Sie das [Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App, um die Eigenschaften der Messaging-Erweiterung einzuschließen. Diese Eigenschaften steuern, wie Ihre Messaging-Erweiterung im Microsoft Teams Client angezeigt wird und wie sie sich verhält. Messaging-Erweiterungen werden ab Version 1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren Der Messaging-Erweiterung

Um eine Messaging-Erweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur auf oberster Ebene in Ihr Manifest mit der `composeExtensions` Eigenschaft ein. Derzeit sind Sie auf die Erstellung einer einzelnen Messaging-Erweiterung für Ihre App beschränkt.

> [!NOTE]
> Das Manifest bezieht sich auf Messaging-Erweiterungen als `composeExtensions` . Dies dient zur Aufrechterhaltung der Abwärtskompatibilität.

Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App übereinstimmen. | Ja |
| `scopes` | Array, das deklariert, ob diese Erweiterung zu bereichen (oder zu beiden) hinzugefügt werden `personal` `team` kann. | Ja |
| `canUpdateConfiguration` | Aktiviert **Einstellungen** Menüelement. | Nein |
| `commands` | Array von Befehlen, die von dieser Messaging-Erweiterung unterstützt werden. Sie sind auf 10 Befehle beschränkt. | Ja |

#### <a name="define-commands"></a>Definieren von Befehlen

Ihre Messaging-Erweiterung sollte einen Befehl deklarieren, der angezeigt wird, wenn der Benutzer Ihre App über die Schaltfläche **"Weitere Optionen"** (**&#8943;**) im Feld "Verfassen" auswählt.

![Screenshot der Liste der Messaging-Erweiterungen in Teams](~/assets/images/compose-extensions/compose-extension-list.png)

Im App-Manifest ist das Befehlselement ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestversion des Manifests |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl bewirkt. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Legen Sie den Befehlstyp fest. Mögliche Werte sind `query` und `action`. Wenn dieser Wert nicht vorhanden ist, wird der Standardwert auf `query` . | Nein | 1.4 |
| `initialRun` | Optionaler Parameter, der mit Befehlen verwendet `query` wird. Wenn der Wert auf **"true"** festgelegt ist, wird angegeben, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `fetchTask` | Optionaler Parameter, der mit Befehlen verwendet `action` wird. Auf **"true"** festgelegt, um die adaptive Karte oder Web-URL abzurufen, die im [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md)angezeigt werden soll. Dies wird verwendet, wenn die Eingaben für den `action` Befehl dynamisch sind, im Gegensatz zu einem statischen Satz von Parametern. Beachten Sie, dass die Statische Parameterliste für den Befehl ignoriert wird, wenn sie auf **"true"** festgelegt ist. | Nein | 1.4 |
| `parameters` | Statische Liste der Parameter für den Befehl. | Ja | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt die Zwecke dieses Parameters oder ein Beispiel für den Wert, der angegeben werden soll. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parametertitel oder -beschriftung. | Ja | 1.0 |
| `parameter.inputType` | Legen Sie den Typ der erforderlichen Eingabe fest. Mögliche Werte sind `text` , , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` . | Nein | 1.4 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Nachrichtenaktion verfügbar ist. Mögliche Werte sind `message` , `compose` oder `commandBox` . Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |
