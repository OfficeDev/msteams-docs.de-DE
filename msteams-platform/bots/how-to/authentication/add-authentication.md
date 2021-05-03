---
title: Hinzufügen der Authentifizierung zu Teams Bot
author: clearab
description: Hinzufügen der OAuth-Authentifizierung zu einem Bot in Microsoft Teams.
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 7f171a791a9ee557e4af2e7d1e1b053046bd9db5
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101488"
---
# <a name="add-authentication-to-your-teams-bot"></a>Hinzufügen der Authentifizierung zu Teams Bot

Es gibt Zeiten, in denen Sie möglicherweise Bots in Microsoft Teams, die im Namen des Benutzers auf Ressourcen zugreifen können, z. B. einen E-Mail-Dienst.

In diesem Artikel wird die Verwendung der Azure Bot Service v4 SDK-Authentifizierung basierend auf OAuth 2.0 veranschaulicht. Dies erleichtert die Entwicklung eines Bots, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann. Entscheidend dabei ist die Verwendung von **Identitätsanbietern,** wie später zu sehen ist.

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

Grundlegende Informationen finden Sie unter [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) und [OAuth 2.0](https://oauth.net/2/) für die vollständige Spezifikation.

Weitere Informationen dazu, wie der Azure Bot Service die Authentifizierung verarbeitet, finden Sie unter [Benutzerauthentifizierung innerhalb einer Unterhaltung](https://aka.ms/azure-bot-authentication).

In diesem Artikel erhalten Sie Informationen zu folgenden Themen:

- **Erstellen eines Authentifizierungs-aktivierten Bots**. Sie verwenden [cs-auth-sample,][teams-auth-bot-cs] um Anmeldeinformationen des Benutzers und das Generieren des Authentifizierungstokens zu verarbeiten.
- **So stellen Sie den Bot in Azure bereit und ordnen ihn einem Identitätsanbieter zu.** Der Anbieter gibt ein Token basierend auf anmeldeinformationen des Benutzers aus. Der Bot kann das Token für den Zugriff auf Ressourcen verwenden, z. B. einen E-Mail-Dienst, für die eine Authentifizierung erforderlich ist. Weitere Informationen finden Sie [Microsoft Teams Authentifizierungsfluss für Bots](auth-flow-bot.md).
- **Integrieren des Bots in Microsoft Teams**. Nachdem der Bot integriert wurde, können Sie sich in einem Chat anmelden und Nachrichten damit austauschen.

## <a name="prerequisites"></a>Voraussetzungen

- Kenntnisse der [Botgrundkenntnisse,][concept-basics] [des Verwaltungsstatus,][concept-state]der [Dialogbibliothek][concept-dialogs]und der Implementierung des sequenziellen [Unterhaltungsflusses.][simple-dialog]
- Kenntnisse der Azure- und OAuth 2.0-Entwicklung.
- Die aktuellen Versionen von Visual Studio und Git.
- Azure-Konto. Bei Bedarf können Sie ein [kostenloses Azure-Konto erstellen.](https://azure.microsoft.com/free/)
- Das folgende Beispiel.

    | Beispiel | BotBuilder-Version | Demonstrates |
    |:---|:---:|:---|
    | **Bot-Authentifizierung** in [cs-auth-sample][teams-auth-bot-cs] | v4 | OAuthCard-Unterstützung |
    | **Bot-Authentifizierung** in [js-auth-sample][teams-auth-bot-js] | v4| OAuthCard-Unterstützung  |
    | **Bot-Authentifizierung** in [py-auth-sample][teams-auth-bot-py] | v4 | OAuthCard-Unterstützung |

## <a name="create-the-resource-group"></a>Erstellen der Ressourcengruppe

Die Ressourcengruppe und der Dienstplan sind nicht unbedingt erforderlich, sie ermöglichen es Ihnen jedoch, die von Ihnen erstellten Ressourcen bequem frei zu lassen. Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.

Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das Bot Framework zu erstellen. Stellen Sie für die Leistung sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.

1. Melden Sie sich in Ihrem Browser beim [**Azure-Portal an.**][azure-portal]
1. Wählen Sie im linken Navigationsbereich **Ressourcengruppen aus.**
1. Wählen Sie oben links im angezeigten Fenster die Registerkarte **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen. Sie werden aufgefordert, Folgendes zur Verfügung zu stellen:
    1. **Abonnement**: Verwenden Sie Ihr vorhandenes Abonnement.
    1. **Ressourcengruppe**. Geben Sie den Namen für die Ressourcengruppe ein. Ein Beispiel könnte *TeamsResourceGroup sein.* Denken Sie daran, dass der Name eindeutig sein muss.
    1. Wählen Sie **im Dropdownmenü** Region die Option *West US* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. Wählen Sie die **Schaltfläche Überprüfen und Erstellen** aus. Es sollte ein Banner mit dem Lesecode *Validation passed angezeigt werden.*
    1. Wählen Sie die **Schaltfläche Erstellen** aus. Das Erstellen der Ressourcengruppe kann einige Minuten dauern.

> [!TIP]
> Wie bei den Ressourcen, die Sie später in diesem Lernprogramm erstellen, sollten Sie diese Ressourcengruppe für den einfachen Zugriff an Ihr Dashboard anheften. Wenn Sie dies tun möchten, wählen Sie das Pinsymbol aus, &#128204; in der oberen rechten Ecke des Dashboards.

## <a name="create-the-service-plan"></a>Erstellen des Dienstplans

1. Wählen Sie [**im Azure-Portal**][azure-portal]im linken Navigationsbereich Die Option **Ressource erstellen aus.**
1. Geben Sie im Suchfeld *App Service Plan ein.* Wählen Sie in den Suchergebnissen die Karte App **Service Plan** aus.
1. Wählen Sie **Erstellen** aus.
1. Sie werden aufgefordert, die folgenden Informationen zur Verfügung zu stellen:
    1. **Abonnement**: Sie können ein vorhandenes Abonnement verwenden.
    1. **Ressourcengruppe**. Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.
    1. **Name**. Geben Sie den Namen für den Dienstplan ein. Ein Beispiel könnte *TeamsServicePlan sein.* Denken Sie daran, dass der Name innerhalb der Gruppe eindeutig sein muss.
    1. **Betriebssystem**. Wählen *Windows* oder Ihr entsprechendes Betriebssystem aus.
    1. **Region**. Wählen *Sie West US* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. **Preisebene**. Stellen Sie sicher, *dass Standard S1* ausgewählt ist. Dies sollte der Standardwert sein.
    1. Wählen Sie die **Schaltfläche Überprüfen und Erstellen** aus. Es sollte ein Banner mit dem Lesecode *Validation passed angezeigt werden.*
    1. Wählen Sie **Erstellen** aus. Das Erstellen des App-Dienstplans kann einige Minuten dauern. Der Plan wird in der Ressourcengruppe aufgeführt.

## <a name="create-the-bot-channels-registration"></a>Erstellen der Registrierung von Botkanälen

Die Registrierung von Botkanälen registriert Ihren Webdienst als Bot beim Bot Framework, vorausgesetzt, Sie verfügen über eine Microsoft App-ID und ein App-Kennwort (geheimer Client).

> [!IMPORTANT]
> Sie müssen Ihren Bot nur registrieren, wenn er nicht in Azure gehostet wird. Wenn Sie [einen Bot über](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert. Wenn Sie Ihren Bot über das [Bot Framework](https://dev.botframework.com/bots/new) oder [AppStudio](~/concepts/build-and-test/app-studio-overview.md) erstellt haben, ist Ihr Bot nicht in Azure registriert.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> Die Ressource Bot Channels Registration zeigt die **globale** Region an, auch wenn Sie "USA, Westen" ausgewählt haben. Dies entspricht dem erwarteten Verhalten.

Weitere Informationen finden Sie unter [Create a bot for Teams](../create-a-bot-for-teams.md).

## <a name="create-the-identity-provider"></a>Erstellen des Identitätsanbieters

Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.
In diesem Verfahren verwenden Sie einen Azure #A0 andere von Azure AD unterstützte Identitätsanbieter können ebenfalls verwendet werden.

1. Wählen Sie [**im Azure-Portal**][azure-portal]im linken Navigationsbereich die **Option Azure Active Directory**.
    > [!TIP]
    > Sie müssen diese Azure AD-Ressource in einem Mandanten erstellen und registrieren, in dem Sie zustimmen können, von einer Anwendung angeforderte Berechtigungen zu delegieren.
    > Anweisungen zum Erstellen eines Mandanten finden Sie unter [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).
1. Wählen Sie im linken Bereich **App-Registrierungen aus.**
1. Wählen Sie im rechten Bereich die Registerkarte **Neue Registrierung** oben links aus.
1. Sie werden aufgefordert, die folgenden Informationen zur Verfügung zu stellen:
   1. **Name**. Geben Sie den Namen für die Anwendung ein. Ein Beispiel könnte *BotTeamsIdentity sein.* Denken Sie daran, dass der Name eindeutig sein muss.
   1. Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus. Wählen Sie Konten in einem beliebigen Organisationsverzeichnis *(Beliebiges Azure AD-Verzeichnis - Multitenant) und persönliche Microsoft-Konten (z. B. Skype, Xbox) aus.*
   1. Für den **Umleitungs-URI:**<br/>
       &#x2713;Wählen Sie **Web aus.** <br/>
       &#x2713; Legen Sie die URL auf `https://token.botframework.com/.auth/web/redirect` .
   1. Wählen Sie **Registrieren** aus.

1. Nachdem es erstellt wurde, zeigt Azure die **Seite Übersicht** für die App an. Kopieren Und speichern Sie die folgenden Informationen in einer Datei:

    1. Der **Wert der Anwendungs-ID (Client).** Sie verwenden diesen Wert später als *Client-ID,* wenn Sie diese Azure-Identitätsanwendung bei Ihrem Bot registrieren.
    1. Der **Wert der Verzeichnis-ID (Mandant).** Sie verwenden diesen Wert später auch als *Mandanten-ID,* um diese Azure-Identitätsanwendung bei Ihrem Bot zu registrieren.

1. Wählen Sie im linken Bereich Zertifikate **& aus,** um einen geheimen Clientgeheimnisse für Ihre Anwendung zu erstellen.

   1. Wählen **Sie unter Geheime** Clientgeheimnisse &#x2795; **Neuen Geheimen Client aus.**
   1. Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen Personen zu identifizieren, die Sie möglicherweise für diese App erstellen müssen, z. B. *bot identity app in Teams*.
   1. Set **Expires** to your selection.
   1. Klicken Sie auf **Hinzufügen**.
   1. Bevor Sie diese Seite verlassen, **müssen Sie den geheimen Eintrag aufzeichnen.** Dieser Wert wird später als  geheimer Clientgeheimnis verwendet, wenn Sie Ihre Azure AD-Anwendung bei Ihrem Bot registrieren.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Konfigurieren sie die Verbindung des Identitätsanbieters, und registrieren Sie sie beim Bot.

Hinweis: Es gibt zwei Optionen für Dienstanbieter hier- Azure AD V1 und Azure AD V2.  Die Unterschiede zwischen den beiden Anbietern sind hier [zusammengefasst,](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison)aber im Allgemeinen bietet V2 mehr Flexibilität bei der Änderung von Botberechtigungen.  Graph API-Berechtigungen sind im Feld Bereiche aufgeführt, und wenn neue hinzugefügt werden, können Bots Benutzern bei der nächsten Anmeldung die Zustimmung zu den neuen Berechtigungen erteilen.  Für V1 muss die Bot-Zustimmung vom Benutzer gelöscht werden, damit neue Berechtigungen im OAuth-Dialogfeld aufgefordert werden. 

#### <a name="azure-ad-v1"></a>Azure AD V1

1. Wählen Sie [**im Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie den Link zur Botkanalregistrierung aus.
1. Öffnen Sie die Ressourcenseite, und wählen **Sie Konfiguration** unter **Einstellungen**. 
1. Wählen **Sie OAuth Connection Einstellungen hinzufügen aus.**    
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:  
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)
1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei. Beispiel: *BotTeamsAuthADv1*.
    1. **Dienstanbieter**. Wählen Sie **Azure Active Directory** aus. Nachdem Sie diese Option ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.
    1. **Geheimer Clientgeheimnis**. Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.
    1. **Grant Type**. Geben Sie `authorization_code` ein.
    1. **Anmelde-URL**. Geben Sie `https://login.microsoftonline.com` ein.
    1. **Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandant) ein,** die Sie zuvor für Ihre Azure-Identitäts-App aufgezeichnet haben oder je nach dem unterstützten Kontotyp, der beim Erstellen der Identitätsanbieter-App ausgewählt wurde.  So entscheiden Sie, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:

        - Wenn Sie nur Konten in diesem Organisationsverzeichnis *(nur Microsoft - Einzelner* Mandant) oder Konten in einem beliebigen Organisationsverzeichnis *(Microsoft AAD-Verzeichnis - Mehr* mandant) ausgewählt haben, geben Sie die Mandanten-ID ein, die Sie zuvor für die AAD-App aufgezeichnet haben.  Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie Konten in einem beliebigen Organisationsverzeichnis ausgewählt haben (Beliebiges AAD-Verzeichnis – Mehr mandanten- und persönliche  Microsoft-Konten, *z. B. Skype, Xbox, Outlook),* geben Sie das Wort common anstelle einer Mandanten-ID ein. Andernfalls überprüft die AAD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    h. Geben **Sie für Ressourcen-URL** `https://graph.microsoft.com/` ein. Dies wird im aktuellen Codebeispiel nicht verwendet.  
    i. Lassen **Sie Bereiche** leer. Die folgende Abbildung ist ein Beispiel:

    ![teams bots app auth connection string adv1 view](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. Wählen Sie **Speichern** aus.

#### <a name="azure-ad-v2"></a>Azure AD V2

1. Wählen Sie [**im Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie den Link zur Botkanalregistrierung aus.
1. Öffnen Sie die Ressourcenseite, und wählen **Sie Konfiguration** unter **Einstellungen**. 
1. Wählen **Sie OAuth Connection Einstellungen hinzufügen aus.**  
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:        
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png) 

1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei. Beispiel: *BotTeamsAuthADv2*.
    1. **Dienstanbieter**. Wählen **Azure Active Directory v2 aus.** Nachdem Sie diese Option ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.
    1. **Geheimer Clientgeheimnis**. Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.
    1. **Token Exchange URL**. Lassen Sie dieses Feld leer.
    1. **Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandant) ein,** die Sie zuvor für Ihre Azure-Identitäts-App aufgezeichnet haben oder je nach dem unterstützten Kontotyp, der beim Erstellen der Identitätsanbieter-App ausgewählt wurde.  So entscheiden Sie, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:

        - Wenn Sie nur Konten in diesem Organisationsverzeichnis *(nur Microsoft - Einzelner* Mandant) oder Konten in einem beliebigen Organisationsverzeichnis *(Microsoft AAD-Verzeichnis - Mehr* mandant) ausgewählt haben, geben Sie die Mandanten-ID ein, die Sie zuvor für die AAD-App aufgezeichnet haben.  Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie Konten in einem beliebigen Organisationsverzeichnis ausgewählt haben (Beliebiges AAD-Verzeichnis – Mehr mandanten- und persönliche  Microsoft-Konten, *z. B. Skype, Xbox, Outlook),* geben Sie das Wort common anstelle einer Mandanten-ID ein. Andernfalls überprüft die AAD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    1. Geben **Sie für** Bereiche eine durch Leerzeichen getrennte Liste von Graphberechtigungen ein, die für diese Anwendung erforderlich sind, z. B.: User.Read User.ReadBasic.All Mail.Read 

1. Wählen Sie **Speichern** aus.

### <a name="test-the-connection"></a>Testen der Verbindung

1. Wählen Sie den Verbindungseintrag aus, um die gerade erstellte Verbindung zu öffnen.
1. Wählen **Sie oben im** Bereich Dienstanbieterverbindungseinstellung die Option Verbindung testen aus. 
1. Wenn Sie dies zum ersten Mal tun, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen. Wählen Sie das zu verwendende Aus.
1. Als Nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu erlauben. Die folgende Abbildung ist ein Beispiel:

    ![teams bot auth connection string adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. Wählen Sie **Annehmen** aus.
1. Dies sollte Sie dann auf eine Seite **"Testverbindung zu \<your-connection-name> Erfolgreich"** umleiten. Aktualisieren Sie die Seite, wenn ein Fehler auftritt. Die folgende Abbildung ist ein Beispiel:

  ![teams bots app auth connection str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

Der Verbindungsname wird vom Botcode zum Abrufen von Benutzerauthentifizierungstoken verwendet.

## <a name="prepare-the-bot-sample-code"></a>Vorbereiten des Bot-Beispielcodes

Wenn die vorläufigen Einstellungen fertig sind, konzentrieren wir uns auf die Erstellung des Bots, der in diesem Artikel verwendet werden soll.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. [Klonen Sie cs-auth-sample][teams-auth-bot-cs].
1. Starten Visual Studio.
1. Wählen Sie auf **der Symbolleiste Datei -> Öffnen -> Project/Lösung** aus, und öffnen Sie das Bot-Projekt.
1. In C# Update **appsettings.jswie** folgt:

    - Legen `ConnectionName` Sie den Namen der Identitätsanbieterverbindung, die Sie der Botkanalregistrierung hinzugefügt haben, festgelegt. Der in diesem Beispiel verwendete Name ist *BotTeamsAuthADv1*.
    - Legen `MicrosoftAppId` Sie die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben, auf.
    - Legen `MicrosoftAppPassword` Sie den **Kundengeheimnis,** den Sie zum Zeitpunkt der Botkanalregistrierung gespeichert haben, auf.

    Abhängig von den Zeichen in Ihrem Geheimen Bot müssen Sie möglicherweise das Kennwort als XML-Escapezeichen verwenden. Beispielsweise müssen ampersands (&) als codiert `&amp;` werden.

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. Navigieren Sie im Projektmappen-Explorer zu dem Ordner, öffnen und legen Sie diese und die `TeamsAppManifest` `manifest.json` `id` `botId` **Bot-App-ID,** die Sie zum Zeitpunkt der Botkanalregistrierung gespeichert haben.

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Clone [node-auth-sample][teams-auth-bot-js].
1. Navigieren Sie in einer Konsole zu dem Projekt: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Installieren von Modulen</br></br>
`npm install`
1. Aktualisieren Sie **die env-Konfiguration** wie folgt:

    - Legen `MicrosoftAppId` Sie die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben, auf.
    - Legen `MicrosoftAppPassword` Sie den **Kundengeheimnis,** den Sie zum Zeitpunkt der Botkanalregistrierung gespeichert haben, auf.
    - Legen Sie `connectionName` den auf den Namen der Verbindung des Identitätsanbieters.
    Abhängig von den Zeichen in Ihrem Geheimen Bot müssen Sie möglicherweise das Kennwort als XML-Escapezeichen verwenden. Beispielsweise müssen ampersands (&) als codiert `&amp;` werden.

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Öffnen Sie im Ordner Ihre Microsoft App-ID und die `teamsAppManifest` Bot-App-ID, die Sie zum Zeitpunkt der Registrierung des `manifest.json` `id`  `botId` Botkanals gespeichert haben. 

# <a name="python"></a>[Python](#tab/python)

1. [Klonen Sie py-auth-sample][teams-auth-bot-py] aus dem github-Repository.
1. Update **config.py**:

    - Legen `ConnectionName` Sie auf den Namen der OAuth-Verbindungseinstellung, die Sie Ihrem Bot hinzugefügt haben, festgelegt.
    - Legen Sie und die App-ID und den geheimen `MicrosoftAppId` App-Schlüssel Ihres `MicrosoftAppPassword` Bots.

      Abhängig von den Zeichen in Ihrem Geheimen Bot müssen Sie möglicherweise das Kennwort als XML-Escapezeichen verwenden. Beispielsweise müssen ampersands (&) als codiert `&amp;` werden.

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Bereitstellen des Bots in Azure

Führen Sie zum Bereitstellen des Bots die Schritte in der Bereitstellung [Ihres Bots in Azure aus.](https://aka.ms/azure-bot-deployment-cli)

Alternativ können Sie im Visual Studio die folgenden Schritte ausführen:

1. Wählen Visual Studio *Projektmappen-Explorer* den Projektnamen aus, und halten Sie ihn fest (oder klicken Sie mit der rechten Maustaste).
1. Wählen Sie im Dropdownmenü Veröffentlichen **aus.**
1. Wählen Sie im angezeigten Fenster den Link **Neu** aus.
1. Wählen Sie im Dialogfeld auf der linken Seite **App-Dienst** und **rechts Neu** erstellen aus.
1. Wählen Sie die **Schaltfläche Veröffentlichen** aus.
1. Geben Sie im nächsten Dialogfeld die erforderlichen Informationen ein. Es folgt ein Beispiel:

   ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. Wählen Sie **Erstellen** aus.
1. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte sie in der Visual Studio. Darüber hinaus wird in Ihrem Standardbrowser eine Seite mit der Meldung *angezeigt, dass Ihr Bot bereit ist!*. Die URL ähnelt der folgende: `https://botteamsauth.azurewebsites.net/` . Speichern Sie es in einer Datei.
1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
1. Überprüfen Sie Ihre Ressourcengruppe, der Bot sollte zusammen mit den anderen Ressourcen aufgelistet werden. Die folgende Abbildung ist ein Beispiel:

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. Wählen Sie in der Ressourcengruppe den Namen der Botkanalregistrierung (Link) aus.
1. Wählen Sie im linken Bereich die **Option Einstellungen** aus.
1. Geben Sie **im Feld** Messagingendpunkt die oben erhaltene URL ein, gefolgt von `api/messages` . Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages` .
1. Wählen Sie **oben** links die Schaltfläche Speichern aus.

## <a name="test-the-bot-using-the-emulator"></a>Testen des Bots mithilfe des Emulators

Wenn Sie dies noch nicht getan haben, installieren Sie [die Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme). Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Damit die Botbeispielanmeldung funktioniert, müssen Sie den Emulator wie unten gezeigt konfigurieren.

### <a name="configure-the-emulator-for-authentication"></a>Konfigurieren des Emulators für die Authentifizierung

Wenn für einen Bot die Authentifizierung erforderlich ist, müssen Sie den Emulator wie unten gezeigt konfigurieren.

1. Starten Sie den Emulator.
1. Wählen Sie im Emulator das Zahnradsymbol &#9881; links unten oder die Registerkarte **Emulator Einstellungen** oben rechts aus.
1. Aktivieren Sie das Kontrollkästchen Verwenden von Authentifizierungstoken der Version **1.0**.
1. Geben Sie den lokalen Pfad zum **ngrok-Tool** ein. *Weitere* Informationen finden Bot Framework Emulator /ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)). Weitere Toolinformationen finden Sie unter [ngrok](https://ngrok.com/).
1. Aktivieren Sie das Kontrollkästchen **durch Ausführen von ngrok, wenn der Emulator gestartet wird.**
1. Wählen Sie die **Schaltfläche Speichern** aus.

Wenn der Bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, die der Benutzer zum Anmelden beim Authentifizierungsanbieter verwenden kann.
Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den Bot. Danach kann der Bot im Namen des Benutzers handeln.

### <a name="test-the-bot-locally"></a>Lokal testen des Bots

Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die eigentlichen Bottests durchführen.  

1. Führen Sie das Botbeispiel lokal auf Ihrem Computer aus, z. B. Visual Studio.
1. Starten Sie den Emulator.
1. Wählen Sie die **Schaltfläche Bot öffnen** aus.
1. Geben Sie **in der Bot-URL** die lokale URL des Bots ein. In der Regel `http://localhost:3978/api/messages` .
1. Geben Sie **in der Microsoft App-ID** die App-ID des Bots von `appsettings.json` ein.
1. Geben Sie **im Microsoft App-Kennwort** das App-Kennwort des Bots aus der `appsettings.json` ein.
1. Wählen **Sie Verbinden** aus.
1. Nachdem der Bot ausgeführt wurde, geben Sie einen beliebigen Text ein, um die Anmeldekarte anzeigen zu können.
1. Wählen Sie die Schaltfläche **Anmelden** aus.
1. Ein Popupdialogfeld wird angezeigt, um open **URL zu bestätigen.** Dadurch kann der Benutzer des Bots (Sie) authentifiziert werden.  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie gefragt werden, wählen Sie das Konto des entsprechenden Benutzers aus.
1. Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:
    1. **Verwenden des Anmeldeüberprüfungscodes**  
      &#x2713; Ein Fenster wird geöffnet, in dem der Überprüfungscode angezeigt wird.  
      &#x2713; Sie den Validierungscode kopieren und in das Chatfeld eingeben, um die Anmeldung durchzuführen.
    1. **Verwenden von Authentifizierungstoken**.  
      &#x2713; Sie sind basierend auf Ihren Anmeldeinformationen angemeldet.

    Die folgende Abbildung ist ein Beispiel für die Bot-UI, nachdem Sie sich angemeldet haben:

    ![Authentifizierungsbot-Anmeldeemulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. Wenn Sie **Ja auswählen,** wenn der Bot fragt, ob Sie Ihr Token anzeigen *möchten?*, erhalten Sie eine Antwort wie die folgende:

    ![Authentifizierungsbot-Anmeldeemulatortoken](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. Geben **Sie abmelden** in das Eingabechatfeld ein, um sich abmelden zu können. Dadurch wird das Benutzertoken veröffentlicht, und der Bot kann erst dann in Ihrem Namen handeln, wenn Sie sich erneut anmelden.

> [!NOTE]
> Die Botauthentifizierung erfordert die Verwendung des **Bot Connector Service**. Der Dienst zugrifft auf die Registrierungsinformationen für den Bot.

## <a name="test-the-deployed-bot"></a>Testen des bereitgestellten Bots

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
1. Suchen Sie nach Ihrer Ressourcengruppe.
1. Wählen Sie den Ressourcenlink aus. Die Ressourcenseite wird angezeigt.
1. Wählen Sie auf der Ressourcenseite **Test in Web Chat aus.** Der Bot startet und zeigt die vordefinierten Begrüßungen an.
1. Geben Sie im Chatfeld alles ein.
1. Aktivieren Sie **das Feld Anmelden.**
1. Ein Popupdialogfeld wird angezeigt, um open **URL zu bestätigen.** Dadurch kann der Benutzer des Bots (Sie) authentifiziert werden.  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie gefragt werden, wählen Sie das Konto des entsprechenden Benutzers aus.
    Die folgende Abbildung ist ein Beispiel für die Bot-UI, nachdem Sie sich angemeldet haben:

    ![Bereitgestellte Authentifizierungsbotanmeldung](../../../assets/images/authentication/auth-bot-login-deployed.PNG).

1. Wählen Sie die **Schaltfläche Ja** aus, um Ihr Authentifizierungstoken anzeigen zu können. Die folgende Abbildung ist ein Beispiel:

    ![Bereitgestelltes Token für die Authentifizierungsbotanmeldung](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG).

1. Geben Sie abmelden ein, um sich abmelden zu können.

    ![Authentifizierungsbot bereitgestellte Anmeldung](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> Wenn Bei der Anmeldung Probleme auftreten, versuchen Sie, die Verbindung wie in den vorherigen Schritten beschrieben erneut zu testen. Dadurch könnte das Authentifizierungstoken neu erstellt werden.
> Mit dem Bot Framework Web Chat-Client in Azure müssen Sie sich möglicherweise mehrmals anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wurde.

## <a name="install-and-test-the-bot-in-teams"></a>Installieren und Testen des Bots in Teams

1. Stellen Sie in Ihrem Bot-Projekt sicher, dass `TeamsAppManifest` der Ordner zusammen mit einer und `manifest.json` `outline.png` -Dateien `color.png` enthält.
1. Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner. Bearbeiten `manifest.json` Sie, indem Sie die folgenden Werte zuweisen:
    1. Stellen Sie sicher, dass die **Bot-App-ID,** die Sie zum Zeitpunkt der Botkanalregistrierung erhalten haben, und zugewiesen `id` `botId` ist.
    1. Weisen Sie diesen Wert zu: `validDomains: [ "token.botframework.com" ]` .
1. Wählen **Sie** die `manifest.json` , und `outline.png` -Dateien aus, und `color.png` zipen Sie sie.
1. Öffnen **Microsoft Teams**.
1. Wählen Sie im linken Bereich unten das **Symbol Apps aus.**
1. Wählen Sie unten im rechten Bereich die Option **Hochladen benutzerdefinierte App aus.**
1. Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.
Der folgende Assistent wird angezeigt:

    ![Hochladen von Authentifizierungsbotteams](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.
1. Wählen Sie im nächsten Fenster das Team aus, in dem Sie den Bot verwenden möchten.
1. Wählen Sie die **Schaltfläche Bot einrichten** aus.
1. Wählen Sie die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) im linken Bereich aus. Wählen Sie dann das **Symbol App Studio** aus.
1. Wählen Sie die **Registerkarte Manifest-Editor** aus. Das Symbol für den hochgeladenen Bot sollte angezeigt werden.
1. Außerdem sollten Sie in der Lage sein, den Bot als Kontakt in der Chatliste aufgeführt zu sehen, die Sie zum Austauschen von Nachrichten mit dem Bot verwenden können.

### <a name="testing-the-bot-locally-in-teams"></a>Testen des Bots lokal in Teams

Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die zugegriffen wird, über HTTPS-Endpunkte in der Cloud verfügbar sein. Damit der Bot (unser Beispiel) in Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder  über ein Tunneltool extern auf eine lokal ausgeführte Instanz zugriffen. Wir empfehlen  [ngrok](https://ngrok.com/download), das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen.
Führen Sie die folgenden Schritte aus, um ngrok in Vorbereitung auf die lokale Ausführung Microsoft Teams App zu einrichten:

1. Wechseln Sie in einem Terminalfenster zu dem Verzeichnis, in dem Sie installiert `ngrok.exe` haben. Wir empfehlen, den Pfad der *Umgebungsvariablen* so zu legen, dass er darauf verweisen kann.
1. Führen Sie z. `ngrok http 3978 --host-header=localhost:3978` B. aus. Ersetzen Sie die Portnummer nach Bedarf.
Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port abzuhören. Im Gegenzug erhalten Sie eine extern adressierbare URL, die so lange gültig ist, wie ngrok ausgeführt wird. Die folgende Abbildung ist ein Beispiel:

    ![teams bot app auth connection string adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG).

1. Kopieren Sie die Weiterleitungs-HTTPS-Adresse. Sie sollte wie folgt sein: `https://dea822bf.ngrok.io/` .
1. Append, `/api/messages` um zu erhalten `https://dea822bf.ngrok.io/api/messages` . Dies ist der **Nachrichtenendpunkt** für den Bot, der lokal auf Ihrem Computer ausgeführt wird und über das Web in einem Chat in einem Microsoft Teams.
1. Ein letzter Schritt besteht im Aktualisieren des Nachrichtenendpunkts des bereitgestellten Bots. Im Beispiel haben wir den Bot in Azure bereitgestellt. Führen wir also die folgenden Schritte aus:
    1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
    1. Wählen Sie Ihre **Bot-Kanal-Registrierung aus.**
    1. Wählen Sie im linken Bereich die **Option Einstellungen** aus.
    1. Geben Sie im rechten  Bereich im Feld Messagingendpunkt die ngrok-URL ein, in unserem Beispiel `https://dea822bf.ngrok.io/api/messages` .
1. Starten Sie Ihren Bot lokal, z. B. im Visual Studio Debugmodus.
1. Testen Sie den Bot während der lokalen Ausführung mithilfe des TestWebchats des **Bot Framework-Portals.** Wie beim Emulator können Sie bei diesem Test nicht auf Teams funktionen zugreifen.
1. Im Terminalfenster, `ngrok` in dem ausgeführt wird, wird der HTTP-Datenverkehr zwischen dem Bot und dem Webchatclient angezeigt. Wenn Sie eine detailliertere Ansicht wünschen, geben Sie in ein Browserfenster ein, das Sie aus `http://127.0.0.1:4040` dem vorherigen Terminalfenster erhalten haben. Die folgende Abbildung ist ein Beispiel:

    ![auth bot teams ngrok testing](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png).

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL. Um ngrok in Ihrem Projekt zu verwenden und je nach den von Ihnen verwendeten Funktionen, müssen Sie alle URL-Verweise aktualisieren.
 

## <a name="additional-information"></a>Weitere Informationen

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.json

Dieses Manifest enthält Informationen, die von Microsoft Teams zum Herstellen einer Verbindung mit dem Bot benötigt werden.  

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

Bei der Authentifizierung verhält Teams sich etwas anders als andere Kanäle, wie unten erläutert.

### <a name="handling-invoke-activity"></a>Behandeln von Aufrufen von Aktivitäten

Eine **Invoke-Aktivität** wird an den Bot gesendet und nicht an die Ereignisaktivität, die von anderen Kanälen verwendet wird.
Dazu wird der **ActivityHandler unterklassigiert.**

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-sample)

**Bots/DialogBot.cs**

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

**Bots/TeamsBot.cs**

Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.

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

Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

**dialogs/mainDialog.js**

Starten Sie in einem Dialogfeldschritt die OAuth-Eingabeaufforderung, in der der Benutzer zur `beginDialog` Anmeldung aufgefordert wird.

- Wenn der Benutzer bereits angemeldet ist, generiert dies ein Tokenantwortereignis, ohne dass der Benutzer dazu aufgefordert wird.
- Andernfalls wird der Benutzer zur Anmeldung aufgefordert. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht, sich zu anmelden.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Überprüfen Sie im folgenden Dialogfeldschritt, ob ein Token im Ergebnis des vorherigen Schritts enthalten ist. Wenn der Wert nicht null ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

**bots/logoutDialog.js**

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[Python](#tab/python-sample)

**bots/dialog_bot.py**

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

**bots/teams_bot.py**

Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

**dialogs/main_dialog.py**

Starten Sie in einem Dialogfeldschritt die OAuth-Eingabeaufforderung, in der der Benutzer zur `begin_dialog` Anmeldung aufgefordert wird.

- Wenn der Benutzer bereits angemeldet ist, generiert dies ein Tokenantwortereignis, ohne dass der Benutzer dazu aufgefordert wird.
- Andernfalls wird der Benutzer zur Anmeldung aufgefordert. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht, sich zu anmelden.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Überprüfen Sie im folgenden Dialogfeldschritt, ob ein Token im Ergebnis des vorherigen Schritts enthalten ist. Wenn der Wert nicht null ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**dialogs/logout_dialog.py**

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

> [!div class="nextstepaction"]
> [Informationen zum Hinzufügen der Authentifizierung über Azure Bot Service](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: https://docs.microsoft.com/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true
[concept-state]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0&preserve-view=true
[concept-dialogs]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0&preserve-view=true
[simple-dialog]: https://docs.microsoft.com/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0&preserve-view=true

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
