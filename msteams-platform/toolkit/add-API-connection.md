---
title: Integrieren vorhandener APIs von Drittanbietern
author: MuyangAmigo
description: In diesem Artikel erfahren Sie, wie das Toolkit Ihnen beim Bootstrap-Beispielzugriff auf vorhandene APIs hilft. Sie enthält eine Liste der verschiedenen Authentifizierungstypen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
ms.openlocfilehash: 6377f7d8a38054dacca76c0f87e39e51f466d925
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833142"
---
# <a name="integrate-existing-third-party-apis"></a>Integrieren vorhandener APIs von Drittanbietern

Das Teams-Toolkit unterstützt Sie beim Zugriff auf vorhandene APIs zum Erstellen von Teams-Anwendungen. Diese APIs werden von Ihrer Organisation oder einem Drittanbieter entwickelt. Wenn Sie teams Toolkit verwenden, um eine Verbindung mit einer vorhandenen API herzustellen, führt Teams Toolkit die folgende Funktion aus:

* Generieren Sie Beispielcode unter `./bot` oder `./api` im Ordner.
* Fügen Sie einen Verweis auf das `@microsoft/teamsfx` Paket zu `package.json`hinzu.
* Fügen Sie Anwendungseinstellungen für Ihre API in  `.env.teamsfx.local` hinzu, die das lokale Debuggen konfiguriert.

## <a name="steps-to-connect-to-api"></a>Schritte zum Herstellen einer Verbindung mit der API

Sie können eine API-Verbindung mithilfe von Visual Studio Code und dem CLI-Befehl hinzufügen.

### <a name="add-api-connection-using-visual-studio-code"></a>Hinzufügen einer API-Verbindung mit Visual Studio Code

Die folgenden Schritte helfen Ihnen beim Hinzufügen einer API-Verbindung mithilfe von Visual Studio Code:

1. Öffnen Sie Visual Studio Code.
2. Wählen Sie auf der Visual Studio Code-Symbolleiste das Symbol für die Teams :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="Toolkit-API"::: aus.
3. Wählen Sie unter **ENTWICKLUNG** **die Option Features hinzufügen** aus:

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-add-features.png" alt-text="API-Features hinzufügen":::

    * Sie können auch die Befehlspalette öffnen und **Teams: Cloudressourcen hinzufügen** eingeben.

4. Wählen Sie im Popupfenster die **API-Verbindung** aus, die Sie Ihrem Teams-App-Projekt hinzufügen möchten:

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-select-features.png" alt-text="API-Auswahlfeatures":::

5. Wählen Sie **OK** aus.

6. Geben Sie endpunkt für die API ein. Sie wird den lokalen Anwendungseinstellungen des Projekts hinzugefügt und ist die Basis-URL für API-Anforderungen.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-endpoint.png" alt-text="API-Endpunkt":::

     > [!NOTE]
     > Stellen Sie sicher, dass der Endpunkt eine gültige HTTP-URL ist.

7. Wählen Sie die Komponente aus, die auf die API zugreift.

8. Wählen Sie **OK** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-invoke.png" alt-text="API-Aufruf":::

9. Geben Sie einen Alias für die API ein. Der Alias generiert einen Anwendungseinstellungsnamen für die API, der der lokalen Anwendungseinstellung des Projekts hinzugefügt wird.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-alias.png" alt-text="API-Alias":::

10. Wählen Sie die erforderliche Authentifizierung für die API-Anforderung aus dem **API-Authentifizierungstyp** aus. Es generiert den entsprechenden Beispielcode und fügt basierend auf Ihrer Auswahl entsprechende lokale Anwendungseinstellungen hinzu.

     :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/myAPI connection.png" alt-text="API-Authentifizierung":::

     Basierend auf dem ausgewählten Authentifizierungstyp sind die folgenden Schritte erforderlich, um die zusätzliche Konfiguration auszuführen.

# <a name="basic"></a>[Basic](#tab/basic)

* Geben Sie den Benutzernamen für die Standardauthentifizierung ein.

  Nun wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="certification"></a>[Zertifizierung](#tab/certification)

   Nun wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="azure-active-directory"></a>[Azure Active Directory](#tab/AAD)

  Nun wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="api-key"></a>[API-Schlüssel](#tab/apikey)

* Wählen Sie die erforderliche API-Schlüsselposition in der Anforderung aus.

* Geben Sie einen API-Schlüsselnamen ein.

  Nun wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="custom-auth-implementation"></a>[Implementierung der benutzerdefinierten Authentifizierung](#tab/CustomAuthImplementation)

  Nun wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

---

## <a name="add-api-connection-using-cli"></a>Hinzufügen einer API-Verbindung mithilfe der CLI

Der Basisbefehl dieses Features ist `teamsfx add api-connection [authentication type]`. Die folgende Tabelle enthält eine Liste der verschiedenen Authentifizierungstypen und deren entsprechende Beispielbefehle:

 > [!TIP]
 > Sie können verwenden `teamsfx add api-connection [authentication type] -h` , um hilfedokument zu erhalten.

   |**Authentifizierungstyp**|**Beispielbefehl**|
   |-----------------------|------------------|
   |Standard|teamsfx add api-connection basic--endpoint <https://example.com> --component bot---alias example--user-name exampleuser--interactive false|
   |API-Schlüssel|teamsfx add api-connection apikey--endpoint <https://example.com> --component bot---alias example---key-location header---key-name example-key-name--interactive false|
   |Azure AD|teamsfx add api-connection aad--endpoint <https://example.com> --component bot--alias example---app-type custom--tenant-id your_tenant_id-app-id your_app_id-interactive false|
   |Zertifikat|teamsfx add api-connection cert---endpoint <https://example.com> --component bot---alias example--interactive false|
   |Benutzerdefiniert|teamsfx add api-connection custom--endpoint <https://example.com> --component bot---alias example--interactive false|

---

## <a name="directory-structure-updates-to-your-project"></a>Verzeichnisstrukturaktualisierungen für Ihr Projekt

 Das Teams-Toolkit ändert `bot` oder `api` den Ordner basierend auf Ihrer Auswahl:

1. Datei generieren `{your_api_alias}.js/ts` . Die Datei initialisiert einen API-Client für Ihre API und exportiert den API-Client.

2. Fügen Sie `@microsoft/teamsfx` paket zu hinzu `package.json`. Das Paket bietet Unterstützung für die allgemeinen API-Authentifizierungsmethoden.

3. Fügen Sie Umgebungsvariablen zu hinzu `.env.teamsfx.local`. Dabei handelt es sich um die Konfigurationen für den ausgewählten Authentifizierungstyp. Der generierte Code liest Werte aus den Umgebungsvariablen.

## <a name="advantages"></a>Vorteile

Teams Toolkit unterstützt Sie beim Bootstrap-Beispielcode für den Zugriff auf die APIs, wenn Sie nicht über sprachgerechte SDKs für den Zugriff auf diese APIs verfügen.

## <a name="see-also"></a>Siehe auch

[Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
