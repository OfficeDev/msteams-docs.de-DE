---
title: Authentifizierung für Ihren Teams-Bot hinzufügen
author: surbhigupta
description: Erfahren Sie, wie Sie einem Bot in Teams mithilfe von Azure Active Directory die OAuth-Authentifizierung hinzufügen. Erfahren Sie, wie Sie authentifizierungsfähige Bots erstellen, bereitstellen und integrieren.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: c66425550bdb989d8e0cb55d806a5e6b8fc92d6a
ms.sourcegitcommit: 9d318eda5589ea8f5519d05cb83e0acf3e13e2f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66150764"
---
# <a name="add-authentication-to-your-teams-bot"></a>Authentifizierung für Ihren Teams-Bot hinzufügen

Es kann vorkommen, dass Sie Bots in Microsoft Teams erstellen müssen, die im Namen des Benutzers auf Ressourcen zugreifen können, z. B. einen E-Mail-Dienst.

In diesem Artikel wird die Verwendung von Azure Bot Service v4 SDK-Authentifizierung basierend auf OAuth 2.0 veranschaulicht. Dies erleichtert die Entwicklung eines Bots, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann. Der Schlüssel in all dem ist die Verwendung von **Identitätsanbietern**, wie wir später sehen werden.

OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Microsoft Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird. Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.

