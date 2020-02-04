## <a name="update-your-application"></a><span data-ttu-id="2078c-101">Aktualisieren Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="2078c-101">Update your application</span></span>

### <a name="_layoutcshtml"></a><span data-ttu-id="2078c-102">_Layout. cshtml</span><span class="sxs-lookup"><span data-stu-id="2078c-102">_Layout.cshtml</span></span>

<span data-ttu-id="2078c-103">Damit Ihre Registerkarte in Teams angezeigt wird, müssen Sie das **Microsoft Teams-JavaScript-Client-SDK** einschließen und `microsoftTeams.initialize()` nach dem Laden einer Seite einen Anruf hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2078c-103">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="2078c-104">So kommunizieren Ihre Registerkarten und die Teams-App:</span><span class="sxs-lookup"><span data-stu-id="2078c-104">This is how your tab and the Teams app communicate:</span></span>

- <span data-ttu-id="2078c-105">Navigieren Sie zum **freigegebenen** Ordner, öffnen Sie **_Layout. cshtml**, und fügen Sie dem `<head>` Abschnitt Tags Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="2078c-105">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

```html
`<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
`<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
```

### <a name="personaltabcshtml"></a><span data-ttu-id="2078c-106">PersonalTab. cshtml</span><span class="sxs-lookup"><span data-stu-id="2078c-106">PersonalTab.cshtml</span></span>

<span data-ttu-id="2078c-107">Öffnen Sie **PersonalTab. cshtml** , und aktualisieren `<script>` Sie die eingebetteten `microsoftTeams.initialize()`Tags durch Aufrufen von.</span><span class="sxs-lookup"><span data-stu-id="2078c-107">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="2078c-108">Stellen Sie sicher, dass Sie Ihre aktualisierten *PersonalTab. cshtml*speichern.</span><span class="sxs-lookup"><span data-stu-id="2078c-108">Make sure to save your updated *PersonalTab.cshtml*.</span></span>