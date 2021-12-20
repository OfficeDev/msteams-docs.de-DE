---
title: Hinzufügen der Authentifizierung zu Ihrem Teams-Bot
author: surbhigupta
description: Hinzufügen der OAuth-Authentifizierung zu einem Bot in Microsoft Teams mithilfe von AAD. Erfahren Sie, wie Sie Authentifizierungsfähige Bots erstellen, bereitstellen und integrieren.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
keywords: Ressourcengruppen-Botkanalregistrierung Azure Emulator-Botmanifest
ms.openlocfilehash: 9bf0b86f3dc1a2462188106173b9a98b5798f6cc
ms.sourcegitcommit: a2d7d2bdf4b056b35f29c6fdb315bc7dc28b6f6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2021
ms.locfileid: "61569525"
---
# <a name="add-authentication-to-your-teams-bot"></a>Hinzufügen der Authentifizierung zu Ihrem Teams-Bot

Es gibt Situationen, in denen Sie bots in Microsoft Teams erstellen müssen, die im Auftrag des Benutzers auf Ressourcen zugreifen können, z. B. einen E-Mail-Dienst.

In diesem Artikel wird die Verwendung der Azure Bot Service v4 SDK-Authentifizierung basierend auf OAuth 2.0 veranschaulicht. Dies erleichtert die Entwicklung eines Bots, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann. Entscheidend ist dabei die Verwendung von **Identitätsanbietern,** wie wir später sehen werden.

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

