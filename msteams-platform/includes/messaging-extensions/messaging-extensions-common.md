## <a name="add-a-messaging-extension-to-your-app"></a>Hinzufügen einer Messagingerweiterung zu Ihrer App

Eine Messagingerweiterung ist ein in der Cloud gehosteter Dienst, der Benutzeranforderungen abhört und mit strukturierten Daten wie einer Karte [antwortet.](~/task-modules-and-cards/what-are-cards.md) Sie integrieren Ihren Dienst in Microsoft Teams über Bot `Activity` Framework-Objekte. Unsere .NET- und Node.js-Erweiterungen für das Bot Builder SDK können Ihnen dabei helfen, Ihrer App Messagingerweiterungsfunktionen hinzuzufügen.

![Diagramm des Nachrichtenflusses für Messagingerweiterungen](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrieren im Bot Framework

Wenn Sie dies noch nicht getan haben, müssen Sie zuerst einen Bot bei der Microsoft Bot Framework. Die Microsoft-App-ID und Rückrufendpunkte für Ihren Bot, wie dort definiert, werden in Ihrer Messagingerweiterung zum Empfangen und Beantworten von Benutzeranforderungen verwendet. Denken Sie daran, den Microsoft Teams für Ihren Bot zu aktivieren.

Notieren Sie Ihre Bot-App-ID und Ihr App-Kennwort. Sie müssen die App-ID im App-Manifest angeben.

### <a name="update-your-app-manifest"></a>Aktualisieren Des App-Manifests

Wie bei Bots und Registerkarten aktualisieren Sie das [Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App so, dass die Eigenschaften der Messagingerweiterung enthalten sind. Diese Eigenschaften steuern, wie Ihre Messagingerweiterung angezeigt wird und sich im Microsoft Teams verhält. Messagingerweiterungen werden ab Version 1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren der Messagingerweiterung

Um eine Messagingerweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur auf oberster Ebene in Ihr Manifest mit der -Eigenschaft `composeExtensions` ein. Derzeit sind Sie auf das Erstellen einer einzelnen Messagingerweiterung für Ihre App beschränkt.

> [!NOTE]
> Das Manifest bezieht sich auf Messagingerweiterungen als `composeExtensions` . Dadurch wird die Abwärtskompatibilität beibehalten.

Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel identisch mit der ID für Ihre Teams sein. | Ja |
| `scopes` | Array, das anmeldet, ob diese Erweiterung zu oder zu Bereich `personal` `team` hinzugefügt werden kann (oder beides). | Ja |
| `canUpdateConfiguration` | Aktiviert **Einstellungen** Menüelement. | Nein |
| `commands` | Array von Befehlen, die von dieser Messagingerweiterung unterstützt werden. Sie sind auf 10 Befehle beschränkt. | Ja |

#### <a name="define-commands"></a>Definieren von Befehlen

Ihre Messagingerweiterung sollte einen Befehl deklarieren, der angezeigt wird, wenn der Benutzer Ihre App aus der Schaltfläche Weitere Optionen **(**&#8943;) im **Verfassenfeld** auswählt.

![Screenshot der Liste der Messagingerweiterungen in Teams](~/assets/images/compose-extensions/compose-extension-list.png)

Im App-Manifest ist Ihr Befehlselement ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl macht. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Legen Sie den Typ des Befehls. Mögliche Werte sind `query` und `action`. Wenn nicht vorhanden, wird der Standardwert auf `query` festgelegt. | Nein | 1.4 |
| `initialRun` | Optionaler Parameter, der mit `query` Befehlen verwendet wird. Wenn dieser Wert **auf true** festgelegt ist, wird angegeben, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche ausgibt. | Nein | 1.0 |
| `fetchTask` | Optionaler Parameter, der mit `action` Befehlen verwendet wird. Auf **true festgelegt,** um die adaptive Karte oder Web-URL zu abrufen, die im [Aufgabenmodul angezeigt werden soll.](~/task-modules-and-cards/what-are-task-modules.md) Dies wird verwendet, wenn die Eingaben für den Befehl dynamisch und nicht `action` statisch sind. Beachten Sie, dass die Liste der statischen Parameter für den Befehl ignoriert wird, wenn sie auf **true** festgelegt ist. | Nein | 1.4 |
| `parameters` | Statische Liste der Parameter für den Befehl. | Ja | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt die Zwecke oder das Beispiel dieses Parameters für den wert, der bereitgestellt werden soll. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurze benutzerfreundlicher Parametertitel oder -bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Auf den typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` festgelegt. | Nein | 1.4 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Nachrichtenaktion verfügbar ist. Mögliche Werte sind `message` , `compose` oder `commandBox` . Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |
