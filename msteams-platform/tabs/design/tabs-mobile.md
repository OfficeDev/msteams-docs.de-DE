---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf mobilen Geräten funktionieren.
ms.topic: conceptual
keywords: Teams Design Guidelines reference framework personal apps mobile tabs
ms.openlocfilehash: 70ff46e446b146b134f34830e8867133cbeeca14
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093288"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

> [!NOTE]
> Wenn Sie ihre Kanal-/Gruppenregisterkarte auf mobilen Teams-Clients anzeigen möchten, muss die Konfiguration einen Wert für die Eigenschaft haben `setSettings()` `websiteUrl` (siehe unten).

Benutzerdefinierte Registerkarten können Teil eines Kanals, Eines Gruppenchats oder einer persönlichen App sein (Apps, die statische Registerkarten und/oder einen 1:1-Bot enthalten).

Persönliche Apps sind auf mobilen Clients in der App-Drawer verfügbar. Die App kann nur von einem Desktop- oder Webclient installiert werden und kann bis zu 24 Stunden dauern, bis sie auf mobilen Clients angezeigt wird.

Kanalregisterkarten sind auch für Mobilgeräte verfügbar. Das Standardverhalten besteht derzeit in der Verwendung ihrer Registerkarte, um die `websiteUrl` Registerkarte in einem Browserfenster zu starten. Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf das Überlaufmenü neben der Registerkarte klicken und "Öffnen" auswählen, wodurch Sie die Registerkarte im mobilen Client von `...` Teams  `contentUrl` laden.

## <a name="accessing-personal-tabs"></a>Zugreifen auf persönliche Registerkarten

Die folgende Abbildung zeigt, wie Sie auf eine persönliche Registerkarte auf mobilen Geräten zugreifen.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Illustration showing the Teams mobile app drawer." border="false":::

## <a name="accessing-channel-tabs"></a>Zugreifen auf Kanalregisterkarten

Die folgende Abbildung zeigt, wie Sie auf eine Kanalregisterkarte auf mobilen Geräten zugreifen.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Abbildung einer mobilen Registerkarte &quot;Teams&quot;." border="false":::

## <a name="design-considerations"></a>Überlegungen zum Entwurf

Unsere mobile Plattform ermöglicht Apps eine immersive Erfahrung mit den App-Inhalten, die den ganzen Bildschirm neben der Hauptnavigation von Teams nutzen. Befolgen Sie diese Richtlinien, um ein immersives Erlebnis zu erstellen, das zu Teams passt.

### <a name="responsive-design"></a>Dynamisches Designs

