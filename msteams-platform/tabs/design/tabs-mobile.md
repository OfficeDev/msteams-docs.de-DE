---
title: Registerkarten auf mobilen Geräten
description: Beschreibt die Richtlinien für das Entwerfen von Registerkarten, die auf mobilen Geräten funktionieren.
keywords: Teams-Entwurfsrichtlinien – Referenzrahmen-Mobile Registerkarten für persönliche apps
ms.openlocfilehash: 928fb8586434eca9cc1577fd45c6b94594724d7f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674346"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

> [!Important]
> Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze verfügbar sein. Um diese Änderung vorzubereiten, sollten Sie die folgenden Anweisungen beim Erstellen Ihrer Registerkarten befolgten. Persönliche Apps (statische Registerkarten) sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar. und Channel/Group Chat Registerkarten stehen im `...` Überlaufmenü für die Registerkarte zur Verfügung.
>
> Wenn die vollständige Unterstützung für Tabs freigegeben wird:
>
> * Alle Registerkarten sind auf mobilen Geräten immer verfügbar.
> * Ihr `contentUrl` **wird in den Mobile Teams-Client geladen**.
> * Bei Kanälen/Gruppenregisterkarten können Benutzer ihre Registerkarte weiterhin in einem separaten Browser öffnen `websiteUrl`, jedoch werden Sie `contentUrl` zuerst geladen.
> * Wenn Ihre Registerkarte die Authentifizierung verwendet, müssen Sie Ihr Microsoft Teams-JavaScript-SDK auf Version 1.4.1 oder höher aktualisieren, oder die Authentifizierung schlägt fehl.

Benutzerdefinierte Registerkarten können Teil eines Kanals, Gruppenchats oder einer persönlichen APP sein (apps, die statische Registerkarten und/oder einen 1:1-bot enthalten).

Persönliche apps sind auf mobilen Clients in der APP-Schublade verfügbar. Die APP kann nur von einem Desktop-oder WebClient installiert werden, und es kann bis zu 24 Stunden dauern, bis Sie auf mobilen Clients angezeigt wird.

Gruppen-und Kanal Registerkarten sind auch auf mobilen Clients verfügbar. Das Standardverhalten besteht derzeit darin, `websiteUrl` dass Sie Ihre Registerkarte in einem Browserfenster starten können. Sie können jedoch auf einem mobilen Client geladen werden, indem Sie auf `...` das Überlaufmenü neben der Registerkarte und dann auf **Öffnen**klicken, `contentUrl` mit dem Sie die Registerkarte in den mobilen Microsoft Teams-Client laden.

![Mobile App Schublade](~/assets/images/app-drawer.png)

## <a name="developer-considerations-for-mobile-support"></a>Entwickler Überlegungen für die Mobile Unterstützung

Wenn Sie eine APP erstellen, die eine Registerkarte enthält, müssen Sie prüfen (und testen), wie Ihre Registerkarte sowohl auf den Android-als auch IOS-Microsoft Teams-Clients funktioniert. In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie in diesem Punkt behandeln müssen.

### <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten in verschiedenen Größen und Qualitäten ordnungsgemäß funktioniert. Für Android-Geräte können Sie die [devtools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen. Es wird empfohlen, sowohl auf High-als auch auf niedrig leistungsfähigen Geräten sowie auf einem Tablet zu testen.

### <a name="responsive-design"></a>Dynamisches Designs

