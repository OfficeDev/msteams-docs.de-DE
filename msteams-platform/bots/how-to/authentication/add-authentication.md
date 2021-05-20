---
title: Hinzufügen der Authentifizierung zu Ihrem Teams-Bot
author: clearab
description: So fügen Sie einem Bot in Microsoft Teams OAuth-Authentifizierung hinzu.
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 36cb6f3de6f97af1d01512175923b79f69f630ad
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566004"
---
# <a name="add-authentication-to-your-teams-bot"></a>Hinzufügen der Authentifizierung zu Ihrem Teams-Bot

Es kann vorkommen, dass Sie Bots in Microsoft Teams erstellen müssen, die im Namen des Benutzers auf Ressourcen zugreifen können, z. B. auf einen E-Mail-Dienst.

In diesem Artikel wird veranschaulicht, wie die Azure Bot Service v4 SDK-Authentifizierung basierend auf OAuth 2.0 verwendet wird. Dies erleichtert die Entwicklung eines Bots, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann. Entscheidend bei all dem ist die Verwendung von **Identitätsanbietern**, wie wir später sehen werden.

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

Unter [OAuth 2 Vereinfacht](https://aka.ms/oauth2-simplified) für ein grundlegendes Verständnis und [OAuth 2.0](https://oauth.net/2/) für die vollständige Spezifikation.

Weitere Informationen dazu, wie der Azure Bot Service die Authentifizierung verarbeitet, finden Sie unter [Benutzerauthentifizierung in einer Unterhaltung](https://aka.ms/azure-bot-authentication).

In diesem Artikel erhalten Sie Informationen zu folgenden Themen:

- **So erstellen Sie einen authentifizierungsfähigen Bot**. Sie verwenden [cs-auth-sample,][teams-auth-bot-cs] um Anmeldeinformationen für Benutzer anmeldungen und das Generieren des Authentifizierungstokens zu verarbeiten.
- **Bereitstellen des Bots in Azure und Zuordnen zu azureieren mit einem Identitätsanbieter**. Der Anbieter gibt ein Token basierend auf Benutzeranmeldeinformationen aus. Der Bot kann das Token für den Zugriff auf Ressourcen verwenden, z. B. auf einen E-Mail-Dienst, für den eine Authentifizierung erforderlich ist. Weitere Informationen finden [Sie unter Microsoft Teams Authentifizierungsablauf für Bots](auth-flow-bot.md).
- **Wie man den Bot in Microsoft Teams integriert.** Sobald der Bot integriert wurde, können Sie sich anmelden und Nachrichten mit ihm in einem Chat austauschen.

## <a name="prerequisites"></a>Voraussetzungen

- Kenntnisse der [Bot-Grundlagen][concept-basics], [Verwalten des Status][concept-state], der [Dialogbibliothek][concept-dialogs]und zum [Implementieren des sequenziellen Konversationsflusses][simple-dialog].
- Kenntnisse der Azure- und OAuth 2.0-Entwicklung.
- Die aktuellen Versionen von Visual Studio und Git.
- Azure-Konto. Bei Bedarf können Sie ein [kostenloses Azure-Konto](https://azure.microsoft.com/free/)erstellen.
- Das folgende Beispiel:

    | Beispiel | BotBuilder-Version | Veranschaulicht |
    |:---|:---:|:---|
    | **Bot-Authentifizierung** in [cs-auth-sample][teams-auth-bot-cs] | v4 | OAuthCard-Unterstützung |
    | **Bot-Authentifizierung** in [js-auth-sample][teams-auth-bot-js] | v4| OAuthCard-Unterstützung  |
    | **Bot-Authentifizierung** in [py-auth-sample][teams-auth-bot-py] | v4 | OAuthCard-Unterstützung |

## <a name="create-the-resource-group"></a>Erstellen der Ressourcengruppe

Die Ressourcengruppe und der Serviceplan sind nicht unbedingt erforderlich, können jedoch die von Ihnen erstellten Ressourcen bequem freigeben. Dies ist eine gute Praxis, um Ihre Ressourcen organisiert und überschaubar zu halten.

Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das Bot Framework zu erstellen. Stellen Sie zur Leistung sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.

1. Melden Sie sich in Ihrem Browser beim [**Azure-Portal**][azure-portal]an.
1. Wählen Sie im linken Navigationsbereich **Ressourcengruppen** aus.
1. Wählen Sie oben links im angezeigten Fenster die Registerkarte **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen. Sie werden aufgefordert, Folgendes bereitzustellen:
    1. **Abonnement**: Verwenden Sie Ihr vorhandenes Abonnement.
    1. **Ressourcengruppe**. Geben Sie den Namen für die Ressourcengruppe ein. Ein Beispiel könnte  *TeamsResourceGroup* sein. Denken Sie daran, dass der Name eindeutig sein muss.
    1. Wählen Sie im Dropdown-Menü **Region** *West US* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. Wählen Sie die Schaltfläche **Überprüfen und Erstellen aus.** Es sollte ein Banner mit der Aufschrift *Validation passed* angezeigt werden.
    1. Wählen Sie die Schaltfläche **Erstellen** aus. Das Erstellen der Ressourcengruppe kann einige Minuten dauern.

> [!TIP]
> Wie bei den Ressourcen, die Sie später in diesem Tutorial erstellen, ist es eine gute Idee, diese Ressourcengruppe an Ihr Dashboard anzuheften, um einfachen Zugriff zu erhalten. Wenn Sie dies wünschen, wählen Sie das Pin-Symbol &#128204; oben rechts im Armaturenbrett.

## <a name="create-the-service-plan"></a>Erstellen des Serviceplans

1. Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Ressource erstellen** aus.
1. Geben Sie im Suchfeld *App Service Plan* ein. Wählen Sie die **App Service Plan-Karte** aus den Suchergebnissen aus.
1. Wählen Sie **Erstellen** aus.
1. Sie werden aufgefordert, die folgenden Informationen anzugeben:
    1. **Abonnement**: Sie können ein vorhandenes Abonnement verwenden.
    1. **Ressourcengruppe**. Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.
    1. **Name**. Geben Sie den Namen für den Serviceplan ein. Ein Beispiel könnte  *TeamsServicePlan* sein. Denken Sie daran, dass der Name innerhalb der Gruppe eindeutig sein muss.
    1. **Betriebssystem**. Wählen Sie *Windows* oder Ihr entsprechendes Betriebssystem aus.
    1. **Region**. Wählen Sie *West US* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. **Preisstufe**. Stellen Sie sicher, dass *Standard S1* ausgewählt ist. Dies sollte der Standardwert sein.
    1. Wählen Sie die Schaltfläche **Überprüfen und Erstellen aus.** Es sollte ein Banner mit der Aufschrift *Validation passed* angezeigt werden.
    1. Wählen Sie **Erstellen** aus. Das Erstellen des App-Serviceplans kann einige Minuten dauern. Der Plan wird in der Ressourcengruppe aufgeführt.

## <a name="create-the-bot-channels-registration"></a>Erstellen der Registrierung der Bot-Kanäle

Der Bot-Channels-Registrierung registriert Ihren Web-Service als Bot mit dem Bot Framework, vorausgesetzt, Sie haben eine Microsoft App-ID und App-Passwort (Client-Geheim).

> [!IMPORTANT]
> Sie müssen Ihren Bot nur registrieren, wenn er nicht in Azure gehostet wird. Wenn Sie [einen Bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) über das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert. Wenn Sie Ihren Bot über [Bot Framework](https://dev.botframework.com/bots/new) oder [AppStudio](~/concepts/build-and-test/app-studio-overview.md) erstellt haben, ist Ihr Bot nicht in Azure registriert.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> Die Datenbankregistrierungsressource "Bot Channels" zeigt die **globale** Region an, auch wenn Sie West US ausgewählt haben. Dies entspricht dem erwarteten Verhalten.

Weitere Informationen finden Sie unter [Erstellen eines Bots für Teams](../create-a-bot-for-teams.md).

## <a name="create-the-identity-provider"></a>Erstellen des Identitätsanbieters

Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.
In diesem Verfahren verwenden Sie einen Azure AD-Anbieter. Andere von Azure AD unterstützte Identitätsanbieter können ebenfalls verwendet werden.

1. Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich **Azure Active Directory** aus.
    > [!TIP]
    > Sie müssen diese Azure AD-Ressource in einem Mandanten erstellen und registrieren, in dem Sie den von einer Anwendung angeforderten Berechtigungen delegieren können.
    > Anweisungen zum Erstellen eines Mandanten finden Sie [unter Zugriff auf das Portal und Erstellen eines Mandanten](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).
1. Wählen Sie im linken Bereich **App-Registrierungen** aus.
1. Wählen Sie im rechten Bereich die Registerkarte **Neue Registrierung** in der oberen linken Seite aus.
1. Sie werden aufgefordert, die folgenden Informationen anzugeben:
   1. **Name**. Geben Sie den Namen für die Anwendung ein. Ein Beispiel könnte  *BotTeamsIdentity* sein. Denken Sie daran, dass der Name eindeutig sein muss.
   1. Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus. Wählen Sie *Konten in einem beliebigen Organisationsverzeichnis (Jedes Azure AD-Verzeichnis - Multitenant) und persönlichen Microsoft-Konten (z. B. Skype, Xbox)* aus.
   1. Für den **Umleitungs-URI**:<br/>
       &#x2713;**Wählen** Sie Web aus . <br/>
       &#x2713; Legen Sie die URL auf `https://token.botframework.com/.auth/web/redirect` .
   1. Wählen Sie **Registrieren** aus.

1. Nach der Erstellung zeigt Azure die **Übersichtsseite** für die App an. Kopieren und speichern Sie die folgenden Informationen in eine Datei:

    1. Der **Anwendungs-ID-Wert (Client).** Sie verwenden diesen Wert später als *Client-ID,* wenn Sie diese Azure-Identitätsanwendung bei Ihrem Bot registrieren.
    1. Der **Verzeichnis-ID-Wert (Tenant).** Sie verwenden diesen Wert später auch als *Mandanten-ID,* um diese Azure-Identitätsanwendung bei Ihrem Bot zu registrieren.

1. Wählen Sie im linken Bereich **Zertifikate & Geheimnisse** aus, um einen geheimen Clientschlüssel für Ihre Anwendung zu erstellen.

   1. Wählen Sie unter **Clientgeheimnisse**&#x2795; **Geheimschlüssel für neue Clients** aus.
   1. Fügen Sie eine Beschreibung hinzu, um diesen Geheimschlüssel von anderen Personen zu identifizieren, die Sie möglicherweise für diese App erstellen müssen, z. B. *Bot-Identitäts-App in Teams*.
   1. Legen Sie **Abläuft** auf Ihre Auswahl.
   1. Klicken Sie auf **Hinzufügen**.
   1. Zeichnen Sie vor dem Verlassen dieser Seite **den geheimen** Wert auf. Sie verwenden diesen Wert später als _geheimen Clientwert,_ wenn Sie Ihre Azure AD-Anwendung bei Ihrem Bot registrieren.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Konfigurieren der Identitätsanbieterverbindung und Registrieren mit dem Bot

Hinweis: Es gibt zwei Optionen für Dienstanbieter hier:Azure AD V1 und Azure AD V2.  Die Unterschiede zwischen den beiden Anbietern sind [hier](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison)zusammengefasst, aber im Allgemeinen bietet V2 mehr Flexibilität in Bezug auf das Ändern von Bot-Berechtigungen.  Graph API-Berechtigungen werden im Feld "Bereiche" aufgeführt, und wenn neue hinzugefügt werden, ermöglichen Bots Benutzern die Zustimmung zu den neuen Berechtigungen für die nächste Anmeldung.  Für V1 muss die Bot-Zustimmung vom Benutzer gelöscht werden, damit neue Berechtigungen im OAuth-Dialog feldaufgefordert werden. 

#### <a name="azure-ad-v1"></a>Azure AD V1

1. Wählen Sie im [**Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie Ihren Link zur Registrierung des Bot-Kanals aus.
1. Öffnen Sie die Ressourcenseite, und wählen Sie **Konfiguration** unter **Einstellungen** aus. 
1. Wählen Sie **OAuth-Verbindung Einstellungen hinzufügen** aus.    
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:  
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)
1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei. Zum Beispiel *BotTeamsAuthADv1*.
    1. **Dienstanbieter**. Wählen Sie **Azure Active Directory** aus. Sobald Sie dies ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure-Identitätsanbieter-App aufgezeichnet haben.
    1. **Geheimer Clientschlüssel**. Geben Sie den Geheimschlüssel, den Sie für Ihre Azure-Identitätsanbieter-App aufgezeichnet haben, in den obigen Schritten ein.
    1. **Grant-Typ**. Geben Sie `authorization_code` ein.
    1. **Login-URL**. Geben Sie `https://login.microsoftonline.com` ein.
    1. **Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure-Identitäts-App oder **allgemein** aufgezeichnet haben, abhängig vom unterstützten Kontotyp, der beim Erstellen der Identitätsanbieter-App ausgewählt wurde. Um zu entscheiden, welchen Wert zugewiesen werden soll, folgen Sie den folgenden Kriterien:

        - Wenn Sie *entweder Konten nur in diesem Organisationsverzeichnis (nur Microsoft - Einzelmandant)* oder *Konten in einem beliebigen Organisationsverzeichnis (Microsoft AAD-Verzeichnis - Multi-Mandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die AAD-App aufgezeichnet haben. Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie Konten in einem beliebigen Organisationsverzeichnis ausgewählt haben *(Any AAD-Verzeichnis - Multi-Mandanten- und persönliche Microsoft-Konten, z. B. Skype, Xbox, Outlook),* geben Sie das **gemeinsame** Wort anstelle einer Mandanten-ID ein. Andernfalls überprüft die AAD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    h. Geben Sie für **Ressourcen-URL** `https://graph.microsoft.com/` ein. Dies wird im aktuellen Codebeispiel nicht verwendet.  
    i. Lassen Sie **die Bereiche** leer. Das folgende Bild ist ein Beispiel:

    ![Teams Bots App auth Verbindung String adv1 Ansicht](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. Klicken Sie auf **Speichern**.

#### <a name="azure-ad-v2"></a>Azure AD V2

1. Wählen Sie im [**Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie Ihren Link zur Registrierung des Bot-Kanals aus.
1. Öffnen Sie die Ressourcenseite, und wählen Sie **Konfiguration** unter **Einstellungen** aus. 
1. Wählen Sie **OAuth-Verbindung Einstellungen hinzufügen** aus.  
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:        
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png) 

1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei. Zum Beispiel *BotTeamsAuthADv2*.
    1. **Dienstanbieter**. Wählen Sie **Azure Active Directory v2**. Sobald Sie dies ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure-Identitätsanbieter-App aufgezeichnet haben.
    1. **Geheimer Clientschlüssel**. Geben Sie den Geheimschlüssel, den Sie für Ihre Azure-Identitätsanbieter-App aufgezeichnet haben, in den obigen Schritten ein.
    1. **Token Exchange URL**. Lassen Sie dieses Feld leer.
    1. **Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure-Identitäts-App oder **allgemein** aufgezeichnet haben, abhängig vom unterstützten Kontotyp, der beim Erstellen der Identitätsanbieter-App ausgewählt wurde. Um zu entscheiden, welchen Wert zugewiesen werden soll, folgen Sie den folgenden Kriterien:

        - Wenn Sie *entweder Konten nur in diesem Organisationsverzeichnis (nur Microsoft - Einzelmandant)* oder *Konten in einem beliebigen Organisationsverzeichnis (Microsoft AAD-Verzeichnis - Multi-Mandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die AAD-App aufgezeichnet haben. Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie Konten in einem beliebigen Organisationsverzeichnis ausgewählt haben *(Any AAD-Verzeichnis - Multi-Mandanten- und persönliche Microsoft-Konten, z. B. Skype, Xbox, Outlook),* geben Sie das **gemeinsame** Wort anstelle einer Mandanten-ID ein. Andernfalls überprüft die AAD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    1. Geben Sie für **Scopes** eine durch Leerzeichen getrennte Liste von Graphenberechtigungen ein, die für diese Anwendung erforderlich sind, z. B.: User.Read User.ReadBasic.All Mail.Read 

1. Klicken Sie auf **Speichern**.

### <a name="test-the-connection"></a>Testen der Verbindung

1. Wählen Sie den Verbindungseintrag aus, um die gerade erstellte Verbindung zu öffnen.
1. Wählen Sie Oben im Bedienfeld **"Verbindungseinstellung des Dienstanbieters"** **die Option Verbindung testen** aus.
1. Wenn Sie dies zum ersten Mal tun, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen. Wählen Sie diejenige aus, die Sie verwenden möchten.
1. Als Nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu gestatten. Das folgende Bild ist ein Beispiel:

    ![Teams Bot auth-Verbindungszeichenfolge adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. Wählen Sie **Annehmen** aus.
1. Dies sollte Sie dann zu einer **Testverbindung zu \<your-connection-name> Erfolgreich** umleiten. Aktualisieren Sie die Seite, wenn eine Fehlermeldung angezeigt wird. Das folgende Bild ist ein Beispiel:

    ![Teams Bots App auth Verbindung str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

Der Verbindungsname wird vom Botcode zum Abrufen von Benutzerauthentifizierungstoken verwendet.

## <a name="prepare-the-bot-sample-code"></a>Vorbereiten des Bot-Beispielcodes

Nachdem die vorläufigen Einstellungen abgeschlossen sind, konzentrieren wir uns auf die Erstellung des Bots, der in diesem Artikel verwendet werden soll.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. [Klonen cs-auth-sample][teams-auth-bot-cs].
1. Starten Sie Visual Studio.
1. Wählen Sie in der Symbolleiste **File -> Open -> Project/Solution** aus und öffnen Sie das Bot-Projekt.
1. In derappsettings.jswie folgt auf der **appsettings.js:**

    - Legen Sie `ConnectionName` den Namen der Identitätsanbieterverbindung fest, die Sie der Registrierung des Botkanals hinzugefügt haben. Der Name, den wir in diesem Beispiel verwendet haben, ist *BotTeamsAuthADv1*.
    - Legen Sie `MicrosoftAppId` die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.
    - Legen Sie `MicrosoftAppPassword` den **Kundenschlüssel** fest, den Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.

    Abhängig von den Zeichen in Ihrem Bot-Geheimnis müssen Sie möglicherweise XML-Escape des Kennworts. Beispielsweise müssen alle von & als codiert `&amp;` werden.

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner, öffnen `manifest.json` und setzen Sie und zur `id` `botId` **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Klonen von [node-auth-sample][teams-auth-bot-js].
1. Navigieren Sie in einer Konsole zum Projekt: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Installieren von Modulen</br></br>
`npm install`
1. Aktualisieren Sie die **.env-Konfiguration** wie folgt:

    - Legen Sie `MicrosoftAppId` die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.
    - Legen Sie `MicrosoftAppPassword` den **Kundenschlüssel** fest, den Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.
    - Legen Sie den `connectionName` Namen der Identitätsanbieterverbindung fest.
    Abhängig von den Zeichen in Ihrem Bot-Geheimnis müssen Sie möglicherweise XML-Escape des Kennworts. Beispielsweise müssen alle von & als codiert `&amp;` werden.

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Öffnen und legen Sie im `teamsAppManifest` Ordner Ihre Microsoft App `manifest.json` `id` **ID** und `botId` die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.

# <a name="python"></a>[Python](#tab/python)

1. Klonen Sie [py-auth-sample][teams-auth-bot-py] aus dem github-Repository.
1. **Update config.py**:

    - Legen Sie `ConnectionName` den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem Bot hinzugefügt haben.
    - Legen Sie `MicrosoftAppId` die `MicrosoftAppPassword` App-ID und den App-Geheimnis Ihres Bots fest.

      Abhängig von den Zeichen in Ihrem Bot-Geheimnis müssen Sie möglicherweise XML-Escape des Kennworts. Beispielsweise müssen alle von & als codiert `&amp;` werden.

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Bereitstellen des Bots in Azure

Um den Bot bereitzustellen, führen Sie die Schritte in der Anleitung [zum Bereitstellen des Bots in Azure](https://aka.ms/azure-bot-deployment-cli)aus.

Alternativ können Sie in Visual Studio die folgenden Schritte ausführen:

1. Wählen Sie im Visual Studio *Projektmappen-Explorer* den Projektnamen aus und halten Sie ihn mit der rechten Maustaste.
1. Wählen Sie im Dropdown-Menü **Publish** aus.
1. Wählen Sie im angezeigten Fenster den Link **Neu** aus.
1. Wählen Sie im Dialogfenster **App Service** auf der linken Seite und **Neu erstellen** auf der rechten Seite aus.
1. Wählen Sie die **Schaltfläche Veröffentlichen** aus.
1. Geben Sie im nächsten Dialogfenster die erforderlichen Informationen ein. Es folgt ein Beispiel:

    ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. Wählen Sie **Erstellen** aus.
1. Wenn die Bereitstellung erfolgreich abgeschlossen wird, sollten Sie sehen, dass sie in Visual Studio widergespiegelt wird. Darüber hinaus wird eine Seite in Ihrem Standardbrowser angezeigt, die besagt, dass *Ihr Bot bereit ist!*. Die URL ist ähnlich wie die folgende: `https://botteamsauth.azurewebsites.net/` . Speichern Sie es in einer Datei.
1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
1. Überprüfen Sie Ihre Ressourcengruppe, der Bot sollte zusammen mit den anderen Ressourcen aufgelistet werden. Das folgende Bild ist ein Beispiel:

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. Wählen Sie in der Ressourcengruppe den Registrierungsnamen des Botkanals (Link) aus.
1. Wählen Sie im linken Bereich **Einstellungen** aus.
1. Geben Sie im Feld **Messagingendpunkt** die oben erhaltene URL gefolgt von `api/messages` ein. Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages` .
1. Wählen Sie die **Schaltfläche Speichern** oben links aus.

## <a name="test-the-bot-using-the-emulator"></a>Testen des Bots mit dem Emulator

Wenn Sie dies noch nicht getan haben, installieren Sie die [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme). Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Damit die Bot-Beispiel-Anmeldung funktioniert, müssen Sie den Emulator konfigurieren.

### <a name="configure-the-emulator-for-authentication"></a>Konfigurieren des Emulators für die Authentifizierung

Wenn ein Bot eine Authentifizierung erfordert, müssen Sie den Emulator konfigurieren. So konfigurieren Sie:

1. Starten Sie den Emulator.
1. Wählen Sie im Emulator das Zahnradsymbol &#9881; unten links oder die Registerkarte **"Emulator Einstellungen"** oben rechts aus.
1. Aktivieren Sie das Kontrollkästchen unter Verwenden von **Authentifizierungstoken der Version 1.0**.
1. Geben Sie den lokalen Pfad zum **ngrok-Werkzeug** ein. *Siehe* Bot Framework Emulator / ngrok Tunneling Integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)). Weitere Toolinformationen finden Sie unter [ngrok](https://ngrok.com/).
1. Aktivieren Sie das Kontrollkästchen durch **Ausführen von ngrok, wenn der Emulator gestartet wird.**
1. Wählen Sie die **Schaltfläche Speichern** aus.

Wenn der Bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, die der Benutzer verwenden kann, um sich beim Authentifizierungsanbieter anzumelden.
Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den Bot. Danach kann der Bot im Namen des Benutzers handeln.

### <a name="test-the-bot-locally"></a>Testen Sie den Bot lokal

Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die eigentlichen Bot-Tests durchführen.  

1. Führen Sie das Bot-Sample lokal auf Ihrem Computer aus, z. B. über Visual Studio.
1. Starten Sie den Emulator.
1. Wählen Sie die Schaltfläche **Bot öffnen** aus.
1. Geben Sie in der **Bot-URL** die lokale URL des Bots ein. In der Regel `http://localhost:3978/api/messages` .
1. Geben Sie in der **Microsoft App ID** die App-ID des Bots aus `appsettings.json` ein.
1. Geben Sie im **Microsoft App-Kennwort** das App-Kennwort des Bots aus `appsettings.json` ein.
1. Wählen Sie **Verbinden aus.**
1. Nachdem der Bot betriebsbereit ist, geben Sie einen beliebigen Text ein, um die Anmeldekarte anzuzeigen.
1. Wählen Sie die Schaltfläche **Anmelden** aus.
1. Ein Popup-Dialogfeld wird angezeigt, um **die URL "Öffnen"** zu bestätigen. Dadurch kann der Benutzer des Bots (Sie) authentifiziert werden.  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie dazu aufgefordert werden, wählen Sie das Konto des entsprechenden Benutzers aus.
1. Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:
    1. **Verwenden des Anmeldeüberprüfungscodes**  
      &#x2713; Ein Fenster mit dem Validierungscode wird geöffnet.  
      &#x2713; Kopieren und geben Sie den Validierungscode in das Chatfeld ein, um die Anmeldung abzuschließen.
    1. **Verwenden von Authentifizierungstoken**.  
      &#x2713; Sie sind basierend auf Ihren Anmeldeinformationen angemeldet.

    Das folgende Bild ist ein Beispiel für die Bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:

    ![auth Bot-Login-Emulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. Wenn Sie **Ja** auswählen, wenn der Bot *fragt, ob Sie Ihr Token anzeigen möchten?*, erhalten Sie eine Antwort ähnlich der folgenden:

    ![Auth-Bot-Anmeldeemulator-Token](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. Geben Sie die **Abmeldung** in das Eingabe-Chat-Feld ein, um sich abzumelden. Dadurch wird das Benutzertoken freigegeben, und der Bot kann erst dann in Ihrem Namen handeln, wenn Sie sich erneut anmelden.

> [!NOTE]
> Die Bot-Authentifizierung erfordert die Verwendung des **Bot Connector-Dienstes**. Der Dienst greift auf die Bot-Kanäle Registrierungsinformationen für Ihren Bot zu.

## <a name="test-the-deployed-bot"></a>Testen des bereitgestellten Bots

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
1. Suchen Sie Ihre Ressourcengruppe.
1. Wählen Sie die Ressourcenverknüpfung aus. Die Ressourcenseite wird angezeigt.
1. Wählen Sie auf der Ressourcenseite **Test in Web Chat** aus. Der Bot startet und zeigt die vordefinierten Grüße an.
1. Geben Sie etwas in die Chat-Box ein.
1. Wählen Sie das Feld **Anmelden** aus.
1. Ein Popup-Dialogfeld wird angezeigt, um **die URL "Öffnen"** zu bestätigen. Dadurch kann der Benutzer des Bots (Sie) authentifiziert werden.  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie dazu aufgefordert werden, wählen Sie das Konto des entsprechenden Benutzers aus.
    Das folgende Bild ist ein Beispiel für die Bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:

    ![auth bot login bereitgestellt](../../../assets/images/authentication/auth-bot-login-deployed.PNG).

1. Wählen Sie die **Schaltfläche Ja** aus, um Ihr Authentifizierungstoken anzuzeigen. Das folgende Bild ist ein Beispiel:

    ![Auth-Bot-Anmeldetoken](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG).

1. Melden Sie sich ab, um sich abzumelden.

    ![Auth Bot bereitgestelltlogout](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> Wenn Sie Probleme bei der Anmeldung haben, versuchen Sie, die Verbindung erneut zu testen, wie in den vorherigen Schritten beschrieben. Dadurch kann das Authentifizierungstoken neu erstellt werden.
> Beim Bot Framework Web Chat-Client in Azure müssen Sie sich möglicherweise mehrmals anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wird.

## <a name="install-and-test-the-bot-in-teams"></a>Installieren und testen Sie den Bot in Teams

1. Stellen Sie in Ihrem Bot-Projekt sicher, dass der `TeamsAppManifest` Ordner die `manifest.json` Zusammenmiten und `outline.png` Dateien `color.png` enthält.
1. Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner. Bearbeiten, `manifest.json` indem Sie die folgenden Werte zuweisen:
    1. Stellen Sie sicher, dass die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Bot-Kanals erhalten haben, und zugewiesen `id` `botId` ist.
    1. Weisen Sie diesen Wert zu: `validDomains: [ "token.botframework.com" ]` .
1. Wählen Sie die , und die Dateien aus, und **verpacken Sie** `manifest.json` `outline.png` `color.png` sie.
1. Öffnen **Sie Microsoft Teams**.
1. Wählen Sie im linken Bereich unten das **Apps-Symbol** aus.
1. Wählen Sie im rechten Bereich unten **Hochladen eine benutzerdefinierte App** aus.
1. Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.
Der folgende Assistent wird angezeigt:

    ![auth Bot-Teams hochladen](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.
1. Wählen Sie im nächsten Fenster das Team aus, in dem Sie den Bot verwenden möchten.
1. Wählen Sie die Schaltfläche **Bot einrichten** aus.
1. Wählen Sie die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) im linken Bereich aus. Wählen Sie dann das **App Studio-Symbol** aus.
1. Wählen Sie die Registerkarte **Manifest-Editor** aus. Sie sollten das Symbol für den Bot sehen, den Sie hochgeladen haben.
1. Außerdem sollten Sie in der Lage sein, den Bot als Kontakt in der Chat-Liste zu sehen, die Sie verwenden können, um Nachrichten mit dem Bot auszutauschen.

### <a name="testing-the-bot-locally-in-teams"></a>Testen des Bots lokal in Teams

Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die es zugreift, über HTTPS-Endpunkte aus der Cloud verfügbar sein. Damit der Bot (unser Beispiel) in Teams arbeiten kann, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder eine lokal ausgeführte Instanz über ein **Tunneling-Tool** extern zugänglich machen. Wir empfehlen  [ngrok](https://ngrok.com/download), das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen.
Führen Sie die folgenden Schritte aus, um ngrok zur Vorbereitung auf die lokale Ausführung Ihrer Microsoft Teams-App einzurichten:

1. Wechseln Sie in einem Terminalfenster in das Verzeichnis, in dem Sie `ngrok.exe` installiert haben. Wir schlagen vor, den Pfad der *Umgebungsvariablen* so festzulegen, dass er darauf zu verweisen ist.
1. Führen Sie z. `ngrok http 3978 --host-header=localhost:3978` B. aus. Ersetzen Sie die Portnummer nach Bedarf.
Dadurch wird ngrok gestartet, um den angegebenen Port zu hören. Im Gegenzug erhalten Sie eine extern adressierbare URL, die so lange gültig ist, wie ngrok ausgeführt wird. Das folgende Bild ist ein Beispiel:

    ![Teams Bot App auth Verbindung String adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG).

1. Kopieren Sie die weiterleitende HTTPS-Adresse. Es sollte ähnlich wie folgt sein: `https://dea822bf.ngrok.io/` .
1. `/api/messages`Anhängen, um `https://dea822bf.ngrok.io/api/messages` zu erhalten. Dies ist der **Nachrichtenendpunkt** für den Bot, der lokal auf Ihrem Computer ausgeführt wird und über das Web in einem Chat in Microsoft Teams erreichbar ist.
1. Ein letzter Schritt besteht darin, den Nachrichtenendpunkt des bereitgestellten Bots zu aktualisieren. Im Beispiel haben wir den Bot in Azure bereitgestellt. Also **Lassen Sie uns die folgenden Schritte ausführen:
    1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
    1. Wählen Sie Ihre **Bot Channel Registrierung**.
    1. Wählen Sie im linken Bereich **Einstellungen** aus.
    1. Geben Sie im rechten Bereich im Feld **Messaging-Endpunkt** die ngrok-URL in unserem Beispiel `https://dea822bf.ngrok.io/api/messages` ein.
1. Starten Sie Ihren Bot lokal, z. B. im Visual Studio-Debug-Modus.
1. Testen Sie den Bot, während Er lokal mit dem **Testweb-Chat** des Bot Framework-Portals ausgeführt wird. Wie der Emulator ermöglicht ihnen dieser Test keinen Zugriff auf Teams-spezifische Funktionen.
1. Im Terminalfenster, in dem `ngrok` ausgeführt wird, können Sie HTTP-Datenverkehr zwischen dem Bot und dem Web-Chat-Client sehen. Wenn Sie eine detailliertere Ansicht wünschen, geben Sie in einem Browserfenster ein, `http://127.0.0.1:4040` das Sie aus dem vorherigen Terminalfenster erhalten haben. Das folgende Bild ist ein Beispiel:

    ![auth bot teams ngrok testing](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png).

> [!NOTE]
> Wenn Sie ngrok anhalten und neu starten, ändert sich die URL. Um ngrok in Ihrem Projekt zu verwenden, müssen Sie je nach den von Ihnen genutzten Funktionen alle URL-Referenzen aktualisieren.
 

## <a name="additional-information"></a>Weitere Informationen

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.jsauf

Dieses Manifest enthält Informationen, die von Microsoft Teams benötigt werden, um sich mit dem Bot zu verbinden:  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0.0",
  "id": "",
  "packageName": "com.teams.auth.bot",
  "developer": {
    "name": "TeamsBotAuth",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.teams.com/privacy",
    "termsOfUseUrl": "https://www.teams.com/termsofuse"
  },
  "icons": {
    "color": "color.png",
    "outline": "outline.png"
  },
  "name": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "description": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "accentColor": "#FFFFFF",
  "bots": [
    {
      "botId": "",
      "scopes": [
        "groupchat",
        "team"
      ],
      "supportsFiles": false,
      "isNotificationOnly": false
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [ "token.botframework.com" ]
}
```

Bei der Authentifizierung verhält sich Teams etwas anders als andere Kanäle, wie unten erläutert.

### <a name="handling-invoke-activity"></a>Behandeln der Invoke-Aktivität

Eine **Invoke-Aktivität** wird an den Bot gesendet und nicht an die Ereignisaktivität, die von anderen Kanälen verwendet wird.
Dies geschieht durch Unterklassen des **ActivityHandler**.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-sample)

**Bots/DialogBot.cs**

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

**Bots/TeamsBot.cs**

Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a>TeamsActivityHandler.cs

```csharp

protected virtual Task OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    switch (turnContext.Activity.Name)
    {
        case "signin/verifyState":
            return OnSigninVerifyStateAsync(turnContext, cancellationToken);

        default:
            return Task.CompletedTask;
    }
}

protected virtual Task OnSigninVerifyStateAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    return Task.CompletedTask;
}
```

# <a name="javascript"></a>[JavaScript](#tab/node-js-dialog-sample)

**bots/dialogBot.js**

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

**bots/teamsBot.js**

Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

**Dialoge/mainDialog.js**

Verwenden Sie in einem Dialogschritt `beginDialog` die OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.

- Wenn der Benutzer bereits angemeldet ist, wird ein Tokenantwortereignis generiert, ohne den Benutzer dazu aufzurufen.
- Andernfalls wird der Benutzer aufgefordert, sich anzumelden. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht hat, sich anzumelden.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Überprüfen Sie im folgenden Dialogschritt, ob im Ergebnis des vorherigen Schritts ein Token angezeigt wird. Wenn es nicht null ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

**bots/logoutDialog.js**

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[Python](#tab/python-sample)

**bots/dialog_bot.py**

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

**bots/teams_bot.py**

Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

**Dialoge/main_dialog.py**

Verwenden Sie in einem Dialogschritt `begin_dialog` die OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.

- Wenn der Benutzer bereits angemeldet ist, wird ein Tokenantwortereignis generiert, ohne den Benutzer dazu aufzurufen.
- Andernfalls wird der Benutzer aufgefordert, sich anzumelden. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht hat, sich anzumelden.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Überprüfen Sie im folgenden Dialogschritt, ob im Ergebnis des vorherigen Schritts ein Token angezeigt wird. Wenn es nicht null ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**Dialoge/logout_dialog.py**

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

## <a name="see-also"></a>Siehe auch

[Hinzufügen der Authentifizierung über Azure Bot Service](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: /azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true
[concept-state]: /azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0&preserve-view=true
[concept-dialogs]: /azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0&preserve-view=true
[simple-dialog]: /azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0&preserve-view=true

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
