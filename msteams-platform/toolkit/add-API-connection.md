---
title: Verbinden vorhandenen APIs
author: MuyangAmigo
description: In diesem Artikel erfahren Sie, wie Toolkit Ihnen beim Bootstrap-Beispielzugriff auf vorhandene APIs hilft. Es enthält eine Liste verschiedener Authentifizierungstypen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
ms.openlocfilehash: 2e00991f42b85e0e053fd94e68298c819a14a730
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66124004"
---
# <a name="add-api-connection-to-teams-app"></a>Hinzufügen einer API-Verbindung zur Teams-App

Teams Toolkit hilft Ihnen beim Zugriff auf vorhandene APIs zum Erstellen Teams Anwendungen. Diese APIs werden von Ihrer Organisation oder von Drittanbietern entwickelt.

## <a name="advantage"></a>Vorteil

Teams Toolkit hilft Ihnen beim Bootstrap-Beispielcode für den Zugriff auf die APIs, wenn Sie nicht über sprachgerechte SDKs für den Zugriff auf diese APIs verfügen.

## <a name="connect-to-the-api"></a>Verbinden zur API

Wenn Sie Teams Toolkit zum Herstellen einer Verbindung mit einer vorhandenen API verwenden, führt Teams Toolkit die folgende Funktion aus:

* Generieren Sie Beispielcode unter `./bot` oder `./api` ordner.
* Fügen Sie dem Paket `package.json`einen Verweis hinzu`@microsoft/teamsfx`.
* Fügen Sie Anwendungseinstellungen für Ihre API hinzu, die  `.env.teamsfx.local` das lokale Debuggen konfigurieren.

### <a name="connect-to-api-in-visual-studio-code"></a>Verbinden der API in Visual Studio Code

* Sie können eine API-Verbindung mit Teams Toolkit in Visual Studio Code hinzufügen:

    1. Öffnen Sie Visual Studio Code.
    2. Wählen Sie Teams Symbol der :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="Toolkit-API"::: in der linken Navigationsleiste aus.
    3. Wählen Sie unter **ENTWICKLUNG** **die Option "Features hinzufügen"** aus:

        :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-add-features.png" alt-text="API-Add-Features":::

       * Sie können auch die Befehlspalette öffnen und **Teams eingeben: Hinzufügen von Cloudressourcen**.

    4. Wählen Sie im Popup die **API-Verbindung** aus, die Sie ihrem Teams App-Projekt hinzufügen möchten:

        :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-select-features.png" alt-text="API-Auswahlfeatures":::

    5. Wählen Sie **OK** aus.

    6. Geben Sie den Endpunkt für die API ein. Es wird den lokalen Anwendungseinstellungen des Projekts hinzugefügt und ist die Basis-URL für API-Anforderungen.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-endpoint.png" alt-text="API-Endpunkt":::

         > [!NOTE]
         > Stellen Sie sicher, dass der Endpunkt eine gültige HTTP-URL ist.

    7. Wählen Sie die Komponente aus, die auf die API zugreift.

    8. Wählen Sie **OK** aus.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-invoke.png" alt-text="API-Aufruf":::

    9. Geben Sie einen Alias für die API ein. Der Alias generiert einen Anwendungseinstellungsnamen für die API, der der lokalen Anwendungseinstellung des Projekts hinzugefügt wird.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-alias.png" alt-text="API-Alias":::

    10. Wählen Sie die erforderliche Authentifizierung für die API-Anforderung aus dem **API-Authentifizierungstyp** aus. Es generiert entsprechenden Beispielcode und fügt basierend auf Ihrer Auswahl entsprechende lokale Anwendungseinstellungen hinzu.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-auth.png" alt-text="API-Authentifizierung":::

         > [!NOTE]
         > Basierend auf dem ausgewählten Authentifizierungstyp ist eine zusätzliche Konfiguration erforderlich.

### <a name="api-connection-in-teamsfx-cli"></a>API-Verbindung in TeamsFx CLI

Der Basisbefehl dieses Features lautet `teamsfx add api-connection [authentication type]`. Die folgende Tabelle enthält eine Liste der verschiedenen Authentifizierungstypen und deren entsprechende Beispielbefehle:

 > [!Tip]
 > Sie können das Hilfedokument abrufen `teamsfx add api-connection [authentication type] -h` .

   |**Authentifizierungstyp**|**Beispielbefehl**|
   |-----------------------|------------------|
   |Standard|teamsfx add api-connection basic --endpoint <https://example.com> --component bot --alias example--user-name exampleuser --interactive false|
   |API-Schlüssel|teamsfx add api-connection apikey --endpoint <https://example.com> --component bot --alias example --key-location header --key-name example-key-name --interactive false|
   |Azure AD|teamsfx add api-connection aad --endpoint <https://example.com> --component bot --alias example --app-type custom --tenant-id your_tenant_id --app-id your_app_id --interactive false|
   |Zertifikat|teamsfx add api-connection cert --endpoint <https://example.com> --component bot --alias example --interactive false|
   |Benutzerdefiniert|teamsfx add api-connection custom --endpoint <https://example.com> --component bot --alias example --interactive false|

## <a name="understand-toolkit-updates-to-your-project"></a>Grundlegendes zu Toolkit-Updates für Ihr Projekt

 Teams Toolkit ändert `bot` oder `api` ändert den Ordner basierend auf Ihrer Auswahl:

1. Datei generieren `{your_api_alias}.js/ts` . Die Datei initialisiert einen API-Client für Ihre API und exportiert den API-Client.

2. Paket hinzufügen `@microsoft/teamsfx` zu `package.json`. Das Paket bietet Unterstützung für die allgemeinen API-Authentifizierungsmethoden.

3. Fügen Sie Umgebungsvariablen zu `.env.teamsfx.local`hinzu. Sie sind die Konfigurationen für den ausgewählten Authentifizierungstyp. Der generierte Code liest Werte aus den Umgebungsvariablen.

## <a name="test-api-connection-in-local-environment"></a>Testen der API-Verbindung in der lokalen Umgebung

