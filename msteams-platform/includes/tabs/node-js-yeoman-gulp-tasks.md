## <a name="create-the-app-package"></a><span data-ttu-id="b28b3-101">Erstellen des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="b28b3-101">Create the app package</span></span>

<span data-ttu-id="b28b3-102">Sie benötigen ein App-Paket, um Ihre Registerkarte in der Teams.</span><span class="sxs-lookup"><span data-stu-id="b28b3-102">You'll need an app package to test your tab in Teams.</span></span> <span data-ttu-id="b28b3-103">Es ist ein ZIP-Ordner, der die folgenden erforderlichen Dateien enthält:</span><span class="sxs-lookup"><span data-stu-id="b28b3-103">It's a zip folder that contains the following required files:</span></span>

- <span data-ttu-id="b28b3-104">Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="b28b3-104">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="b28b3-105">Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="b28b3-105">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="b28b3-106">Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="b28b3-106">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="b28b3-107">Das Paket wird über eine gulp-Aufgabe erstellt, die die Datei manifest.jsüberprüft und den Ordner "ZIP" in `./package directory` generiert.</span><span class="sxs-lookup"><span data-stu-id="b28b3-107">The package is created via a gulp task that validates the manifest.json file and generates the zip folder in the `./package directory`.</span></span> <span data-ttu-id="b28b3-108">Geben Sie in der Eingabeaufforderung die folgenden Eingabeaufforderungen ein:</span><span class="sxs-lookup"><span data-stu-id="b28b3-108">In the command prompt enter:</span></span>

```bash
gulp manifest
```

## <a name="build-your-application"></a><span data-ttu-id="b28b3-109">Erstellen Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="b28b3-109">Build your application</span></span>

<span data-ttu-id="b28b3-110">Der Buildbefehl überlagert Ihre Lösung in den *Ordner ./dist.*</span><span class="sxs-lookup"><span data-stu-id="b28b3-110">The build command transpiles your solution into the *./dist* folder.</span></span> <span data-ttu-id="b28b3-111">Geben Sie als Nächstes ein:</span><span class="sxs-lookup"><span data-stu-id="b28b3-111">Next,enter:</span></span>

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a><span data-ttu-id="b28b3-112">Ausführen der Anwendung in localhost</span><span class="sxs-lookup"><span data-stu-id="b28b3-112">Run your application in localhost</span></span>

<span data-ttu-id="b28b3-113">Starten Sie einen lokalen Webserver, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="b28b3-113">Start a local web server by entering the following:</span></span>

```bash
gulp serve
```

<span data-ttu-id="b28b3-114">Geben `http://localhost:3007/<yourDefaultAppNameTab>/` Sie in Ihren Browser ein, und zeigen Sie die Homepage Ihrer Anwendung an:</span><span class="sxs-lookup"><span data-stu-id="b28b3-114">Enter `http://localhost:3007/<yourDefaultAppNameTab>/` in your browser and view your application's home page:</span></span>

![Screenshot der Startseite](~/assets/images/tab-images/homePage.png)