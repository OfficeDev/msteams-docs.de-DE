---
title: Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als ein SPFx-Web part
author: laujan
description: Bereitstellen Ihrer vorhandenen Registerkarte "Teams" in SharePoint als SharePoint-Framework-Web part.
keywords: Teams-Registerkarten- SharePoint-Framework-Entwicklung
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2e5d1b01aa5f7566e25c7720d6a0539386226576
ms.sourcegitcommit: 6caf503de5544fb8b9c8c6bef8eff4ff5a46068c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2021
ms.locfileid: "50270791"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a>Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als ein SPFx-Web part

## <a name="rich-integration-between-teams-and-sharepoint"></a>Umfassende Integration zwischen Teams und SharePoint

Mit der Novemberversion von Teams und SharePoint Framework v. 1.7, Entwickler verfügen über zwei leistungsstarke Funktionen:

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
                        <h3>Registerkarten für Teams in SharePoint</h3>
                        <p>Erstellen Sie umfangreiche App-Erfahrungen in SharePoint, indem Sie Ihre Teams-App in SharePoint (dieser Artikel) bringen.</p>
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
                        <h3>SharePoint Framework in Teams</h3>
                        <p>Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Registerkarten "Teams" in SharePoint

Mit SharePoint Framework v.1.7 unterstützen wir entwicklern jetzt die Möglichkeit, ihre Registerkarten in Teams zu verwenden und in SharePoint zu hosten. Da in SharePoint gehostete Registerkarten eine ähnliche "ganzseitige" Erfahrung erhalten, werden alle Features von Registerkarten von Teams verfügbar gemacht, während der Kontext und die Vertrautheit einer SharePoint-Website beibehalten werden.

### <a name="sharepoint-framework-in-teams"></a>SharePoint Framework in Teams

Sie können Ihre Microsoft Teams-Registerkarten auch mithilfe von SharePoint Framework implementieren. Für SharePoint-Entwickler vereinfacht dies den Entwicklungsprozess für Registerkarten von Teams erheblich, da SharePoint-Framework-Webparts in SharePoint gehostet werden, ohne dass externe Dienste wie Azure benötigt werden. [Erfahren Sie mehr über die Verwendung von SharePoint Framework in Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Einführung

In diesen Anweisungen wird erläutert, wie Sie eine Registerkarte aus einer Microsoft Teams-Beispiel-App verwenden und in SharePoint verwenden können. Wir verwenden eine Registerkarte, die bereits in Azure gehostet wird, um uns auf die erforderliche Integrationsarbeit zu konzentrieren.

Die von uns verwendeten Beispiel-App ist eine Talentverwaltungsanwendung. Er verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team. (Die App selbst hat zwar ein gutes Aussehen, aber sie hat eigentlich nichts zu tun. Wir möchten uns darauf konzentrieren, eine Teams-App zu erstellen und sie in Teams zu laden, und keine echte Talentverwaltungsanwendung erstellen.)

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

- Erreichen von SharePoint-Benutzern mit Ihrer vorhandenen Registerkarte "Teams"
- Laden Sie Ihr App-Manifest direkt in Ihren SharePoint-App-Katalog hoch. [Teams-Anwendungspakete werden](~/concepts/build-and-test/apps-package.md) jetzt von SharePoint unterstützt
- Endbenutzer konfigurieren die Registerkarte auf einer Seite wie jedes andere SharePoint-Web part
- Ihre Registerkarte kann auf den Kontext [zugreifen,](~/tabs/how-to/access-teams-context.md) so wie es möglich ist, wenn sie in Teams ausgeführt wird.

## <a name="step-1-testing-the-sample-app"></a>Schritt 1: Testen der Beispiel-App

Laden Sie das Beispiel-App-Manifest hier [**herunter.**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)

Klicken Sie in Microsoft Teams unten links auf das Store-Symbol und dann links unten auf "Benutzerdefinierte App hochladen". Die hochzuladende Datei befindet sich in Ihrem Downloadordner. Sie wird als TalentMgmt-Azure.zip. Wenn alles gut läuft, wird der Installations-/Zustimmungsbildschirm für die Talentmanagement-App angezeigt. Wählen Sie das Team aus, in dem Sie installieren möchten, und klicken Sie auf die Schaltfläche "Installieren". Sie können jetzt mit der App experimentieren.

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a>Schritt 2: Verwenden der Registerkarte "Teams" in SharePoint

Laden Sie Ihr Teams-App-Paket hoch, und stellen Sie es in Ihren SharePoint-App-Katalog ein, indem Sie `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` z. B. . `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`

Wenn Sie dazu aufgefordert werden, aktivieren Sie "Diese Lösung für alle Websites in der Organisation verfügbar machen":

![Registerkarten in der SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

Erstellen Sie auf Ihrer Website eine neue Seite, indem Sie oben rechts auf die Zahnradschaltfläche und dann auf "Seite hinzufügen" klicken:

![SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

Sie sehen die Erstellungserfahrung für SharePoint-Seiten. Nennen Sie Ihre Seite "Registerkarte "Meine Teams".

Öffnen Sie die Web part-Toolbox, indem Sie die Schaltfläche +drücken, und wählen Sie Ihre Registerkarte "Teams" (mit dem Namen "Contoso HR") aus. Webparts sind alphabetisch sortiert. Wenn es sich um eine lange Liste gibt, können Sie die Suchleiste verwenden, um sie zu finden. Dadurch wird ein Web part in der Canvas erstellt, die Ihre Registerkarte "Teams" enthält:

![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

Klicken Sie auf die Schaltfläche "Veröffentlichen", wenn Sie die Bearbeitung abgeschlossen haben.

Sie können auf "Seite zur Navigation hinzufügen" klicken, um einen Kurzverweis auf Ihre Seite in der linken Navigationsleiste zu erhalten:

![Registerkarte in SharePoint Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a>Schritt 3: Erkunden von App-Seiten in SharePoint

Nachdem Ihre Seite veröffentlicht wurde, können Sie erkunden, wie Sie Ihre Teams-App in eine vollständigere Erfahrung [in SharePoint umschließen.](/sharepoint/dev/spfx/web-parts/single-part-app-pages) Dadurch wird die aktuelle Seite in eine App-Seite konvertiert, die das normale SharePoint-Seitenlayout mit einer ganzseitigen Besensung für die Registerkarte "Teams" zeigt:

![Abbildung von Registerkarten in Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a>Codebeispiel
| **Beispielname** | **Beschreibung** | **SPFx** |
|-----------------|-----------------|----------|
| SPFx-Web part | SPFx-Web-Part-Beispiele für Registerkarten, Kanäle und Gruppen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="more-information"></a>Weitere Informationen

- [Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