Die folgenden Schritte helfen beim Testen der API-Verbindung in der lokalen Umgebung des Teams Toolkits:

 1. **Ausführen npm Installation**

    Führen Sie `npm install` die Datei oder `api` den Ordner aus`bot`, um hinzugefügte Pakete zu installieren.

 2. **Hinzufügen von API-Anmeldeinformationen zu den lokalen Anwendungseinstellungen**

    Teams Toolkit fragt nicht nach Anmeldeinformationen, lässt aber Platzhalter in der lokalen Anwendungseinstellungsdatei zurück. Ersetzen Sie die Platzhalter durch die entsprechenden Anmeldeinformationen für den Zugriff auf die API. Die lokale Anwendungseinstellungsdatei ist die `.env.teamsfx.local` Datei im ordner oder `api` im `bot` Ordner.

 3. **Verwenden des API-Clients zum Erstellen von API-Anforderungen**

    Importieren Sie den API-Client aus dem Quellcode, der Zugriff auf die API benötigt:

    ```BASH
    import { yourApiClient } from '{relative path to the generated file}'
    ```

 4. **Generieren von HTTP-Anforderungen für die Ziel-API (mit Axios)**

    Der generierte API-Client ist ein Axios-API-Client. Verwenden Sie den Axios-Client, um Anforderungen an die API zu senden.

     > [!Note]
     > [Axios](https://www.npmjs.com/package/axios) ist ein beliebtes nodejs-Paket, das Sie bei HTTP-Anforderungen unterstützt. Weitere Informationen zum Erstellen von HTTP(s)-Anforderungen finden Sie in der [Axios-Beispieldokumentation](https://axios-http.com/docs/example) , um zu erfahren, wie Sie HTTP(s) erstellen.

## <a name="deploy-your-application-to-azure"></a>Bereitstellen Ihrer Anwendung in Azure

Um Ihre Anwendung in Azure bereitzustellen, müssen Sie die Authentifizierung den Anwendungseinstellungen für die entsprechende Umgebung hinzufügen. Ihre API kann z. B. unterschiedliche Anmeldeinformationen für `dev` und `prod`haben. Konfigurieren Sie basierend auf den Umgebungsanforderungen Teams Toolkit.

Teams Toolkit konfiguriert Ihre lokale Umgebung. Der Bootstrapped-Beispielcode enthält Kommentare, die Ihnen mitteilen, welche App-Einstellungen Sie konfigurieren müssen. Weitere Informationen zu Anwendungseinstellungen finden [Sie unter Hinzufügen von App-Einstellungen](https://github.com/OfficeDev/TeamsFx/wiki/%5BDocument%5D-Add-app-settings).

## <a name="advanced-scenarios"></a>Erweiterte Szenarien

  Im folgenden Abschnitt werden erweiterte Szenarien erläutert:

<br>

<details>
<summary><b>Benutzerdefinierter Authentifizierungsanbieter</b></summary>

Neben dem im `@microsoft/teamsfx` Paket enthaltenen Authentifizierungsanbieter können Sie auch einen benutzerdefinierten Authentifizierungsanbieter implementieren, der `AuthProvider` die Schnittstelle implementiert und in `createApiClient(..)` der Funktion verwendet:

```Bash
import { AuthProvider } from '@microsoft/teamsfx'

class CustomAuthProvider implements AuthProvider {
    constructor() {
        // You can add necessary parameters for your customized logic in constructor
    }

    AddAuthenticationInfo: (config: AxiosRequestConfig) => Promise<AxiosRequestConfig> = async (
        config
    ) => {
        /*
        * The config parameter contains all the request information and can be updated to include extra authentication info.
        * Refer https://axios-http.com/docs/req_config for detailed document for the config object.
        * 
        * Add your customized logic that returns updated config
        */
    };
}
```

</details>
<details>
<summary><b>Verbinden zu APIs für Azure AD-Berechtigungen</b></summary>
Azure AD authentifiziert einige Dienste. Die folgende Liste hilft beim Zugriff auf diese Dienste zum Konfigurieren von API-Berechtigungen.

* [Verwenden Access Control Listen (ACLs)](#access-control-lists-acls)
* [Verwenden von Azure AD-Anwendungsberechtigungen](#azure-ad-application-permissions)

Das Abrufen eines Tokens mit den richtigen Ressourcenbereichen für Ihre API hängt von der Implementierung der API ab.

Sie können die Schritte ausführen, um auf diese APIs zuzugreifen, während Sie Folgendes verwenden:

#### <a name="access-control-lists-acls"></a>Access Control Listen (ACLs)

   1. Starten Sie das lokale Debuggen in der Cloudumgebung für Ihr Projekt. Sie erstellt eine Azure AD-Anwendungsregistrierung für Ihre Teams Anwendung.
  
   2. Öffnen `.fx/states/state.{env}.json`Sie , und notieren Sie sich den Wert von `clientId` under-Eigenschaft `fx-resource-aad-app-for-teams` .

   3. Geben Sie die Client-ID für den API-Anbieter an, um ACLs im API-Dienst zu konfigurieren.

#### <a name="azure-ad-application-permissions"></a>Azure AD-Anwendungsberechtigungen

  1. Öffnen `templates/appPackage/aad.template.json` Sie die Eigenschaft, und fügen Sie der `requiredResourceAccess` Eigenschaft folgenden Inhalt hinzu:

```JSON
 {
     "resourceAppId": "The AAD App Id for the service providing the API you are connecting to",
     "resourceAccess": [
         {
             "id": "Target API's application permission Id",
             "type": "Role"
         }
     ]
 }
```

   2. Starten Sie das lokale Debuggen in der Cloudumgebung für Ihr Projekt. Sie erstellt eine Azure AD-Anwendungsregistrierung für Ihre Teams Anwendung.

   3. Öffnen `.fx/states/state.{env}.json` Und notieren Sie sich den Wert von `clientId` under-Eigenschaft `fx-resource-aad-app-for-teams` . Es ist die Anwendungsclient-ID.

   4. Erteilen der Administratorzustimmung für die erforderliche Anwendungsberechtigung. Weitere Informationen finden Sie [unter "Administratorzustimmung erteilen"](/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-in-app-registrations).

        > [!NOTE]
        > Verwenden Sie für Anwendungsberechtigungen Ihre Client-ID.
        >
</details>

## <a name="see-also"></a>Siehe auch

* [Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
