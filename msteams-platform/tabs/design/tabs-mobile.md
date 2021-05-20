---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien zum Entwerfen von Registerkarten, die auf Mobilgeräten funktionieren.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams entwerfen Richtlinien Referenz Framework persönliche Apps mobile Registerkarten
ms.openlocfilehash: 853ab2c52edd1f4faedcc92e6f0e8d0821b580c7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566698"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Sie können Registerkarten in Teams mobilen Kanälen, Chats und persönlichen Apps einschließen.

## <a name="accessing-personal-tabs"></a>Zugriff auf persönliche Registerkarten

Sie können auf persönliche Registerkarten in der App-Schublade zugreifen.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung mit der Teams mobilen App-Schublade." border="false":::

## <a name="accessing-channel-tabs"></a>Zugriff auf Kanalregisterkarten

Sie können auf Kanal- und Gruppenregisterkarten zugreifen, indem Sie die Schaltfläche **Mehr** im Kanal oder Chat auswählen, in dem sie hinzugefügt wurden.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung mit einer Teams mobilen Registerkarte." border="false":::

## <a name="design-considerations"></a>Überlegungen zum Entwurf

Unsere mobile Plattform ermöglicht Apps ein immersives Erlebnis mit den App-Inhalten, die den gesamten Bildschirm außer der Haupt-Teams Navigation einnehmen. Um ein immersives Erlebnis zu schaffen, das zu Teams passt, befolgen Sie diese Richtlinien.

### <a name="responsive-design"></a>Dynamisches Designs

