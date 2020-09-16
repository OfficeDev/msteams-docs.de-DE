---
title: Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als SPFx-Webpart
author: laujan
description: Vorgehensweise zum Bereitstellen Ihrer vorhandenen Teams-Registerkarte in SharePoint als SharePoint-Framework-WebPart.
keywords: Teams-Registerkarten SharePoint Framework-Entwicklung
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2bdc7ab578be485eee33020b3b0c1a4099fd8ade
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818941"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a>Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als SPFx-Webpart

> [!IMPORTANT]
> Dieses Feature ist derzeit in der Vorschau und kann jederzeit geändert werden. Sie wird für die Verwendung in Produktionsumgebungen nicht unterstützt. Wir freuen uns über Ihr Feedback und Ihre Meinung zu dieser Funktion über die [SharePoint Dev Docs-Problemliste](https://github.com/SharePoint/sp-dev-docs/issues).

## <a name="rich-integration-between-teams-and-sharepoint"></a>Umfassende Integration zwischen Microsoft Teams und SharePoint

Mit der November-Version von Microsoft Teams und SharePoint Framework v. 1,7 haben Entwickler zwei leistungsstarke Funktionen:

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
                        <h3>Teams-Registerkarten in SharePoint</h3>
                        <p>Erstellen Sie reichhaltige App-Erlebnisse in SharePoint, indem Sie Ihre Teams-app in SharePoint (diesen Artikel) einbringen.</p>
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
                        <h3>SharePoint-Framework in Microsoft Teams</h3>
                        <p>Bringen Sie Ihre SharePoint-Webparts in Microsoft Teams, und lassen Sie SharePoint das Hosting für Sie verwalten.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a>Teams-Registerkarten in SharePoint

Mit SharePoint Framework v. 1.7 unterstützen wir nun die Möglichkeit für Entwickler, ihre Teams-Registerkarten zu nehmen und in SharePoint zu hosten. Wenn Tabs in SharePoint gehostet werden, erhalten Sie eine ähnliche "ganzseitige" Oberfläche, wobei Sie alle Funktionen von Teams-Registerkarten unter Beibehaltung des Kontexts und der Vertrautheit einer SharePoint-Website verfügbar machen.

### <a name="sharepoint-framework-in-teams"></a>SharePoint-Framework in Microsoft Teams

Sie können auch Ihre Microsoft Teams-Registerkarten mit SharePoint Framework implementieren. Für SharePoint-Entwickler wird dadurch der Entwicklungsprozess für Teams-Registerkarten erheblich vereinfacht, da SharePoint-Framework-Webparts in SharePoint gehostet werden, ohne dass externe Dienste wie Azure erforderlich sind. [Erfahren Sie mehr über die Verwendung des SharePoint-Frameworks in Microsoft Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a>Einführung

In diesen Anweisungen wird erklärt, wie Sie eine Registerkarte aus einer Microsoft Teams-Beispiel-app erstellen und in SharePoint verwenden können. Wir verwenden eine Registerkarte, die bereits auf Azure gehostet wird, um sich auf die erforderliche Integrationsarbeit zu konzentrieren.

Die Beispiel-APP, die wir verwenden, ist eine Talent Verwaltungsanwendung. Es verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team. (Die APP selbst, während Sie nett aussieht, tut tatsächlich nichts. Wir möchten uns darauf konzentrieren, eine Teams-APP zu erstellen und Sie in Teams zu laden, ohne eine echte Talent Verwaltungsanwendung zu erstellen.)

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

- Erreichen von SharePoint-Benutzern mit der Registerkarte "vorhandene Teams"
- Laden Sie Ihr App-Manifest direkt in Ihren SharePoint-App-Katalog hoch. Microsoft [Teams-Anwendungspakete](~/concepts/build-and-test/apps-package.md) werden jetzt von SharePoint unterstützt
- Endbenutzer konfigurieren die Registerkarte auf einer Seite genauso wie alle anderen SharePoint-Webparts
- Ihre Registerkarte kann auf Ihren [Kontext](~/tabs/how-to/access-teams-context.md) zugreifen, genauso wie Sie es kann, wenn Sie innerhalb von Teams läuft

## <a name="step-1-testing-the-sample-app"></a>Schritt 1: Testen der Beispiel-App

Laden Sie das Beispiel-App-Manifest von [**hier**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)herunter.

Klicken Sie in Microsoft Teams auf das Store-Symbol unten links und dann auf "benutzerdefinierte App hochladen" unten links. Die Datei, die hochgeladen werden soll, befindet sich im Ordner "Downloads"; Es heißt TalentMgmt-Azure.zip. Wenn alles gut geht, sehen Sie den Bildschirm "Installation/Zustimmung" für die Talent Management-APP. Wählen Sie das Team aus, das Sie installieren möchten, und klicken Sie auf die Schaltfläche installieren. Sie können jetzt mit der APP experimentieren.

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a>Schritt 2: Verwenden der Registerkarte "Teams" in SharePoint

Laden Sie Ihr Teams-App-Paket in Ihren SharePoint-App-Katalog hoch, indem Sie beispielsweise einen Besuch durchsuchen. `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`

Wenn Sie dazu aufgefordert werden, aktivieren Sie die Option "Diese Lösung für alle Websites in der Organisation verfügbar machen":

![Registerkarten in der SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

Erstellen Sie in Ihrer Website eine neue Seite, indem Sie auf die Schaltfläche Gear oben rechts und dann auf "Seite hinzufügen" klicken:

![SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

Die Erstellungsumgebung für SharePoint-Seiten wird angezeigt. Nennen Sie Ihre Seite "meine Teams-Registerkarte".

Öffnen Sie die Webpart-Toolbox durch Drücken der +-Schaltfläche, und wählen Sie Ihre Teams-Registerkarte ("Contoso HR" genannt) aus. Webparts werden alphabetisch sortiert; Wenn es sich um eine lange Liste handelt, können Sie die Suchleiste verwenden, um Sie zu finden. Dadurch wird ein Webpart im Canvas-Bereich erstellt, der die Registerkarte Teams enthält:

![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

Drücken Sie die Schaltfläche "veröffentlichen", wenn Sie die Bearbeitung abgeschlossen haben.

Möglicherweise möchten Sie auf "Seite zur Navigation hinzufügen" klicken, um in der linken Navigationsleiste eine Kurzübersicht zu Ihrer Seite zu haben:

![Registerkarte in SharePoint-Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a>Schritt 3: Durchsuchen von App-Seiten in SharePoint

Nachdem Sie Ihre Seite veröffentlicht haben, können Sie [Ihre Teams-app in eine umfassendere Erfahrung in SharePoint umwandeln](/sharepoint/dev/spfx/web-parts/single-part-app-pages). Dadurch wird die aktuelle Seite in eine APP-Seite umgewandelt, die das normale SharePoint-Seitenlayout mit einer ganzseitigen Oberfläche für die Registerkarte "Teams" zeigt:

![Bild von Registerkarten in SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="more-information"></a>Weitere Informationen

- [Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
