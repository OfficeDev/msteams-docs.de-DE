## <a name="create-the-app-package"></a>Erstellen des App-Pakets

Sie benötigen ein App-Paket, um Ihre Registerkarte in Microsoft Teams zu testen. Es handelt sich um einen ZIP-Ordner, der die folgenden erforderlichen Dateien enthält:

- Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.
- Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.
- Eine **Manifest. JSON** -Datei, die die Attribute Ihrer APP angibt.

Das Paket wird über eine Schluck Aufgabe erstellt, mit der die Manifest. JSON-Datei überprüft und der ZIP-Ordner `./package directory`in generiert wird. Geben Sie an der Eingabeaufforderung Folgendes ein:

```bash
gulp manifest
```

## <a name="build-your-application"></a>Erstellen der Anwendung

Der Befehl Build stapelt die Lösung in den Ordner *./dist-Ordner.* . Geben Sie als nächstes Folgendes ein:

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a>Ausführen Ihrer Anwendung in localhost

Starten Sie einen lokalen Webserver, indem Sie Folgendes eingeben:

```bash
gulp serve
```

Geben `http://localhost:3007/<yourDefaultAppNameTab>/` Sie in Ihren Browser ein, und zeigen Sie die Startseite der Anwendung an:

![Screenshot der Startseite](~/assets/images/tab-images/homePage.png)