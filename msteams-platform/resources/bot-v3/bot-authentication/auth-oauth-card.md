---
title: Verwenden von Azure Bot Service für die Authentifizierung in Teams
description: Beschreibt den Azure Bot Service OAuthCard und seine Verwendung für die Authentifizierung
ms.topic: conceptual
localization_priority: Normal
keywords: Teams-Authentifizierung OAuthCard OAuth Card Azure Bot Service
ms.openlocfilehash: 3d0df4f04625c5be3468d12319b54096ae06de90
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020681"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a>Verwenden von Azure Bot Service für die Authentifizierung in Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Ohne die OAuthCard des Azure Bot Service ist es kompliziert, die Authentifizierung in einem Bot zu implementieren. Es handelt sich um eine Herausforderung mit vollem Stapel, die das Erstellen einer Weberfahrung, die Integration mit externen OAuth-Anbietern, die Tokenverwaltung und die Verarbeitung der richtigen Server-zu-Server-API-Aufrufe zum sicheren Abschließen des Authentifizierungsflusses erfordert. Dies kann zu unübersichtlichen Erfahrungen führen, bei denen die Eingabe von "magischen Zahlen" erforderlich ist.

Mit der OAuthCard von Azure Bot Service ist es für Ihren Teams einfacher, sich bei Ihren Benutzern zu registrieren und auf externe Datenanbieter zu zugreifen. Unabhängig davon, ob Sie die Authentifizierung bereits implementiert haben und zu einer einfacheren Lösung wechseln möchten oder wenn Sie ihren Botdienst zum ersten Mal Authentifizierung hinzufügen möchten, kann die OAuthCard dies vereinfachen.

In anderen Themen in [der](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) Authentifizierung wird die Authentifizierung ohne OAuthCard beschrieben. Wenn Sie also die Authentifizierung in Teams genauer verstehen möchten oder die OAuthCard nicht verwenden können, können Sie sich weiterhin auf diese Themen beziehen.

## <a name="support-for-the-oauthcard"></a>Unterstützung für OAuthCard

Es gibt derzeit einige Einschränkungen, wo Sie OAuthCard verwenden können. Zu diesen zählen:

