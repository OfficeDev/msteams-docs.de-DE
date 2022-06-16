---
title: Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint
author: surbhigupta
description: Erfahren Sie anhand von Codebeispielen, wie Sie Ihre bestehende Microsoft Teams-Registerkarte als SharePoint-Framework-Webpart für SharePoint bereitstellen.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: f889a4e1932feb02eeb502ab2f85f051093a5b58
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123647"
---
# <a name="add-teams-tab-to-sharepoint"></a>Hinzufügen einer Microsoft Teams-Registerkarte zu SharePoint

Sie können eine vielfältig nutzbare Integration zwischen Microsoft Teams und Sharepoint erhalten, indem Sie eine Microsoft Teams-Registerkarte in SharePoint als SPFx-Webpart hinzufügen. In diesem Dokument erfahren Sie, wie Sie eine Registerkarte aus einer Microsoft Teams-Beispiel-App in SharePoint verwenden.

## <a name="rich-integration-between-teams-and-sharepoint"></a>Umfassende Integration zwischen Microsoft Teams und SharePoint

Mit der November-Version von Microsoft Teams und SharePoint-Framework Version 1.7 verfügen Entwickler über zwei leistungsstarke Funktionen:

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
                        <h3>Microsoft Teams-Registerkarten in SharePoint</h3>
                        <p>Sorgen Sie für vielfältige App-Nutzungsmöglichkeiten in SharePoint, indem Sie Ihre Microsoft Teams-App in SharePoint integrieren (dieser Artikel).</p>
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
                        <h3>SharePoint-Framework in Microsoft Teams</h3>
                        <p>Integrieren Sie Ihre SharePoint-Webparts in Microsoft Teams und überlassen Sie SharePoint die Hostingverwaltung.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Microsoft Teams-Registerkarten in SharePoint

Ab SharePoint-Framework Version 1.7 können Sie Ihre Microsoft Teams-Registerkarten in SharePoint hosten. Registerkarten, die in SharePoint gehostet werden, weisen eine ähnliche **ganzseitige** Darstellung auf, in der alle Features von Microsoft Teams-Registerkarten verfügbar sein werden, während der Kontext und die Vertrautheit einer SharePoint-Site erhalten bleiben.

### <a name="sharepoint-framework-in-teams"></a>SharePoint-Framework in Microsoft Teams

