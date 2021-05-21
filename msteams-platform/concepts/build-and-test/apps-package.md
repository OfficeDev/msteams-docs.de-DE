---
title: Packen Ihrer App
description: Erfahren Sie, wie Sie Microsoft Teams App zum Testen, Hochladen und Speichern von Veröffentlichungen packen.
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

Sie benötigen ein App-Paket, planen jedoch, Ihre app Microsoft Teams verteilen. Ein gültiges Paket ist eine ZIP-Datei, die Folgendes enthält:

* **App-Manifest:** Beschreibt, wie Ihre App konfiguriert ist, einschließlich ihrer Funktionen, erforderlichen Ressourcen und anderer wichtiger Attribute.
* **App-Symbole:** Jedes Paket erfordert ein Farb- und Gliederungssymbol für Ihre App.

## <a name="app-manifest"></a>App-Manifest

Ihre App-Manifestdatei muss auf der obersten Ebene des Pakets mit dem Namen `manifest.json` sein. 

Stellen Sie beim Veröffentlichen im Teams sicher, dass das Manifest auf das neueste Schema [verweist.](~/resources/schema/manifest-schema.md)

## <a name="app-icons"></a>App-Symbole

Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: eine Farb- und Gliederungsversion.

> [!Note]
> Wenn Ihre App über einen Bot oder eine Messagingerweiterung verfügt, werden Ihre Symbole auch in Ihrer Microsoft Azure Bot Service-Registrierung enthalten.

Damit Ihre App die Teams bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.

### <a name="color-icon"></a>Farbsymbol

Die Farbversion Des Symbols wird in den meisten Teams angezeigt und muss 192 x 192 Pixel groß sein. Ihr Symbol (96 x 96 Pixel) kann eine beliebige Farbe sein, muss jedoch auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund stehen.

Teams Symbol automatisch zu, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und eine hexagonale Form in Botszenarien angezeigt. Um das Symbol zuschneiden, ohne Details zu verlieren, schließen Sie 48 Pixel Abstand um das Symbol ein.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams Farbsymbol und Entwurfsanleitung." border="false":::

### <a name="outline-icon"></a>Gliederungssymbol

Ein Gliederungssymbol wird in zwei Szenarien angezeigt:

* Wenn Ihre App verwendet wird und auf der App-Leiste auf der linken Seite des Teams.
* Wenn ein Benutzer die Messagingerweiterung Ihrer App anheften.

Das Symbol muss 32 x 32 Pixel groß sein. Es kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig). Das Gliederungssymbol sollte keinen zusätzlichen Abstand um das Symbol haben.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams Gliederungssymbolentwurfsanleitung." border="false":::

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

Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein. Runden Sie nicht die Ecken Ihres Symbols. Teams automatisch den Eckenradius an.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Don't: Copy other brands

Ihre Symbole dürfen keine urheberrechtlich geschützten Produkte imitieren, die Sie nicht besitzen. Beispiel: ein Design, das einem Microsoft-Produkt oder einer Marke ähnelt.

### <a name="examples"></a>Beispiele

Hier sehen Sie, wie App-Symbole in verschiedenen Teams und Kontexten angezeigt werden.

#### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a>Bot (Kanal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb eines Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a>Messaging-Erweiterung

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<text>" border="false":::

## <a name="next-step"></a>Nächster Schritt

Wählen Sie aus, wie Sie Ihre App verteilen möchten:

> [!div class="nextstepaction"]
> [Querladen Ihrer App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Veröffentlichen Ihrer App in Ihrer Organisation](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Veröffentlichen Ihrer App im Store](~/concepts/deploy-and-publish/appsource/publish.md)
