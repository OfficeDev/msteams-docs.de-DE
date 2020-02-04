---
title: Verwenden des Azure bot-Diensts für die Authentifizierung in Microsoft Teams
description: Beschreibt den Azure bot-Dienst OAuthCard und wie er für die Authentifizierung verwendet wird
keywords: Microsoft Teams-Authentifizierung OAuthCard OAuth Card Azure bot Service
ms.openlocfilehash: 0397c45b39470d97c1158b2681462038de618a39
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674388"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a>Verwenden des Azure bot-Diensts für die Authentifizierung in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ohne den OAuthCard des Azure bot-Diensts ist es kompliziert, die Authentifizierung in einem bot zu implementieren. Es handelt sich um eine Full-Stack-Herausforderung, die das Erstellen einer Weberfahrung, die Integration mit externen OAuth-Anbietern, die Tokenverwaltung und das Behandeln der richtigen Server-zu-Server-API-Aufrufe zum Sicherstellen des vollständigen Authentifizierungs Flusses umfasst. Dies kann zu klobigen Erfahrungen führen, die die Eingabe von "Magic Numbers" erfordern.

Mit dem OAuthCard des Azure bot-Diensts ist es für Ihre Teams einfacher, sich bei ihren Benutzern anzumelden und auf externe Datenanbieter zuzugreifen. Unabhängig davon, ob Sie die Authentifizierung bereits implementiert haben und auf eine einfachere Funktion umstellen möchten, oder wenn Sie das erste Mal die Authentifizierung zu Ihrem bot-Dienst hinzufügen möchten, können Sie das OAuthCard vereinfachen.

In anderen Themen in der [Authentifizierung](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) wird die Authentifizierung ohne Verwendung des OAuthCard beschrieben, wenn Sie also die Authentifizierung in Microsoft Teams genauer verstehen möchten oder eine Situation haben, in der Sie die OAuthCard nicht verwenden können, können Sie sich trotzdem auf diese Themen berufen.

## <a name="support-for-the-oauthcard"></a>Unterstützung für die OAuthCard

Es gibt derzeit einige Einschränkungen, wo Sie die OAuthCard verwenden können. Zu diesen zählen:

