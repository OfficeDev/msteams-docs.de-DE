## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels für die Registerkarte

Microsoft Teams ist ein vollständig Cloud-basiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. In Microsoft Teams wird kein lokales Hosting zugelassen. Sie müssen entweder Ihre Registerkarte in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet verbundene URL verfügbar macht.

Zum Testen der Registerkarte verwenden Sie [ngrok](https://ngrok.com/docs). Die Webendpunkte Ihres Servers sind verfügbar, während ngrok auf Ihrem lokalen Computer läuft. Wenn Sie ngrok schließen, sind die URLs unterschiedlich, wenn Sie das nächste Mal starten.