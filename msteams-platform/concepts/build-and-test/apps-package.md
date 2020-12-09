---
title: Verpacken Ihrer APP
description: Hier erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, hochladen und Speichern von Veröffentlichungen verpacken.
ms.topic: conceptual
ms.openlocfilehash: 6929375c8d6a1602f01d83d15bfa0dab7f02a664
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605274"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Erstellen eines App-Pakets für Ihre Microsoft Teams-App

Apps in Microsoft Teams werden durch eine JSON-Datei für App-Manifeste definiert und in einem App-Paket mit ihren Symbolen gebündelt. Sie benötigen ein App-Paket, um Ihre APP in Microsoft Teams hochzuladen und zu installieren und entweder in Ihrem Branchen-App-Katalog oder in AppSource zu veröffentlichen.

Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:

* Eine Manifestdatei mit dem Namen `manifest.json` , die Attribute Ihrer APP angibt und auf erforderliche Ressourcen für Ihre Benutzeroberfläche verweist, beispielsweise den Speicherort der Registerkarten-Konfigurationsseite oder die Microsoft App-ID für den bot.
* [Symbole für Farben und Gliederungen für Ihre APP](#app-icons).

## <a name="creating-a-manifest"></a>Erstellen einer Manifestdatei

*Teams App Studio* kann bei der Konfiguration ihres Manifests behilflich sein. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Siehe [Übersicht über das App-Studio](~/concepts/build-and-test/app-studio-overview.md).

Ihre Manifestdatei muss den Namen "manifest.json" tragen und sich auf der obersten Ebene des Upload-Pakets befinden. Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen. Für Microsoft Teams-apps und insbesondere AppSource (ehemals Office Store)-Übermittlung müssen Sie das aktuelle [Manifest-Schema](~/resources/schema/manifest-schema.md)verwenden.

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren:
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="app-icons"></a>App-Symbole

Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: ein Farbsymbol und ein Gliederungssymbol. Damit Ihre APP die AppSource-Überprüfung übergibt, müssen diese Symbole die folgenden Größenanforderungen erfüllen.

> [!Note]
> Wenn Ihre APP über eine bot-oder Messaging-Erweiterung verfügt, werden Ihre Symbole auch in Ihrer Microsoft Azure bot-Dienstregistrierung enthalten sein.

### <a name="color-icon"></a>Farbsymbol

Die Farbversion Ihres Symbols wird in den meisten Microsoft Teams-Szenarien angezeigt und muss 192x192 Pixel sein. Das Symbol Symbol (96x96 Pixel) kann eine beliebige Farbe oder Farbe sein, es muss jedoch auf einem soliden oder vollständig transparenten Quadrat Hintergrund sitzen.

Teams schneidet ihr Symbol automatisch so ab, dass in bot-Szenarien ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und einer hexagonalen Form angezeigt wird. Fügen Sie 48 Pixelabstand um Ihr Symbol ein, damit diese Kulturen ohne jegliche Details gemacht werden können.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Microsoft Teams Color Icon Design Guidance." border="false":::

### <a name="outline-icon"></a>Gliederungssymbol

Ein Gliederungssymbol wird in zwei Szenarien angezeigt:

* Wenn Ihre APP in der APP-Leiste auf der linken Seite von Microsoft Teams verwendet und "gehisst" wird.
* Wenn ein Benutzer die Messaging Erweiterung der APP anstiftet.

Das Symbol muss 32x32 Pixel sein. Er kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (es sind keine anderen Farben zulässig). Das Symbol "Gliederung" sollte keinen zusätzlichen Abstand um das Symbol haben.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Microsoft Teams Color Icon Design Guidance." border="false":::

### <a name="best-practices"></a>Bewährte Methoden

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Illustration, die zeigt, wie Sie Ihre APP-Symbole entwerfen." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Ausführen: Folgen Sie den genauen Gliederungssymbol-Richtlinien

Die in Ihrem Symbol verwendeten RGB-Werte von weiß müssen rot sein: 255, grün: 255, blau: 255. Alle anderen Teile des Gliederungs Symbols müssen vollständig transparent sein, wobei der Alphakanal auf 0 festgelegt ist.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Illustration, die zeigt, wie Sie Ihre APP-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Nicht: Zuschneiden in einer kreisförmigen oder runden quadratischen Form

Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein. Runden Sie die Ecken Ihres Symbols nicht ab. Teams passt den Eckenradius automatisch an.

   :::column-end:::
:::row-end:::

### <a name="examples"></a>Beispiele

Hier erfahren Sie, wie App-Symbole in verschiedenen Teams-Funktionen und Kontexten angezeigt werden.

#### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a>Bot (Kanal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem bot-Inside-Kanal aussieht." border="false":::

#### <a name="messaging-extension"></a>Messaging-Erweiterung

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<alt-Text>" border="false":::
