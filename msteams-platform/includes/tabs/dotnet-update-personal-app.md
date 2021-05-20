## <a name="update-your-application"></a><span data-ttu-id="13eb9-101">Aktualisieren Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="13eb9-101">Update your application</span></span>

### <a name="_layoutcshtml"></a><span data-ttu-id="13eb9-102">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="13eb9-102">_Layout.cshtml</span></span>

<span data-ttu-id="13eb9-103">Damit Ihre Registerkarte in Teams angezeigt wird, müssen Sie das **Microsoft Teams JavaScript-Client-SDK** und einen Aufruf an die Seite nach dem Laden der Seite einschließen. `microsoftTeams.initialize()`</span><span class="sxs-lookup"><span data-stu-id="13eb9-103">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="13eb9-104">So kommunizieren Ihre Registerkarte und die Teams-App:</span><span class="sxs-lookup"><span data-stu-id="13eb9-104">This is how your tab and the Teams app communicate:</span></span>

- <span data-ttu-id="13eb9-105">Navigieren Sie zum **freigegebenen** Ordner, öffnen **Sie _Layout.cshtml**, und fügen Sie dem `<head>` Tags-Abschnitt Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="13eb9-105">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

    ```html
    `<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
    `<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
    ```

### <a name="personaltabcshtml"></a><span data-ttu-id="13eb9-106">PersonalTab.cshtml</span><span class="sxs-lookup"><span data-stu-id="13eb9-106">PersonalTab.cshtml</span></span>

<span data-ttu-id="13eb9-107">Öffnen Sie **PersonalTab.cshtml** und aktualisieren Sie die eingebetteten `<script>` Tags, indem Sie `microsoftTeams.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="13eb9-107">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="13eb9-108">Achten Sie darauf, Ihre aktualisierte **PersonalTab.cshtml** zu speichern.</span><span class="sxs-lookup"><span data-stu-id="13eb9-108">Make sure to save your updated **PersonalTab.cshtml**.</span></span>