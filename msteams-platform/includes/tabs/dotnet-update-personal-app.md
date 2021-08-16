## <a name="update-your-application"></a>Aktualisieren Der Anwendung

### <a name="_layoutcshtml"></a>_Layout.cshtml

Damit Ihre Registerkarte in Teams angezeigt werden kann, müssen Sie das **Microsoft Teams JavaScript-Client-SDK** und einen Aufruf nach `microsoftTeams.initialize()` dem Laden der Seite einschließen. So kommunizieren Ihre Registerkarte und die Teams-App:

Wechseln Sie zum **Freigegebenen** Ordner, öffnen **Sie _Layout.cshtml,** und fügen Sie dem Abschnitt "Tags" Folgendes `<head>` hinzu:

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

### <a name="personaltabcshtml"></a>PersonalTab.cshtml

Öffnen Sie **PersonalTab.cshtml,** und aktualisieren Sie die eingebetteten `<script>` Tags durch Aufrufen von `microsoftTeams.initialize()` .

Stellen Sie sicher, dass Sie die aktualisierte Datei **"PersonalTab.cshtml"** speichern.