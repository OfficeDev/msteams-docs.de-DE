---
title: Verwenden von Azure Bot Service für die Authentifizierung in Teams
description: Beschreibt die Azure Bot Service OAuthCard und ihre Verwendung für die Authentifizierung
ms.topic: conceptual
localization_priority: Normal
keywords: Teams-Authentifizierung OAuthCard OAuth-Karte Azure Bot Service
ms.openlocfilehash: 7731e4d1148e50c748d9c5e1b55371628a78dea7
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143165"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a>Verwenden von Azure Bot Service für die Authentifizierung in Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ohne die OAuthCard des Azure Bot Service ist es kompliziert, die Authentifizierung in einem Bot zu implementieren. Dies ist eine Herausforderung, die das Erstellen einer Weboberfläche, die Integration mit externen OAuth-Anbietern, die Tokenverwaltung und die Behandlung der richtigen Server-zu-Server-API-Aufrufe umfasst, um den Authentifizierungsfluss sicher abzuschließen. Dies kann zu klobigen Erfahrungen führen, die den Eintrag von "magischen Zahlen" erfordern.

Mit der OAuthCard von Azure Bot Service ist es für Ihren Teams Bot einfacher, sich bei Ihren Benutzern anzumelden und auf externe Datenanbieter zuzugreifen. Ganz gleich, ob Sie die Authentifizierung bereits implementiert haben und zu einem einfacheren Element wechseln möchten, oder wenn Sie ihrem Botdienst zum ersten Mal eine Authentifizierung hinzufügen möchten, kann die OAuthCard dies vereinfachen.

Andere Themen in der [Authentifizierung](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) beschreiben die Authentifizierung, ohne die OAuthCard zu verwenden. Wenn Sie also die Authentifizierung in Teams tiefer verstehen möchten oder wenn Sie die OAuthCard nicht verwenden können, können Sie dennoch auf diese Themen verweisen.

## <a name="support-for-the-oauthcard"></a>Unterstützung für die OAuthCard

Es gibt derzeit einige Einschränkungen, wo Sie die OAuthCard verwenden können. Zu diesen zählen:

