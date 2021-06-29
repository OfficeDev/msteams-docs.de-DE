## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Microsoft Teams ist ein cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind. Teams lässt kein lokales Hosting zu. Sie müssen Ihre Registerkarte entweder über eine öffentliche URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine internetbasierte URL verfügbar macht.

Verwenden Sie zum Testen Der Registerkarte [ngrok](https://ngrok.com/docs). Die Webendpunkte Ihres Servers sind verfügbar, während ngrok auf Ihrem Computer ausgeführt wird. In der kostenlosen Version von ngrok unterscheiden sich die URLs beim nächsten Start von ngrok, wenn Sie ngrok schließen.