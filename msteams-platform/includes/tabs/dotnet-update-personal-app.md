## <a name="update-your-application"></a><span data-ttu-id="546ac-101">Aktualisieren Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="546ac-101">Update your application</span></span>

### <a name="_layoutcshtml"></a><span data-ttu-id="546ac-102">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="546ac-102">_Layout.cshtml</span></span>

<span data-ttu-id="546ac-103">Damit Ihre Registerkarte in Teams angezeigt werden kann, müssen Sie das **Microsoft Teams JavaScript-Client-SDK** und einen Aufruf nach `microsoftTeams.initialize()` dem Laden der Seite einschließen.</span><span class="sxs-lookup"><span data-stu-id="546ac-103">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="546ac-104">So kommunizieren Ihre Registerkarte und die Teams-App:</span><span class="sxs-lookup"><span data-stu-id="546ac-104">This is how your tab and the Teams app communicate:</span></span>

<span data-ttu-id="546ac-105">Wechseln Sie zum **Freigegebenen** Ordner, öffnen Sie **_Layout.cshtml,** und fügen Sie dem Abschnitt "tags" Folgendes `<head>` hinzu:</span><span class="sxs-lookup"><span data-stu-id="546ac-105">Go to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

### <a name="personaltabcshtml"></a><span data-ttu-id="546ac-106">PersonalTab.cshtml</span><span class="sxs-lookup"><span data-stu-id="546ac-106">PersonalTab.cshtml</span></span>

<span data-ttu-id="546ac-107">Öffnen Sie **PersonalTab.cshtml,** und aktualisieren Sie die eingebetteten `<script>` Tags durch Aufrufen von `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="546ac-107">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="546ac-108">Stellen Sie sicher, dass Sie die aktualisierte Datei **"PersonalTab.cshtml"** speichern.</span><span class="sxs-lookup"><span data-stu-id="546ac-108">Ensure you save your updated **PersonalTab.cshtml** file.</span></span>