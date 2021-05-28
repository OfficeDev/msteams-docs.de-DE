### <a name="optional-adjust-your-browser-launch-settings"></a><span data-ttu-id="3a2a8-101">(Optional) Anpassen der Einstellungen für den Browserstart</span><span class="sxs-lookup"><span data-stu-id="3a2a8-101">(Optional) Adjust your browser launch settings</span></span>

<span data-ttu-id="3a2a8-102">Wenn Sie eine Teams entwickeln, wird Ihre App häufig in einem alternativen Entwickler-Mandanten oder mit alternativen Anmeldeinformationen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-102">When developing a Teams app, it is common to run your app in an alternate developer tenant or with alternate credentials.</span></span>  <span data-ttu-id="3a2a8-103">Sowohl Microsoft Edge als auch Google Chrome bieten Möglichkeiten zum Anpassen der Starteinstellungen für Ihren Browser.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-103">Both Microsoft Edge and Google Chrome provide facilities to adjust the launch settings for your browser.</span></span>  <span data-ttu-id="3a2a8-104">Um das Projekt beispielsweise so zu aktualisieren, dass der InPrivate-Modus (Microsoft Edge) unterstützt wird, öffnen Sie die `.vscode/launch.json` Datei in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-104">For example, to update the project to support InPrivate mode (Microsoft Edge), open the `.vscode/launch.json` file in your project.</span></span>  <span data-ttu-id="3a2a8-105">Suchen Sie nach den entsprechenden Starteinstellungen, und fügen Sie jeweils den folgenden Block hinzu:</span><span class="sxs-lookup"><span data-stu-id="3a2a8-105">Look for the appropriate launch settings, and add the following block to each one:</span></span>

``` json
"runtimeArgs": [ "--inprivate" ]
```

<span data-ttu-id="3a2a8-106">Beispielsweise sieht die Starteinstellung für die lokale Ausführung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="3a2a8-106">For instance, the launch setting for running locally looks like this:</span></span>

``` json
{
   "name": "Start and Attach to Frontend (Edge)",
   "type": "pwa-msedge",
   "request": "launch",
   "url": "https://teams.microsoft.com/_#/l/app/${localTeamsAppId}?installAppPackage=true",
   "preLaunchTask": "Start Frontend",
   "postDebugTask": "Stop All Services",
   "presentation": {
         "group": "all",
         "hidden": true
   },
   "runtimeArgs": [ "--inprivate" ]
},
```

<span data-ttu-id="3a2a8-107">Alternativ können Sie Ihren Browser für die Verwendung des letzten bekannten Profils konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-107">Alternatively, you can configure your browser to use the last known profile.</span></span> <span data-ttu-id="3a2a8-108">[Erstellen Sie ein neues Profil](https://support.microsoft.com/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435) in Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-108">[Create a new profile](https://support.microsoft.com/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435) in Microsoft Edge.</span></span>  <span data-ttu-id="3a2a8-109">Passen Sie dann die Einstellungen an, um das letzte bekannte Profil für neue Links zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="3a2a8-109">Then adjust the settings to use the last known profile for new links:</span></span>

- <span data-ttu-id="3a2a8-110">Öffnen Microsoft Edge in der Datei `edge://settings/profiles/multiProfileSettings` .</span><span class="sxs-lookup"><span data-stu-id="3a2a8-110">In Microsoft Edge, open `edge://settings/profiles/multiProfileSettings`.</span></span>
- <span data-ttu-id="3a2a8-111">Automatisches **Profilschalten deaktivieren.**</span><span class="sxs-lookup"><span data-stu-id="3a2a8-111">Turn off **Automatic profile switching**.</span></span>
- <span data-ttu-id="3a2a8-112">Wählen Sie **für das Standardprofil für externe Links** die Option Zuletzt verwendet **(Standard) aus.**</span><span class="sxs-lookup"><span data-stu-id="3a2a8-112">For the **Default profile for external links**, select **Last used (default)**.</span></span>

<span data-ttu-id="3a2a8-113">Stellen Sie sicher, dass Ihr Browser für das richtige Profil geöffnet ist, bevor Sie Ihre App debuggen.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-113">Ensure your browser is opened to the correct profile before debugging your app.</span></span>