Sie können Microsoft Teams-Registerkarten auch mithilfe von SharePoint-Framework implementieren. SharePoint-Framework-Webparts werden automatisch innerhalb von SharePoint gehostet, ohne dass externe Dienste wie Azure nötig sind. SharePoint-Entwicklern vereinfacht dies den Entwicklungsprozess für Microsoft Teams-Registerkarten erheblich. Weitere Informationen zu SharePoint-Framework in Microsoft Teams finden Sie unter [Verwenden des SharePoint-Frameworks in Microsoft Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Einführung

Die hier verwendete Registerkarte wird bereits in Azure gehostet, um sich auf die erforderlichen Integrationsarbeiten zu konzentrieren.

Die verwendete Beispiel-App ist eine Talentmanagement-Anwendung. Sie wird für die Verwaltung des Einstellungsprozesses von Bewerbern für offene Positionen in einem Team verwendet. Erstellen Sie eine Microsoft Teams-Beispiel-App, und laden Sie sie in Microsoft Teams. Erstellen Sie keine echte Talentmanagementanwendung.

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

* Erreichen Sie mit Ihrer bestehenden Microsoft Teams-Registerkarte SharePoint-Benutzer.
* Laden Sie Ihr App-Manifest direkt in den SharePoint-App-Katalog hoch. [Microsoft Teams-Anwendungspakete](~/concepts/build-and-test/apps-package.md) werden jetzt von SharePoint unterstützt.
* Die Benutzer konfigurieren die Registerkarte auf einer Seite wie jedes andere SharePoint-Webparts.
* Ihre Registerkarte kann auf ihren [Kontext](~/tabs/how-to/access-teams-context.md) genauso wie innerhalb Microsoft Teams zugreifen.

Um eine Microsoft Teams-Registerkarte in SharePoint hinzuzufügen, führen Sie die folgenden Schritte aus:

## <a name="1-test-the-sample-app"></a>1. Testen der Beispiel-App

Laden Sie das [Beispiel-App-Manifest](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip) herunter.

1. Öffnen Sie Microsoft Teams.
1. Klicken Sie unten links auf der Registerkarte auf das **App Store-Symbol**.
1. Wählen Sie unten links **Benutzerdefinierte App hochladen** aus. In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:  

    ![Benutzerdefinierte App hochladen](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. Die hochzuladende Datei befindet sich im Ordner **Downloads**. Es wird TalentMgmt-Azure.zip genannt. In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

    ![TalentMgmt in Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. Sie können den Installations- oder Zustimmungsbildschirm für die Talentmanagement-App sehen. Wählen Sie das Team aus, das Sie installieren möchten.
1. Klicken Sie auf **Installieren**, und beginnen Sie mit dem Experimentieren mit der App.

## <a name="2-use-teams-tab-in-sharepoint"></a>2. Verwenden einer Microsoft Teams-Registerkarte in SharePoint

1. Laden Sie Ihr Microsoft Teams-App-Paket in Ihren SharePoint-App-Katalog hoch, und stellen Sie es bereit, indem Sie `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`besuchen. Beispiel: `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.

1. Wenn Sie dazu aufgefordert werden, aktivieren Sie die Option **Diese Lösung allen Sites in Ihrer Organisation zur Verfügung stellen**.
In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

   ![Registerkarten in der SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. Erstellen Sie auf Ihrer Website eine neue Seite, indem Sie die Zahnradschaltfläche oben rechts und dann **Seite hinzufügen** anklicken.
In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:

   ![SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. Sie können die Erstellungsumgebung für SharePoint-Seiten sehen. Benennen Sie Ihre Seite als **Meine Microsoft Teams-Registerkarte**.

1. Öffnen Sie die Webpart-Toolbox durch Anklicken der `+`-Schaltfläche, und wählen Sie Ihre Microsoft Teams-Registerkarte namens **Contoso HR** aus. Webparts werden alphabetisch sortiert. Wenn es sich um eine lange Liste handelt, können Sie die Suchleiste verwenden, um sie zu finden. Dadurch wird ein Webpart im Canvas erstellt, das Ihre Microsoft Teams-Registerkarte enthält. In der folgenden Abbildung ist die Registerkartenansicht zu sehen:

   ![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. Klicken Sie auf die Schaltfläche **Veröffentlichen**, nachdem Sie die Bearbeitung abgeschlossen haben.

1. Wählen Sie **Seite zu Navigation hinzufügen** aus, um in der linken Navigationsleiste einen Schnellverweis auf Ihre Seite zu erhalten.
Die folgende Abbildung zeigt die Registerkarte in Sharepoint:

   ![Abbildung der Registerkarte in SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a>3. Erkunden von App-Seiten in SharePoint

Nachdem Ihre Seite veröffentlicht wurde, können Sie erkunden, [wie Sie Ihre Microsoft Teams-App in eine umfassendere Lösung innerhalb SharePoint verwandeln](/sharepoint/dev/spfx/web-parts/single-part-app-pages). Dadurch wird die aktuelle Seite in eine App-Seite konvertiert, die das normale SharePoint-Seitenlayout mit ganzseitiger Darstellung der Microsoft Teams-Registerkarte aufweist.

Die folgende Abbildung zeigt die vollständige Microsoft Teams- App-Oberfläche in SharePoint: ![Abbildung von Registerkarten in SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **SPFx** |
|-----------------|-----------------|----------|
| SPFx-Webpart | SPFx-Webpartbeispiele für Registerkarten, Kanäle und Gruppen | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
* [Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
