## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels für Ihre Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams lokales Hosting ist nicht zulässig. Sie müssen Ihre Registerkarte entweder in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet zugängliche URL verfügbar macht.

Zum Testen Ihrer Registerkarte verwenden Sie [ngrok](https://ngrok.com/docs). Die Webendpunkte Ihres Servers stehen zur Verfügung, während ngrok auf Ihrem lokalen Computer ausgeführt wird. Wenn Sie ngrok schließen, unterscheiden sich die URLs beim nächsten Starten.