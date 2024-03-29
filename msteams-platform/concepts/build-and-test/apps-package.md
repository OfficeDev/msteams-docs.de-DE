---
title: Verpacken Ihrer App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App packen und in Teams hochladen. Erstellen Sie ein App-Paket, aktivieren Sie das benutzerdefinierte Hochladen, und stellen Sie sicher, dass Ihre App mit HTTPs ausgeführt und zugänglich ist.
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: cd2bb1c2f0ff97a28f467334148c283142b2d535
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791454"
---
# <a name="create-teams-app-package"></a>Teams-App-Paket erstellen

Sie benötigen ein App-Paket. Sie planen jedoch, Ihre Microsoft Teams-App zu verteilen. Ein gültiges Paket ist eine ZIP-Datei, die Folgendes enthält:

* **App-Manifest**: Das Manifest beschreibt, wie Ihre App konfiguriert ist, einschließlich ihrer Funktionen, der erforderlichen Ressourcen und anderer wichtiger Attribute.
* **App-Symbole**: Jedes Paket erfordert ein Farb- und ein Kontursymbol für Ihre App.

## <a name="teams-doesnt-host-your-app"></a>Teams hostet Ihre App nicht

Wenn ein Benutzer Ihre App in Teams installiert, wird ein App-Paket installiert, das nur eine einzige Konfigurationsdatei (auch als App-Manifest bekannt) und die Symbole Ihrer App enthält. Die Logik und der Datenspeicher der App werden an anderer Stelle gehostet, z. B. während der Entwicklung auf „localhost“ und unter Azure Web Services. Teams greift über HTTPS auf diese Ressourcen zu.

:::image type="content" source="../../assets/images/teams-app-host.png" alt-text="Abbildung des App-Hostings der Teams-App":::

## <a name="app-manifest"></a>App-Manifest

Ihre App-Manifestdatei muss sich auf der obersten Ebene des Pakets befinden und den Namen `manifest.json` aufweisen.

Stellen Sie beim Veröffentlichen im Microsoft Teams-Store sicher, dass Ihr Manifest auf das neueste [Schema](~/resources/schema/manifest-schema.md) verweist.

## <a name="app-icons"></a>App-Symbole

Ihr App-Paket muss zwei .png-Versionen Ihres App-Symbols enthalten: eine Farb- und eine Konturversion.

> [!Note]
> Wenn Ihre App über eine Bot- oder Nachrichtenerweiterung verfügt, werden Ihre Symbole auch in Ihre Microsoft Azure Bot Service-Registrierung aufgenommen.

Damit Ihre App die Microsoft Teams Store-Überprüfung bestehen kann, müssen diese Symbole die folgenden Größenanforderungen erfüllen.

### <a name="color-icon"></a>Farbsymbol

Die Farbversion Ihres Symbols wird in den meisten Teams-Szenarien angezeigt und muss 192x192 Pixel groß sein. Die Symbolgrafik (96 x 96 Pixel) kann eine beliebige Farbe aufweisen, muss sich jedoch auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund befinden.

In Microsoft Teams wird Ihr Symbol in verschiedenen Szenarien automatisch auf ein Quadrat mit abgerundeten Ecken und in Bot-Szenarien auf eine sechseckige Form zugeschnitten. Damit beim Zuschneiden keine Details verloren gehen, fügen Sie rund um das Symbol einen Abstand von 48 Pixel hinzu.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Leitfaden für die Gestaltung von Microsoft Teams-Farbsymbolen.":::

### <a name="outline-icon"></a>Kontursymbol

Ein Kontursymbol wird in zwei Szenarien angezeigt:

* Wenn Ihre App verwendet wird und auf der App-Leiste auf der linken Seite von Microsoft Teams "hervorgehoben" ist.
* Wenn ein Benutzer die Nachrichtenerweiterung Ihrer App anheftet.

Das Symbol muss 32 x 32 Pixel groß sein. Es kann weiß mit transparentem Hintergrund oder transparent mit weißem Hintergrund sein (es sind keine anderen Farben zulässig). Das Kontursymbol sollte keinen zusätzlichen Abstand um das Symbol aufweisen.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Leitfaden für die Gestaltung von Microsoft Teams-Kontursymbolen.":::

### <a name="best-practices"></a>Bewährte Methoden

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole gestalten müssen.":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Richtig: Befolgen Sie die Vorgaben für Kontursymbole

Die RGB-Werte von Weiß, das in Ihrem Symbol verwendet wird, müssen sein: Rot: 255, Grün: 255, Blau: 255. Alle anderen Teile des Kontursymbols müssen vollständig transparent sein, wobei der Alphakanal auf 0 festgelegt ist.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Abbildung, die zeigt, wie Sie Ihre App-Symbole nicht gestalten sollten.":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Zu vermeiden: Kreisförmig oder zu einem Quadrat mit abgerundeten Ecken zuschneiden

Das in Ihrem App-Paket übermittelte Farbsymbol muss quadratisch sein. Runden Sie die Ecken des Symbols nicht ab. Die Ecken werden in Microsoft Teams automatisch angepasst.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Zu vermeiden: Andere Marken kopieren

Ihre Symbole dürfen keine urheberrechtlich geschützten Produkte imitieren, deren Eigentümer Sie nicht sind. Beispiel: ein Design, das dem eines Microsoft-Produkts oder einer Microsoft-Marke ähnelt.

### <a name="examples"></a>Beispiele

Hier sehen Sie, wie App-Symbole in verschiedenen Microsoft Teams-Funktionen und -Kontexten angezeigt werden.

#### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einer persönlichen App aussieht.":::

#### <a name="bot-channel"></a>Bot (Kanal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Beispiel, das zeigt, wie ein App-Symbol in einem Bot innerhalb eines Kanals aussieht.":::

#### <a name="message-extension"></a>Nachrichtenerweiterung

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="Alternativer Text":::

## <a name="next-step"></a>Nächster Schritt

Wählen Sie aus, wie Sie Ihre App verteilen möchten:

> [!div class="nextstepaction"]
> [Querladen der App in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Veröffentlichen der App in Ihrer Organisation](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Veröffentlichen Ihrer App im Store](~/concepts/deploy-and-publish/appsource/publish.md)

## <a name="see-also"></a>Siehe auch

[Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md)