Die vollständige Spezifikation finden Sie unter [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) für ein grundlegendes Verständnis und [OAuth 2.0.](https://oauth.net/2/)

Weitere Informationen dazu, wie der Azure Bot Service die Authentifizierung behandelt, finden Sie unter [Benutzerauthentifizierung innerhalb einer Unterhaltung.](https://aka.ms/azure-bot-authentication)

In diesem Artikel erhalten Sie Informationen zu folgenden Themen:

- **So erstellen Sie einen bot mit Authentifizierung.** Sie verwenden [cs-auth-sample,][teams-auth-bot-cs] um Anmeldeinformationen von Benutzern und das Generieren des Authentifizierungstokens zu verarbeiten.
- **So stellen Sie den Bot in Azure bereit und ordnen ihn einem Identitätsanbieter zu.** Der Anbieter gibt ein Token basierend auf Anmeldeinformationen des Benutzers aus. Der Bot kann das Token für den Zugriff auf Ressourcen wie z. B. einen E-Mail-Dienst verwenden, für den eine Authentifizierung erforderlich ist. Weitere Informationen finden Sie unter [Microsoft Teams Authentifizierungsfluss für Bots.](auth-flow-bot.md)
- **Integrieren des Bots in Microsoft Teams**. Nachdem der Bot integriert wurde, können Sie sich anmelden und Nachrichten mit ihm in einem Chat austauschen.

## <a name="prerequisites"></a>Voraussetzungen

- Kenntnisse der [Botgrundlagen,][concept-basics] [des Verwaltens des Zustands,][concept-state]der [Dialogfeldbibliothek][concept-dialogs]und der Implementierung des [sequenziellen Unterhaltungsflusses.][simple-dialog]
- Kenntnisse der Azure- und OAuth 2.0-Entwicklung.
- Die aktuellen Versionen von Visual Studio und Git.
- Azure-Konto. Bei Bedarf können Sie ein [kostenloses Azure-Konto](https://azure.microsoft.com/free/)erstellen.
- Das folgende Beispiel:

    | Beispiel | BotBuilder-Version | Veranschaulicht |
    |:---|:---:|:---|
    | **Bot-Authentifizierung** in [cs-auth-sample][teams-auth-bot-cs] | v4 | OAuthCard-Unterstützung |
    | **Bot-Authentifizierung** in [js-auth-sample][teams-auth-bot-js] | v4| OAuthCard-Unterstützung  |
    | **Bot-Authentifizierung** im [Py-Auth-Beispiel][teams-auth-bot-py] | v4 | OAuthCard-Unterstützung |

## <a name="create-the-resource-group"></a>Erstellen der Ressourcengruppe

Die Ressourcengruppe und der Serviceplan sind nicht unbedingt erforderlich, ermöglichen es Ihnen jedoch, die erstellten Ressourcen bequem freizugeben. Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.

Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das Bot Framework zu erstellen. Stellen Sie aus Leistungsgründen sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.

1. Melden Sie sich in Ihrem Browser beim [**Azure-Portal an.**][azure-portal]
1. Wählen Sie im linken Navigationsbereich **Ressourcengruppen** aus.
1. Wählen Sie oben links im angezeigten Fenster die Registerkarte **"Hinzufügen"** aus, um eine neue Ressourcengruppe zu erstellen. Sie werden aufgefordert, Folgendes anzugeben:
    1. **Abonnement**: Verwenden Sie Ihr vorhandenes Abonnement.
    1. **Ressourcengruppe**. Geben Sie den Namen für die Ressourcengruppe ein. Ein Beispiel könnte  *TeamsResourceGroup* sein. Denken Sie daran, dass der Name eindeutig sein muss.
    1. Wählen Sie im Dropdownmenü **"Region"** die Option *"Usa( Westen)* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. Wählen Sie die Schaltfläche **"Überprüfen" und "Erstellen"** aus. Es sollte ein Banner angezeigt werden, in dem die *Validierung gelesen wird.*
    1. Wählen Sie die Schaltfläche **"Erstellen"** aus. Es kann einige Minuten dauern, bis die Ressourcengruppe erstellt wurde.

> [!TIP]
> Wie bei den Ressourcen, die Sie später in diesem Lernprogramm erstellen werden, empfiehlt es sich, diese Ressourcengruppe für einfachen Zugriff an Ihr Dashboard anheften. Wenn Sie dies wünschen, wählen Sie das Pin-Symbol &#128204; in der oberen rechten Ecke des Dashboards.

## <a name="create-the-service-plan"></a>Erstellen des Serviceplans

1. Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **"Ressource erstellen"** aus.
1. Geben Sie im Suchfeld *App Service Plan* ein. Wählen Sie in den Suchergebnissen die Karte **"App-Serviceplan"** aus.
1. Wählen Sie **Erstellen** aus.
1. Sie werden aufgefordert, die folgenden Informationen anzugeben:
    1. **Abonnement**: Sie können ein vorhandenes Abonnement verwenden.
    1. **Ressourcengruppe**. Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.
    1. **Name**. Geben Sie den Namen für den Serviceplan ein. Ein Beispiel könnte  *TeamsServicePlan* sein. Denken Sie daran, dass der Name innerhalb der Gruppe eindeutig sein muss.
    1. **Betriebssystem**. Wählen Sie *Windows* oder das entsprechende Betriebssystem aus.
    1. **Region**. Wählen Sie *"West US"* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. **Preisniveau**. Stellen Sie sicher, dass *Standard S1* ausgewählt ist. Dies sollte der Standardwert sein.
    1. Wählen Sie die Schaltfläche **"Überprüfen" und "Erstellen"** aus. Es sollte ein Banner angezeigt werden, in dem die *Validierung gelesen wird.*
    1. Wählen Sie **Erstellen** aus. Es kann einige Minuten dauern, bis der App-Dienstplan erstellt wurde. Der Plan wird in der Ressourcengruppe aufgeführt.

## <a name="create-the-bot-channels-registration"></a>Erstellen der Registrierung von Bot-Kanälen

Die Registrierung von Bot-Kanälen registriert Ihren Webdienst als Bot beim Bot Framework, vorausgesetzt, Sie verfügen über eine Microsoft App-ID und ein App-Kennwort (geheimer Clientschlüssel).

> [!IMPORTANT]
> Sie müssen Ihren Bot nur registrieren, wenn er nicht in Azure gehostet wird. Wenn Sie einen Bot über das Azure-Portal [erstellt haben,](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) ist er bereits beim Dienst registriert. Wenn Sie Ihren Bot über das [Bot Framework](https://dev.botframework.com/bots/new) oder Entwicklerportal erstellt [haben,](../../../concepts/build-and-test/teams-developer-portal.md) ist Ihr Bot nicht in Azure registriert.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> Die Registrierungsressource für Bot-Kanäle zeigt die **globale** Region an, auch wenn Sie "West US" ausgewählt haben. Dies entspricht dem erwarteten Verhalten.

Weitere Informationen finden Sie unter [Erstellen eines Bots für Teams.](../create-a-bot-for-teams.md)

## <a name="create-the-identity-provider"></a>Erstellen des Identitätsanbieters

Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.
In diesem Verfahren verwenden Sie einen Azure AD Anbieter. Es können auch andere Azure AD unterstützte Identitätsanbieter verwendet werden.

1. Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich **Azure Active Directory** aus.
    > [!TIP]
    > Sie müssen diese Azure AD Ressource in einem Mandanten erstellen und registrieren, in dem Sie zustimmen können, von einer Anwendung angeforderte Berechtigungen zu delegieren.
    > Anweisungen zum Erstellen eines Mandanten finden Sie unter ["Zugreifen auf das Portal und Erstellen eines Mandanten".](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)
1. Wählen Sie im linken Bereich **App-Registrierungen aus.**
1. Wählen Sie im rechten Bereich oben links die Registerkarte **"Neue Registrierung"** aus.
1. Sie werden aufgefordert, die folgenden Informationen anzugeben:
   1. **Name**. Geben Sie den Namen für die Anwendung ein. Ein Beispiel könnte  *BotTeamsIdentity* sein. Denken Sie daran, dass der Name eindeutig sein muss.
   1. Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus. Wählen Sie *Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD verzeichnis – mehrinstanzenfähig) und persönliche Microsoft-Konten (z. B. Skype, Xbox) aus.*
   1. Für den **Umleitungs-URI:**<br/>
       &#x2713;**Web** auswählen. <br/>
       &#x2713; Legen Sie die URL auf `https://token.botframework.com/.auth/web/redirect` .
   1. Wählen Sie **Registrieren** aus.

1. Nach der Erstellung zeigt Azure die **Übersichtsseite** für die App an. Kopieren und speichern Sie die folgenden Informationen in einer Datei:

    1. Der **Wert der Anwendungs-ID (Client).** Sie verwenden diesen Wert später als *Client-ID,* wenn Sie diese Azure-Identitätsanwendung bei Ihrem Bot registrieren.
    1. Der Wert der **Verzeichnis-ID (Mandant).** Sie verwenden diesen Wert später auch als *Mandanten-ID,* um diese Azure-Identitätsanwendung bei Ihrem Bot zu registrieren.

1. Wählen Sie im linken Bereich **Zertifikate & geheimen Schlüssel** aus, um einen geheimen Clientschlüssel für Ihre Anwendung zu erstellen.

   1. Wählen Sie unter **"Geheime Clientschlüssel"**&#x2795; **Neuen geheimen Clientschlüssel** aus.
   1. Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen Benutzern zu identifizieren, die Sie möglicherweise für diese App erstellen müssen, z. *B. die Bot-Identitäts-App in Teams.*
   1. Legen Sie **"Läuft ab"** auf Ihre Auswahl fest.
   1. Klicken Sie auf **Hinzufügen**.
   1. Bevor Sie diese Seite verlassen, **zeichnen Sie den geheimen Schlüssel auf.** Sie verwenden diesen Wert später als _geheimen Clientschlüssel,_ wenn Sie Ihre Azure AD-Anwendung bei Ihrem Bot registrieren.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Konfigurieren der Identitätsanbieterverbindung und Registrieren beim Bot

Hinweis: Hier gibt es zwei Optionen für Dienstanbieter– Azure AD V1 und Azure AD V2.  Die Unterschiede zwischen den beiden Anbietern werden [hier](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison)zusammengefasst, aber im Allgemeinen bietet V2 mehr Flexibilität in Bezug auf das Ändern von Bot-Berechtigungen.  Graph API-Berechtigungen im Bereichsfeld aufgeführt sind, und wenn neue hinzugefügt werden, ermöglichen Bots Benutzern, den neuen Berechtigungen bei der nächsten Anmeldung zuzustimmen.  Für V1 muss die Bot-Zustimmung vom Benutzer gelöscht werden, damit neue Berechtigungen im OAuth-Dialogfeld angezeigt werden. 

#### <a name="azure-ad-v1"></a>Azure AD V1

1. Wählen Sie im [**Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie ihren Bot-Kanal-Registrierungslink aus.
1. Öffnen Sie die Ressourcenseite, und wählen Sie **"Konfiguration"** unter **Einstellungen** aus. 
1. Wählen **Sie OAuth-Verbindung hinzufügen Einstellungen** aus.    
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:  
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)
1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei. Beispiel: *BotTeamsAuthADv1*.
    1. **Dienstanbieter**. Wählen Sie **Azure Active Directory** aus. Sobald Sie dies ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie die Anwendungs-ID (Client-ID), die Sie für Ihre Azure Identity Provider-App aufgezeichnet haben, in den obigen Schritten ein.
    1. **Geheimer Clientschlüssel**. Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App notiert haben.
    1. **Grant Type**. Geben Sie `authorization_code` .
    1. **Anmelde-URL**. Geben Sie `https://login.microsoftonline.com` .
    1. **Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure-Identitäts-App notiert haben oder **die je** nach unterstütztem Kontotyp beim Erstellen der Identitätsanbieter-App ausgewählt wurde. Gehen Sie folgendermaßen vor, um zu entscheiden, welcher Wert zugewiesen werden soll:

        - Wenn Sie entweder *"Konten" nur in diesem Organisationsverzeichnis (nur Microsoft – einzelner Mandant)* oder *"Konten" in einem beliebigen Organisationsverzeichnis (Microsoft AAD-Verzeichnis - Mehrfachmandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die AAD-App notiert haben. Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie *"Konten" in einem beliebigen Organisationsverzeichnis (any AAD directory - Multi tenant and personal Microsoft accounts, z. B. Skype, Xbox, Outlook)* ausgewählt haben, geben Sie das Wort **"Common"** anstelle einer Mandanten-ID ein. Andernfalls überprüft die AAD App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    h. Geben Sie für **die Ressourcen-URL** `https://graph.microsoft.com/` . Dies wird im aktuellen Codebeispiel nicht verwendet.  
    i. Lassen Sie **Bereiche** leer. Die folgende Abbildung ist ein Beispiel:

    ![App-Authentifizierungs-Verbindungszeichenfolge adv1-Ansicht für Teams-Bots](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. Wählen Sie **Speichern**.

#### <a name="azure-ad-v2"></a>Azure AD V2

1. Wählen Sie im [**Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie ihren Bot-Kanal-Registrierungslink aus.
1. Öffnen Sie die Ressourcenseite, und wählen Sie **"Konfiguration"** unter **Einstellungen** aus. 
1. Wählen **Sie OAuth-Verbindung hinzufügen Einstellungen** aus.  
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:        
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png) 

1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei. Beispiel: *BotTeamsAuthADv2*.
    1. **Dienstanbieter**. Wählen Sie **Azure Active Directory v2** aus. Sobald Sie dies ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie die Anwendungs-ID (Client-ID), die Sie für Ihre Azure Identity Provider-App aufgezeichnet haben, in den obigen Schritten ein.
    1. **Geheimer Clientschlüssel**. Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App notiert haben.
    1. **Token Exchange URL**. Lassen Sie dieses Feld leer.
    1. **Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure-Identitäts-App notiert haben oder **die je** nach unterstütztem Kontotyp beim Erstellen der Identitätsanbieter-App ausgewählt wurde. Gehen Sie folgendermaßen vor, um zu entscheiden, welcher Wert zugewiesen werden soll:

        - Wenn Sie entweder *"Konten" nur in diesem Organisationsverzeichnis (nur Microsoft – einzelner Mandant)* oder *"Konten" in einem beliebigen Organisationsverzeichnis (Microsoft AAD-Verzeichnis - Mehrfachmandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die AAD-App notiert haben. Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie *"Konten" in einem beliebigen Organisationsverzeichnis (any AAD directory - Multi tenant and personal Microsoft accounts, z. B. Skype, Xbox, Outlook)* ausgewählt haben, geben Sie das Wort **"Common"** anstelle einer Mandanten-ID ein. Andernfalls überprüft die AAD App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    1. Geben Sie für **Bereiche** eine durch Leerzeichen getrennte Liste von Diagrammberechtigungen ein, die diese Anwendung erfordert, z. B.: User.Read User.ReadBasic.All Mail.Read 

1. Wählen Sie **Speichern**.

### <a name="test-the-connection"></a>Testen der Verbindung

1. Wählen Sie den Verbindungseintrag aus, um die gerade erstellte Verbindung zu öffnen.
1. Wählen Sie oben im Bereich **"Verbindungseinstellung für Dienstanbieter"** die Option **"Verbindung testen"** aus.
1. Wenn Sie dies zum ersten Mal tun, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen. Wählen Sie die gewünschte Option aus.
1. Als Nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu erlauben. Die folgende Abbildung ist ein Beispiel:

    ![Teams-Bot-Authentifizierungs-Verbindungszeichenfolge adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. Wählen Sie **Annehmen** aus.
1. Dies sollte Sie dann zu einer Seite **"Verbindung zum \<your-connection-name> erfolgreichen Testen" umleiten.** Aktualisieren Sie die Seite, wenn ein Fehler auftritt. Die folgende Abbildung ist ein Beispiel:

    ![Teams-Bots App-Authentifizierungsverbindung str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

Der Verbindungsname wird vom Botcode verwendet, um Benutzerauthentifizierungstoken abzurufen.

## <a name="prepare-the-bot-sample-code"></a>Vorbereiten des Bot-Beispielcodes

Nachdem die vorläufigen Einstellungen abgeschlossen sind, konzentrieren wir uns auf die Erstellung des Bots, der in diesem Artikel verwendet werden soll.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. Clone [cs-auth-sample][teams-auth-bot-cs].
1. Starten Sie Visual Studio.
1. Wählen Sie auf der Symbolleiste **Datei -> Öffnen -> Project/Projektmappe** aus, und öffnen Sie das Bot-Projekt.
1. In C# Update **appsettings.json** wie folgt:

    - Legen Sie den Namen der Identitätsanbieterverbindung fest, `ConnectionName` die Sie zur Registrierung des Botkanals hinzugefügt haben. Der Name, den wir in diesem Beispiel verwendet haben, ist *BotTeamsAuthADv1*.
    - Legen Sie `MicrosoftAppId` die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben.
    - Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel fest,** den Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.

    Abhängig von den Zeichen in Ihrem geheimen Bot-Schlüssel müssen Sie möglicherweise ein XML-Escapezeichen für das Kennwort verwenden. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als codiert `&amp;` werden.

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner, öffnen `manifest.json` und festlegen Sie `id` die `botId` **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben.

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Clone [node-auth-sample][teams-auth-bot-js].
1. Navigieren Sie in einer Konsole zum Projekt: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Installieren von Modulen</br></br>
`npm install`
1. Aktualisieren Sie die **.env-Konfiguration** wie folgt:

    - Legen Sie `MicrosoftAppId` die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben.
    - Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel fest,** den Sie zum Zeitpunkt der Registrierung des Bot-Kanals gespeichert haben.
    - Legen Sie `connectionName` den Namen der Identitätsanbieterverbindung fest.
    Abhängig von den Zeichen in Ihrem geheimen Bot-Schlüssel müssen Sie möglicherweise ein XML-Escapezeichen für das Kennwort verwenden. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als codiert `&amp;` werden.

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Öffnen Sie im `teamsAppManifest` Ordner `manifest.json` Ihre `id` **Microsoft-App-ID** und `botId` die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben, und legen Sie sie fest.

# <a name="python"></a>[Python](#tab/python)

1. Klonen Sie [py-auth-sample][teams-auth-bot-py] aus dem GitHub-Repository.
1. Aktualisieren **sie config.py:**

    - Legen Sie `ConnectionName` den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem Bot hinzugefügt haben.
    - Legen Sie `MicrosoftAppId` die `MicrosoftAppPassword` App-ID und den geheimen App-Schlüssel Ihres Bots fest.

      Abhängig von den Zeichen in Ihrem geheimen Bot-Schlüssel müssen Sie möglicherweise ein XML-Escapezeichen für das Kennwort verwenden. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als codiert `&amp;` werden.

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Bereitstellen des Bots in Azure

Um den Bot bereitzustellen, führen Sie die Schritte in der [Vorgehensweise zum Bereitstellen Ihres Bots in Azure](https://aka.ms/azure-bot-deployment-cli)aus.

Alternativ können Sie in Visual Studio die folgenden Schritte ausführen:

1. Wählen Sie Visual Studio *Projektmappen-Explorer* den Projektnamen aus und halten Sie den Projektnamen gedrückt (oder klicken Sie mit der rechten Maustaste).
1. Wählen Sie im Dropdownmenü **"Veröffentlichen"** aus.
1. Wählen Sie im angezeigten Fenster den Link **"Neu"** aus.
1. Wählen Sie im Dialogfeld auf der linken Seite **"App-Dienst"** und auf der rechten Seite **"Neu erstellen"** aus.
1. Wählen Sie die Schaltfläche **"Veröffentlichen"** aus.
1. Geben Sie im nächsten Dialogfeld die erforderlichen Informationen ein. Es folgt ein Beispiel:

    ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. Wählen Sie **Erstellen** aus.
1. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte sie in Visual Studio angezeigt werden. Darüber hinaus wird in Ihrem Standardbrowser eine Seite angezeigt, die besagt, dass *Ihr Bot bereit ist!*. Die URL ähnelt folgendem Code: `https://botteamsauth.azurewebsites.net/` . Speichern Sie sie in einer Datei.
1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal.**][azure-portal]
1. Überprüfen Sie Ihre Ressourcengruppe, der Bot sollte zusammen mit den anderen Ressourcen aufgelistet werden. Die folgende Abbildung ist ein Beispiel:

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. Wählen Sie in der Ressourcengruppe den Registrierungsnamen des Botkanals (Link) aus.
1. Wählen Sie im linken Bereich **Einstellungen** aus.
1. Geben Sie im Feld **"Messaging-Endpunkt"** die oben abgerufene URL ein, gefolgt von `api/messages` . Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages` .
1. Wählen Sie oben links die Schaltfläche **"Speichern"** aus.

## <a name="test-the-bot-using-the-emulator"></a>Testen des Bots mithilfe der Emulator

Wenn Sie dies noch nicht getan haben, installieren Sie die [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme). Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Damit die Bot-Beispielanmeldung funktioniert, müssen Sie die Emulator konfigurieren.

### <a name="configure-the-emulator-for-authentication"></a>Konfigurieren der Emulator für die Authentifizierung

Wenn ein Bot eine Authentifizierung erfordert, müssen Sie die Emulator konfigurieren. So konfigurieren Sie:

1. Starten Sie die Emulator.
1. Wählen Sie im Emulator das Zahnradsymbol &#9881; unten links oder die **Registerkarte Emulator Einstellungen** in der oberen rechten Ecke aus.
1. Aktivieren Sie das Kontrollkästchen nach Verwendung von **Authentifizierungstoken der Version 1.0.**
1. Geben Sie den lokalen Pfad zum **ngrok-Tool** ein. *Weitere Informationen finden Sie* im [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok))zur Integration von Bot Framework Emulator/ngrok-Tunneling. Weitere Toolinformationen finden Sie unter [ngrok](https://ngrok.com/).
1. Aktivieren Sie das Kontrollkästchen nach Ausführen von **"ngrok", wenn das Emulator gestartet wird.**
1. Wählen Sie die Schaltfläche **"Speichern"** aus.

Wenn der Bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet das Emulator eine Seite, die der Benutzer zum Anmelden beim Authentifizierungsanbieter verwenden kann.
Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den Bot. Danach kann der Bot im Namen des Benutzers handeln.

### <a name="test-the-bot-locally"></a>Testen des Bots lokal

Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die tatsächlichen Bottests durchführen.  

1. Führen Sie das Bot-Beispiel lokal auf Ihrem Computer aus, z. B. über Visual Studio.
1. Starten Sie die Emulator.
1. Wählen Sie die Schaltfläche **"Bot öffnen"** aus.
1. Geben Sie in der **Bot-URL** die lokale URL des Bots ein. In der Regel `http://localhost:3978/api/messages` .
1. Geben Sie in der **Microsoft App-ID** die App-ID des Bots aus `appsettings.json` ein.
1. Geben Sie im **Microsoft App-Kennwort** das App-Kennwort des Bots aus der `appsettings.json` ein.
1. Wählen Sie **Verbinden** aus.
1. Nachdem der Bot eingerichtet und ausgeführt wurde, geben Sie beliebigen Text ein, um die Anmeldekarte anzuzeigen.
1. Wählen Sie die Schaltfläche **Anmelden** aus.
1. Ein Popupdialogfeld wird angezeigt, um die **Öffnen-URL** zu bestätigen. Dies ermöglicht die Authentifizierung des Bot-Benutzers (Sie).  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie dazu aufgefordert werden, wählen Sie das konto des entsprechenden Benutzers aus.
1. Je nachdem, welche Konfiguration Sie für die Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:
    1. **Verwenden des Anmeldeüberprüfungscodes**  
      &#x2713; Ein Fenster mit dem Überprüfungscode geöffnet wird.  
      &#x2713; Kopieren Sie den Validierungscode, und geben Sie diesen in das Chatfeld ein, um die Anmeldung abzuschließen.
    1. **Verwenden von Authentifizierungstoken.**  
      &#x2713; Sie basierend auf Ihren Anmeldeinformationen angemeldet sind.

    Die folgende Abbildung ist ein Beispiel für die Bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:

    ![Authentifizierungs-Bot-Anmelde-Emulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. Wenn Sie **"Ja"** auswählen, wenn der Bot *fragt, ob Sie Ihr Token anzeigen möchten?*, erhalten Sie eine Antwort ähnlich der folgenden:

    ![Token des Authentifizierungsbot-Anmelde-Emulators](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. Geben Sie die **Abmeldung** in das Eingabechatfeld ein, um sich abmelden zu können. Dadurch wird das Benutzertoken veröffentlicht, und der Bot kann erst in Ihrem Auftrag handeln, wenn Sie sich erneut anmelden.

> [!NOTE]
> Die Bot-Authentifizierung erfordert die Verwendung des **Bot Connector Service.** Der Dienst greift auf die Registrierungsinformationen der Botkanäle für Ihren Bot zu.

## <a name="test-the-deployed-bot"></a>Testen des bereitgestellten Bots

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal.**][azure-portal]
1. Suchen Sie Ihre Ressourcengruppe.
1. Wählen Sie den Ressourcenlink aus. Die Ressourcenseite wird angezeigt.
1. Wählen Sie auf der Ressourcenseite **"Im Webchat testen"** aus. Der Bot startet und zeigt die vordefinierten Begrüßungen an.
1. Geben Sie alles in das Chatfeld ein.
1. Aktivieren Sie das **Anmeldefeld.**
1. Ein Popupdialogfeld wird angezeigt, um die **Öffnen-URL** zu bestätigen. Dies ermöglicht die Authentifizierung des Bot-Benutzers (Sie).  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie dazu aufgefordert werden, wählen Sie das konto des entsprechenden Benutzers aus.
    Die folgende Abbildung ist ein Beispiel für die Bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:

    ![Authentifizierungs-Bot-Anmeldung bereitgestellt](../../../assets/images/authentication/auth-bot-login-deployed.PNG).

1. Wählen Sie die Schaltfläche **"Ja"** aus, um Ihr Authentifizierungstoken anzuzeigen. Die folgende Abbildung ist ein Beispiel:

    ![Bereitgestelltes Token für die Authentifizierungs-Bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG).

1. Melden Sie sich ab, um sich abmelden zu können.

    ![Vom Authentifizierungsbot bereitgestelltes Abmelden](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> Wenn Beim Anmelden Probleme auftreten, versuchen Sie, die Verbindung erneut zu testen, wie in den vorherigen Schritten beschrieben. Dadurch könnte das Authentifizierungstoken neu erstellt werden.
> Beim Bot Framework Web Chat-Client in Azure müssen Sie sich möglicherweise mehrmals anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wird.

## <a name="install-and-test-the-bot-in-teams"></a>Installieren und Testen des Bots in Teams

1. Stellen Sie in Ihrem Botprojekt sicher, dass der `TeamsAppManifest` Ordner das `manifest.json` Samt und die Dateien `outline.png` `color.png` enthält.
1. Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner. Bearbeiten `manifest.json` Sie, indem Sie die folgenden Werte zuweisen:
    1. Stellen Sie sicher, dass die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals erhalten haben, und zugewiesen `id` `botId` ist.
    1. Weisen Sie diesen Wert zu: `validDomains: [ "token.botframework.com" ]` .
1. Wählen Sie die Dateien aus, und **zippen** Sie `manifest.json` `outline.png` `color.png` sie.
1. Öffnen **Sie Microsoft Teams**.
1. Wählen Sie im linken Bereich unten das **Symbol "Apps"** aus.
1. Wählen Sie im rechten Bereich unten **Hochladen einer benutzerdefinierten App** aus.
1. Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.
Der folgende Assistent wird angezeigt:

    ![Hochladen von Authentifizierungs-Bot-Teams](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.
1. Wählen Sie im nächsten Fenster das Team aus, in dem Sie den Bot verwenden möchten.
1. Wählen Sie die Schaltfläche **"Bot einrichten"** aus.
1. Wählen Sie die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) im linken Bereich aus. Wählen Sie dann das **App Studio-Symbol** aus.
1. Wählen Sie die Registerkarte **"Manifest-Editor"** aus. Das Symbol für den von Ihnen hochgeladenen Bot sollte angezeigt werden.
1. Außerdem sollten Sie in der Lage sein, den Bot als Kontakt in der Chatliste aufgeführt zu sehen, den Sie zum Austauschen von Nachrichten mit dem Bot verwenden können.

### <a name="testing-the-bot-locally-in-teams"></a>Lokales Testen des Bots in Teams

Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die es zugreift, über HTTPS-Endpunkte aus der Cloud verfügbar sein. Damit der Bot (unser Beispiel) in Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder über ein **Tunneling-Tool** extern auf eine lokal ausgeführte Instanz zugreifen. Wir empfehlen  [ngrok](https://ngrok.com/download), das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen.
Führen Sie die folgenden Schritte aus, um ngrok in Vorbereitung auf die lokale Ausführung Ihrer Microsoft Teams-App einzurichten:

1. Wechseln Sie in einem Terminalfenster zum Verzeichnis, in dem Sie `ngrok.exe` installiert haben. Es wird empfohlen, den Pfad der *Umgebungsvariablen* so festzulegen, dass er darauf zeigt.
1. Führen Sie z. `ngrok http 3978 --host-header=localhost:3978` B. . Ersetzen Sie die Portnummer nach Bedarf.
Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port abzuhören. Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird. Die folgende Abbildung ist ein Beispiel:

    ![Teams-Bot-App- Authentifizierungs-Verbindungszeichenfolge adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG).

1. Kopieren Sie die HTTPS-Weiterleitungsadresse. Es sollte etwa wie folgt aussehen: `https://dea822bf.ngrok.io/` .
1. Append `/api/messages` to obtain `https://dea822bf.ngrok.io/api/messages` . Dies ist der **Nachrichtenendpunkt** für den Bot, der lokal auf Ihrem Computer ausgeführt wird und in einem Chat in Microsoft Teams über das Web erreichbar ist.
1. Ein letzter Schritt besteht darin, den Nachrichtenendpunkt des bereitgestellten Bots zu aktualisieren. In dem Beispiel haben wir den Bot in Azure bereitgestellt. **Führen wir also die folgenden Schritte aus:
    1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal.**][azure-portal]
    1. Wählen Sie Ihre **Bot-Kanalregistrierung aus.**
    1. Wählen Sie im linken Bereich **Einstellungen** aus.
    1. Geben Sie im rechten Bereich im Feld **"Messaging-Endpunkt"** die ngrok-URL in unser Beispiel `https://dea822bf.ngrok.io/api/messages` ein.
1. Starten Sie Ihren Bot lokal, z. B. im Visual Studio Debugmodus.
1. Testen Sie den Bot während der lokalen Ausführung mithilfe des **Testwebchats** des Bot Framework-Portals. Wie die Emulator können Sie bei diesem Test nicht auf Teams spezifische Funktionalität zugreifen.
1. Im Terminalfenster, in dem `ngrok` ausgeführt wird, können Sie HTTP-Datenverkehr zwischen dem Bot und dem Webchat-Client anzeigen. Wenn Sie eine detailliertere Ansicht wünschen, geben Sie in einem Browserfenster `http://127.0.0.1:4040` die aus dem vorherigen Terminalfenster abgerufene Ansicht ein. Die folgende Abbildung ist ein Beispiel:

    ![auth bot teams ngrok testing](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png).

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL. Um ngrok in Ihrem Projekt zu verwenden, und abhängig von den von Ihnen verwendeten Funktionen, müssen Sie alle URL-Verweise aktualisieren.
 

## <a name="additional-information"></a>Weitere Informationen

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.json

Dieses Manifest enthält Informationen, die von Microsoft Teams benötigt werden, um eine Verbindung mit dem Bot herzustellen:  

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

### <a name="handling-invoke-activity"></a>Behandeln von Aufrufaktivitäten

Eine **Aufrufaktivität** wird an den Bot gesendet und nicht an die Ereignisaktivität, die von anderen Kanälen verwendet wird.
Dies geschieht durch Unterklassen des **ActivityHandler**.

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

**Bots/dialogBot.js**

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

**Bots/teamsBot.js**

Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

**Dialogfelder/mainDialog.js**

Starten Sie in einem Dialogfeld `beginDialog` die OAuth-Eingabeaufforderung, in der der Benutzer zur Anmeldung aufgefordert wird.

- Wenn der Benutzer bereits angemeldet ist, generiert dies ein Tokenantwortereignis, ohne den Benutzer aufzufordern.
- Andernfalls wird der Benutzer aufgefordert, sich anzumelden. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht, sich anzumelden.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Überprüfen Sie im folgenden Dialogfeldschritt, ob im Ergebnis des vorherigen Schritts ein Token vorhanden ist. Wenn der Wert nicht NULL ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

**Bots/logoutDialog.js**

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[Python](#tab/python-sample)

**bots/dialog_bot.py**

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

**bots/teams_bot.py**

Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

**dialogs/main_dialog.py**

Starten Sie in einem Dialogfeld `begin_dialog` die OAuth-Eingabeaufforderung, in der der Benutzer zur Anmeldung aufgefordert wird.

- Wenn der Benutzer bereits angemeldet ist, generiert dies ein Tokenantwortereignis, ohne den Benutzer aufzufordern.
- Andernfalls wird der Benutzer aufgefordert, sich anzumelden. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht, sich anzumelden.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Überprüfen Sie im folgenden Dialogfeldschritt, ob im Ergebnis des vorherigen Schritts ein Token vorhanden ist. Wenn der Wert nicht NULL ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**dialogs/logout_dialog.py**

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
