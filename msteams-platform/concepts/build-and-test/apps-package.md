---
title: Packen Ihrer App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, Hochladen und Speichern der Veröffentlichung packen.
ms.topic: conceptual
ms.openlocfilehash: 222ea5459b3496c00b1186f15a68c3288ce419f7
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922510"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Erstellen eines App-Pakets für Ihre Microsoft Teams-App

Apps in Teams werden durch eine App-Manifest-JSON-Datei definiert und in einem App-Paket mit ihren Symbolen gebündelt. Sie benötigen ein App-Paket, um Ihre App in Teams hochzuladen und zu installieren und entweder in Ihrem Line of Business-App-Katalog oder in AppSource zu veröffentlichen.

Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:

* Eine Manifestdatei mit dem Namen , die Attribute Ihrer App angibt und auf erforderliche Ressourcen für Ihre Erfahrung verweist, z. B. den Speicherort der Registerkartenkonfigurationsseite oder die `manifest.json` Microsoft-App-ID für den Bot.
* [Farb- und Gliederungssymbole für Ihre App](#app-icons).

## <a name="creating-a-manifest"></a>Erstellen einer Manifestdatei

**Teams App Studio kann** Ihnen bei der Konfiguration Ihres Manifests helfen. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Weitere Informationen finden Sie unter [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).

Ihre Manifestdatei muss den Namen "manifest.jsein" haben und sich auf der obersten Ebene des Uploadpakets begnaufen. Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen. Für Teams-Apps und insbesondere die AppSource-Übermittlung (früher Office Store) müssen Sie das aktuelle [Manifestschema verwenden.](~/resources/schema/manifest-schema.md)

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung von Ihrem Code-Editor zu aktivieren:
>
> `"$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.9/MicrosoftTeams.schema.json",`
 
## <a name="app-icons"></a>App-Symbole

Ihr App-Paket muss zwei PNG-Versionen ihres App-Symbols enthalten– ein Farbsymbol und ein Gliederungssymbol. Damit Ihre App die AppSource-Überprüfung bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.

> [!Note]
> Wenn Ihre App über einen Bot oder eine Messagingerweiterung verfügt, werden Ihre Symbole auch in Ihre Microsoft Azure Bot Service-Registrierung einbezogen.

### <a name="color-icon"></a>Farbsymbol

Die Farbversion Ihres Symbols wird in den meisten Teams-Szenarien angezeigt und muss 192 x 192 Pixel groß sein. Ihr Symbol (96 x 96 Pixel) kann eine beliebige Farbe oder Farbe sein, muss jedoch auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund stehen.

Teams ackert Ihr Symbol automatisch, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und eine hexagonale Form in Botszenarien zu zeigen. Schließen Sie 48 Pixel Abstand um das Symbol ein, damit diese Kulturen ohne Detailverlust hergestellt werden können.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Designanleitungen für Teams-Farbsymbole." border="false":::

### <a name="outline-icon"></a>Gliederungssymbol

Ein Gliederungssymbol wird in zwei Szenarien angezeigt:

* Wenn Ihre App verwendet wird und auf der App-Leiste links von Teams "gehissen" wird.
* wenn ein Benutzer die Messagingerweiterung Ihrer App anheften.

Das Symbol muss 32 x 32 Pixel groß sein. Es kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig). Das Gliederungssymbol sollte keinen zusätzlichen Abstand um das Symbol haben.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Richtlinien zum Entwerfen von Symbolen in Teams." border="false":::

### <a name="best-practices"></a>Bewährte Methoden

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole entwerfen." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Do: Befolgen Sie die Richtlinien für genaue Gliederungssymbole.

Die RGB-Werte von Weiß, die in Ihrem Symbol verwendet werden, müssen Rot sein: 255, Grün: 255, Blau: 255. Alle anderen Teile des Gliederungssymbols müssen vollständig transparent sein, und der Alphakanal ist auf 0 festgelegt.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Don't: Crop in a circular or rounded square shape

Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein. Runden Sie nicht die Ecken Ihres Symbols. Teams passt den Eckenradius automatisch an.

   :::column-end:::
:::row-end:::

### <a name="examples"></a>Beispiele

Hier sehen Sie, wie App-Symbole in verschiedenen Teams-Funktionen und Kontexten angezeigt werden.

#### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a>Bot (Kanal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb eines Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a>Messaging-Erweiterung

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<text>" border="false":::
