## <a name="create-the-app-package"></a><span data-ttu-id="084ed-101">Erstellen des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="084ed-101">Create the app package</span></span>

<span data-ttu-id="084ed-102">Sie benötigen ein App-Paket, um Ihre Registerkarte in Microsoft Teams zu testen.</span><span class="sxs-lookup"><span data-stu-id="084ed-102">You'll need an app package to test your tab in Teams.</span></span> <span data-ttu-id="084ed-103">Es handelt sich um einen ZIP-Ordner, der die folgenden erforderlichen Dateien enthält:</span><span class="sxs-lookup"><span data-stu-id="084ed-103">It's a zip folder that contains the following required files:</span></span>

- <span data-ttu-id="084ed-104">Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="084ed-104">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="084ed-105">Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="084ed-105">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="084ed-106">Eine **Manifest. JSON** -Datei, die die Attribute Ihrer APP angibt.</span><span class="sxs-lookup"><span data-stu-id="084ed-106">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="084ed-107">Das Paket wird über eine Schluck Aufgabe erstellt, mit der die Manifest. JSON-Datei überprüft und der ZIP-Ordner `./package directory`in generiert wird.</span><span class="sxs-lookup"><span data-stu-id="084ed-107">The package is created via a gulp task that validates the manifest.json file and generates the zip folder in the `./package directory`.</span></span> <span data-ttu-id="084ed-108">Geben Sie an der Eingabeaufforderung Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="084ed-108">In the command prompt enter:</span></span>

```bash
gulp manifest
```

## <a name="build-your-application"></a><span data-ttu-id="084ed-109">Erstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="084ed-109">Build your application</span></span>

<span data-ttu-id="084ed-110">Der Befehl Build stapelt die Lösung in den Ordner *./dist-Ordner.* .</span><span class="sxs-lookup"><span data-stu-id="084ed-110">The build command transpiles your solution into the *./dist* folder.</span></span> <span data-ttu-id="084ed-111">Geben Sie als nächstes Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="084ed-111">Next,enter:</span></span>

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a><span data-ttu-id="084ed-112">Ausführen Ihrer Anwendung in localhost</span><span class="sxs-lookup"><span data-stu-id="084ed-112">Run your application in localhost</span></span>

<span data-ttu-id="084ed-113">Starten Sie einen lokalen Webserver, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="084ed-113">Start a local web server by entering the following:</span></span>

```bash
gulp serve
```

<span data-ttu-id="084ed-114">Geben `http://localhost:3007/<yourDefaultAppNameTab>/` Sie in Ihren Browser ein, und zeigen Sie die Startseite der Anwendung an:</span><span class="sxs-lookup"><span data-stu-id="084ed-114">Enter `http://localhost:3007/<yourDefaultAppNameTab>/` in your browser and view your application's home page:</span></span>

![Screenshot der Startseite](~/assets/images/tab-images/homePage.png)