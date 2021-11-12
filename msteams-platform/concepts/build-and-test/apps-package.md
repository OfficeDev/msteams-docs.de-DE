---
title: Verpacken Ihrer App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App zum Testen, Hochladen und Veröffentlichen im Store verpacken.
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 1879bcab13ff9ba355bcebdf68e4c8c061f153a1
ms.sourcegitcommit: 1431dfe08d5a19a63dbf1542a2e6c661e4dd7fc1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2021
ms.locfileid: "60949075"
---
# <a name="create-a-microsoft-teams-app-package"></a>Erstellen eines Microsoft Teams App-Pakets

Sie benötigen ein App-Paket, aber Sie planen, Ihre Microsoft Teams App zu verteilen. Ein gültiges Paket ist eine ZIP-Datei, die Folgendes enthält:

* **App-Manifest:** Beschreibt, wie Ihre App konfiguriert ist, einschließlich der Funktionen, der erforderlichen Ressourcen und anderer wichtiger Attribute.
* **App-Symbole:** Jedes Paket erfordert ein Farb- und Gliederungssymbol für Ihre App.

## <a name="app-manifest"></a>App-Manifest

Die App-Manifestdatei muss sich auf der obersten Ebene des Pakets mit dem Namen `manifest.json` befinden. 

Stellen Sie beim Veröffentlichen im Teams Speicher sicher, dass Ihre Manifestverweise auf das neueste [Schema](~/resources/schema/manifest-schema.md)verweisen.

## <a name="app-icons"></a>App-Symbole

Ihr App-Paket muss zwei PNG-Versionen des App-Symbols enthalten: eine Farb- und Gliederungsversion.

> [!Note]
> Wenn Ihre App über eine Bot- oder Messaging-Erweiterung verfügt, werden Ihre Symbole auch in Ihre Microsoft Azure Bot Service-Registrierung einbezogen.

Damit Ihre App Teams Store-Überprüfung bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.

### <a name="color-icon"></a>Farbsymbol

Die Farbversion Ihres Symbols wird in den meisten Teams-Szenarien angezeigt und muss 192x192 Pixel groß sein. Das Symbolsymbol (96 x 96 Pixel) kann eine beliebige Farbe sein, muss sich jedoch auf einem durchgezogenen oder vollständig transparenten quadratischen Hintergrund befinden.

Teams ihr Symbol automatisch zuschneidet, um ein Quadrat mit abgerundeten Ecken in mehreren Szenarien und eine fiktive Form in Bot-Szenarien anzuzeigen. Um das Symbol zuzuschneiden, ohne Details zu verlieren, fügen Sie 48 Pixel Abstand um ihr Symbol ein.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams Farbsymbol und Designanleitung." border="false":::

### <a name="outline-icon"></a>Gliederungssymbol

Ein Gliederungssymbol wird in zwei Szenarien angezeigt:

* Wenn Ihre App verwendet und auf der App-Leiste auf der linken Seite von Teams "hervorgehoben" wird.
* Wenn ein Benutzer die Messaging-Erweiterung Ihrer App anheftet.

Das Symbol muss 32 x 32 Pixel groß sein. Es kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig). Das Gliederungssymbol sollte keinen zusätzlichen Abstand um das Symbol aufweisen.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams Entwurfsanleitung für Gliederungssymbole." border="false":::

### <a name="best-practices"></a>Bewährte Methoden

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole entwerfen." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Do: Befolgen Sie die genauen Richtlinien für Gliederungssymbole.

Die RGB-Werte von Weiß, das in Ihrem Symbol verwendet wird, müssen Rot sein: 255, Grün: 255, Blau: 255. Alle anderen Teile des Gliederungssymbols müssen vollständig transparent sein, wobei der Alphakanal auf 0 festgelegt ist.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole nicht entwerfen." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Nicht empfohlen: Zuschneiden in einer kreisförmigen oder abgerundeten Quadratform

Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein. Runden Sie nicht die Ecken Des Symbols. Teams passt den Winkelradius automatisch an.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Don't: Copy other labels

Ihre Symbole dürfen keine urheberrechtlich geschützten Produkte imitieren, die Sie nicht besitzen. Beispielsweise ein Design, das einem Microsoft-Produkt oder einer Microsoft-Marke ähnelt.

### <a name="examples"></a>Beispiele

Hier sehen Sie, wie App-Symbole in verschiedenen Teams Funktionen und Kontexten angezeigt werden.

#### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht." border="false":::

#### <a name="bot-channel"></a>Bot (Kanal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol auf einem Bot innerhalb des Kanals aussieht." border="false":::

#### <a name="messaging-extension"></a>Messaging-Erweiterung

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<alternativ>" border="false":::

## <a name="next-step"></a>Nächster Schritt

Wählen Sie aus, wie Sie Ihre App verteilen möchten:

> [!div class="nextstepaction"]
> [Querladen Ihrer App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Veröffentlichen Ihrer App in Ihrer Organisation](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Veröffentlichen Ihrer App im Store](~/concepts/deploy-and-publish/appsource/publish.md)

## <a name="see-also"></a>Siehe auch

[Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md)