* Die Karte funktioniert nicht mit [gastzugriff](/MicrosoftTeams/guest-access)
* Es funktioniert nicht mit [Microsoft Teams kostenlos](https://products.office.com/microsoft-teams/free)
* Es kann nur für die Botauthentifizierung verwendet werden
* Es funktioniert nur für Bots, die im [Azure Bot Service registriert sind.](https://azure.microsoft.com/services/bot-service/)

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a>Wie hilft mir der Azure Bot Service bei der Authentifizierung?

Vollständige Dokumentation mit der OAuthCard finden Sie im Thema: Hinzufügen der Authentifizierung [zu Ihrem Bot über Azure Bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0&preserve-view=true). Beachten Sie, dass sich dieses Thema im Azure Bot Framework-Dokumentationssatz befindet und nicht spezifisch für Teams.

In den folgenden Abschnitten wird die Verwendung der OAuthCard in Teams.

## <a name="main-benefits-for-teams-developers"></a>Hauptvorteile für Teams Entwickler

Die OAuthCard hilft bei der Authentifizierung auf folgende Weise:

* Stellt einen standardbasierten webbasierten Authentifizierungsfluss zur Verfügung: Sie müssen keine Webseite mehr schreiben und hosten, um an externe Anmeldeerfahrungen zu leiten oder eine Umleitung bereitstellen zu können.
* Ist nahtlos für Endbenutzer: Füllen Sie die vollständige Anmeldeerfahrung direkt innerhalb Teams.
* Umfasst eine einfache Tokenverwaltung: Sie müssen kein Tokenspeichersystem mehr implementieren– stattdessen übernimmt der Bot-Dienst die Zwischenspeicherung von Token und stellt einen sicheren Mechanismus zum Abrufen dieser Token zur Verfügung.
* Wird von vollständigen SDKs unterstützt: einfach zu integrieren und von Ihrem Botdienst zu nutzen.
* Verfügt über eine out-of-box-Unterstützung für viele beliebte OAuth-Anbieter, z. B. Azure AD/MSA, Facebook und Google.

## <a name="when-should-i-implement-my-own-solution"></a>Wann sollte ich meine eigene Lösung implementieren?

Da Zugriffstoken vertrauliche Informationen sind, möchten Sie sie möglicherweise nicht in einem externen Dienst speichern lassen. In diesem Fall können Sie ihr eigenes Tokenverwaltungssystem und die Anmeldeerfahrung weiterhin in Teams implementieren, wie in den restlichen Themen Teams [Authentifizierung](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) beschrieben.

## <a name="getting-started-with-oauthcard-in-teams"></a>Erste Schritte mit OAuthCard in Teams

> [!NOTE]
> In diesem Handbuch wird das Bot Framework v3 SDK verwendet. Die v4-Implementierung finden Sie [hier](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true). Sie müssen weiterhin ein Manifest erstellen und token.botframework.com in den Abschnitt hinzufügen, da andernfalls das Authentifizierungsfenster nicht mit der Schaltfläche Anmelden `validDomains` geöffnet wird. Verwenden Sie [das App Studio,](~/concepts/build-and-test/app-studio-overview.md) um Ihr Manifest zu generieren.

Sie müssen zunächst Ihren Azure-Botdienst konfigurieren, um externe Authentifizierungsanbieter einrichten zu können. Ausführliche [Schritte finden Sie unter](~/concepts/authentication/configure-identity-provider.md) Konfigurieren von Identitätsanbietern.

Um die Authentifizierung mithilfe des Azure Bot Service zu aktivieren, müssen Sie die folgenden Ergänzungen zu Ihrem Code erstellen:

1. Schließen token.botframework.com in den Abschnitt Ihres App-Manifests ein, da Teams die Anmeldeseite des `validDomains` Botdiensts einbetten wird.
2. Rufen Sie das Token aus dem Botdienst ab, wenn Ihr Bot auf authentifizierte Ressourcen zugreifen muss. Wenn kein Token verfügbar ist, senden Sie eine Nachricht mit einer OAuthCard an den Benutzer, der ihn anfordert, sich beim externen Dienst zu melden.
3. Behandeln Sie die Anmeldeabschlussaktivität. Dadurch wird sichergestellt, dass die Authentifizierungsanforderung und das Token dem Benutzer zugeordnet sind, der derzeit mit Ihrem Bot interagiert.
4. Rufen Sie das Token ab, wenn Ihr Bot authentifizierte Aktionen ausführen muss, z. B. das Aufrufen externer REST-APIs.

Im Dialogfeldcode müssen Sie diesen Codeausschnitt (C#) hinzufügen, der nach einem vorhandenen Zugriffstoken sucht:

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

Zum Verarbeiten der vollständigen Anmeldeaktivität müssen Sie diesen Aufruf verarbeiten:

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

In Ihrem Dialogfeldcode können Sie das Token dann vom Bot-Authentifizierungsdienst abrufen:

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

## <a name="using-oauthcard-with-messaging-extensions"></a>Verwenden von OAuthCard mit Messagingerweiterungen

Sie können azure bot Service auch verwenden, um Drittanbieter mit Ihrer Messagingerweiterung zu verbinden. Der Fluss ist mit einem Bot identisch, außer anstatt eine OAuthCard zurück zu geben, gibt Ihr Dienst eine Anmeldeaufforderung zurück.

Der folgende Codeausschnitt (C#) veranschaulicht das Erstellen der Anmeldeantwort:

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

Beachten Sie, dass Sie im obigen Beispiel den Aufruf direkt `GetSignInLinkAsync` für die Eigenschaft erstellen `client.OAuthApi` müssen.

Wenn der Benutzer die Anmeldesequenz erfolgreich abgeschlossen hat, erhält Ihr Dienst eine weitere Invoke-Anforderung, die die ursprüngliche Benutzerabfrage enthält, sowie eine State-Parameterzeichenfolge, die den "magischen Code" enthält. Sie können nun das Token mit dieser Zeichenfolge zusammen mit der Benutzer-ID und dem Verbindungsnamen abrufen.

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