Da Ihre Registerkarte auf Geräten mit einer Vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [den Grundsätzen des responsiven Designs](https://www.w3schools.com/html/html_responsive.asp) folgen. Alle Schlüsselkonstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden. Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links über die fingerbasierte Navigation leicht zugänglich sind.

### <a name="layouts"></a>Layouts

Es ist wichtig, das richtige Layout für Ihre Registerkarte auszuwählen. Sie sollten die Art der Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das es für den einfachen Verbrauch organisiert. Im Folgenden werden einige mögliche Optionen erläutert.

#### <a name="single-canvas"></a>Einzelleinwand

Dies ist ein großer Bereich, in dem gearbeitet wird. Die Teams Wiki-App folgt diesem Muster. Wenn Sie eine App haben, die Inhalte nicht in kleinere Komponenten aufteilt, würde dies gut passen.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung mit einer Teams mobilen Registerkarte für einzelne Arbeitsfläche." border="false":::

#### <a name="list"></a>Liste

Listen eignen sich hervorragend zum Sortieren und Filtern großer Datenmengen und eignen sich hervorragend, um die wichtigsten Dinge an der Spitze zu halten. Es ist hilfreich, sortierbare Spalten zu verwenden. Aktionen können jedem Listenelement im Menü auslipsisiell hinzugefügt werden.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung mit einer Registerkarte Teams mobilen Liste." border="false":::

#### <a name="grid"></a>Raster

Raster sind nützlich, um Elemente zu zeigen, die sehr visuell sind. Es hilft, einen Filter oder suchgesteuert an der Spitze einzuschließen.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung mit einer Teams mobilen Registerkarte mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Tabs mit Bots auf Mobilgeräten

Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot:

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung zeigt, wie mobile Teams App mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a>UI-Komponenten

### <a name="color-palettes"></a>Farbpaletten

Wenn Sie unsere genehmigte neutrale Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen verwenden, fühlen Sie sich Ihrer App in Teams mehr zu Hause. Da Teams-Mobil zwei Farbthemen (hell und dunkel) hat, ist es eine gute Idee, sicherzustellen, dass Ihre App in beiden Bereichen gut aussieht.

#### <a name="light-color"></a>Lichtfarbe

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Dunkle Farbe

![dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Tasten und Steuerelemente

Die Art und Weise, wie Schaltflächen gestylt werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen. Wir pflegen eine breite Palette von Tasten, die formatiert sind, um verschiedene Schwerpunkte anzuzeigen. Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und Symbol enthalten. Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen innerhalb jeder Kategorie entworfen.

#### <a name="buttons"></a>Schaltflächen

Primäre und sekundäre Schaltflächen.

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Auswahlsteuerungen

Optionsfelder, Kontrollkästchen und Umschalter.

![Auswahlsteuerungen](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Chiclets und Pillen

![Chiclets und Pillen](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Typografie

Die Typografie sollte klar und zielgerichtet sein. Betonen Sie wichtige Informationen, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden. Wir empfehlen, den Satzfall zu verwenden und die Verwendung aller Kappen für Lokalisierung und Lesbarkeit zu vermeiden.

![mobiler Typograph](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Felder und Flyouts

Felder sind Bereiche, in die Benutzer Text eingeben können. Flyouts sind leichter als Dialoge und werden im oberen Bereich angezeigt.

#### <a name="list-controls"></a>Steuerelemente auflisten

![Mobile Listensteuerungen](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Feldkontrollen

![mobile Feldsteuerungen](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Überlegungen zu Entwicklern

Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf Android- als auch auf iOS-Microsoft Teams-Clients funktioniert. In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

### <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

### <a name="low-bandwidth-and-intermittent-connections"></a>Geringe Bandbreite und intermittierende Verbindungen

Mobile Clients müssen regelmäßig mit geringer Bandbreite und intermittierenden Verbindungen funktionieren. Ihre App sollte alle Timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht bereitstellt. Sie sollten auch Benutzerfortschrittsindikatoren verwenden, um Ihren Benutzern Feedback für lang andauernde Prozesse zu geben.

> [!NOTE]
> Registerkarten werden auf Mobilgeräten erst aktiviert, nachdem die Anwendung basierend auf der Eingabe des Genehmigungsteams zu einer Zulassungsliste hinzugefügt wurde. Um die mobile Reaktionsfähigkeit zu überprüfen, wenden Sie sich an teamsubm@microsoft.com.

### <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert. Für Android-Geräte können Sie die [DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte zu debuggen, während sie ausgeführt wird. Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf niedriger Leistung, einschließlich eines Tablets, zu testen.

### <a name="distribution"></a>Verteilung

Apps, die im Teams Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im Teams mobilen Clients ordnungsgemäß funktionieren. Die Verfügbarkeit und das Verhalten der Registerkartehängt hängt davon ab, ob Ihre App genehmigt wurde.

#### <a name="apps-on-teams-store-approved-for-mobile"></a>Apps auf Teams Store für Mobilgeräte zugelassen

In der folgenden Tabelle wird die Verfügbarkeit und das Verhalten der Registerkarten beschrieben, wenn die App im Teams Store aufgeführt und für die mobile Verwendung zugelassen ist:

|Funktion   |Mobile Verfügbarkeit?   |Mobiles Verhalten|
|----------|-----------|------------|
|Kanal <br /> und Gruppenregisterkarte|Ja|Die Registerkarte wird im Teams mobilen Clients mithilfe der Konfiguration Ihrer App `contentUrl` geöffnet.|
|Persönliche App|Ja|Jede Registerkarte in der Registerkarte Persönliche App wird im Teams mobileclient mit der entsprechenden `contentUrl` Konfiguration geöffnet.|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Apps auf Teams Store nicht für Mobilgeräte zugelassen

In der folgenden Tabelle wird die Verfügbarkeit und das Verhalten der Registerkarten beschrieben, wenn die App im Teams Store aufgeführt, aber nicht für die mobile Verwendung zugelassen ist:

| Funktion | Mobile Verfügbarkeit? | Mobiles Verhalten |
|----------|-----------|------------|
|Kanal- und Gruppenregisterkarte|Ja|Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients mithilfe der Konfiguration Ihrer App `websiteUrl` geöffnet, die ebenfalls in die Funktion Ihres Quellcodes einbezogen werden `setSettings()` [](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true)muss. Benutzer können die Registerkarte jedoch weiterhin im Teams mobilen Clients anzeigen, indem sie neben der App **Mehr** auswählen und **Öffnen** auswählen, was die Konfiguration Ihrer App `contentUrl` auslöst.|
|Persönliche App|Nein|Nicht zutreffend|

#### <a name="apps-not-on-teams-store"></a>Apps, die nicht auf Teams Store sind

Wenn Sie Ihre App nebeneinander laden oder im App-Katalog einer Organisation veröffentlichen, entspricht das Tabstoppverhalten mit Teams Store-Apps, die von Microsoft für Mobilgeräte genehmigt wurden.
