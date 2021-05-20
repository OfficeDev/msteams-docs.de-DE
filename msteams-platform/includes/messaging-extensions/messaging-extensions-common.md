## <a name="add-a-messaging-extension-to-your-app"></a>Hinzufügen einer Messagingerweiterung zu Ihrer App

Eine Messagingerweiterung ist ein in der Cloud gehosteter Dienst, der Benutzeranfragen abhört und mit strukturierten Daten, z. B. einer [Karte](~/task-modules-and-cards/what-are-cards.md), antwortet. Sie integrieren Ihren Service über Bot Framework-Objekte in `Activity` Microsoft Teams. Unsere Erweiterungen .NET und Node.js für das Bot Builder SDK können Ihnen dabei helfen, Ihrer App Messagingerweiterungsfunktionen hinzuzufügen.

![Diagramm des Nachrichtenflusses für Messagingerweiterungen](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrieren Sie sich im Bot-Framework

Wenn Sie dies noch nicht getan haben, müssen Sie zuerst einen Bot bei der Microsoft Bot Framework registrieren. Die Microsoft-App-ID und die Rückrufendpunkte für Ihren Bot, wie dort definiert, werden in Ihrer Messagingerweiterung verwendet, um Benutzeranfragen zu empfangen und darauf zu reagieren. Denken Sie daran, den Microsoft Teams Kanal für Ihren Bot zu aktivieren.

Zeichnen Sie Ihre Bot-App-ID und Ihr App-Kennwort auf, sie müssen die App-ID in Ihrem App-Manifest angeben.

### <a name="update-your-app-manifest"></a>Aktualisieren Ihres App-Manifests

Wie bei Bots und Registerkarten aktualisieren Sie das [Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App, um die Messagingerweiterungseigenschaften einzuschließen. Diese Eigenschaften bestimmen, wie Ihre Messagingerweiterung im Microsoft Teams Client angezeigt wird und sich verhält. Messagingerweiterungen werden ab v1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren Ihrer Messagingerweiterung

Um eine Messagingerweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur der obersten Ebene in Ihr Manifest mit der `composeExtensions` Eigenschaft ein. Derzeit sind Sie darauf beschränkt, eine einzelne Messagingerweiterung für Ihre App zu erstellen.

> [!NOTE]
> Das Manifest bezieht sich auf Messagingerweiterungen als `composeExtensions` . Dies dient der Aufrechterhaltung der Abwärtskompatibilität.

Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App identisch sein. | Ja |
| `scopes` | Array, das deklariert, ob diese Erweiterung hinzugefügt werden `personal` kann, oder `team` zu Bereichen (oder beidem). | Ja |
| `canUpdateConfiguration` | Aktiviert **Einstellungen** Menüelement. | Nein |
| `commands` | Array von Befehlen, die von dieser Messagingerweiterung unterstützt werden. Sie sind auf 10 Befehle beschränkt. | Ja |

#### <a name="define-commands"></a>Definieren von Befehlen

Ihre Messagingerweiterung sollte einen Befehl deklarieren, der angezeigt wird, wenn der Benutzer Ihre App über die Schaltfläche **Weitere Optionen** (**&#8943;**) im Feld Verfassen auswählt.

![Screenshot der Liste der Messagingerweiterungen in Teams](~/assets/images/compose-extensions/compose-extension-list.png)

Im App-Manifest ist Ihr Befehlselement ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl bewirkt. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Legen Sie den Befehlstyp fest. Mögliche Werte sind `query` und `action`. Wenn nicht vorhanden, ist der Standardwert auf `query` festgelegt. | Nein | 1.4 |
| `initialRun` | Optionaler Parameter, der mit Befehlen verwendet `query` wird. Wenn auf **true** gesetzt, gibt dieser Befehl an, dass er ausgeführt werden soll, sobald der Benutzer diesen Befehl in der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `fetchTask` | Optionaler Parameter, der mit Befehlen verwendet `action` wird. Legen Sie **den** Wert fest, um die adaptive Karte oder Web-URL abzurufen, die im [Taskmodul](~/task-modules-and-cards/what-are-task-modules.md)angezeigt werden soll. Dies wird verwendet, wenn die Eingaben für den `action` Befehl dynamisch sind und nicht ein statischer Satz von Parametern. Beachten Sie, dass die if, die auf **true** der statischen Parameterliste für den Befehl festgelegt ist, ignoriert wird. | Nein | 1.4 |
| `parameters` | Statische Liste der Parameter für den Befehl. | Ja | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt die Zwecke dieses Parameters oder ein Beispiel für den wert, der bereitgestellt werden soll. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parametertitel oder -beschriftung. | Ja | 1.0 |
| `parameter.inputType` | Wird auf den erforderlichen Eingabetyp festgelegt. Mögliche Werte sind `text` , , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` festgelegt. | Nein | 1.4 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Nachrichtenaktion verfügbar ist. Mögliche Werte sind `message` , `compose` oder `commandBox` . Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |
