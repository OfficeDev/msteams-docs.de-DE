---
title: Verpacken Sie Ihre App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, Hochladen und Store-Publishing verpacken.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 219e2d5341707ed51b7e0a3a8077f93df9eac640
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565214"
---
# <a name="create-a-microsoft-teams-app-package"></a>Erstellen eines Microsoft Teams-App-Pakets

Sie benötigen ein App-Paket, wie auch immer Sie Ihre Microsoft Teams-App verteilen möchten. Ein gültiges Paket ist eine ZIP-Datei, die Folgendes enthält:

* **App-Manifest**: Beschreibt, wie Ihre App konfiguriert ist, einschließlich ihrer Funktionen, erforderlichen Ressourcen und anderer wichtiger Attribute.
* **App-Symbole**: Jedes Paket erfordert ein Farb- und Umrisssymbol für Ihre App.

## <a name="app-manifest"></a>App-Manifest

Ihre App-Manifestdatei muss sich auf der obersten Ebene des Pakets mit dem Namen `manifest.json` befinden. 

Stellen Sie beim Veröffentlichen im Teams-Speicher sicher, dass das Manifest auf das neueste [Schema](~/resources/schema/manifest-schema.md)verweist.

## <a name="app-icons"></a>App-Symbole

Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: eine Farb- und Gliederungsversion.

> [!Note]
> Wenn Ihre App über einen Bot oder eine Messaging-Erweiterung verfügt, werden Ihre Symbole auch in Ihre Microsoft Azure Bot Service-Registrierung einbezogen.

Damit Ihre App Teams Store-Überprüfung bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.

### <a name="color-icon"></a>Farbsymbol

Die Farbversion ihres Symbols wird in den meisten Teams Szenarien angezeigt und muss 192x192 Pixel betragen. Ihr Symbolsymbol (96x96 Pixel) kann eine beliebige Farbe haben, muss jedoch auf einem durchgezogenen oder vollständig transparenten quadratischen Hintergrund sitzen.

Teams schneidet Ihr Symbol automatisch zu, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und einer sechseckigen Form in Bot-Szenarien anzuzeigen. Um das Symbol zuzuschneiden, ohne Details zu verlieren, schließen Sie 48 Pixel Auffüllung um Ihr Symbol ein.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams Farbsymbol und Designanleitung." border="false":::

### <a name="outline-icon"></a>Gliederungssymbol

In zwei Szenarien wird ein Gliederungssymbol angezeigt:

* Wenn Ihre App verwendet und in der App-Leiste auf der linken Seite von Teams "gehisst" wird.
* Wenn ein Benutzer die Messagingerweiterung Ihrer App anheftet.

Das Symbol muss 32x32 Pixel groß sein. Es kann weiß mit einem transparenten Hintergrund oder transparent mit einem weißen Hintergrund sein (keine anderen Farben sind erlaubt). Das Umrisssymbol sollte keine zusätzliche Auffüllung um das Symbol herum haben.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams Anleitung zum Entwurf des Umrisssymbols." border="false":::

### <a name="best-practices"></a>Bewährte Methoden

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung zum Entwerfen Ihrer App-Symbole." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Tun: Befolgen Sie die genauen Richtlinien für das Gliederungssymbol

Die RGB-Werte von Weiß, die in Ihrem Symbol verwendet werden, müssen Rot sein: 255, Grün: 255, Blau: 255. Alle anderen Teile des Gliederungssymbols müssen vollständig transparent sein, wobei der Alphakanal auf 0 gesetzt ist.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung zeigt, wie Sie Ihre App-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Nicht: Zuschneiden in kreisförmiger oder abgerundeter quadratischer Form

Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein. Umrunden Sie nicht die Ecken Ihres Symbols. Teams passt den Eckenradius automatisch an.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Nicht: Andere Marken kopieren

Ihre Symbole dürfen keine urheberrechtlich geschützten Produkte imitieren, die Sie nicht besitzen. Beispielsweise ein Design, das einem Microsoft-Produkt oder einer Microsoft-Marke ähnelt.

### <a name="examples"></a>Beispiele

So werden App-Symbole in verschiedenen Teams Funktionen und Kontexten angezeigt.

#### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a>Bot (Kanal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb des Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a>Messaging-Erweiterung

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<Alt-Text>" border="false":::

## <a name="next-step"></a>Nächster Schritt

Wählen Sie aus, wie Sie Ihre App verteilen möchten:

> [!div class="nextstepaction"]
> [Sideload Ihre App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Veröffentlichen Sie Ihre App in Ihrer Organisation](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Veröffentlichen Ihrer App im Store](~/concepts/deploy-and-publish/appsource/publish.md)
