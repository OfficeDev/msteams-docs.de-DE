---
title: Tools und SDKs
author: surbhigupta
description: In diesem Artikel lernen Sie Tools und SDKs zum Erstellen Microsoft Teams Bots und Bots mit dem Microsoft Bot Framework kennen.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 0b344b6a2db0abc4d1769c47aca6f496f69b98d7
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142465"
---
# <a name="bots-and-sdks"></a>Tools und SDKs

Mit den folgenden Tools oder Funktionen können Sie einen Bot für die Verwendung in Microsoft Teams erstellen:

* [Microsoft Bot Framework SDK](#bots-with-the-microsoft-bot-framework)
* [Power Virtual Agents](#bots-with-power-virtual-agents)
* [Virtual Assistant](~/samples/virtual-assistant.md)
* [Webhooks und Connectors](#bots-with-webhooks-and-connectors)
* [Azure Bot-Dienst](#azure-bot-service)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots mit Microsoft Bot Framework

Ihr Teams-Bot besteht aus folgenden Komponenten:

* Einem öffentlich zugänglichen von Ihnen gehosteten Webdienst.
* Eine Microsoft Bot Framework-Registrierung für Ihren Webdienst.
* Ihrem Teams App-Paket, das den Teams-Client mit Ihrem Webdienst verbindet.

> [!TIP]
> Verwenden Sie das Entwicklerportal, um Ihren Webdienst bei Microsoft Bot Framework zu registrieren und Ihre App-Konfigurationen anzugeben. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md).

[Microsoft Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zur Erstellung von Bots mit C#, Java, Python und JavaScript. Wenn Sie bereits über einen Bot verfügen, der auf Microsoft Bot Framework basiert, können Sie ihn mühelos zur Verwendung in Microsoft Teams ändern. Microsoft empfiehlt die Verwendung von C# oder Node.js, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools) nutzen zu können. Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs folgendermaßen:

* Sie können spezielle Kartentypen wie die Office 365-Connector-Karte verwenden.
* Sie können Teams-spezifische Kanaldaten zu Aktivitäten festlegen.
* Sie können Nachrichtenerweiterungsanforderungen verarbeiten.

> [!IMPORTANT]
> Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und die [Microsoft Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen in allen Fällen die Tokenverarbeitung vornehmen.

## <a name="bots-with-power-virtual-agents"></a>Bots mit Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Chatbotdienst, der auf Microsoft Power Platform und Microsoft Bot Framework aufbaut. Der Power Virtual Agent-Entwicklungsprozess verwendet einen geführten Ansatz ohne Code mit einer grafischen Schnittstelle, um Ihre Teammitglieder in die Lage zu versetzen, mühelos einen intelligenten virtuellen Agent zu erstellen und zu pflegen. Sobald Sie Ihr Chatbot im [Power Virtual Agents-Portal](https://powervirtualagents.microsoft.com) erstellt haben, können Sie ihn mühelos [in Microsoft Teams integrieren](how-to/add-power-virtual-agents-bot-to-teams.md). Weitere Informationen zu den ersten Schritten finden Sie in der [Power Virtual Agents-Dokumentation](/power-virtual-agents).

>[!NOTE]
>Sie dürfen mit Microsoft Power Platform erstellte Apps nicht im Teams App Store veröffentlichen. Microsoft Power Platform-Apps können nur im App Store einer Organisation veröffentlicht werden.

## <a name="bots-with-webhooks-and-connectors"></a>Bots mit Webhooks und Connectors

Webhooks und Connectors verbinden Ihren Bot mit Ihren Webdiensten. Mit Webhooks und Connectors können Sie einen Bot für grundlegende Interaktionen erstellen, wie das Erstellen eines Workflows oder andere einfache Befehle. Sie sind nur in dem Team verfügbar, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Unter [Was sind Webhooks und Connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) finden Sie weitere Informationen.

## <a name="azure-bot-service"></a>Azure Bot-Dienst

Der Azure-Bot-Dienst bietet zusammen mit dem Bot Framework Tools zum Erstellen, Testen, Bereitstellen und Verwalten intelligenter Bots an einem zentralen Ort. Sie können Ihren Bot auch im Azure-Bot-Dienst erstellen.

> [!IMPORTANT]
> Bot-Anwendungen in Microsoft Teams sind in GCC-High über [Azure Bot Service](/azure/bot-service/channel-connect-teams) verfügbar.

> [!NOTE]
> * Bots in GCCH unterstützen nur bis zur Manifestversion v1.10.
> * Bild-URLs in adaptiven Karten werden in der GCCH-Umgebung nicht unterstützt. Sie können eine Bild-URL durch Base64-codierten DataUri ersetzen.
> * Bei der Registrierung des Botkanals in Azure Government werden Web-App-Bots, App-Dienste (App-Serviceplan) und Anwendungserkenntnisse bereitgestellt, die Bereitstellung des Azure-Bot-Diensts wird jedoch nicht unterstützt (kein App-Dienst).
>   <details>
>   <summary><b>Wenn Sie nur eine Bot-Registrierung durchführen möchten</b></summary>
>
>   * Wechseln Sie zur Ressourcengruppe, und löschen Sie die nicht verwendeten Ressourcen manuell. Beispielsweise der App-Dienst, der App-Serviceplan (wenn Sie während der Bot-Registrierung erstellt haben) und die Anwendungserkenntnisse (wenn Sie ihn während der Bot-Registrierung aktivieren).
>   * Sie können az-cli auch für die Bot-Registrierung verwenden:
>
>     1. Melden Sie sich bei Azure an, und legen Sie das Abonnement fest. <br> 
>           &nbsp; az cloud set –name "AzureUSGovernment" <br> 
>           &nbsp; az account set –name "`subscriptionname/id`".<br>
>     1. Erstellen einer App-Registrierung  
>           &nbsp; az ad app create --display-name "`name`" <br> 
>           &nbsp; --password "`password`" --available-to-other-tenants.<br> 
>           Ihre App-ID würde hier erstellt.<br>
>     1. Erstellen einer Botressource <br>
>           &nbsp; az bot create –resource-group "`resource-group`"<br>
>           &nbsp; --appid "`appid`"<br>
>           &nbsp; --name "`botid`"<br>
>           &nbsp; --Art "Registrierung".<br>
>
> </details>

Für die GCCH-Umgebung müssen Sie einen Bot über [Azure Government Portal](https://portal.azure.us) registrieren.

:::image type="content" source="../assets/videos/abs-bot.gif" alt-text="Azure Government Portal":::
<br>
<br>
Die folgenden Änderungen sind im Bot für GCC-High Umgebung erforderlich:
<br>
<br>
<details>
<summary><b>Konfigurationsänderungen</b></summary>

Wenn die Bot-Registrierung in Azure Government Portal erfolgt, müssen Sie die Bot-Konfigurationen aktualisieren, um eine Verbindung mit Azure-Govermnet-Instanzen herzustellen. Im Folgenden finden Sie die Konfigurationsdetails:

| Konfigurationsname | Value |
|----|----|
| ChannelService | `https://botframework.azure.us` |
| OAuthUrl | `https://tokengcch.botframework.azure.us` |
| ToChannelFromBotLoginUrl | `https://login.microsoftonline.us/MicrosoftServices.onmicrosoft.us` |
| ToChannelFromBotOAuthScope | `https://api.botframework.us` |
| ToBotFromChannelTokenIssuer | `https://api.botframework.us`  |
| BotOpenIdMetadata | `https://login.botframework.azure.us/v1/.well-known/openidconfiguration` |

</details>
<br>
<details>
<summary><b>Aktualisieren auf "appsettings.json" & "startup.cs"</b></summary>

1. **appsettings.json aktualisieren:**

    * Legen Sie `ConnectionName` auf den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem Bot hinzugefügt haben.

    * Legen Sie `MicrosoftAppId` und `MicrosoftAppPassword` auf die App-ID und den geheimen App-Schlüssel Ihres Bots fest.
    
    Abhängig von den Zeichen in Ihrem geheimen Botschlüssel müssen Sie das Kennwort möglicherweise mit XML-ESCAPEZEICHEN versehen. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als `&amp;`codiert werden.

    ```json
    {
      "MicrosoftAppType": "",
      "MicrosoftAppId": "",
      "MicrosoftAppPassword": "",
      "MicrosoftAppTenantId": "",
      "ConnectionName": ""
    }
    ```
2. **Startup.cs aktualisieren:**

    Um OAuth in *nicht öffentlichen Azure-Clouds* wie der Government Cloud oder in Bots mit Datenaufbewahrung zu verwenden, müssen Sie den folgenden Code in der Datei **"Startup.cs** " hinzufügen.
    
    ```csharp
    string uri = "<uri-to-use>";
    MicrosoftAppCredentials.TrustServiceUrl(uri);
    OAuthClientConfig.OAuthEndpoint = uri;
    ```
    
    Dabei \<uri-to-use\> ist eine der folgenden URIs:

    |**uri**|**Beschreibung**|
    |---|---|
    |`https://europe.api.botframework.com`|Für Public-Cloud-Bots mit Data Residency in Europa.|
    |`https://unitedstates.api.botframework.com`|Für Public-Cloud-Bots mit Datenaufbewahrung im USA.|
    |`https://apiGCCH.botframework.azure.us`|Für USA Government-Cloud-Bots ohne Datenaufbewahrung.|
    |`https://api.botframework.com`|Für Public-Cloud-Bots ohne Datenaufbewahrung. Dies ist der Standard-URI und erfordert keine Änderung an **Startup.cs**.|

3. Die Umleitungs-URL für die App-Registrierung von Azure sollte auf `https://tokengcch.botframework.azure.us/.auth/web/redirect`aktualisiert werden.

</details>

## <a name="advantages-of-bots"></a>Vorteile von Bots

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet für Ihren Unterhaltungs-Bot besondere Chancen und Herausforderungen.

| In einem Kanal | In einem Gruppenchat | In einem 1:1-Chat. |
| :-- | :-- | :-- |
| Massive Reichweite | Weniger Mitglieder | Traditionelle Art und Weise |
| Präzise individuelle Interaktionen | @erwähnen-Bot  | F&A-Bots |
| @erwähnen-Bot | Ähnlich wie Kanal | Bots, die Witze erzählen und Notizen machen |

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Unterhaltungsthreads zwischen mehreren Personen (bis zu 2.000). Dadurch erhält Ihr Bot potenziell eine enorme Reichweite, die einzelnen Interaktionen müssen aber präzise sein. Herkömmliche Multi-Turn-Interaktionen funktionieren nicht. Stattdessen müssen Sie versuchen, interaktive Karten oder Aufgabenmodule einzusetzen, oder die Unterhaltung in eine 1:1-Unterhaltung auszulagern, um viele Informationen zu sammeln. Ihr Bot hat nur Zugriff auf Nachrichten, in denen er sich befindet `@mentioned`. Mithilfe von Microsoft Graph und Berechtigungen auf Organisationsebene können Sie zusätzliche Nachrichten aus der Unterhaltung abrufen.

Bots funktionieren in einem Kanal in den folgenden Fällen besser:

* Benachrichtigungen, wenn Sie eine interaktive Karte für die Benutzer bereitstellen, die weitere Informationen aufnimmt.
* Feedbackszenarien wie Abstimmungen und Umfragen.
* Ein einzelner Anforderungs- oder Antwortzyklus löst Interaktionen auf, und die Ergebnisse sind für mehrere Mitglieder der Unterhaltung nützlich.
* Soziale/Spaß-Bots, bei denen Sie tolle Katzenbilder erhalten, zufällig einen Gewinner auswählen, usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threading zwischen drei oder mehr Personen. Sie weisen tendenziell weniger Mitglieder auf als ein Kanal und sind kurzlebiger. Ähnlich wie bei einem Kanal hat Ihr Bot nur Zugriff auf Nachrichten, in denen er sich direkt befindet `@mentioned` .

In den Fällen, in denen Bots in einem Kanal besser funktionieren, funktionieren auch in einem Gruppenchat besser.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat.

Ein 1:1-Chat ist ein herkömmliches Interaktionsverfahren eines Unterhaltungs-Bots mit einem Benutzer. Einige Beispiele für 1:1-Unterhaltungs-Bots sind:

* F&A-Bots
* Bots, die Workflows in anderen Systemen initiieren
* Bots, die Witze erzählen
* Bots, die Notizen erstellen. Bevor Sie einen 1:1-Chatbot erstellen, überprüfen Sie, ob eine unterhaltungsbasierte Oberfläche die beste Möglichkeit ist, Ihre Funktionalität darzustellen.

## <a name="disadvantages-of-bots"></a>Nachteile von Bots

Ein umfangreicher Dialog zwischen Ihrem Bot und dem Benutzer ist ein langsamer und übermäßig komplexer Weg, um eine Aufgabe zu erledigen. Ein Bot, der übermäßige Befehle unterstützt, insbesondere eine breite Palette von Befehlen, ist nicht erfolgreich oder wird von Benutzern nicht positiv gesehen.

### <a name="have-multi-turn-experiences-in-chat"></a>Komplexe Aufgaben im Chat

Ein umfangreiches Dialogfeld erfordert, dass der Entwickler den Status beibehält. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Timeout oder **"Abbrechen"** auswählen. Auch der Prozess ist mühsam. Sehen Sie sich beispielsweise das folgende Unterhaltungsszenario an:

BENUTZER: Plane eine Besprechung mit Marie.

BOT: Ich habe 200 Ergebnisse gefunden, bitte geben Sie einen Vor- und Nachnamen an.

BENUTZER: Plane eine Besprechung mit Marie Krause.

BOT: OK, Wann möchten Sie sich mit Marie Krause treffen?

BENUTZER: um 13:00 Uhr.

BOT: An welchem Tag?

### <a name="support-too-many-commands"></a>Unterstützung zu vieler Befehle

Da es im aktuellen Bot-Menü nur sechs sichtbare Befehle gibt, wird alles andere wahrscheinlich nicht häufig verwendet. Bots, die detailliert auf einen bestimmten Bereich eingehen, anstatt zu versuchen, ein allgemeiner Assistent zu sein, werden besser funktionieren und besser abschneiden.

### <a name="maintain-a-large-knowledge-base"></a>Verwalten eines großen Wissensdatenbank

Einer der Nachteile von Bots ist, dass es schwierig ist, einen großen Abruf Wissensdatenbank mit nicht gerankten Antworten zu verwalten. Bots sind am besten für kurze, schnelle Interaktionen geeignet, nicht für das Durchsuchen langer Listen auf der Suche nach einer Antwort.

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für Bot-Aktivitäten für einen Kanalteambereich:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var mention = new Mention
    {
        Mentioned = turnContext.Activity.From,
        Text = $"<at>{XmlConvert.EncodeName(turnContext.Activity.From.Name)}</at>",
    };

    var replyActivity = MessageFactory.Text($"Hello {mention.Text}.");
    replyActivity.Entities = new List<Entity> { mention };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}

```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

this.onMessage(async (turnContext, next) => {
    const mention = {
        mentioned: turnContext.activity.from,
        text: `<at>${ new TextEncoder().encode(turnContext.activity.from.name) }</at>`,
    } as Mention;

    const replyActivity = MessageFactory.text(`Hello ${mention.text}`);
    replyActivity.entities = [mention];

    await turnContext.sendActivity(replyActivity);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});

```

---

Der folgende Code enthält ein Beispiel für Bot-Aktivitäten für einen 1:1-Chat:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle message activity
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    turnContext.Activity.RemoveRecipientMention();
    var text = turnContext.Activity.Text.Trim().ToLower();
  await turnContext.SendActivityAsync(MessageFactory.Text($"Your message is {text}."), cancellationToken);
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
this.onMessage(async (context, next) => {
    await context.sendActivity(MessageFactory.text("Your message is:" + context.activity.text));
    await next();
});
```

---

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NETCore | Node.js | Python|
|----------------|-----------------|--------------|----------------|-------|
| Teams-Unterhaltungsbot | Verarbeitung von Nachrichten- und Unterhaltungsereignissen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
| Bot-Beispiele | Gruppe von Bot-Beispielen | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore) |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Aktivitätenhandler](~/bots/bot-basics.md)

## <a name="see-also"></a>Siehe auch

* [Bots für Anrufe und Besprechungen](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
* [Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
* [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)
* [Authentifizierungsfluss für Bots in Microsoft Teams](~/bots/how-to/authentication/auth-flow-bot.md)
* [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
