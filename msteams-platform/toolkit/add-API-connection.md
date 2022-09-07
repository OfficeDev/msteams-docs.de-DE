---
title: Integrieren vorhandener Drittanbieter-APIs
author: MuyangAmigo
description: In diesem Artikel erfahren Sie, wie Toolkit Ihnen beim Bootstrap-Beispielzugriff auf vorhandene APIs hilft. Es enthält eine Liste verschiedener Authentifizierungstypen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
ms.openlocfilehash: 5933227f9ba4c8b684d624a8857304c044761578
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616809"
---
# <a name="integrate-existing-third-party-apis"></a>Integrieren vorhandener Drittanbieter-APIs

Das Teams-Toolkit hilft Ihnen beim Zugriff auf vorhandene APIs zum Erstellen von Teams-Anwendungen. Diese APIs werden von Ihrer Organisation oder von Drittanbietern entwickelt. Wenn Sie das Teams-Toolkit verwenden, um eine Verbindung mit einer vorhandenen API herzustellen, führt das Teams-Toolkit die folgende Funktion aus:

* Generieren Sie Beispielcode unter `./bot` oder `./api` ordner.
* Fügen Sie dem Paket `package.json`einen Verweis hinzu`@microsoft/teamsfx`.
* Fügen Sie Anwendungseinstellungen für Ihre API hinzu, die  `.env.teamsfx.local` das lokale Debuggen konfigurieren.

## <a name="steps-to-connect-to-api"></a>Schritte zum Herstellen einer Verbindung mit der API

Sie können eine API-Verbindung mit Visual Studio Code und dem CLI-Befehl hinzufügen.

### <a name="add-api-connection-using-visual-studio-code"></a>Hinzufügen einer API-Verbindung mit Visual Studio Code

Die folgenden Schritte helfen Ihnen beim Hinzufügen einer API-Verbindung mit Visual Studio Code:

1. Öffnen Sie Visual Studio Code.
2. Wählen Sie :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="das Symbol der Teams-Toolkit-API"::: auf der Visual Studio Code-Symbolleiste aus.
3. Wählen Sie unter **ENTWICKLUNG** **die Option "Features hinzufügen"** aus:

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-add-features.png" alt-text="API-Add-Features":::

    * Sie können auch die Befehlspalette öffnen und **Teams eingeben: Cloudressourcen hinzufügen**.

4. Wählen Sie im Popup die **API-Verbindung** aus, die Sie Ihrem Teams-App-Projekt hinzufügen möchten:

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

     :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/myAPI connection.png" alt-text="API-Authentifizierung":::

     Basierend auf dem ausgewählten Authentifizierungstyp sind die folgenden Schritte erforderlich, um eine zusätzliche Konfiguration auszuführen.

# <a name="basic"></a>[Basic](#tab/basic)

* Geben Sie den Benutzernamen für die einfache Authentifizierung ein.

  Jetzt wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="certification"></a>[Zertifizierung](#tab/certification)

   Jetzt wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="azure-active-directory"></a>[Azure Active Directory](#tab/AAD)

  Jetzt wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="api-key"></a>[API-Schlüssel](#tab/apikey)

* Wählen Sie die erforderliche API-Schlüsselposition in der Anforderung aus.

* Geben Sie einen API-Schlüsselnamen ein.

  Jetzt wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

# <a name="custom-auth-implementation"></a>[Benutzerdefinierte Authentifizierungsimplementierung](#tab/CustomAuthImplementation)

  Jetzt wurde der Beispielcode generiert, um Ihre API bei bot\myAPI.js aufzurufen.

---

## <a name="add-api-connection-using-cli"></a>Hinzufügen einer API-Verbindung mithilfe von CLI

Der Basisbefehl dieses Features lautet `teamsfx add api-connection [authentication type]`. Die folgende Tabelle enthält eine Liste der verschiedenen Authentifizierungstypen und deren entsprechende Beispielbefehle:

 > [!TIP]
 > Sie können das Hilfedokument abrufen `teamsfx add api-connection [authentication type] -h` .

   |**Authentifizierungstyp**|**Beispielbefehl**|
   |-----------------------|------------------|
   |Standard|teamsfx add api-connection basic--endpoint <https://example.com> --component bot--alias example--user-name exampleuser--interactive false|
   |API-Schlüssel|teamsfx add api-connection apikey---endpoint <https://example.com> --component bot--alias example--key-location header--key-name example-key-name--interactive false|
   |Azure AD|teamsfx add api-connection aad--endpoint <https://example.com> --component bot--alias example--app-type custom--tenant-id your_tenant_id--app-id your_app_id--interactive false|
   |Zertifikat|teamsfx add api-connection cert--endpoint <https://example.com> --component bot--alias example--interactive false|
   |Benutzerdefiniert|teamsfx add api-connection custom--endpoint <https://example.com> --component bot--alias example--interactive false|

---

## <a name="directory-structure-updates-to-your-project"></a>Verzeichnisstrukturupdates für Ihr Projekt

 Teams-Toolkit ändert `bot` oder `api` Ordner basierend auf Ihrer Auswahl:

1. Datei generieren `{your_api_alias}.js/ts` . Die Datei initialisiert einen API-Client für Ihre API und exportiert den API-Client.

2. Paket hinzufügen `@microsoft/teamsfx` zu `package.json`. Das Paket bietet Unterstützung für die allgemeinen API-Authentifizierungsmethoden.

3. Fügen Sie Umgebungsvariablen zu `.env.teamsfx.local`hinzu. Sie sind die Konfigurationen für den ausgewählten Authentifizierungstyp. Der generierte Code liest Werte aus den Umgebungsvariablen.

## <a name="advantages"></a>Vorteile

Das Teams-Toolkit hilft Ihnen beim Bootstrap-Beispielcode für den Zugriff auf die APIs, wenn Sie nicht über sprachgerechte SDKs für den Zugriff auf diese APIs verfügen.

## <a name="see-also"></a>Siehe auch

* [Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