Siehe [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) für grundlegende Informationen und [OAuth 2.0](https://oauth.net/2/) für die vollständige Spezifikation.

Weitere Informationen dazu, wie der Azure Bot Service die Authentifizierung verarbeitet, finden Sie unter [Benutzerauthentifizierung in einer Unterhaltung](https://aka.ms/azure-bot-authentication).

In diesem Artikel erhalten Sie Informationen zu folgenden Themen:

- **So erstellen Sie einen Bot mit Authentifizierungsfunktion**. Sie verwenden [cs-auth-sample][teams-auth-bot-cs] zum Behandeln von Anmeldeinformationen für Benutzer und zum Generieren des Authentifizierungstokens.
- **So stellen Sie den Bot in Azure bereit und ordnen ihn einem Identitätsanbieter zu**. Der Anbieter gibt ein Token basierend auf Anmeldeinformationen des Benutzers aus. Der Bot kann das Token für den Zugriff auf Ressourcen verwenden, z. B. einen E-Mail-Dienst, der eine Authentifizierung erfordert. Weitere Informationen finden Sie [unter Microsoft Teams Authentifizierungsfluss für Bots](auth-flow-bot.md).
- **So integrieren Sie den Bot in Microsoft Teams**. Nachdem der Bot integriert wurde, können Sie sich anmelden und Nachrichten mit ihm in einem Chat austauschen.

## <a name="prerequisites"></a>Voraussetzungen

- Kenntnisse der [Bot-Grundlagen][concept-basics], der [Verwaltung des Zustands][concept-state], der [Dialogbibliothek][concept-dialogs] und der [Implementierung eines sequentiellen Unterhaltungsablaufs][simple-dialog].
- Kenntnisse der Azure- und OAuth 2.0-Entwicklung.
- Die aktuellen Versionen von Microsoft Visual Studio und Git.
- Azure-Konto. Bei Bedarf können Sie ein [kostenloses Azure-Konto](https://azure.microsoft.com/free/)erstellen.
- Es folgen einige Beispielszenarien:

    | Beispiel | BotBuilder-Version | Veranschaulichung |
    |:---|:---:|:---|
    | **Bot-Authentifizierung** in [cs-auth-sample][teams-auth-bot-cs] | v3, v4 | OAuthCard-Unterstützung |
    | **Bot-Authentifizierung** in [js-auth-sample][teams-auth-bot-js] | v3, v4| OAuthCard-Unterstützung  |
    | **Bot-Authentifizierung** in [py-auth-sample][teams-auth-bot-py] | v3, v4 | OAuthCard-Unterstützung |

## <a name="create-the-resource-group"></a>Erstellen der Ressourcengruppe

Die Ressourcengruppe und der Serviceplan sind nicht unbedingt erforderlich, aber sie ermöglichen es Ihnen, die von Ihnen erstellten Ressourcen bequem freizugeben. Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.

Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das Bot-Framework zu erstellen. Stellen Sie aus Leistungsgründen sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.

1. Melden Sie sich in Ihrem Browser beim [**Microsoft Azure-Portal**][azure-portal] an.
1. Wählen Sie im linken Navigationsbereich **Ressourcengruppen** aus.
1. Wählen Sie oben links im angezeigten Fenster die Registerkarte **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen. Sie werden aufgefordert, Folgendes anzugeben:
    1. **Abonnement**: Verwenden Sie Ihr vorhandenes Abonnement.
    1. **Ressourcengruppe**. Geben Sie den Namen für die Ressourcengruppe ein. Ein Beispiel hierfür ist *TeamsResourceGroup*. Denken Sie daran, dass der Name eindeutig sein muss.
    1. Wählen Sie im Dropdownmenü **Region** die Option *USA, Westen* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. Wählen Sie die Schaltfläche **Überprüfen und erstellen** aus. Es sollte ein Banner mit der Aufschrift *Prüfung bestanden* angezeigt werden.
    1. Wählen Sie die Schaltfläche **Erstellen** aus. Das Erstellen der Ressourcengruppe kann einige Minuten dauern.

> [!TIP]
> Wie bei den Ressourcen, die Sie später in diesem Tutorial erstellen, empfiehlt es sich, diese Ressourcengruppe für den einfachen Zugriff an Ihr Dashboard anzuheften. Wenn Sie dies tun möchten, wählen Sie das Stecknadelsymbol &#128204; in der oberen rechten Ecke des Dashboards.

## <a name="create-the-service-plan"></a>Erstellen des Serviceplans

1. Wählen Sie im linken Navigationsbereich im [**Azure-Portal**][azure-portal] die Option **Ressource erstellen** aus.
1. Geben Sie im Suchfeld *App-Serviceplan* ein. Wählen Sie in den Suchergebnissen die Karte **App-Serviceplan** aus.
1. Wählen Sie **Erstellen** aus.
1. Sie werden aufgefordert, die folgenden Informationen anzugeben:
    1. **Abonnement**: Sie können ein vorhandenes Abonnement verwenden.
    1. **Ressourcengruppe**. Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.
    1. **Name**. Geben Sie den Namen für den Serviceplan ein. Ein Beispiel hierfür ist *TeamsServicePlan*. Denken Sie daran, dass der Name innerhalb der Gruppe eindeutig sein muss.
    1. **Betriebssystem**. Wählen Sie *Windows* oder Ihr entsprechendes Betriebssystem aus.
    1. **Region**. Wählen Sie *USA, Westen* oder eine Region in der Nähe Ihrer Anwendungen aus.
    1. **Preisstufe**. Stellen Sie sicher, dass *Standard S1* ausgewählt ist. Dies sollte der Standardwert sein.
    1. Wählen Sie die Schaltfläche **Überprüfen und erstellen** aus. Es sollte ein Banner mit der Aufschrift *Prüfung bestanden* angezeigt werden.
    1. Wählen Sie **Erstellen** aus. Das Erstellen des App-Serviceplans kann einige Minuten dauern. Der Plan wird in der Ressourcengruppe aufgeführt.

## <a name="create-azure-bot-resource-registration"></a>Erstellen der Azure Bot-Ressourcenregistrierung

Die Azure Bot-Ressourcenregistrierung registriert Ihren Webdienst als Bot beim Bot Framework, das Ihnen eine Microsoft-App-ID und ein App-Kennwort (geheimer Clientschlüssel) bereitstellt.

> [!IMPORTANT]
> Sie müssen Ihren Bot nur registrieren, wenn er nicht in Azure gehostet wird. Wenn Sie [einen Bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) über das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert. Wenn Sie Ihren Bot über das [Bot-Framework](https://dev.botframework.com/bots/new) oder das [Entwicklerportal](../../../concepts/build-and-test/teams-developer-portal.md) erstellt haben, ist Ihr Bot nicht in Azure registriert.

1. Besuchen Sie [**Azure-Portal**][azure-portal] und suchen Sie im Abschnitt **Erstellen einer Ressource** nach **Azure Bot**.
1. Öffnen Sie den **Azure Bot**, und wählen Sie **Erstellen** aus.
1. Geben Sie den Namen des Bot-Handle in das Feld **Bot-Handle** ein.
1. Wählen Sie Ihr **Abonnement** aus der Dropdownliste aus.
1. Wählen Sie Ihre **Ressourcengruppe** aus der Dropdownliste aus.
1. Wählen Sie den **App-Typ** als **Mehrinstanzenfähig** für die **Microsoft-App-ID** aus.

    ![Mehrinstanzenfähig](~/assets/images/adaptive-cards/multi-tenant.png)

1. Wählen Sie **Überprüfen + erstellen** aus.

    ![Erstellen von Azure Bot](~/assets/images/adaptive-cards/create-azure-bot.png)

1. Wenn die Prüfung bestanden wurde, wählen Sie **Erstellen** aus.

    Es dauert einige Augenblicke, bis Ihr Botdienst bereitgestellt wurde.

    ![Azure Bot-Prüfung](~/assets/images/adaptive-cards/validation-pane.png)

1. Wählen Sie **Zu Ressource wechseln** aus. Der Bot und die zugehörigen Ressourcen werden in der Ressourcengruppe aufgeführt.

    ![Hilfreiche Ressource:](~/assets/images/adaptive-cards/go-to-resource-card.png)

    Jetzt wird Ihr Azure-Bot erstellt.

    ![Azure-Bot-Ressource erstellt](~/assets/images/adaptive-cards/azure-bot-ui.png)

So erstellen Sie den geheimen Clientschlüssel:

1. Wählen Sie in **Einstellungen** die Option **Konfiguration** aus. Speichern Sie die **Microsoft App-ID** (Client-ID) zur zukünftigen Referenz.

    ![Microsoft App-ID](~/assets/images/adaptive-cards/config-microsoft-app-id.png)

1. Wählen Sie neben **"Microsoft-App-ID**" die Option **"Verwalten"** aus.

    ![Bot verwalten](~/assets/images/adaptive-cards/manage-bot-label.png)

1. Wählen Sie im Abschnitt **Geheime Clientschlüssel** die Option **Neuer geheimer Clientschlüssel** aus. Das Fenster **Geheimen Clientschlüssel hinzufügen** wird angezeigt.

    ![Neuer geheimer Clientschlüssel](~/assets/images/adaptive-cards/new-client-secret.png)

1. Geben Sie **Beschreibung** ein, und wählen Sie **Hinzufügen** aus.

    ![Geheimer Clientschlüssel](~/assets/images/adaptive-cards/client-secret.png)

1. Wählen Sie in der Spalte **Wert** **In Zwischenablage kopieren** aus, und speichern Sie die Clientgeheimnis-ID zur späteren Referenz.

    ![Wert des geheimen Clientschlüssels](~/assets/images/adaptive-cards/client-secret-value.png)

So fügen Sie den Microsoft Teams-Kanal hinzu:

1. Wechseln Sie zu **Startseite**.

    ![Bot-Homepage](~/assets/images/adaptive-cards/bot-home-page.png)

1. Öffnen Sie Ihren Bot, der im Abschnitt **Zuletzt verwendete Ressourcen** aufgeführt ist.

1. Wählen Sie im linken Bereich **Kanäle** und dann **Microsoft Teams** :::image type="icon" source="../../../assets/icons/teams-icon.png" border="false"::: aus.

   :::image type="content" source="../../../assets/images/adaptive-cards/channel-teams.png" alt-text="Kanal Teams":::

1. Aktivieren Sie das Kontrollkästchen, um die Nutzungsbedingungen zu akzeptieren, und wählen Sie **Zustimmen** aus.</br>

    ![Wählen Sie Vertragsbedingungen](~/assets/images/adaptive-cards/select-terms-of-service.png)

1. Wählen Sie **Speichern**.

    ![Wählen Sie Teams](~/assets/images/adaptive-cards/select-teams.png)

Weitere Informationen finden Sie unter [Erstellen eines Bot für Microsoft Teams](../create-a-bot-for-teams.md).

## <a name="create-the-identity-provider"></a>Erstellen des Identitätsanbieters

Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.
In diesem Verfahren verwenden Sie einen Azure AD-Anbieter. andere von Azure AD unterstützte Identitätsanbieter können ebenfalls verwendet werden.

1. Wählen Sie im [**Azure-Portal**][azure-portal] im linken Navigationsbereich **Azure Active Directory** aus.
    > [!TIP]
    > Sie müssen diese Azure AD-Ressource in einem Mandanten erstellen und registrieren, in dem Sie der Delegierung von Berechtigungen zustimmen können, die von einer Anwendung angefordert werden.
    > Anweisungen zum Erstellen eines Mandanten finden Sie unter [Zugreifen auf das Portal und Erstellen eines Mandanten](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).
1. Wählen Sie im linken Bereich **App-Registrierungen** aus.
1. Wählen Sie im rechten Bereich oben links die Registerkarte **Neue Registrierung** aus.
1. Sie werden aufgefordert, die folgenden Informationen anzugeben:
   1. **Name**. Geben Sie den Namen für die Anwendung ein. Ein Beispiel hierfür ist *BotTeamsIdentity*. Denken Sie daran, dass der Name eindeutig sein muss.
   1. Wählen Sie **Unterstützte Kontotypen** für Ihre Anwendung aus. Wählen Sie *Konten in einem beliebigen Organisationsverzeichnis (Any Microsoft Azure Active Directory (Azure AD) – Multitenant) und persönliche Microsoft-Konten (z. B. Skype, Xbox)* aus.
   1. Für den **Umleitungs-URI**:<br/>
       &#x2713;**Web** auswählen.<br/>
       &#x2713; Legen Sie die URL auf `https://token.botframework.com/.auth/web/redirect`.
   1. Wählen Sie **Registrieren** aus.

1. Nachdem sie erstellt wurde, zeigt Azure die **Übersichtsseite** für die App an. Kopieren und speichern Sie die folgenden Informationen in eine Datei:

    1. Der Wert der **Anwendungs-ID (Client)**. Sie verwenden diesen Wert später als *Client-ID*, wenn Sie diese Azure-Identitätsanwendung bei Ihrem Bot registrieren.
    1. Der Wert der **Verzeichnis-ID (Mandant)**. Sie verwenden diesen Wert später auch als *Mandanten-ID*, um diese Azure-Identitätsanwendung bei Ihrem Bot zu registrieren.

1. Wählen Sie im linken Bereich **Zertifikate & geheime Schlüssel** aus, um einen geheimen Clientschlüssel für Ihre Anwendung zu erstellen.

   1. Wählen Sie unter **Geheime Clientschlüssel** &#x2795; **Neuer geheimer Clientschlüssel** aus.
   1. Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen zu identifizieren, die Sie möglicherweise für diese App erstellen müssen, z. B. *Bot-Identitäts-App in Teams*.
   1. Legen Sie das **Ablaufdatum** auf das gewünschte Datum fest.
   1. Klicken Sie auf **Hinzufügen**.
   1. Bevor Sie diese Seite verlassen, **den geheimen Schlüssel notieren**. Sie verwenden diesen Wert später als *geheimen Clientschlüssel*, wenn Sie Ihre Azure AD-Anwendung bei Ihrem Bot registrieren.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Konfigurieren der Identitätsanbieterverbindung und Registrieren beim Bot

Beachten Sie, dass es hier zwei Optionen für Dienstanbieter gibt: Azure AD V1 und Azure AD V2.  Die Unterschiede zwischen den beiden Anbietern werden [hier](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison) zusammengefasst. Im Allgemeinen bietet V2 jedoch mehr Flexibilität in Bezug auf das Ändern von Botberechtigungen.  Graph-API-Berechtigungen werden im Feld "Bereiche" aufgeführt, und wenn neue hinzugefügt werden, ermöglichen Bots Benutzern, den neuen Berechtigungen bei der nächsten Anmeldung zuzustimmen.  Für V1 muss die Bot-Zustimmung vom Benutzer gelöscht werden, damit neue Berechtigungen im OAuth-Dialogfeld angezeigt werden.

#### <a name="microsoft-azure-active-directory-azure-ad-v1"></a>Microsoft Azure Active Directory (Azure AD) V1

1. Wählen Sie im [**Azure-Portal**][azure-portal] Ihre Ressourcengruppe aus dem Dashboard aus.
1. Wählen Sie den Link zur Botregistrierung aus.
1. Öffnen Sie die Ressourcenseite, und wählen Sie **Konfiguration** unter **Einstellungen** aus.
1. Wählen Sie **OAuth-Verbindungseinstellungen hinzufügen** aus.
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:  
![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)
1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json`-Datei. Beispiel: *BotTeamsAuthADv1*.
    1. **Dienstanbieter**. Wählen Sie **Microsoft Azure Active Directory (Azure AD)** aus. Sobald Sie diese Option ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure Identity Provider-App notiert haben.
    1. **Geheimer Clientschlüssel**. Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App notiert haben.
    1. **Gewährungstyp**. `authorization_code` eingeben.
    1. **Anmelde-URL**. `https://login.microsoftonline.com` eingeben.
    1. **Mandanten-ID**: Geben Sie die **Directory-ID (Mandant)** ein, die Sie zuvor für Ihre Azure-Identitäts-App notiert haben, oder **Allgemeines**, je nachdem, welchen unterstützten Kontotyp Sie beim Erstellen der Identitätsanbieter-App ausgewählt haben. Um zu entscheiden, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:

        - Wenn Sie entweder "*Konten" nur in diesem Organisationsverzeichnis (nur Microsoft – einzelner Mandant)* oder *"Konten" in einem beliebigen Organisationsverzeichnis (Microsoft Azure Active Directory (Azure AD) – Mehrere Mandanten)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die Microsoft Azure Active Directory (Azure) aufgezeichnet haben. AD) app. Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie *"Konten" in einem Beliebigen Organisationsverzeichnis (Any Microsoft Azure Active Directory (Azure AD) ausgewählt haben, geben* Sie anstelle einer Mandanten-ID das Wort **"common**" (Mehrere Mandanten- und persönliche Microsoft-Konten, z. B. Skype, Xbox, Outlook) ein. Andernfalls überprüft die Azure AD -App (Azure AD) über den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    h. Geben Sie für die **Ressourcen-URL** "`https://graph.microsoft.com/`" ein. Dies wird im aktuellen Codebeispiel nicht verwendet.  
    i. Lassen Sie das Feld **Bereiche** leer. Die folgende Abbildung dient lediglich als Beispiel:

    ![teams bots app auth connection string adv1 view](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. Wählen Sie **Speichern**.

#### <a name="microsoft-azure-active-directory-azure-ad-v2"></a>Microsoft Azure Active Directory (Azure AD) V2

1. Wählen Sie im [**Azure-Portal**][azure-portal] Ihren Azure-Bot aus dem Dashboard aus.
1. Wählen Sie auf der Ressourcenseite unter **Einstellungen** **Konfiguration** aus.
1. Wählen Sie **OAuth-Verbindungseinstellungen hinzufügen** aus.  
In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt: ![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)

1. Füllen Sie das Formular wie folgt aus:

    1. **Name**. Geben Sie einen Namen für die Verbindung ein. Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json`-Datei. Beispiel: *BotTeamsAuthADv2*.
    1. **Dienstanbieter**. Wählen Sie **Microsoft Azure Active Directory v2** aus. Sobald Sie dies ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.
    1. **Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure Identity Provider-App notiert haben.
    1. **Geheimer Clientschlüssel**. Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App notiert haben.
    1. **Tokenaustausch-URL**. Lassen Sie dieses Feld leer.
    1. **Mandanten-ID**. Geben Sie die **Directory-ID (Mandant)** ein, die Sie zuvor für Ihre Azure-Identitäts-App notiert haben, oder **Allgemeines**, je nachdem, welchen unterstützten Kontotyp Sie beim Erstellen der Identitätsanbieter-App ausgewählt haben. Um zu entscheiden, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:

        - Wenn Sie entweder "*Konten" nur in diesem Organisationsverzeichnis (nur Microsoft – einzelner Mandant)* oder *"Konten" in einem beliebigen Organisationsverzeichnis (Microsoft Azure Active Directory – Mehrere Mandanten)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die Azure AD-App aufgezeichnet haben. Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.

        - Wenn Sie *"Konten" in einem Beliebigen Organisationsverzeichnis (Any Microsoft Azure Active Directory (Azure AD) ausgewählt haben, geben* Sie anstelle einer Mandanten-ID das Wort **"common**" (Mehrere Mandanten- und persönliche Microsoft-Konten, z. B. Skype, Xbox, Outlook) ein. Andernfalls überprüft die Azure AD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.

    1. Geben Sie für Bereiche eine durch Leerzeichen getrennte Liste von **Diagrammberechtigungen** ein, die diese Anwendung benötigt, z. B.: User.Read User.ReadBasic.All Mail.Read

1. Wählen Sie **Speichern**.

### <a name="test-the-connection"></a>Testen der Verbindung

1. Wählen Sie den Verbindungseintrag aus, um die erstellte Verbindung zu öffnen.
1. Wählen Sie oben im Bereich **Verbindungseinstellung für  Dienstanbieter** **Verbindung testen** aus.
1. Wenn Sie dies zum ersten Mal tun, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen. Wählen Sie das Konto, das Sie verwenden möchten.
1. Als Nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu erlauben. Die folgende Abbildung dient lediglich als Beispiel:

    ![teams bot auth connection string adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. Wählen Sie **Annehmen** aus.
1. Dies sollte Sie dann zu einer Seite **Verbindung testen auf \<your-connection-name>Erfolgreich** weiterleiten. Aktualisieren Sie die Seite, wenn ein Fehler angezeigt wird. Die folgende Abbildung dient lediglich als Beispiel:

    ![teams bots app auth connection str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

Der Verbindungsname wird vom Botcode verwendet, um Benutzerauthentifizierungstoken abzurufen.

## <a name="prepare-the-bot-sample-code"></a>Vorbereiten des Bot-Beispielcodes

Nachdem die vorläufigen Einstellungen abgeschlossen sind, konzentrieren wir uns auf die Erstellung des Bots, der in diesem Artikel verwendet werden soll.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. Klonen Sie [cs-auth-sample][teams-auth-bot-cs].
1. Starten Sie Visual Studio.
1. Wählen Sie auf der Symbolleiste **"Datei" > "-> Project/Lösung** öffnen" aus, und öffnen Sie das Bot-Projekt.
1. Aktualisieren Sie in C# **appsettings.json** wie folgt:

    - Legen Sie `ConnectionName` auf den Namen der Identitätsanbieterverbindung fest, die Sie der Botregistrierung hinzugefügt haben. Der in diesem Beispiel verwendete Name ist *BotTeamsAuthADv1*.
    - Legen Sie `MicrosoftAppId` auf die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Botregistrierung gespeichert haben.
    - Legen Sie `MicrosoftAppPassword` auf den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der Botregistrierung gespeichert haben.

    Abhängig von den Zeichen in Ihrem geheimen Botschlüssel müssen Sie das Kennwort möglicherweise mit XML-ESCAPEZEICHEN versehen. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als `&amp;` codiert werden.

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. Navigieren Sie im Projektmappen-Explorer zum Ordner `TeamsAppManifest`, öffnen Sie `manifest.json`, legen Sie `id` und `botId` auf die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Botregistrierung gespeichert haben.

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Klonen Sie [node-auth-sample][teams-auth-bot-js].
1. Navigieren Sie in einer Konsole zum Projekt: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Module installieren</br></br>
`npm install`
1. Aktualisieren Sie die Konfiguration **.env** wie folgt:

    - Legen Sie `MicrosoftAppId` auf die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Botregistrierung gespeichert haben.
    - Legen Sie `MicrosoftAppPassword` auf den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der Botregistrierung gespeichert haben.
    - Legen Sie `connectionName` auf den Namen der Identitätsanbieterverbindung fest.
    Abhängig von den Zeichen in Ihrem geheimen Botschlüssel müssen Sie das Kennwort möglicherweise mit XML-ESCAPEZEICHEN versehen. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als `&amp;` codiert werden.

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Öffnen Sie `manifest.json` im Ordner `teamsAppManifest`, und legen Sie `id` auf Ihre **Microsoft App-ID** und `botId` auf die **Bot-App-ID** fest, die Sie zum Zeitpunkt der Botregistrierung gespeichert haben.

# <a name="python"></a>[Python](#tab/python)

1. Klonen Sie [py-auth-sample][teams-auth-bot-py] aus dem GitHub-Repository.
1. Aktualisieren Sie **config.py**:

    - Legen Sie `ConnectionName` auf den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem Bot hinzugefügt haben.
    - Legen Sie `MicrosoftAppId` und `MicrosoftAppPassword` auf die App-ID und den geheimen App-Schlüssel Ihres Bots fest.

      Abhängig von den Zeichen in Ihrem geheimen Botschlüssel müssen Sie das Kennwort möglicherweise mit XML-ESCAPEZEICHEN versehen. Beispielsweise müssen alle kaufmännischen Und-Zeichen (&) als `&amp;` codiert werden.

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Bereitstellen des Bots in Azure

Um den Bot bereitzustellen, führen Sie die Schritte in der Anleitung zum [Bereitstellen Ihres Bots in Azure](https://aka.ms/azure-bot-deployment-cli) aus.

Alternativ können Sie in Visual Studio die folgenden Schritte ausführen:

1. Halten Sie in Visual Studio *Projektmappen-Explorer* den Projektnamen gedrückt (oder klicken Sie mit der rechten Maustaste darauf).
1. Wählen Sie im Dropdownmenü **Veröffentlichen** aus.
1. Wählen Sie im angezeigten Fenster den Link **Neu** aus.
1. Wählen Sie im Dialogfeld auf der linken Seite **App Service** und auf der rechten Seite **Neu erstellen** aus.
1. Klicken Sie auf die Schaltfläche **Veröffentlichen**.
1. Geben Sie im nächsten Dialogfeld die erforderlichen Informationen ein. Es folgt ein Beispiel:

    ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. Wählen Sie **Erstellen** aus.
1. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte sie in Visual Studio angezeigt werden. Darüber hinaus wird in Ihrem Standardbrowser eine Seite mit der Meldung *Ihr Bot ist bereit!* angezeigt. Die URL sieht folgendermaßen aus: `https://botteamsauth.azurewebsites.net/`. Speichern Sie sie in einer Datei.
1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
1. Überprüfen Sie Ihre Ressourcengruppe, der Bot sollte zusammen mit den anderen Ressourcen aufgeführt werden. Die folgende Abbildung dient lediglich als Beispiel:

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. Wählen Sie in der Ressourcengruppe den Namen der Botregistrierung (Link) aus.
1. Wählen Sie im linken Bereich **Einstellungen** aus.
1. Geben Sie im Feld **Messagingendpunkt** die oben abgerufene URL gefolgt von `api/messages` ein. Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages`.
    > [!NOTE]
    > Für einen Bot ist nur ein Messaging-Endpunkt zulässig.
1. Wählen Sie oben links die Schaltfläche **Speichern** aus.

## <a name="test-the-bot-using-the-emulator"></a>Testen des Bots mithilfe von Emulator

Wenn Sie dies noch nicht getan haben, installieren Sie den [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme). Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Damit die Bot-Beispielanmeldung funktioniert, müssen Sie den Emulator konfigurieren.

### <a name="configure-the-emulator-for-authentication"></a>Konfigurieren des Emulators für die Authentifizierung

Wenn ein Bot eine Authentifizierung erfordert, müssen Sie den Emulator konfigurieren. So konfigurieren Sie:

1. Starten Sie den Emulator.
1. Wählen Sie im Emulator das Zahnradsymbol &#9881; unten links oder die Registerkarte **Emulatoreinstellungen** in der oberen rechten Ecke.
1. Aktivieren Sie das Kontrollkästchen **Authentifizierungstoken der Version 1.0** verwenden.
1. Geben Sie den lokalen Pfad zum **ngrok**-Tool ein. *Siehe* Bot Framework Emulator/ngrok-Tunnelingintegration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)). Weitere Toolinformationen finden Sie unter [ngrok](https://ngrok.com/).
1. Aktivieren Sie das Kontrollkästchen, indem Sie **ngrok ausführen, wenn der Emulator gestartet wird**.
1. Wählen Sie die Schaltfläche **Speichern** aus.

Wenn der Bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, mit der sich der Benutzer beim Authentifizierungsanbieter anmelden kann.
Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den Bot. Danach kann der Bot im Namen des Benutzers handeln.

### <a name="test-the-bot-locally"></a>Lokales Testen des Bots

Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die tatsächlichen Bot-Tests durchführen.  

1. Führen Sie das Botbeispiel lokal auf Ihrem Computer aus, z. B. über Visual Studio.
1. Starten Sie den Emulator.
1. Wählen Sie die Schaltfläche **Bot öffnen** aus.
1. Geben Sie in der **Bot-URL** die lokale URL des Bots ein. In der Regel unter `http://localhost:3978/api/messages`.
1. Geben Sie in der **Microsoft-App-ID** die App-ID des Bots aus `appsettings.json` ein.
1. Geben Sie im **Microsoft App-Kennwort** das App-Kennwort des Bots aus `appsettings.json` ein.
1. Wählen Sie **Verbinden** aus.
1. Nachdem der Bot ausgeführt wurde, geben Sie einen beliebigen Text ein, um die Anmeldekarte anzuzeigen.
1. Wählen Sie die Schaltfläche **Anmelden** aus.
1. Ein Popupdialogfeld wird mit der Aufforderung **URL öffnen bestätigen** angezeigt. Dies soll die Authentifizierung des Bot-Benutzers (Sie) ermöglichen.  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie dazu aufgefordert werden, wählen Sie das Konto des entsprechenden Benutzers aus.
1. Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:
    1. **Verwenden des Anmeldungsprüfcodes**  
      &#x2713; Ein Fenster wird geöffnet, in dem der Prüfcode angezeigt wird.  
      &#x2713; Kopieren Sie den Prüfcode, und geben Sie diesen in das Chatfeld ein, um die Anmeldung abzuschließen.
    1. **Verwenden von Authentifizierungstoken**.  
      &#x2713; Sie sind basierend auf Ihren Anmeldeinformationen angemeldet.

    Die folgende Abbildung ist ein Beispiel für die Bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:

    ![auth bot login emulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. Wenn Sie **"Ja** " auswählen, wenn der Bot sie fragt *, ob Sie Ihr Token anzeigen möchten?* Sie erhalten eine Antwort ähnlich der folgenden:

    ![auth bot login emulator token](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. Geben Sie **Abmelden** in das Eingabe-Chatfeld ein, um sich abzumelden. Dadurch wird das Benutzertoken veröffentlicht, und der Bot kann erst in Ihrem Namen handeln, wenn Sie sich erneut anmelden.

> [!NOTE]
> Die Bot-Authentifizierung erfordert die Verwendung des **Bot Connector-Diensts**. Der Dienst greift auf die Bots-Registrierungsinformationen für Ihren Bot zu.

## <a name="test-the-deployed-bot"></a>Testen des bereitgestellten Bots

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
1. Suchen Sie Ihre Ressourcengruppe.
1. Wählen Sie den Ressourcenlink aus. Die Ressourcenseite wird angezeigt.
1. Wählen Sie auf der Ressourcenseite **Testen im Webchat** aus. Der Bot startet und zeigt die vordefinierten Begrüßungen an.
1. Geben Sie etwas in das Chatfeld ein.
1. Wählen Sie das Feld **Anmelden** aus.
1. Ein Popupdialogfeld wird mit der Aufforderung **URL öffnen bestätigen** angezeigt. Dies soll die Authentifizierung des Bot-Benutzers (Sie) ermöglichen.  
1. Wählen Sie **Bestätigen** aus.
1. Wenn Sie dazu aufgefordert werden, wählen Sie das Konto des entsprechenden Benutzers aus.
    Die folgende Abbildung ist ein Beispiel für die Bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:

    ![auth bot login deployed](../../../assets/images/authentication/auth-bot-login-deployed.PNG).

1. Wählen Sie die Schaltfläche **Ja** aus, um Ihr Authentifizierungstoken anzuzeigen. Die folgende Abbildung dient lediglich als Beispiel:

    ![auth bot login deployed token](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG).

1. Geben Sie "Abmelden" ein, um sich abzumelden.

    ![auth bot deployed logout](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> Wenn Sie Probleme beim Anmelden haben, versuchen Sie erneut, die Verbindung zu testen, wie in den vorherigen Schritten beschrieben. Dadurch kann das Authentifizierungstoken neu erstellt werden.
> Mit dem Bot Framework Webchat-Client in Azure müssen Sie sich möglicherweise mehrmals anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wird.

## <a name="install-and-test-the-bot-in-teams"></a>Installieren und Testen des Bots in Teams

1. Stellen Sie in Ihrem Botprojekt sicher, dass der Ordner `TeamsAppManifest` die `manifest.json` zusammen mit einer `outline.png` und `color.png`-Dateien enthält.
1. Navigieren Sie in Projektmappen-Explorer zum Ordner `TeamsAppManifest`. Bearbeiten Sie `manifest.json`, indem Sie die folgenden Werte zuweisen:
    1. Stellen Sie sicher, dass die **Bot-App-ID**, die Sie zum Zeitpunkt der Botregistrierung erhalten haben, `id` und `botId`zugewiesen ist.
    1. Weisen Sie diesen Wert zu: `validDomains: [ "token.botframework.com" ]`.
1. Wählen Sie die Dateien `manifest.json`, `outline.png` und `color.png` aus und **zippen Sie** sie.
1. Öffnen Sie **Microsoft Teams**.
1. Wählen Sie im linken Bereich unten das **Apps-Symbol** aus.
1. Wählen Sie im rechten Bereich unten **Benutzerdefinierte App hochladen** aus.
1. Navigieren Sie zum Ordner `TeamsAppManifest`, und laden Sie das ZIP-Manifest hoch.
Der folgende Assistent wird angezeigt:

    ![auth bot teams upload](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.
1. Wählen Sie im nächsten Fenster das Team aus, in dem Sie den Bot verwenden möchten.
1. Wählen Sie die Schaltfläche **Bot einrichten** aus.
1. Wählen Sie die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) im linken Bereich aus. Wählen Sie dann das Symbol **App Studio** aus.
1. Wählen Sie die Registerkarte **Manifest-Editor** aus. Das Symbol für den hochgeladenen Bot sollte angezeigt werden.
1. Außerdem sollte der Bot in der Chatliste als Kontakt aufgeführt sein, über den Sie Nachrichten mit dem Bot austauschen können. 

### <a name="testing-the-bot-locally-in-teams"></a>Testen des Bots lokal in Teams

Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die es zugreift, über HTTPS-Endpunkte aus der Cloud verfügbar sein. Damit der Bot (unser Beispiel) in Teams funktioniert, müssen Sie daher entweder den Code in der Cloud Ihrer Wahl veröffentlichen oder eine lokal ausgeführte Instanz extern über ein **Tunneling**-Tool zugänglich machen. Wir empfehlen [ngrok](https://ngrok.com/download), wodurch eine extern adressierbare URL für einen Port erstellt wird, den Sie lokal auf Ihrem Computer öffnen.
Führen Sie die folgenden Schritte aus, um ngrok in Vorbereitung auf die lokale Ausführung Ihrer Teams-App einzurichten:

1. Wechseln Sie in einem Terminalfenster zu dem Verzeichnis, in dem Sie `ngrok.exe` installiert haben. Es wird empfohlen, den Pfad *Umgebungsvariable* so festzulegen, dass er darauf zeigt.
1. Führen Sie z. B `ngrok http 3978 --host-header=localhost:3978` aus. Ersetzen Sie die Portnummer nach Bedarf.
Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port lauschen zu können. Im Gegenzug erhalten Sie eine extern adressierbare URL, die so lange gültig ist, wie ngrok ausgeführt wird. Die folgende Abbildung dient lediglich als Beispiel:

    ![teams bot app auth connection string adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG).

1. Kopieren Sie die HTTPS-Adresse unter Forwarding. Sie sieht folgendermaßen aus: `https://dea822bf.ngrok.io/`.
1. Fügen Sie `/api/messages` an, um `https://dea822bf.ngrok.io/api/messages` abzurufen. Dies ist der **Nachrichtenendpunkt** für den Bot, der lokal auf Ihrem Computer ausgeführt wird und über das Web in einem Chat in Teams erreichbar ist.
1. Ein letzter Schritt besteht darin, den Nachrichtenendpunkt des bereitgestellten Bots zu aktualisieren. Im Beispiel haben wir den Bot in Azure bereitgestellt. Führen wir also die folgenden Schritte aus:
    1. Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].
    1. Wählen Sie Ihre **Bot-Registrierung** aus.
    1. Wählen Sie im linken Bereich **Einstellungen** aus.
    1. Geben Sie im rechten Bereich im Feld **Nachrichtenendpunkt** die ngrok-URL ein, in unserem Beispiel, `https://dea822bf.ngrok.io/api/messages`.
1. Starten Sie Ihren Bot lokal, z. B. im Debugmodus von Visual Studio.
1. Testen Sie den Bot während der lokalen Ausführung, indem Sie **Webchat testen** des Bot Framework-Portals verwenden. Wie der Emulator ermöglicht ihnen dieser Test nicht den Zugriff auf Teams-spezifische Funktionalität.
1. Im Terminalfenster, in dem `ngrok` ausgeführt wird, wird HTTP-Datenverkehr zwischen dem Bot und dem Webchatclient angezeigt. Wenn Sie eine detailliertere Ansicht wünschen, geben Sie in einem Browserfenster `http://127.0.0.1:4040` ein, die Sie aus dem vorherigen Terminalfenster abgerufen haben. Die folgende Abbildung dient lediglich als Beispiel:

    ![auth bot teams ngrok testing](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png).

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL. Um ngrok in Ihrem Projekt zu verwenden, und abhängig von den verwendeten Funktionen müssen Sie alle URL-Verweise aktualisieren.

## <a name="additional-information"></a>Weitere Informationen

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.json

Dieses Manifest enthält Informationen, die von Teams benötigt werden, um eine Verbindung mit dem Bot herzustellen:  

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

### <a name="handling-invoke-activity"></a>Behandeln der Aufrufaktivität

Eine **Aufrufaktivität** wird an den Bot und nicht an die Ereignisaktivität gesendet, die von anderen Kanälen verwendet wird.
Dazu wird **ActivityHandler** unterklassiert.

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

Verwenden Sie in einem Dialogschritt `beginDialog`, um die OAuth-Eingabeaufforderung zu starten, die den Benutzer zur Anmeldung auffordert.

- Wenn der Benutzer bereits angemeldet ist, wird ein Tokenantwortereignis generiert, ohne dass der Benutzer dazu aufgefordert wird.
- Andernfalls wird der Benutzer aufgefordert, sich anzumelden. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht hat, sich anzumelden.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Überprüfen Sie im folgenden Dialogfeldschritt, ob im Ergebnis des vorherigen Schritts ein Token vorhanden ist. Wenn sie nicht null ist, hat sich der Benutzer erfolgreich angemeldet.

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

Verwenden Sie in einem Dialogschritt `begin_dialog`, um die OAuth-Eingabeaufforderung zu starten, die den Benutzer zur Anmeldung auffordert.

- Wenn der Benutzer bereits angemeldet ist, wird ein Tokenantwortereignis generiert, ohne dass der Benutzer dazu aufgefordert wird.
- Andernfalls wird der Benutzer aufgefordert, sich anzumelden. Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht hat, sich anzumelden.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Überprüfen Sie im folgenden Dialogfeldschritt, ob im Ergebnis des vorherigen Schritts ein Token vorhanden ist. Wenn sie nicht null ist, hat sich der Benutzer erfolgreich angemeldet.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**dialogs/logout_dialog.py**

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

## <a name="code-sample"></a>Codebeispiel

Dieser Abschnitt enthält ein Beispiel für botauthentifizierung v3 SDK.

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Bot-Authentifizierung | In diesem Beispiel wird gezeigt, wie Sie mit der Authentifizierung in einem Bot für Teams beginnen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| Registerkarten-, Bot- und Nachrichtenerweiterungs-SSO (ME) | Dieses Beispiel zeigt SSO für Tab, Bot und ME – Suche, Aktion, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Nicht verfügbar |

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
