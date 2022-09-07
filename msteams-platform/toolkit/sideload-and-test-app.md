---
title: Querladen und Testen der App in der Teams-Umgebung
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie die App in einer anderen Umgebung querladen und testen.
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: ee1d3ee3a4f545a6c988c421fb18626a4a7276b7
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617218"
---
# <a name="sideload-and-test-app-in-teams-environment"></a>Querladen und Testen der App in der Teams-Umgebung

Nach dem Hinzufügen einer API-Verbindung können Sie die API-Verbindung in der lokalen Umgebung des Teams-Toolkits testen und Ihre Anwendung in der Cloud bereitstellen. In der CI/CD-Pipeline müssen Sie nach der Einrichtung mit einer anderen Plattform den Azure-Dienstprinzipal zum Bereitstellen und Bereitstellen von Ressourcen erstellen.

In diesem Abschnitt erfahren Sie mehr über

* [Testen der API-Verbindung in der lokalen Umgebung](#test-api-connection-in-local-environment)
* [Bereitstellen Ihrer Anwendung in Azure](#deploy-your-application-to-azure)
* [Bereitstellen und Bereitstellen von CI/CD-Ressourcen](#provision-and-deploy-cicd-resources)

## <a name="test-api-connection-in-local-environment"></a>Testen der API-Verbindung in der lokalen Umgebung

Die folgenden Schritte helfen beim Testen der API-Verbindung in der lokalen Umgebung des Teams-Toolkits:

 1. **Ausführen der npm-Installation**

    Führen Sie `npm install` die Datei oder `api` den Ordner aus`bot`, um hinzugefügte Pakete zu installieren.

 2. **Hinzufügen von API-Anmeldeinformationen zu den lokalen Anwendungseinstellungen**

    Das Teams-Toolkit fragt nicht nach Anmeldeinformationen, lässt aber Platzhalter in der lokalen Anwendungseinstellungsdatei zurück. Ersetzen Sie die Platzhalter durch die entsprechenden Anmeldeinformationen für den Zugriff auf die API. Die lokale Anwendungseinstellungsdatei ist die `.env.teamsfx.local` Datei im ordner oder `api` im `bot` Ordner.

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

Um Ihre Anwendung in Azure bereitzustellen, müssen Sie die Authentifizierung den Anwendungseinstellungen für die entsprechende Umgebung hinzufügen. Ihre API kann z. B. unterschiedliche Anmeldeinformationen für `dev` und `prod`haben. Konfigurieren Sie basierend auf den Umgebungsanforderungen das Teams-Toolkit.

Das Teams-Toolkit konfiguriert Ihre lokale Umgebung. Der Bootstrapped-Beispielcode enthält Kommentare, die Ihnen mitteilen, welche App-Einstellungen Sie konfigurieren müssen. Weitere Informationen zu Anwendungseinstellungen finden Sie unter [Hinzufügen von App-Einstellungen](https://github.com/OfficeDev/TeamsFx/wiki/%5BDocument%5D-Add-app-settings)

## <a name="provision-and-deploy-cicd-resources"></a>Bereitstellen und Bereitstellen von CI/CD-Ressourcen

Um Ressourcen für Azure innerhalb von CI/CD bereitzustellen, müssen Sie einen Azure-Dienstprinzipal erstellen und verwenden.

Führen Sie die folgenden Schritte aus, um Azure-Dienstprinzipale zu erstellen:

1. Registrieren Sie eine Microsoft Azure Active Directory (Azure AD)-Anwendung in einem einzelnen Einzelmandanten.
2. Weisen Sie Ihrer Azure AD-Anwendung eine Rolle zu, um auf Ihr Azure-Abonnement zuzugreifen. Die`Contributor`Rolle wird empfohlen.
3. Erstellen Sie ein neues Azure AD-Anwendungsgeheimnis.

> [!TIP]
> Speichern Sie Ihre Mandanten-ID, Anwendungs-ID (AZURE_SERVICE_PRINCIPAL_NAME) und den geheimen Schlüssel (AZURE_SERVICE_PRINCIPAL_PASSWORD) für die zukünftige Verwendung.

Weitere Informationen finden Sie in den [Richtlinien für Azure-Dienstprinzipale](/azure/active-directory/develop/howto-create-service-principal-portal). Es folgen die drei Möglichkeiten zum Erstellen von Dienstprinzipalen:

* [Microsoft Azure-Portal](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [Microsoft Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="see-also"></a>Siehe auch

* [Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
