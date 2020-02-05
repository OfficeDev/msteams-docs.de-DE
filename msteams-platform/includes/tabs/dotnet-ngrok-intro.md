## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="71172-101">Einrichten eines sicheren Tunnels für die Registerkarte</span><span class="sxs-lookup"><span data-stu-id="71172-101">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="71172-102">Microsoft Teams ist ein vollständig Cloud-basiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="71172-102">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="71172-103">In Microsoft Teams wird kein lokales Hosting zugelassen.</span><span class="sxs-lookup"><span data-stu-id="71172-103">Teams doesn't allow local hosting.</span></span> <span data-ttu-id="71172-104">Sie müssen entweder Ihre Registerkarte in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet verbundene URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="71172-104">You'll need to either publish your tab to a public URL, or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="71172-105">Zum Testen der Registerkarte verwenden Sie [ngrok](https://ngrok.com/docs).</span><span class="sxs-lookup"><span data-stu-id="71172-105">To test your tab you'll use [ngrok](https://ngrok.com/docs).</span></span> <span data-ttu-id="71172-106">Die Webendpunkte Ihres Servers sind verfügbar, während ngrok auf Ihrem lokalen Computer läuft.</span><span class="sxs-lookup"><span data-stu-id="71172-106">Your server's web endpoints will be available while ngrok is running on your local machine.</span></span> <span data-ttu-id="71172-107">Wenn Sie ngrok schließen, sind die URLs unterschiedlich, wenn Sie das nächste Mal starten.</span><span class="sxs-lookup"><span data-stu-id="71172-107">If you close ngrok, the URLs will be different the next time you start it.</span></span>