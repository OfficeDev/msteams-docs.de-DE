---
title: Authentifizierung für Bots mit Azure-Active Directory
description: Beschreibt Azure AD Authentifizierung in Microsoft Teams und deren Verwendung in ihren Bots
keywords: Teams Authentication Bots Aad
ms.date: 03/01/2018
ms.openlocfilehash: 268af02c51b21b65214bce4673b54ac564a125ae
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674387"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a>Authentifizieren eines Benutzers in einem Microsoft Teams-bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Es gibt viele Dienste, die Sie in Ihrer Teams-App möglicherweise nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um Zugriff auf den Dienst zu erhalten. Zu den Diensten gehören Facebook, Twitter und natürlich Teams. Benutzer von Teams haben Benutzerprofilinformationen, die in Azure Active Directory (Azure AD) mit Microsoft Graph gespeichert werden. Dieser Artikel konzentriert sich auf die Authentifizierung mit Azure AD, um Zugriff auf diese Informationen zu erhalten.

OAuth 2,0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird. Das Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung der Authentifizierung in Microsoft Teams und Azure AD. Die folgenden Beispiele verwenden den impliziten Grant-Fluss von OAuth 2,0 mit dem Ziel, die Profilinformationen des Benutzers schließlich aus Azure AD und Microsoft Graph zu lesen.

Der in diesem Artikel beschriebene Authentifizierungs Fluss ähnelt dem von Tabs, mit der Ausnahme, dass Registerkarten den webbasierten Authentifizierungs Fluss verwenden können, und Bots erfordern, dass die Authentifizierung von Code gesteuert wird. Die Konzepte in diesem Artikel sind auch hilfreich, wenn Sie die Authentifizierung von der mobilen Plattform implementieren.

Eine allgemeine Übersicht über den Authentifizierungsablauf für Bots finden Sie im Thema [Authentifizierungs Fluss in Bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

## <a name="configuring-identity-providers"></a>Konfigurieren von Identitätsanbietern

Lesen Sie das Thema [configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) for ausführliche steps on Configuring OAuth 2,0 Callback Redirect URL (s) bei Verwendung von Azure Active Directory als Identitätsanbieter.

## <a name="initiate-authentication-flow"></a>Initiieren des Authentifizierungs Flusses

Der Authentifizierungs Fluss sollte durch eine Benutzeraktion ausgelöst werden. Sie sollten das Authentifizierungs Popup nicht automatisch öffnen, da dies wahrscheinlich den Popupblocker des Browsers auslösen und den Benutzer verwirren kann.

## <a name="add-ui-to-start-authentication"></a>Hinzufügen einer Benutzeroberfläche zum Starten der Authentifizierung

Fügen Sie der bot-Benutzeroberfläche hinzu, um dem Benutzer die Anmeldung bei Bedarf zu ermöglichen. Hier erfolgt die Arbeit über eine Miniatur Ansichtskarte in einer Fingerabdruck Ansicht:

```typescript
// Show prompt of options
protected async promptForAction(session: builder.Session): Promise<void> {
    let msg = new builder.Message(session)
        .addAttachment(new builder.ThumbnailCard(session)
            .title(this.providerDisplayName)
            .buttons([
                 builder.CardAction.messageBack(session, "{}", "Sign in")
                     .text("SignIn")
                     .displayText("Sign in"),
                  builder.CardAction.messageBack(session, "{}", "Show profile")
                     .text("ShowProfile")
                     .displayText("Show profile"),
                  builder.CardAction.messageBack(session, "{}", "Sign out")
                     .text("SignOut")
                     .displayText("Sign out"),
            ]));
    session.send(msg);
}
```

Der Hero Card wurden drei Schaltflächen hinzugefügt: anmelden, Profil anzeigen und abmelden.

## <a name="sign-the-user-in"></a>Signieren des Benutzers in

Aufgrund der Überprüfung, die aus Sicherheitsgründen ausgeführt werden muss, und der Unterstützung für die mobilen Versionen von Teams wird der Code hier nicht gezeigt, aber [hier sehen Sie ein Beispiel für den Code, der den Prozess startet, wenn der Benutzer auf die Schaltfläche Anmelden klickt.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195).

Die Überprüfung und Mobile Unterstützung werden im Thema [Authentifizierungs Fluss in Bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md)erläutert.

Stellen Sie sicher, dass Sie die Domäne ihrer Authentifizierungs Umleitungs-URL dem [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) Abschnitt des Manifests hinzufügen. Wenn dies nicht der Fall ist, wird das Anmeldefenster nicht angezeigt.

## <a name="showing-user-profile-information"></a>Anzeigen von Benutzerprofilinformationen

Obwohl das Abrufen eines Zugriffstokens aufgrund aller Übergänge zwischen verschiedenen Websites und der Sicherheitsprobleme, die behoben werden müssen, schwierig ist, wenn Sie über ein Token verfügen, ist das Abrufen von Informationen aus Azure Active Directory einfach. Der bot führt einen Aufruf des `me` Graph-Endpunkts mit dem Zugriffstoken aus. Graph antwortet mit den Benutzerinformationen für die Person, die sich angemeldet hat. Informationen aus der Antwort werden verwendet, um eine bot-Karte zu erstellen und zu senden.

```typescript
// Show user profile
protected async showUserProfile(session: builder.Session): Promise<void> {
    let azureADApi = this.authProvider as AzureADv1Provider;
    let userToken = this.getUserToken(session);

    if (userToken) {
        let profile = await azureADApi.getProfileAsync(userToken.accessToken);
        let profileCard = new builder.ThumbnailCard()
            .title(profile.displayName)
            .subtitle(profile.mail)
            .text(`${profile.jobTitle}<br/> ${profile.officeLocation}`);
        session.send(new builder.Message().addAttachment(profileCard));
    } else {
        session.send("Please sign in to AzureAD so I can access your profile.");
    }

    await this.promptForAction(session);
}

// Helper function to make the Graph API call
public async getProfileAsync(accessToken: string): Promise<any> {
    let options = {
        url: "https://graph.microsoft.com/v1.0/me",
        json: true,
        headers: {
            "Authorization": `Bearer ${accessToken}`,
        },
    };
    return await request.get(options);
}
```

Wenn der Benutzer nicht angemeldet ist, werden Sie dazu aufgefordert.

## <a name="sign-the-user-out"></a>Den Benutzer abmelden

```typescript
// Handle user logout request
private async handleLogout(session: builder.Session): Promise<void> {
    if (!utils.getUserToken(session, this.providerName)) {
        session.send(`You're already signed out of ${this.providerDisplayName}.`);
    } else {
        utils.setUserToken(session, this.providerName, null);
        session.send(`You're now signed out of ${this.providerDisplayName}.`);
    }

    await this.promptForAction(session);
}
```

## <a name="other-samples"></a>Weitere Beispiele

Beispielcode zum Anzeigen des bot-Authentifizierungsprozesses finden Sie unter:

* [Beispiel für Microsoft Teams-bot-Authentifizierung](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
