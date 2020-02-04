## <a name="add-a-messaging-extension-to-your-app"></a>Hinzufügen einer Messaging Erweiterung zu Ihrer APP

Eine Messaging Erweiterung ist ein in der Cloud gehosteter Dienst, der Benutzeranforderungen überwacht und mit strukturierten Daten wie einer [Karte](~/task-modules-and-cards/what-are-cards.md)antwortet. Sie integrieren Ihren Dienst in Microsoft Teams über bot- `Activity` Framework-Objekte. Unsere .net-und Node. js-Erweiterungen für das bot Builder SDK können Ihnen helfen, Ihrer APP Messaging Erweiterungsfunktionen hinzuzufügen.

![Diagramm des Nachrichtenflusses für Messaging Erweiterungen](~/assets/images/compose-extensions/ceflow.png)

### <a name="register-in-the-bot-framework"></a>Registrieren im bot-Framework

Wenn Sie dies noch nicht getan haben, müssen Sie zuerst einen bot mit dem Microsoft bot Framework registrieren. Die Microsoft-App-ID und die Rückruf Endpunkte für Ihren bot, wie dort definiert, werden in Ihrer Messaging-Erweiterung verwendet, um Benutzeranforderungen zu empfangen und darauf zu reagieren. Denken Sie daran, den Microsoft Teams-Kanal für Ihren bot zu aktivieren.

Notieren Sie sich Ihre bot-APP-ID und Ihr App-Kennwort, müssen Sie die APP-ID in Ihrem App-Manifest angeben.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Wie bei Bots und Tabs aktualisieren Sie das [Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer APP so, dass die Eigenschaften der Messaging Erweiterung enthalten sind. Diese Eigenschaften bestimmen, wie Ihre Messaging Erweiterung angezeigt wird und sich im Microsoft Teams-Client verhält. Messaging Erweiterungen werden beginnend mit v 1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren der Messaging Erweiterung

Um eine Messaging Erweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur der obersten Ebene in Ihr `composeExtensions` Manifest mit der-Eigenschaft ein. Derzeit ist es nur möglich, eine einzelne Messaging Erweiterung für Ihre APP zu erstellen.

> [!NOTE]
> Das Manifest bezieht sich auf Messaging `composeExtensions`Erweiterungen als. Dadurch wird die Abwärtskompatibilität gewährleistet.

Die Erweiterungs Definition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den bot, die im bot-Framework registriert ist. Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App übereinstimmen. | Ja |
| `scopes` | Array, `personal` das angibt, ob dieser Erweiterung oder `team` Bereichen (oder beides) hinzugefügt werden kann. | Ja |
| `canUpdateConfiguration` | Aktiviert das Menüelement **Einstellungen** . | Nein |
| `commands` | Array von Befehlen, die von dieser Messaging Erweiterung unterstützt werden. Sie sind auf 10 Befehle limitiert. | Ja |

#### <a name="define-commands"></a>Definieren von Befehlen

Ihre Messaging Erweiterung sollte einen Befehl deklarieren, der angezeigt wird, wenn der Benutzer Ihre APP über die Schaltfläche **Weitere Optionen** (**&#8943;**) im Feld Verfassen auswählt.

![Screenshot der Liste der Messaging Erweiterungen in Microsoft Teams](~/assets/images/compose-extensions/compose-extension-list.png)

Im App-Manifest ist Ihr Befehls Element ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Diese ID wird von der Benutzeranforderung eingeschlossen. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl ausführt. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Legen Sie den Typ des Befehls fest. Mögliche Werte sind `query` und `action`. Wenn nicht vorhanden, wird der Standardwert auf festgelegt.`query` | Nein | 1.4 |
| `initialRun` | Optionaler Parameter, der `query` mit Befehlen verwendet wird. Bei Festlegung auf " **true**" gibt an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `fetchTask` | Optionaler Parameter, der `action` mit Befehlen verwendet wird. Legen Sie den Wert auf **true** fest, um die Adaptive Karte oder die weburl abzurufen, die im [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md)angezeigt werden soll. Dies wird verwendet, wenn die Eingaben für `action` den Befehl im Gegensatz zu einer statischen Gruppe von Parametern dynamisch sind. Beachten Sie, dass bei Festlegung auf **true** die Liste der statischen Parameter für den Befehl ignoriert wird. | Nein | 1.4 |
| `parameters` | Statische Liste von Parametern für den Befehl. | Ja | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt den Zweck oder das Beispiel dieses Parameters des Werts, der angegeben werden sollte. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parameter Titel oder Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Legt den Typ der erforderlichen Eingabe fest. Mögliche Werte sind `text`: `textarea`, `number`, `date`, `time`, `toggle`,. Default ist auf festgelegt`text` | Nein | 1.4 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Nachrichtenaktion verfügbar ist. Mögliche Werte sind `message`, `compose`oder `commandBox`. Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |
