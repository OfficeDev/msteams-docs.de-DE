## <a name="update-your-application"></a>Aktualisieren Sie Ihre Anwendung

### <a name="_layoutcshtml"></a>_Layout.cshtml

Damit Ihre Registerkarte in Teams angezeigt wird, müssen Sie das **Microsoft Teams JavaScript-Client-SDK** und einen Aufruf an die Seite nach dem Laden der Seite einschließen. `microsoftTeams.initialize()` So kommunizieren Ihre Registerkarte und die Teams-App:

- Navigieren Sie zum **freigegebenen** Ordner, öffnen **Sie _Layout.cshtml**, und fügen Sie dem `<head>` Tags-Abschnitt Folgendes hinzu:

    ```html
    `<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
    `<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
    ```

### <a name="personaltabcshtml"></a>PersonalTab.cshtml

Öffnen Sie **PersonalTab.cshtml** und aktualisieren Sie die eingebetteten `<script>` Tags, indem Sie `microsoftTeams.initialize()` aufrufen.

Achten Sie darauf, Ihre aktualisierte **PersonalTab.cshtml** zu speichern.