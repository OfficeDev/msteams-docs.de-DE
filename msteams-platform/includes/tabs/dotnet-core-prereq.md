## <a name="prerequisites"></a>Voraussetzungen

- Um diesen Schnellstart abzuschließen, benötigen Sie einen Microsoft 365-Mandanten und ein Team, das so konfiguriert ist, *dass das Hochladen benutzerdefinierter apps* aktiviert ist. Weitere Informationen finden Sie unter [Vorbereiten Ihres Microsoft 365-Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).
  - Wenn Sie derzeit kein Microsoft 365-Konto haben, können Sie sich über das [Microsoft-Entwicklerprogramm](https://developer.microsoft.com/en-us/microsoft-365/dev-program)für ein kostenloses Abonnement registrieren. Das Abonnement bleibt aktiv, solange Sie es für die laufende Entwicklung verwenden.

- Sie verwenden App Studio, um Ihre Anwendung in Microsoft Teams zu importieren. Um App Studio zu installieren, wählen Sie **apps** ![ Store ](~/assets/images/tab-images/storeApp.png) -app in der unteren linken Ecke der Teams-App aus, und suchen Sie nach App Studio. Nachdem Sie die Kachel gefunden haben, wählen Sie Sie aus, und wählen Sie im Dialogfeld Popupfenster installieren aus.

Dieses Projekt erfordert außerdem, dass in Ihrer Entwicklungsumgebung Folgendes installiert ist:

- Die aktuelle Version die Visual Studio-IDE mit installierter **.net-Kern plattformübergreifender Entwicklungs** Arbeitslast. Wenn Sie noch nicht über Visual Studio verfügen, können Sie die neueste [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) -Version kostenlos herunterladen und installieren.

- Das [ngrok](https://ngrok.com) -Reverseproxy-Tool. Sie verwenden ngrok, um einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers zu erstellen. Sie können [es hier herunterladen](https://ngrok.com/download).
