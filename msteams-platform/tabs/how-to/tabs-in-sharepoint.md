---
title: Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint
author: surbhigupta
description: Bereitstellen der vorhandenen Teams-Registerkarte für SharePoint als SharePoint-Framework-Webpart.
keywords: Teams-Registerkarten für die SharePoint-Framework-Entwicklung
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 6561164f177277e76b80e3c33ee57b9383bbd527
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156410"
---
# <a name="add-teams-tab-to-sharepoint"></a>Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint 

Sie können eine umfassende Integrationserfahrung zwischen Microsoft Teams und SharePoint erzielen, indem Sie eine Microsoft Teams Registerkarte in SharePoint als SPFx Webpart hinzufügen. Dieses Dokument führt Sie durch die Verwendung einer Registerkarte aus einer Microsoft Teams Beispiel-App und deren Verwendung in SharePoint. 

## <a name="rich-integration-between-teams-and-sharepoint"></a>Umfassende Integration zwischen Teams und SharePoint

Mit der November-Version von Teams und SharePoint-Framework Version 1.7 verfügen Entwickler über zwei leistungsstarke Funktionen:

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
                        <p>Erstellen Sie umfangreiche App-Funktionen in SharePoint, indem Sie Ihre Teams-App in SharePoint (dieser Artikel) integrieren.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
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
                        <p>Bringen Sie Ihre SharePoint-Webparts in Teams, und lassen Sie SharePoint das Hosting für Sie verwalten.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Teams Registerkarten in SharePoint

Mit SharePoint-Framework Version 1.7 können Sie Ihre Teams Registerkarten in SharePoint hosten. Wenn Registerkarten in SharePoint eine ähnliche **ganzseitige Oberfläche** erhalten, werden alle Features von Teams Registerkarten verfügbar, während der Kontext und die Vertrautheit einer SharePoint Website beibehalten werden.

### <a name="sharepoint-framework-in-teams"></a>SharePoint-Framework in Teams

Sie können Ihre Microsoft Teams Registerkarten auch mit SharePoint-Framework implementieren. SharePoint-Framework Webparts werden in SharePoint gehostet, ohne dass externe Dienste wie Azure erforderlich sind. Für SharePoint Entwickler vereinfacht dies den Entwicklungsprozess für Teams Registerkarten erheblich. Weitere Informationen zu SharePoint-Framework in Teams finden Sie unter [Verwendung der SharePoint-Framework in Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Einführung

Die hier verwendete Registerkarte wird bereits in Azure gehostet, um sich auf die erforderlichen Integrationsarbeit zu konzentrieren.

Die verwendete Beispiel-App ist eine Talent management-Anwendung. Sie verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team. Erstellen Sie ein Beispiel Teams App, und laden Sie es in Teams. Erstellen Sie keine echte Talentverwaltungsanwendung.

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

* Erreichen Sie SharePoint Benutzer mit Ihrer vorhandenen Teams Registerkarte.
* Hochladen Sie Ihr App-Manifest direkt im SharePoint App-Katalog an. [Teams Anwendungspakete](~/concepts/build-and-test/apps-package.md) werden jetzt von SharePoint unterstützt.
* Die Benutzer konfigurieren die Registerkarte auf einer Seite genau wie jedes andere SharePoint Webparts.
* Ihre Registerkarte kann auf den gleichen [Kontext](~/tabs/how-to/access-teams-context.md) zugreifen wie sie kann, wenn sie innerhalb Teams ausgeführt wird.

**So fügen Sie Teams Registerkarte zu SharePoint hinzu**

Führen Sie die folgenden Schritte aus, um SharePoint Teams Registerkarte hinzuzufügen:

## <a name="1-test-the-sample-app"></a>1. Testen der Beispiel-App

Laden Sie das [Beispiel-App-Manifest herunter.](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)

1. Öffnen Sie Microsoft Teams.
1. Wählen Sie das **Appstore-Symbol** unten links auf der Registerkarte aus.
1. Wählen Sie unten links **Hochladen einer benutzerdefinierten App** aus. In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:  

    ![Hochladen einer benutzerdefinierten App](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. Die hochzuladende Datei befindet sich im **Ordner "Downloads".** Sie wird TalentMgmt-Azure.zip genannt. In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:
 
    ![TalentMgmt in Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. Sie können den Installations- oder Zustimmungsbildschirm für die Talentmanagement-App anzeigen. Wählen Sie das Team aus, das Sie installieren möchten. 
1. Wählen Sie die **Option "Installieren" aus,** und beginnen Sie mit dem Experimentieren mit der App.

## <a name="2-use-teams-tab-in-sharepoint"></a>2. Verwenden sie Teams Registerkarte in SharePoint

1. Hochladen und stellen Sie Ihr Teams-App-Paket im SharePoint App-Katalog bereit. `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` Beispiel: `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.

1. Wenn Sie dazu aufgefordert werden, aktivieren **Sie "Diese Lösung für alle Websites in der Organisation verfügbar machen".**
In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

   ![Registerkarten in der SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. Erstellen Sie auf Ihrer Website eine neue Seite, indem Sie oben rechts die Zahnradschaltfläche auswählen und dann **eine Seite hinzufügen** auswählen.
In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

   ![SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. Sie können die Erstellungsoberfläche für SharePoint Seiten anzeigen. Benennen Sie Ihre Seite als **Registerkarte "Meine Teams".**

1. Öffnen Sie die Webpart-Toolbox, indem Sie die `+` Schaltfläche auswählen, und wählen Sie Ihre Teams Registerkarte namens **Contoso HR** aus. Webparts werden alphabetisch sortiert. Wenn es sich um eine lange Liste handelt, können Sie die Suchleiste verwenden, um sie zu finden. Dadurch wird ein Webpart im Zeichenbereich erstellt, das ihre Teams Registerkarte enthält. In der folgenden Abbildung wird die Registerkartenansicht angezeigt:

   ![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. Wählen Sie die Schaltfläche **"Veröffentlichen"** aus, nachdem Sie die Bearbeitung abgeschlossen haben.

1. Wählen Sie **"Seite zur Navigation hinzufügen"** aus, um in der linken Navigationsleiste einen Schnellverweis auf Ihre Seite zu erhalten. In der folgenden Abbildung wird die Registerkarte in SharePoint angezeigt: 

   ![Registerkarte in SharePoint-Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a>3. Erkunden von App-Seiten in SharePoint

Nachdem Ihre Seite veröffentlicht wurde, können Sie erkunden, [wie Sie Ihre Teams App in SharePoint zu einer umfassenderen Oberfläche machen.](/sharepoint/dev/spfx/web-parts/single-part-app-pages) Dadurch wird die aktuelle Seite in eine App-Seite konvertiert, auf der das normale SharePoint Seitenlayout mit einer vollständigen Seitenoberfläche für die Registerkarte Teams angezeigt wird. 

Die folgende Abbildung zeigt die vollständige Benutzeroberfläche von Teams App in SharePoint: ![ Abbildung der Registerkarten in SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Codebeispiel
| **Beispielname** | **Beschreibung** | **SPFx** |
|-----------------|-----------------|----------|
| SPFx-Webpart | SPFx Webpartbeispiele für Registerkarten, Kanäle und Gruppen. | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
* [Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
