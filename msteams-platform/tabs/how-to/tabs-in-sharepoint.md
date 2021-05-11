---
title: Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint
author: laujan
description: Bereitstellen der vorhandenen registerkarte Teams in SharePoint als SharePoint-Framework Web part.
keywords: Teams registerkarten sharepoint framework development
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a2ea6c470f094a9d7b8617a210559e911f5f81c9
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058481"
---
# <a name="add-teams-tab-to-sharepoint"></a>Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint 

Sie können eine umfassende Integrationserfahrung zwischen Microsoft Teams und SharePoint erhalten, indem Sie eine registerkarte Microsoft Teams in SharePoint web part SPFx hinzufügen. In diesem Dokument erfahren Sie, wie Sie eine Registerkarte aus einer Microsoft Teams Beispiel-App nehmen und in einer SharePoint. 

## <a name="rich-integration-between-teams-and-sharepoint"></a>Umfassende Integration zwischen Teams und SharePoint

Mit der Novemberversion von Teams und SharePoint-Framework v.1.7 verfügen Entwickler über zwei leistungsstarke Funktionen:

<ul  class="panelContent cardsC">
<li>
    <a href="#introduction">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/image084.png" alt="tab-in-sharepoint view"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Teams Registerkarten in SharePoint</h3>
                        <p>Erstellen Sie umfassende App-SharePoint, indem Sie Ihre Teams in Sharepoint (in diesem Artikel) verwenden.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" alt="web-part-exposed-as-a-tab" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>SharePoint-Framework in Teams</h3>
                        <p>Bringen Sie SharePoint Webparts zu Teams und lassen SharePoint Hosting für Sie verwalten.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Teams Registerkarten in SharePoint

Mit SharePoint-Framework v.1.7 können Sie Ihre registerkarten Teams in SharePoint. Wenn in SharePoint gehostete Registerkarten  eine ähnliche vollständige Seitenerfahrung erhalten, werden alle Features von Teams-Registerkarten verfügbar gemacht, während der Kontext und die Vertrautheit einer SharePoint bleiben.

### <a name="sharepoint-framework-in-teams"></a>SharePoint-Framework in Teams

Sie können ihre Registerkarten Microsoft Teams auch mithilfe von SharePoint-Framework. SharePoint-Framework Webparts werden innerhalb von SharePoint gehostet, ohne dass externe Dienste wie Azure benötigt werden. Für SharePoint Entwickler vereinfacht dies den Entwicklungsprozess für Teams Registerkarten erheblich. Weitere Informationen zu SharePoint-Framework in Teams finden Sie unter Verwenden der SharePoint-Framework [in Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Einführung

Die hier verwendete Registerkarte wird bereits in Azure gehostet, um sich auf die erforderliche Integrationsarbeit zu konzentrieren.

Die verwendete Beispiel-App ist eine Talentverwaltungsanwendung. Es verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team. Erstellen Sie ein Teams-App, und laden Sie sie in Teams. Erstellen Sie keine echte Talentverwaltungsanwendung.

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

* Erreichen SharePoint Benutzer mit ihrer vorhandenen Teams Registerkarte.
* Hochladen Ihr App-Manifest direkt in Ihren SharePoint-App-Katalog. [Teams Anwendungspakete](~/concepts/build-and-test/apps-package.md) werden jetzt von der SharePoint.
* Die Benutzer konfigurieren die Registerkarte auf einer Seite genau wie alle anderen SharePoint Web part.
* Ihre Registerkarte kann auf ihren [Kontext](~/tabs/how-to/access-teams-context.md) zugreifen, wie er kann, wenn sie innerhalb der Teams.

**So fügen Sie Teams Registerkarte zu SharePoint**

Führen Sie die folgenden Schritte aus, um Teams Registerkarte zu SharePoint:

## <a name="1-test-the-sample-app"></a>1. Testen der Beispiel-App

Laden Sie das [Beispiel-App-Manifest herunter.](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)

1. Öffnen Sie Microsoft Teams.
1. Wählen Sie **das Appstore-Symbol** unten links neben der Registerkarte aus.
1. Wählen **Hochladen eine benutzerdefinierte App** unten links aus. In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:  

    ![Hochladen einer benutzerdefinierten App](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. Die datei, die hochgeladen werden soll, befindet sich im **Ordner Downloads.** Es wird als TalentMgmt-Azure.zip. In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:
 
    ![TalentMgmt in Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. Sie können den Installations- oder Zustimmungsbildschirm für die Talentverwaltungs-App sehen. Wählen Sie das Team aus, das Sie installieren möchten. 
1. Wählen Sie **installieren** aus, und beginnen Sie mit dem Experimentieren mit der App.

## <a name="2-use-teams-tab-in-sharepoint"></a>2. Verwenden Teams Registerkarte in SharePoint

1. Hochladen Sie Ihr Teams-App-Paket in Ihrem SharePoint-App-Katalog, indem Sie `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` besuchen. Beispiel: `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.

1. Wenn Sie dazu aufgefordert werden, aktivieren **Sie Diese Lösung für alle Websites in der Organisation verfügbar machen.**
In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

   ![Registerkarten in der Sharepoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. Erstellen Sie auf Ihrer Website eine neue Seite, indem Sie oben rechts die Zahnradschaltfläche auswählen und dann **Seite hinzufügen auswählen.**
In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

   ![Sharepoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. Sie können die Erstellungserfahrung SharePoint Seiten anzeigen. Benennen Sie Ihre Seite als **Registerkarte "Teams".**

1. Öffnen Sie die Web part-Toolbox, indem Sie die Schaltfläche drücken, und wählen Sie Teams `+` Registerkarte namens Contoso HR **aus.** Webparts werden alphabetisch sortiert. Wenn es sich um eine lange Liste handelt, können Sie die Suchleiste verwenden, um sie zu finden. Dadurch wird ein Webteil im Zeichenbereich erstellt, das ihre Teams enthält. In der folgenden Abbildung wird die Registerkartenansicht angezeigt:

   ![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. Drücken Sie die **Schaltfläche Veröffentlichen,** nachdem Sie die Bearbeitung abgeschlossen haben.

1. Wählen **Sie Seite zur Navigation hinzufügen aus,** um einen Schnellverweis auf Ihre Seite in der linken Navigationsleiste zu haben. In der folgenden Abbildung wird die Registerkarte in Sharepoint angezeigt: 

   ![Registerkarte im Sharepoint-Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a>3. Erkunden von App-Seiten in SharePoint

Nachdem Ihre Seite veröffentlicht wurde, können Sie erkunden, wie Sie Ihre [Teams-App](/sharepoint/dev/spfx/web-parts/single-part-app-pages)in eine vollständigere Umgebung innerhalb von SharePoint. Dadurch wird die aktuelle Seite in eine App-Seite konvertiert, die das normale SharePoint seitenlayout mit einer vollständigen Seitenerfahrung für die Registerkarte Teams zeigt. 

Die folgende Abbildung zeigt die vollständige Erfahrung Teams App in Sharepoint: ![ Abbildung von Registerkarten in Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Codebeispiel
| **Beispielname** | **Beschreibung** | **SPFx** |
|-----------------|-----------------|----------|
| SPFx Web part | SPFx web part samples for tabs, channels, and groups. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a>Siehe auch

- [Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

- [Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)

- [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