* Die Karte funktioniert nicht mit [Gastzugriff](/MicrosoftTeams/guest-access).
* Es funktioniert nicht mit [Microsoft Teams kostenlos](https://products.office.com/microsoft-teams/free).
* Es kann nur für die Bot-Authentifizierung verwendet werden.
* Dies funktioniert nur für Bots, die im [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) registriert sind.

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a>Wie hilft mir das Azure Bot Service bei der Authentifizierung?

Die vollständige Dokumentation mithilfe der OAuthCard finden Sie im Thema: [Hinzufügen der Authentifizierung zu Ihrem Bot über Azure Bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0&preserve-view=true). Beachten Sie, dass dieses Thema im Azure Bot Framework-Dokumentationssatz enthalten ist und nicht spezifisch für Teams ist.

In den folgenden Abschnitten wird die Verwendung der OAuthCard in Teams beschrieben.

## <a name="main-benefits-for-teams-developers"></a>Hauptvorteile für Teams Entwickler

Die OAuthCard hilft bei der Authentifizierung auf folgende Weise:

* Bietet einen vordefinierten webbasierten Authentifizierungsfluss: Sie müssen keine Webseite mehr schreiben und hosten, um zu externen Anmeldeumgebungen zu gelangen oder eine Umleitung bereitzustellen.
* Ist für Endbenutzer nahtlos: Füllen Sie die vollständige Anmeldeerfahrung direkt innerhalb Teams aus.
* Umfasst eine einfache Tokenverwaltung: Sie müssen kein Tokenspeichersystem mehr implementieren– stattdessen kümmert sich die Bot Service um die Tokenzwischenspeicherung und bietet einen sicheren Mechanismus zum Abrufen dieser Token.
* Wird von vollständigen SDKs unterstützt: einfach zu integrieren und von Ihrem Bot-Dienst zu nutzen.
* Bietet out-of-box-Unterstützung für viele beliebte OAuth-Anbieter, z. B. Azure AD/MSA, Facebook und Google.

## <a name="when-should-i-implement-my-own-solution"></a>Wann sollte ich meine eigene Lösung implementieren?

Da Zugriffstoken vertrauliche Informationen sind, möchten Sie möglicherweise nicht, dass sie in einem externen Dienst gespeichert werden. In diesem Fall können Sie weiterhin Ihr eigenes Tokenverwaltungssystem und Ihre Anmeldeerfahrung innerhalb Teams implementieren, wie in den restlichen Themen zur Teams [Authentifizierung](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) beschrieben.

## <a name="getting-started-with-oauthcard-in-teams"></a>Erste Schritte mit OAuthCard in Teams

> [!NOTE]
> In diesem Handbuch wird das Bot Framework v3 SDK verwendet. Die v4-Implementierung finden Sie [hier](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true). Sie müssen weiterhin ein Manifest erstellen und token.botframework.com in den `validDomains` Abschnitt aufnehmen, da andernfalls das Authentifizierungsfenster nicht mit der Schaltfläche "Anmelden" geöffnet wird. Verwenden Sie [App Studio](~/concepts/build-and-test/app-studio-overview.md) , um Ihr Manifest zu generieren.

Sie müssen zuerst Ihren Azure-Botdienst konfigurieren, um externe Authentifizierungsanbieter einzurichten. Ausführliche Schritte [finden Sie unter Konfigurieren von Identitätsanbietern](~/concepts/authentication/configure-identity-provider.md) .

Um die Authentifizierung mithilfe der Azure Bot Service zu aktivieren, müssen Sie ihrem Code die folgenden Ergänzungen hinzufügen:

1. Fügen Sie token.botframework.com in den `validDomains` Abschnitt ihres App-Manifests ein, da Teams die Anmeldeseite des Bot Service einbettet.
2. Rufen Sie das Token aus dem Bot Service ab, wenn Ihr Bot auf authentifizierte Ressourcen zugreifen muss. Wenn kein Token verfügbar ist, senden Sie eine Nachricht mit einer OAuthCard an den Benutzer, der sie auffordert, sich beim externen Dienst anzumelden.
3. Behandeln Sie die Anmeldeabschlussaktivität. Dadurch wird sichergestellt, dass die Authentifizierungsanforderung und das Token dem Benutzer zugeordnet sind, der derzeit mit Ihrem Bot interagiert.
4. Rufen Sie das Token immer dann ab, wenn Ihr Bot authentifizierte Aktionen ausführen muss, z. B. das Aufrufen externer REST-APIs.

In Ihrem Dialogfeldcode müssen Sie diesen Codeausschnitt (C#) hinzufügen, der nach einem vorhandenen Zugriffstoken sucht:

```CSharp
// First ask Bot Service if it already has a token for this user
var token = await context.GetUserTokenAsync(ConnectionName).ConfigureAwait(false);
if (token != null)
{
    // use the token to do exciting things!
}
else
{
    // If Bot Service does not have a token, send an OAuth card to sign in 
    await SendOAuthCardAsync(context, (Activity)context.Activity);
}
```

Wenn kein Zugriffstoken vorhanden ist, sendet Ihr Code eine Nachricht mit einer OAuthCard an den Benutzer:

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

Um die Aktivität zum Abschließen der Anmeldung zu behandeln, müssen Sie diesen Aufruf verarbeiten:

```CSharp
if (activity.Name == "signin/verifyState")
{
  // We do this so that we can pass handling to the right logic in the dialog. You can
  // set this to be whatever string you want.
  activity.Text = "loginComplete";
  await Conversation.SendAsync(activity, () => new Dialogs.RootDialog());

  return Request.CreateResponse(HttpStatusCode.OK);
}
```

In Ihrem Dialogfeldcode können Sie dann das Token aus dem Bot-Authentifizierungsdienst abrufen:

```CSharp
if (text.Contains("loginComplete"))
  {
    // Handle login completion event.
    JObject ctx = activity.Value as JObject;

    if (ctx != null)
    {
      string code = ctx["state"].ToString();

      var oauthClient = activity.GetOAuthClient();
      var token = await oauthClient.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, magicCode: code).ConfigureAwait(false);
      if (token != null)
      {
        // Make whatever API calls here you want
        await context.PostAsync($"Success! You are now signed in.");
      }
    }
  // Need to respond to the Invoke.
  return;
}
```

## <a name="using-oauthcard-with-messaging-extensions"></a>Verwenden von OAuthCard mit Messaging-Erweiterungen

Sie können auch Azure Bot Service verwenden, um Drittanbieter mit Ihrer Messaging-Erweiterung zu verbinden. Der Fluss ist der gleiche wie bei einem Bot, außer dass Ihr Dienst keine OAuthCard zurückgibt, sondern eine Anmeldeaufforderung zurückgibt.

Der folgende Codeausschnitt (C#) veranschaulicht, wie die Anmeldeantwort erstellt wird:

```CSharp
var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName).ConfigureAwait(false);

if (token == null)
{
  // Send the login response with the auth link.
  string link = await client.OAuthApi.GetSignInLinkAsync(activity, ConnectionName);

  response = new ComposeExtensionResponse()
  {
    ComposeExtension = new ComposeExtensionResult()
  };
  response.ComposeExtension.Type = "auth";
  response.ComposeExtension.SuggestedActions = new ComposeExtensionSuggestedAction()
  {
    Actions = new List<CardAction>()
      {
        new CardAction(ActionTypes.OpenUrl, title: "Sign into this app", value: link)
      }
    };
  return response;
}
```

Beachten Sie, dass Sie im obigen Beispiel den Aufruf `GetSignInLinkAsync` direkt für die `client.OAuthApi` Eigenschaft ausführen müssen.

Wenn der Benutzer die Anmeldesequenz erfolgreich abgeschlossen hat, erhält Ihr Dienst eine weitere Invoke-Anforderung, die die ursprüngliche Benutzerabfrage enthält, zusammen mit einer Statusparameterzeichenfolge, die den "magischen Code" enthält. Sie können das Token jetzt mithilfe dieser Zeichenfolge zusammen mit der Benutzer-ID und dem Verbindungsnamen abrufen.

```CSharp
var query = activity.GetComposeExtensionQueryData();
JObject data = activity.Value as JObject;

var client = activity.GetOAuthClient();

// Check if the request comes with login state
if (data != null && data["state"] != null)
{
  var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, data["state"].ToString());

  // Do stuff with the token here.

}
```
