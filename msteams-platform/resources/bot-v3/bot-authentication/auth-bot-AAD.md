---
title: Authentifizierung für Bots mit Azure Active Directory
description: Beschreibt Azure AD Authentifizierung in Teams und wie sie in Ihren Bots verwendet wird
keywords: Teams-Authentifizierungs-Bots Azure AD
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: 7456580b3c0cd45ed9f2032e08068d542986cfea
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212398"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a>Authentifizieren eines Benutzers in einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Es gibt viele Dienste, die Sie in Ihrer Teams-App nutzen möchten, und die meisten dieser Dienste erfordern Authentifizierung und Autorisierung, um den Zugriff zu erhalten. Zu den Diensten gehören Facebook, Twitter und Teams. Benutzer von Teams verfügen über Benutzerprofilinformationen, die in Azure Active Directory unter Verwendung von Microsoft Graph gespeichert sind. In diesem Thema geht es um die Authentifizierung mithilfe von Azure AD, um Zugriff zu erhalten.
OAuth 2.0 ist ein offener Standard für die Authentifizierung, der von Azure AD und vielen anderen Dienstanbietern verwendet wird. Das Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams und Azure AD. In den folgenden Beispielen wird der Fluss "Implizite OAuth 2.0-Genehmigung" verwendet, um die Profilinformationen des Benutzers aus Azure AD und Microsoft Graph zu lesen.

Der in diesem Thema beschriebene Authentifizierungsfluss ähnelt den Registerkarten, mit der Ausnahme, dass Registerkarten den webbasierten Authentifizierungsfluss verwenden können und Bots die Authentifizierung aus Code gesteuert werden müssen. Die Konzepte in diesem Thema sind auch hilfreich bei der Implementierung der Authentifizierung über die mobile Plattform.

Eine allgemeine Übersicht über den Authentifizierungsfluss für Bots finden Sie im Thema [Authentifizierungsfluss in Bots.](~/resources/bot-v3/bot-authentication/auth-flow-bot.md)

## <a name="configuring-identity-providers"></a>Konfigurieren von Identitätsanbietern

Ausführliche Schritte zum Konfigurieren von OAuth 2.0-Rückrufumleitungs-URL(n) bei Verwendung von Azure Active Directory als Identitätsanbieter finden Sie im Thema ["Konfigurieren](~/concepts/authentication/configure-identity-provider.md) von Identitätsanbietern".

## <a name="initiate-authentication-flow"></a>Initiieren des Authentifizierungsflusses

Der Authentifizierungsfluss sollte durch eine Benutzeraktion ausgelöst werden. Öffnen Sie das Authentifizierungs-Popup nicht automatisch, da es möglicherweise den Popupblocker des Browsers auslöst und den Benutzer verwirren kann.

## <a name="add-ui-to-start-authentication"></a>Hinzufügen einer Benutzeroberfläche zum Starten der Authentifizierung

Fügen Sie dem Bot eine Benutzeroberfläche hinzu, damit sich der Benutzer bei Bedarf anmelden kann. Dies erfolgt über eine Miniaturansichtskarte in TypeScript:

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

Der Hero-Karte wurden drei Schaltflächen hinzugefügt: Anmelden, Profil anzeigen und Abmelden.

## <a name="sign-the-user-in"></a>Anmelden des Benutzers

Aufgrund der Überprüfung, die aus Sicherheitsgründen durchgeführt werden muss, und der Unterstützung für die mobilen Versionen von Teams wird der Code hier nicht angezeigt, aber [hier ist ein Beispiel für den Code, der den Prozess startet, wenn der Benutzer die Anmeldeschaltfläche drückt.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195)

Die Validierung und die mobile Unterstützung werden im Thema [Authentifizierungsfluss in Bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md)erläutert.

Fügen Sie dem Abschnitt des Manifests unbedingt die Domäne Ihrer Authentifizierungsumleitungs-URL [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) hinzu. Wenn Sie sich nicht anmelden, wird das Popup nicht angezeigt.

## <a name="showing-user-profile-information"></a>Anzeigen von Benutzerprofilinformationen

Obwohl das Abrufen eines Zugriffstokens aufgrund aller Übergänge zwischen verschiedenen Websites und der Sicherheitsprobleme, die behoben werden müssen, schwierig ist, nachdem Sie über ein Token verfügen, ist das Abrufen von Informationen von Azure Active Directory einfach. Der Bot ruft den `me` Graph Endpunkt mit dem Zugriffstoken auf. Graph antwortet mit den Benutzerinformationen für die Person, die sich angemeldet hat. Informationen aus der Antwort werden verwendet, um eine Botkarte zu erstellen und zu senden.

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

Wenn der Benutzer nicht angemeldet ist, wird er dazu aufgefordert.

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

## <a name="other-samples"></a>Andere Beispiele

Beispielcode für den Bot-Authentifizierungsprozess finden Sie unter:

* [Beispiel für Microsoft Teams Bot-Authentifizierung](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
