## <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

### <a name="_layoutcshtml"></a>_Layout. cshtml

Damit Ihre Registerkarte in Teams angezeigt wird, müssen Sie das **Microsoft Teams-JavaScript-Client-SDK** einschließen und `microsoftTeams.initialize()` nach dem Laden einer Seite einen Anruf hinzufügen. So kommunizieren Ihre Registerkarten und die Teams-App:

- Navigieren Sie zum **freigegebenen** Ordner, öffnen Sie **_Layout. cshtml**, und fügen Sie dem `<head>` Abschnitt Tags Folgendes hinzu:

```html
`<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
`<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
```

### <a name="personaltabcshtml"></a>PersonalTab. cshtml

Öffnen Sie **PersonalTab. cshtml** , und aktualisieren `<script>` Sie die eingebetteten `microsoftTeams.initialize()`Tags durch Aufrufen von.

Stellen Sie sicher, dass Sie Ihre aktualisierten *PersonalTab. cshtml*speichern.