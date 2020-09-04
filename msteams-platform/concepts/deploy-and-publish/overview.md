---
title: Verteilen Ihrer App
description: Beschreibt die drei Optionen zum Verteilen Ihrer APP.
keywords: Teams veröffentlichen Store Office Distribute AppSource querladen Upload-App
ms.openlocfilehash: d3fd81e69f74b6332d9033412a7b6688239cd801
ms.sourcegitcommit: 02ab2cb7820dc8665bb4ec6a1a40c3b8b8f29d66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2020
ms.locfileid: "47340959"
---
# <a name="distribute-your-microsoft-teams-app"></a>Verteilen Ihrer Microsoft Teams-App

Nachdem Sie Ihre APP erstellt haben, gibt es drei Optionen für die Verteilung:

1. [Laden Sie Ihre APP direkt hoch](#upload-your-app-directly).
2. [Veröffentlichen Sie Ihre APP im App-Katalog Ihrer Organisation](#publish-to-your-organizations-app-catalog).
3. [Veröffentlichen Sie Ihre APP über AppSource](#publish-to-appsource).

## <a name="enterprise-organizations"></a>Unternehmensorganisationen

### <a name="upload-your-app-directly"></a>Direktes Hochladen Ihrer APP

Dies ist die einfachste Möglichkeit zum Testen und Verwenden Ihrer APP. Wenn Sie der Teambesitzer sind und/oder [benutzerdefinierte apps hochladen aktiviert ist](/microsoftteams/admin-settings), können Sie die APP [direkt hochladen (oder querladen)](./apps-upload.md) und sofort mit der Anwendung beginnen. Wenn Sie die APP jedoch für andere freigeben möchten, müssen Sie Ihr App-Paket senden und Sie bitten, es unabhängig voneinander hochzuladen.

Wenn Sie Ihre APP breiter verteilen möchten, stellt Microsoft Teams einen in-App-Katalog bereit, mit dem Benutzer qualitativ hochwertige Teams-Apps suchen oder entdecken können. Damit Ihre Lösung im Katalog verfügbar ist, müssen Sie entweder im [App-Katalog Ihrer Organisation veröffentlichen](#publish-to-your-organizations-app-catalog) oder in [AppSource veröffentlichen](./appsource/publish.md).

### <a name="publish-to-your-organizations-app-catalog"></a>Veröffentlichen im App-Katalog Ihrer Organisation

Der APP-Katalog Ihrer Organisation enthält apps, die für Ihre Organisation eindeutig sind und vollständig unter der Kontrolle Ihrer Organisation liegen. Weitere Informationen finden Sie im Artikel veröffentlichen von [*apps im App-Katalog Ihrer Organisation*](/microsoftteams/tenant-apps-catalog-teams). Dieses Feature kann nur von Microsoft Teams-Benutzern mit Microsoft Office 365 mandantenadministrator rechten verwaltet werden.

### <a name="publish-to-appsource"></a>Veröffentlichen in AppSource

AppSource (früher bekannt als Office Store) bietet einen geeigneten Ort zum Verteilen Ihrer Microsoft Teams-App sowie andere Office 365 Erweiterungstypen wie Office-Add-Ins und SharePoint-Add-Ins. Befolgen Sie unsere Richtlinien, um [Ihre APP an AppSource zu übermitteln](./appsource/publish.md).

## <a name="government-community-cloud-gcc-organizations"></a>GCC-Organisationen (Government Community Cloud)

### <a name="upload-your-custom-app-directly-to-teams"></a>Laden Sie Ihre benutzerdefinierte App direkt in Microsoft Teams hoch.

 Als gcc-mandantenadministrator entscheiden Sie, ob Sie eine benutzerdefinierte app in Ihre Mandanten Umgebung hochladen und ob Sie Sie in Ihrem Mandanten-App-Katalog veröffentlichen möchten. Microsoft besitzt oder steuert Ihre benutzerdefinierten Anwendungen nicht, daher müssen Sie sicherstellen, dass alle Endpunkte mit den Anforderungen Ihrer Organisation konform sind. Wenn die APP-Lösung außerdem eine bot-oder Nachrichten Erweiterung enthält, müssen Sie die bot- [Framework](https://dev.botframework.com/) -Registrierung wie folgt abschließen:

1. Wählen Sie auf der Seite mit **Kanälen verbinden** unter **Add a Featured Channel**die Option **Teams**aus.
1. Navigieren Sie zur Seite **configure MSTeams** (*Siehe* unten).
1. Wählen Sie unter **Messaging** das Optionsfeld **Microsoft Teams for Government Customers** aus.
1. Klicken Sie in der unteren linken Ecke der Seite auf **Speichern**.  

>[!IMPORTANT]
> Sie können die Geschäfts Konfiguration von Teams nicht verwenden, um Ihre benutzerdefinierte app in eine gcc-Umgebung hochzuladen/querladen, Sie müssen das Optionsfeld **Microsoft Teams for Government Customers** für eine gcc-konforme Konfiguration auswählen.

![Microsoft Teams-Messaging-Konfigurationsseite](../../assets/images/gcc-configure.png)

> [!NOTE]
>
> * Die oben beschriebenen Upload-Anweisungen für gcc-Umgebungen gelten für benutzerdefinierte Microsoft Teams-apps. </br>
> * Kompatible Microsoft-apps sind in der gcc-Umgebung standardmäßig in Teams aktiviert.
> * Drittanbieter-apps sind auf Mandantenebene deaktiviert und sollten über die [App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies)Ihrer Organisation verwaltet werden. Stellen Sie sicher, dass Sie alle Drittanbieter-apps überprüfen, um sicherzustellen, dass Sie mit den Richtlinien und Verfahren Ihrer Organisation übereinstimmen.

> [!TIP]
>
> Microsoft 365-Entwickler Partner bieten Sicherheits-, Datenverarbeitungs-und Kompatibilitätsdetails für Ihre Drittanbieter-Teams-Apps über das [Microsoft 365-App-Zertifizierungsprogramm](/microsoft-365-app-certification/overview). *Siehe auch* [Microsoft Teams-App-Zertifizierung](/microsoftteams/platform/concepts/deploy-and-publish/appsource/post-publish/application-certification).
</br></br>
