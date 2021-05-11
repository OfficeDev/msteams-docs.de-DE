## <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

### <a name="_layoutcshtml"></a>_Layout.cshtml

Damit Ihre Registerkarte in Teams angezeigt werden kann, müssen Sie das Microsoft Teams **JavaScript-Client-SDK** und einen Aufruf nach dem Laden der `microsoftTeams.initialize()` Seite hinzufügen. So kommunizieren Ihre Registerkarte und die Teams App:

- Navigieren Sie zum Ordner **Freigegeben,** öffnen **Sie _Layout.cshtml**, und fügen Sie dem Abschnitt tags `<head>` Folgendes hinzu:

```html
`<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
`<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
```

### <a name="personaltabcshtml"></a>PersonalTab.cshtml

Öffnen **Sie PersonalTab.cshtml,** und aktualisieren Sie die eingebetteten `<script>` Tags, indem Sie `microsoftTeams.initialize()` aufrufen.

Stellen Sie sicher, dass Sie Ihr *aktualisiertes PersonalTab.cshtml speichern.*