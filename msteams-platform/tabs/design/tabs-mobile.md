---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf Mobilen funktionieren.
ms.topic: conceptual
localization_priority: Normal
keywords: teams design guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: 853ab2c52edd1f4faedcc92e6f0e8d0821b580c7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566698"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Sie können Registerkarten in Teams mobilen Kanälen, Chats und persönlichen Apps hinzufügen.

## <a name="accessing-personal-tabs"></a>Zugreifen auf persönliche Registerkarten

Sie können auf persönliche Registerkarten in der App-Schublade zugreifen.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung der Teams mobilen App-Schublade." border="false":::

## <a name="accessing-channel-tabs"></a>Zugreifen auf Kanalregisterkarten

Sie können auf Kanal- und Gruppenregisterkarten zugreifen, indem Sie die Schaltfläche **Mehr** im Kanal oder Chat auswählen, in dem sie hinzugefügt wurden.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer Teams mobilen Registerkarte." border="false":::

## <a name="design-considerations"></a>Überlegungen zum Entwurf

Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm außer der Hauptnavigation Teams werden. Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu Teams erstellen.

### <a name="responsive-design"></a>Dynamisches Designs

Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [reaktionsfähige Entwurfsprinzipien](https://www.w3schools.com/html/html_responsive.asp) befolgen. Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden. Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät über die fingerbasierte Navigation problemlos auf alle Schaltflächen und Links zugegriffen werden kann.

### <a name="layouts"></a>Layouts

Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig. Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie zur einfachen Nutzung organisiert. Einige potenzielle Optionen sind unten beschrieben.

#### <a name="single-canvas"></a>Einzelner Canvas

Dies ist ein großer Bereich, in dem die Arbeit erledigt wird. Die Teams Wiki-App folgt diesem Muster. Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten trennt, ist dies eine gute Passform.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer Teams mobilen Registerkarte für einen einzelnen Zeichenbereich." border="false":::

#### <a name="list"></a>Liste

Listen nen sich gut zum Sortieren und Filtern großer Datenmengen nen und nen, um die wichtigsten Dinge oben zu behalten. Es ist hilfreich, sortierbare Spalten zu verwenden. Aktionen können zu jedem Listenelement unter dem Auslassungsmenü hinzugefügt werden.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer Teams mobilen Listenregisterkarte." border="false":::

#### <a name="grid"></a>Grid

Raster n nen nützlich sein, um Elemente zu zeigen, die hochgradig visuell sind. Es hilft, einen Filter oder ein Suchsteuerelement oben zu enthalten.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer Teams mobilen Registerkarte mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Registerkarten mit Bots auf Mobilgeräten

Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot:

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung, die zeigt, Teams app mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a>Benutzeroberflächenkomponenten

### <a name="color-palettes"></a>Farbpaletten

Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in ihrem Teams. Da Teams mobile zwei Farbthemen (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs großartig aussieht.

#### <a name="light-color"></a>Helle Farbe

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Dunkle Farbe

![Dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Schaltflächen und Steuerelemente

Die Art und Weise, wie Schaltflächen gestylt werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen. Wir verwalten eine vielzahl von Schaltflächen, die so formatiert sind, dass sie unterschiedliche Betonungsebenen anzeigen. Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und einem Symbol enthalten. Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen in jeder Kategorie entworfen.

#### <a name="buttons"></a>Schaltflächen

Primäre und sekundäre Schaltflächen.

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Auswahlsteuerelemente

Optionsfelder, Kontrollkästchen und Umschaltflächen.

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Schickchen und Pillen

![Zichorlets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Typografie

Die Typografie sollte klar und zweckvoll sein. Heben Sie wichtige Informationen hervor, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden. Es wird empfohlen, den Satzfall zu verwenden und die Verwendung aller Obergrenzen für die Lokalisierung und Lesbarkeit zu vermeiden.

![Mobile Typografie](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Felder und Flyouts

Felder sind Bereiche, in denen Benutzer Text eingeben können. Flyouts sind leichter als Dialogfelder und werden im oberen Bereich angezeigt.

#### <a name="list-controls"></a>Steuerelemente auflisten

![Steuerelemente für mobile Listen](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Feldsteuerelemente

![Steuerelemente für mobile Felde](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Überlegungen zu Entwicklern

Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf den Android- als auch auf iOS-Microsoft Teams funktioniert. In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

### <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

### <a name="low-bandwidth-and-intermittent-connections"></a>Niedrige Bandbreite und zeitweilige Verbindungen

Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweiligen Verbindungen funktionieren. Ihre App sollte timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht zur Verfügung stellt. Sie sollten auch Fortschrittsindikatoren der Benutzer verwenden, um Ihren Benutzern Feedback für alle lang laufenden Prozesse zu geben.

> [!NOTE]
> Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung einer Zulassungsliste hinzugefügt wurde, basierend auf der Eingabe des Genehmigungsteams. Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, erreichen Sie die teamsubm@microsoft.com.

### <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert. Für Android-Geräte können Sie [devTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen. Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf niedriger Leistung zu testen, einschließlich eines Tablets.

### <a name="distribution"></a>Verteilung

Apps, die im Teams-Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im mobilen Client Teams funktionieren. Verfügbarkeit und Verhalten von Registerkarten hängen davon ab, ob Ihre App genehmigt wurde.

#### <a name="apps-on-teams-store-approved-for-mobile"></a>Apps im Teams für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams und für die mobile Verwendung genehmigt ist:

|Funktion   |Mobile Verfügbarkeit?   |Mobiles Verhalten|
|----------|-----------|------------|
|Kanal <br /> Registerkarte "Gruppe" und "Gruppe"|Ja|Die Registerkarte wird im Teams mobilen Client mithilfe der Konfiguration Ihrer App `contentUrl` geöffnet.|
|Persönliche App|Ja|Jede Registerkarte auf der Registerkarte persönliche App wird im Teams mobilen Client mit der entsprechenden Konfiguration `contentUrl` geöffnet.|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Apps im Teams store nicht für mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams,jedoch nicht für die mobile Verwendung genehmigt ist:

| Funktion | Mobile Verfügbarkeit? | Mobiles Verhalten |
|----------|-----------|------------|
|Registerkarte "Kanal" und "Gruppe"|Ja|Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients geöffnet, der die Konfiguration Ihrer App verwendet, die ebenfalls in der Quellcodefunktion `websiteUrl` enthalten `setSettings()` [sein muss.](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true) Benutzer können die Registerkarte jedoch weiterhin im mobilen Client  Teams anzeigen, indem Sie neben der App weitere auswählen und **Öffnen** auswählen, wodurch die Konfiguration Ihrer App ausgelöst `contentUrl` wird.|
|Persönliche App|Nein|Nicht zutreffend|

#### <a name="apps-not-on-teams-store"></a>Apps, die nicht im Teams sind

Wenn Sie Ihre App oder Veröffentlichung querladen im App-Katalog einer Organisation, ist das Registerkartenverhalten identisch mit Teams von Microsoft für Mobile genehmigten Store-Apps.