Da die Registerkarte auf Geräten mit einer großen Bandbreite von Bildschirmgrößen geöffnet werden kann, muss Sie den Grundsätzen für das [reagieren auf Designs](https://www.w3schools.com/html/html_responsive.asp) entsprechen. Auf alle Schlüssel Konstrukte sollte auf mobilen Geräten zugegriffen werden können, und die Ansichten sollten nicht verzerrt werden. Stellen Sie sicher, dass beim Laden der Registerkarte auf einem mobilen Gerät alle Schaltflächen und Links leicht über die Finger basierte Navigation zugänglich sind.

### <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Microsoft Teams js SDK auf mindestens Version 1.4.1 aktualisieren.

### <a name="low-bandwidth--intermittent-connections"></a>Geringe Bandbreiten #a0 intermittierende Verbindungen

Mobile Clients müssen regelmäßig mit niedriger Bandbreite und zeitweiligen Verbindungen arbeiten. Ihre APP sollte alle Timeouts entsprechend behandeln, indem Sie dem Benutzer eine Kontext Meldung bereitstellt. Sie sollten auch Benutzer Fortschrittsindikatoren angeben, um Ihren Benutzern Feedback für alle langwierigen Prozesse zur Verfügung zu stellen.

## <a name="design-considerations-for-mobile"></a>Entwurfsüberlegungen für mobile Geräte

Mit unserer mobilen Plattform können apps eine immersive Erfahrung mit dem App-Inhalt sein, der den gesamten Bildschirm außer der Navigation in den Haupt Teams aufnimmt. Befolgen Sie die nachstehenden Richtlinien, um eine immersive Umgebung zu erstellen, die nahtlos in den Microsoft Teams-Client passt.

### <a name="layouts"></a>Layouts

Die Auswahl des richtigen Layouts für Ihre Registerkarte ist wichtig. Sie sollten die Art von Informationen berücksichtigen, die Sie präsentieren, und ein Layout auswählen, das es für einen einfachen Verbrauch organisiert. Einige potenzielle Optionen werden unten erläutert.

#### <a name="single-canvas"></a>Einzelne Leinwand

Dies ist ein großer Bereich, in dem Arbeit erledigt wird. Die wiki-app folgt diesem Muster. Wenn Sie über eine APP verfügen, die Inhalte nicht in kleinere Komponenten unterteilt, wäre dies gut geeignet.

![einzelnes Canvas-Layout](~/assets/images/mobile-single-canvas.png)

#### <a name="list"></a>Liste

Listen eignen sich hervorragend zum Sortieren und Filtern großer Datenmengen und bieten eine große Rolle, um die wichtigsten Dinge am besten zu halten. Es ist hilfreich, sortierbare Spalten zu verwenden. Im Menü mit den Auslassungspunkten können jedem Listenelementaktionen hinzugefügt werden.

![Listenlayout](~/assets/images/mobile-list.png)

#### <a name="grid"></a>Raster

Raster sind nützlich, um Elemente anzuzeigen, die sehr visuell sind. Es hilft, ein Filter-oder Suchsteuerelement am oberen Rand einzuschließen.

![Rasterlayout](~/assets/images/mobile-grid.png)

### <a name="tabs-with-bots-on-mobile"></a>Tabs mit Bots auf mobilen Geräten

Im folgenden finden Sie ein Beispiel für eine persönliche APP, die zwei statische Registerkarten und einen bot enthält.

![Tabs und Bots auf mobilen Geräten](~/assets/images/mobile-tab-with-bot.png)

### <a name="ui-components"></a>Benutzeroberflächenkomponenten

#### <a name="color-palettes"></a>Farbpaletten

Die Verwendung unserer genehmigten neutralen Palette für Hintergründe, Benachrichtigungen, Text und Schaltflächen hilft Ihrer APP, sich in Microsoft Teams zu Hause zu fühlen. Da Teams Mobile zwei Farbdesigns (hell und dunkel) aufweist, sollten Sie sicherstellen, dass Ihre APP in beiden Farben gut aussieht.

##### <a name="light-color"></a>Helle Farbe

![helle Farbpalette](~/assets/images/light-color.png)

##### <a name="dark-color"></a>Dunkle Farbe

![dunkle Farbpalette](~/assets/images/dark-color.png)

#### <a name="buttons-and-controls"></a>Schaltflächen und Steuerelemente

Die Art und Weise, wie Schaltflächen formatiert werden, hilft bei der Kommunikation, welche Art von Aktion ausgelöst wird. Wir halten eine Vielzahl von Schaltflächen, die formatiert sind, um unterschiedliche Schwerpunkte anzuzeigen. Schaltflächen können Text, ein Symbol oder eine Kombination aus Text und Symbol aufweisen. Um verschiedene Ebenen in einer Hierarchie zu kommunizieren, haben wir die primären und sekundären Schaltflächen innerhalb der einzelnen Kategorien entworfen.

![Schaltflächen](~/assets/images/buttons.png)

![Auswahlsteuerelemente](~/assets/images/selection-controls.png)

![Chiclets und Pillen](~/assets/images/chiclets-and-pills.png)

#### <a name="typography"></a>Typografie

Typografie sollte eindeutig und zielgerichtet sein. Betonen Sie wichtige Informationen, und vermeiden Sie die Verwendung mehrerer Schriftarten und Größen zur Verringerung von Verwirrung. Wir empfehlen die Verwendung von satzfall und vermeiden die Verwendung aller Caps für Lokalisierung und Lesbarkeit.

![Mobile Typograph](~/assets/images/mobile-typography.png)

#### <a name="fields-and-flyouts"></a>Felder und Flyouts

Felder sind Bereiche, in denen Benutzer Text eingeben können. Flyouts sind leichter als Dialogfelder und werden aus dem oberen Bereich angezeigt.

##### <a name="list-controls"></a>Steuerelemente auflisten

![Mobile Listensteuerelemente](~/assets/images/mobile-list-controls.png)

##### <a name="field-controls"></a>Feldsteuerelemente

![Mobile Feldsteuerelemente](~/assets/images/mobile-field-controls.png)
