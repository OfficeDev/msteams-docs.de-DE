### <a name="optional-adjust-your-browser-launch-settings"></a>(Optional) Anpassen der Einstellungen für den Browserstart

Wenn Sie eine Teams entwickeln, wird Ihre App häufig in einem alternativen Entwickler-Mandanten oder mit alternativen Anmeldeinformationen ausgeführt.  Sowohl Microsoft Edge als auch Google Chrome bieten Möglichkeiten zum Anpassen der Starteinstellungen für Ihren Browser.  Um das Projekt beispielsweise so zu aktualisieren, dass der InPrivate-Modus (Microsoft Edge) unterstützt wird, öffnen Sie die `.vscode/launch.json` Datei in Ihrem Projekt.  Suchen Sie nach den entsprechenden Starteinstellungen, und fügen Sie jeweils den folgenden Block hinzu:

``` json
"runtimeArgs": [ "--inprivate" ]
```

Beispielsweise sieht die Starteinstellung für die lokale Ausführung wie dies aus:

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

Alternativ können Sie Ihren Browser für die Verwendung des letzten bekannten Profils konfigurieren. [Erstellen Sie ein neues Profil](https://support.microsoft.com/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435) in Microsoft Edge.  Passen Sie dann die Einstellungen an, um das letzte bekannte Profil für neue Links zu verwenden:

- Öffnen Microsoft Edge in der Datei `edge://settings/profiles/multiProfileSettings` .
- Automatisches **Profilschalten deaktivieren.**
- Wählen Sie **für das Standardprofil für externe Links** die Option Zuletzt verwendet **(Standard) aus.**

Stellen Sie sicher, dass Ihr Browser für das richtige Profil geöffnet ist, bevor Sie Ihre App debuggen.