* Die Karte kann nicht mit [Gastzugriff](/MicrosoftTeams/guest-access) verwendet werden
* Es kann nicht mit [Microsoft Teams kostenlos](https://products.office.com/microsoft-teams/free) verwendet werden
* Sie kann nur für die bot-Authentifizierung verwendet werden.
* Es funktioniert nur für Bots, die im [Azure bot-Dienst](https://azure.microsoft.com/services/bot-service/) registriert sind.

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a>Wie hilft mir der Azure bot-Dienst bei der Authentifizierung?

Eine vollständige Dokumentation mit OAuthCard steht im Thema: [Add Authentication to your bot via Azure bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0)zur Verfügung. Beachten Sie, dass dieses Thema in der Azure bot Framework-Dokumentationsgruppe liegt und nicht für Teams spezifisch ist.

In den folgenden Abschnitten erfahren Sie, wie Sie das OAuthCard in Microsoft Teams verwenden.

## <a name="main-benefits-for-teams-developers"></a>Hauptvorteile für Entwickler von Teams

Das OAuthCard hilft bei der Authentifizierung auf folgende Weise:

* Stellt einen Out-of-Box-webbasierten Authentifizierungs Fluss bereit: Sie müssen keine Webseite mehr schreiben und hosten, um an externe Anmeldeinformationen zu verweisen oder eine Umleitung bereitzustellen.
* Ist nahtlos für Endbenutzer: führen Sie das vollständige anmeldeerlebnis direkt in Microsoft Teams aus.
* Enthält einfache Tokenverwaltung: Sie müssen kein Tokenspeicher mehr implementieren – stattdessen übernimmt der bot-Dienst die Token-Zwischenspeicherung und stellt einen sicheren Mechanismus zum Abrufen dieser Token bereit.
* Wird von Complete SDKs unterstützt: einfach zu integrieren und von Ihrem bot-Dienst zu nutzen.
* Verfügt über eine Out-of-Box-Unterstützung für viele beliebte OAuth-Anbieter wie Azure AD/MSA, Facebook und Google.

## <a name="when-should-i-implement-my-own-solution"></a>Wann sollte ich eine eigene Lösung implementieren?

Da es sich bei Zugriffstoken um vertrauliche Informationen handelt, möchten Sie möglicherweise nicht, dass Sie in einem externen Dienst gespeichert werden. In diesem Fall können Sie sich entscheiden, weiterhin Ihr eigenes Token-Verwaltungssystem und ihre Anmelde Erfahrung in Microsoft Teams zu implementieren, wie in den restlichen Teams- [Authentifizierungs](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) Themen beschrieben.

## <a name="getting-started-with-oauthcard-in-teams"></a>Erste Schritte mit OAuthCard in Microsoft Teams

> [!NOTE]
> In diesem Leitfaden wird das bot Framework V3 SDK verwendet. Sie können die V4-Implementierung [hier](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp)finden. Sie müssen dennoch ein Manifest erstellen und Token.botframework.com in den `validDomains` Abschnitt einbeziehen, da andernfalls die Schaltfläche Anmelden das Authentifizierungsfenster nicht öffnet. Verwenden Sie das [App Studio](~/concepts/build-and-test/app-studio-overview.md) , um Ihr Manifest zu generieren.

Zunächst müssen Sie Ihren Azure bot-Dienst konfigurieren, um externe Authentifizierungsanbieter einzurichten. Lesen Sie [Konfigurieren von Identitätsanbietern](~/concepts/authentication/configure-identity-provider.md) für detaillierte Schritte.

Um die Authentifizierung mit dem Azure bot-Dienst zu aktivieren, müssen Sie diese Ergänzungen an Ihrem Code vornehmen:

1. Schließen Sie Token.botframework.com in `validDomains` den Abschnitt des App-Manifests ein, da Microsoft Teams die Anmeldeseite des bot-Diensts einbetten wird.
2. Holen Sie das Token aus dem bot-Dienst, wenn Ihr bot Zugriff auf authentifizierte Ressourcen benötigt. Wenn kein Token verfügbar ist, senden Sie eine Nachricht mit einem OAuthCard an den Benutzer, der Sie anfordert, sich beim externen Dienst anzumelden.
3. Behandeln Sie die Anmelde Abschlussaktivität. Dadurch wird sichergestellt, dass die Authentifizierungsanforderung und das Token dem Benutzer zugeordnet sind, der derzeit mit Ihrem bot interagiert.
4. Rufen Sie das Token ab, wenn Ihr bot authentifizierte Aktionen durchführen muss, beispielsweise das Aufrufen externer Rest-APIs.

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

Wenn kein Zugriffstoken vorhanden ist, sendet Ihr Code dann eine Nachricht mit einem OAuthCard an den Benutzer:

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

Um die vollständige Anmeldungs Aktivität zu verarbeiten, müssen Sie diesen Aufruf verarbeiten:

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

Im Dialogfeldcode können Sie das Token dann aus dem bot-Authentifizierungsdienst abrufen:

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

## <a name="using-oauthcard-with-messaging-extensions"></a>Verwenden von OAuthCard mit Messaging Erweiterungen

Sie können auch den Azure bot-Dienst verwenden, um Drittanbieter mit Ihrer Messaging Erweiterung zu verbinden. Der Fluss ist identisch mit einem bot, es sei denn, es wird ein OAuthCard zurückgegeben, Ihr Dienst gibt eine Anmeldeaufforderung zurück.

Der folgende Codeausschnitt (C#) veranschaulicht, wie die Anmelde Antwort erstellt wird:

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

Beachten Sie, dass Sie im obigen Beispiel den Aufruf direkt für `GetSignInLinkAsync` die `client.OAuthApi` Eigenschaft vornehmen müssen.

Wenn der Benutzer die Anmeldesequenz erfolgreich abgeschlossen hat, erhält der Dienst eine weitere Invoke-Anforderung, die die ursprüngliche Benutzerabfrage enthält, zusammen mit einer Statusparameter Zeichenfolge, die den "Magic Code" enthält. Sie können nun das Token mit dieser Zeichenfolge zusammen mit der Benutzer-ID und dem Verbindungsnamen abrufen.

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
