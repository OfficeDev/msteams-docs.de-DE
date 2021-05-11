## <a name="create-the-app-package"></a>Erstellen des App-Pakets

Sie benötigen ein App-Paket, um Ihre Registerkarte in der Teams. Es ist ein ZIP-Ordner, der die folgenden erforderlichen Dateien enthält:

- Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.
- Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.
- Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.

Das Paket wird über eine gulp-Aufgabe erstellt, die die Datei manifest.jsüberprüft und den Ordner "ZIP" in `./package directory` generiert. Geben Sie in der Eingabeaufforderung die folgenden Eingabeaufforderungen ein:

```bash
gulp manifest
```

## <a name="build-your-application"></a>Erstellen Ihrer Anwendung

Der Buildbefehl überlagert Ihre Lösung in den *Ordner ./dist.* Geben Sie als Nächstes ein:

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a>Ausführen der Anwendung in localhost

Starten Sie einen lokalen Webserver, indem Sie Folgendes eingeben:

```bash
gulp serve
```

Geben `http://localhost:3007/<yourDefaultAppNameTab>/` Sie in Ihren Browser ein, und zeigen Sie die Homepage Ihrer Anwendung an:

![Screenshot der Startseite](~/assets/images/tab-images/homePage.png)