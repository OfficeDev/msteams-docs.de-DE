## <a name="update-your-application"></a><span data-ttu-id="b1492-101">Aktualisieren Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="b1492-101">Update your application</span></span>

### <a name="_layoutcshtml"></a><span data-ttu-id="b1492-102">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="b1492-102">_Layout.cshtml</span></span>

<span data-ttu-id="b1492-103">Damit Ihre Registerkarte in Teams angezeigt werden kann, müssen Sie das Microsoft Teams **JavaScript-Client-SDK** und einen Aufruf nach dem Laden der `microsoftTeams.initialize()` Seite hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b1492-103">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="b1492-104">So kommunizieren Ihre Registerkarte und die Teams App:</span><span class="sxs-lookup"><span data-stu-id="b1492-104">This is how your tab and the Teams app communicate:</span></span>

- <span data-ttu-id="b1492-105">Navigieren Sie zum Ordner **Freigegeben,** öffnen **Sie _Layout.cshtml**, und fügen Sie dem Abschnitt tags `<head>` Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="b1492-105">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

    ```html
    `<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>`
    `<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>`
    ```

### <a name="personaltabcshtml"></a><span data-ttu-id="b1492-106">PersonalTab.cshtml</span><span class="sxs-lookup"><span data-stu-id="b1492-106">PersonalTab.cshtml</span></span>

<span data-ttu-id="b1492-107">Öffnen **Sie PersonalTab.cshtml,** und aktualisieren Sie die eingebetteten `<script>` Tags, indem Sie `microsoftTeams.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b1492-107">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="b1492-108">Stellen Sie sicher, dass Sie Ihr **aktualisiertes PersonalTab.cshtml speichern.**</span><span class="sxs-lookup"><span data-stu-id="b1492-108">Make sure to save your updated **PersonalTab.cshtml**.</span></span>