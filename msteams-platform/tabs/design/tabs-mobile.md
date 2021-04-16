---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf Mobilen funktionieren.
ms.topic: conceptual
keywords: teams design guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: 72d1cf4623a9f4c1b5c993f1477f755b51d9fe64
ms.sourcegitcommit: 0e252159f53ff9b4452e0574b759bfe73cbf6c84
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2021
ms.locfileid: "51762025"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

> [!NOTE]
> Wenn Sie ihre Kanal-/Gruppenregisterkarte auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration einen Wert für die Eigenschaft `setSettings()` `websiteUrl` haben (siehe unten).

Benutzerdefinierte Registerkarten können Teil eines Kanals, Eines Gruppenchats oder einer persönlichen App sein (Apps, die statische Registerkarten und/oder einen 1:1-Bot enthalten).

Persönliche Apps sind auf mobilen Clients in der App-Schublade verfügbar. Die App kann nur von einem Desktop- oder Webclient installiert werden und kann bis zu 24 Stunden dauern, bis sie auf mobilen Clients angezeigt wird. Alternativ können Sie ein Erneutes Laden auf dem mobilen Client erzwingen, indem Sie sich ab- und anmelden. Dadurch sollte die mobile App sofort verfügbar gemacht werden.

Kanalregisterkarten sind auch auf Mobilgeräten verfügbar. Das Standardverhalten besteht derzeit in der Verwendung Von zum Starten `websiteUrl` Ihrer Registerkarte in einem Browserfenster. Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf das Überlaufmenü neben der Registerkarte klicken und Öffnen auswählen, mit dem Sie die Registerkarte im mobilen `...`  `contentUrl` Teams-Client laden.

## <a name="accessing-personal-tabs"></a>Zugreifen auf persönliche Registerkarten

Die folgende Abbildung zeigt, wie Sie auf eine persönliche Registerkarte auf mobilen Geräten zugreifen.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Abbildung der Mobile -App-Schublade von Teams." border="false":::

## <a name="accessing-channel-tabs"></a>Zugreifen auf Kanalregisterkarten

Die folgende Abbildung zeigt, wie Sie auf eine Kanalregisterkarte auf mobilen Geräten zugreifen.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer mobilen Registerkarte &quot;Teams&quot;." border="false":::

## <a name="design-considerations"></a>Überlegungen zum Entwurf

Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm außer der Hauptnavigation von Teams nutzen. Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu erstellen, das zu Teams passt.

### <a name="responsive-design"></a>Dynamisches Designs

Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie [reaktionsfähige Entwurfsprinzipien](https://www.w3schools.com/html/html_responsive.asp) befolgen. Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt werden. Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät über die fingerbasierte Navigation problemlos auf alle Schaltflächen und Links zugegriffen werden kann.

### <a name="layouts"></a>Layouts

Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig. Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie zur einfachen Nutzung organisiert. Einige potenzielle Optionen sind unten beschrieben.

#### <a name="single-canvas"></a>Einzelner Canvas

Dies ist ein großer Bereich, in dem die Arbeit erledigt wird. Die Teams Wiki-App folgt diesem Muster. Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten trennt, ist dies eine gute Passform.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer mobilen Registerkarte für einen einzelnen Zeichenbereich von Teams." border="false":::

#### <a name="list"></a>Liste

Listen nen sich gut zum Sortieren und Filtern großer Datenmengen nen und nen, um die wichtigsten Dinge oben zu behalten. Es ist hilfreich, sortierbare Spalten zu verwenden. Aktionen können zu jedem Listenelement unter dem Auslassungsmenü hinzugefügt werden.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer mobilen Listenregisterkarte von Teams." border="false":::

#### <a name="grid"></a>Grid

Raster n nen nützlich sein, um Elemente zu zeigen, die hochgradig visuell sind. Es hilft, einen Filter oder ein Suchsteuerelement oben zu enthalten.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer mobilen Registerkarte von Teams mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Registerkarten mit Bots auf Mobilgeräten

Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot.

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Abbildung der mobilen Teams-App mit Registerkarten und einem Bot." border="false":::

## <a name="ui-components"></a>Benutzeroberflächenkomponenten

### <a name="color-palettes"></a>Farbpaletten

Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in Teams wohler zu fühlen. Da Teams mobile zwei Farbthemen (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs großartig aussieht.

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

Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf den Android- als auch auf iOS Microsoft Teams-Clients funktioniert. In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

### <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert. Für Android-Geräte können Sie [devTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen. Es wird empfohlen, sowohl auf Geräten mit hoher und niedriger Leistung als auch auf einem Tablet zu testen.

### <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie das Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

### <a name="low-bandwidth-and-intermittent-connections"></a>Niedrige Bandbreite und zeitweilige Verbindungen

Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweiligen Verbindungen funktionieren. Ihre App sollte timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht zur Verfügung stellt. Sie sollten auch Fortschrittsindikatoren der Benutzer verwenden, um Ihren Benutzern Feedback für alle lang laufenden Prozesse zu geben.

> [!NOTE]
> Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung einer Zulassungsliste hinzugefügt wurde, basierend auf der Eingabe des Genehmigungsteams. Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, erreichen Sie die teamsubm@microsoft.com. 