Da Ihre Registerkarte auf Geräten mit einer vielzahl von Bildschirmgrößen geöffnet werden kann, muss sie den Prinzipien des [reaktionsschnellen Designs](https://www.w3schools.com/html/html_responsive.asp) entsprechen. Alle wichtigen Konstrukte sollten auf mobilen Geräten zugänglich sein, und die Ansichten sollten nicht verzerrt sein. Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links über die fingerbasierte Navigation leicht zugänglich sind.

### <a name="layouts"></a>Layouts

Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig. Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das sie für einen einfachen Verbrauch organisiert. Im Folgenden werden einige mögliche Optionen beschrieben.

#### <a name="single-canvas"></a>Einzelner Zeichenbereich

Dies ist ein großer Bereich, in dem Arbeit erledigt wird. Die Teams-Wiki-App folgt diesem Muster. Wenn Sie über eine App verfügen, die Inhalte nicht in kleinere Komponenten aufteilen, ist dies gut geeignet.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Abbildung einer mobilen Registerkarte mit einem einzelnen Zeichenbereich in Teams." border="false":::

#### <a name="list"></a>List

Listen n nen sich gut zum Sortieren und Filtern großer Datenmengen nnen und sind gut dafür, die wichtigsten Dinge ganz oben zu behalten. Es ist hilfreich, sortierbare Spalten zu verwenden. Aktionen können jedem Listenelement unter dem Auslassungspunktmenü hinzugefügt werden.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Abbildung einer Registerkarte für mobile Teams-Listen." border="false":::

#### <a name="grid"></a>Raster

Raster sind nützlich, um Elemente zu zeigen, die hochgradig visuell sind. Es hilft, oben einen Filter oder ein Suchsteuerelement zu verwenden.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Abbildung einer mobilen Registerkarte von Teams mit einem Rasterlayout." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Registerkarten mit Bots auf Mobilgeräten

Das folgende Beispiel ist eine persönliche App mit Registerkarten und einem Bot.

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Illustration showing how mobile Teams app that has tabs and a bot." border="false":::

## <a name="ui-components"></a>Benutzeroberflächenkomponenten

### <a name="color-palettes"></a>Farbpaletten

Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer App, sich in Teams besser zu hause zu fühlen. Da Teams Mobile zwei helle Designs (hell und dunkel) hat, sollten Sie sicherstellen, dass Ihre App in beiden Designs gut aussieht.

#### <a name="light-color"></a>Helle Farbe

![Helle Farbpalette](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Dunkle Farbe

![Dunkle Farbpalette](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Schaltflächen und Steuerelemente

Die Art und Weise, wie Schaltflächen formatiert werden, hilft zu kommunizieren, welche Art von Aktion sie auslösen. Wir verwalten eine Vielzahl von Schaltflächen, die so formatiert sind, dass sie unterschiedliche Akzentstufen anzeigen. Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und einem Symbol enthalten. Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir primäre und sekundäre Schaltflächen innerhalb jeder Kategorie entworfen.

#### <a name="buttons"></a>Schaltflächen

Primäre und sekundäre Schaltflächen.

![Schaltflächenbild](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Auswahlsteuerelemente

Optionsfelder, Kontrollkästchen und Umschaltflächen.

![Auswahlsteuerelemente](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Kapseln und Kapseln

![- und -kapseln](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Typografie

Typografie sollte klar und zielvoll sein. Heben Sie wichtige Informationen hervor, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen, um Verwirrung zu vermeiden. Wir empfehlen die Verwendung von Groß-/B0 und die Verwendung von Großbuchstaben für die Lokalisierung und Lesbarkeit.

![Mobile Typografie](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Felder und Flyouts

Felder sind Bereiche, in denen Benutzer Text eingeben können. Flyouts sind einfacher als Dialogfelder und werden im oberen Bereich angezeigt.

#### <a name="list-controls"></a>Steuerelemente auflisten

![Mobile Listensteuerelemente](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Feldsteuerelemente

![Mobile Feldsteuerelemente](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Überlegungen für Entwickler

Wenn Sie eine App erstellen, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte auf den Android- und iOS Microsoft Teams-Clients funktioniert. In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

### <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten verschiedener Größen und Qualitäten ordnungsgemäß funktioniert. Für Android-Geräte können Sie [die DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen. Es wird empfohlen, sowohl auf Geräten mit hoher und niedriger Leistung als auch auf einem Tablet zu testen.

### <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Das JavaScript SDK für Teams auf mindestens Version 1.4.1 aktualisieren.

### <a name="low-bandwidth-and-intermittent-connections"></a>Geringe Bandbreite und zeitweilige Verbindungen

Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweilig unterbrochenen Verbindungen funktionieren. Ihre App sollte alle Timeouts entsprechend behandeln, indem sie dem Benutzer eine Kontextnachricht zur Verfügung stellt. Sie sollten auch Statusindikatoren für Benutzer verwenden, um Ihren Benutzern Feedback für lang dauernde Prozesse zu geben.

> [!NOTE]
> Registerkarten werden auf mobilen Geräten nur aktiviert, nachdem die Anwendung basierend auf der Eingabe des Genehmigungsteams einer Zulassungsliste hinzugefügt wurde. Um die Reaktionsfähigkeit mobiler Geräte zu überprüfen, greifen Sie auf teamsubm@microsoft.com. 