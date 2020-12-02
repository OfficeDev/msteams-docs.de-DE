---
title: Verpacken Ihrer APP
description: Erfahren Sie, wie Sie Ihre APP zum Testen, hochladen und veröffentlichen in Microsoft Teams verpacken.
keywords: Apps für Teams-Verpackungen
ms.topic: conceptual
ms.openlocfilehash: 4c20e2c1b3c8d7ef13d16b354449887b3c0f1147
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552570"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Erstellen eines App-Pakets für Ihre Microsoft Teams-App

Apps in Microsoft Teams werden durch eine JSON-Datei für App-Manifeste definiert und in einem App-Paket mit ihren Symbolen gebündelt. Sie benötigen ein App-Paket, um Ihre APP in Microsoft Teams hochzuladen und zu installieren und entweder im App-Katalog ihrer Branche oder in AppSource zu veröffentlichen.

Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:

* Eine Manifestdatei mit dem Namen "manifest.json", die Attribute Ihrer APP angibt und auf erforderliche Ressourcen für Ihre Benutzeroberfläche verweist, beispielsweise den Speicherort der Registerkarten-Konfigurationsseite oder die Microsoft App-ID für den bot.
* Ein transparentes "Outline"-Symbol und ein vollständiges "Color"-Symbol. Weitere Informationen finden Sie unter [Icons](#icons) weiter unten in diesem Thema.

## <a name="creating-a-manifest"></a>Erstellen einer Manifestdatei

*Teams App Studio* kann bei der Konfiguration ihres Manifests behilflich sein. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Siehe [Übersicht über das App-Studio](~/concepts/build-and-test/app-studio-overview.md).

Ihre Manifestdatei muss den Namen "manifest.json" tragen und sich auf der obersten Ebene des Upload-Pakets befinden. Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen. Für Microsoft Teams-apps und insbesondere AppSource (ehemals Office Store)-Übermittlung müssen Sie das aktuelle [Manifest-Schema](~/resources/schema/manifest-schema.md)verwenden.

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren:
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="icons"></a>Symbole

> [!Note]
> Wenn Ihre APP eine bot-oder Messaging-Erweiterung enthält, werden die Symbole verwendet, die in Ihre bot-Registrierung im bot-Framework hochgeladen werden.

Microsoft Teams benötigt zwei Symbole für Ihre APP-Erfahrung, die innerhalb des Produkts verwendet werden. Symbole müssen im Paket enthalten sein und über relative Pfade im Manifest referenziert werden. Die maximale Länge jedes Pfads beträgt 2048 Bytes, und das Format des Symbols ist. png.

### <a name="color"></a>color

Das `color` Symbol wird in Microsoft Teams verwendet (in App-und Tab-Galerien, Bots, Flyouts usw.). Dieses Symbol sollte 192x192 Pixel sein. Bei Ihrem Symbol kann es sich um eine beliebige Farbe (oder Farben) handeln, der Hintergrund sollte jedoch ihre Branding-Akzentfarbe sein. Es sollte auch eine kleine Menge von Textabstand um das Symbol verfügen, um das hexagonale Zuschneiden für die bot-Version des Symbols unterzubringen.

### <a name="outline"></a>outline

Das `outline` Symbol wird an diesen Stellen verwendet: die APP-Leiste und die Messaging Erweiterungen, die der Benutzer als Favorit markiert hat. Dieses Symbol muss 32x32 Pixel sein. Das Gliederungssymbol muss nur weiß und Transparenz enthalten (keine anderen Farben). Das Symbol kann weiß mit transparentem Hintergrund oder transparent mit weißem Hintergrund sein. Das Symbol für die Gliederung sollte nicht über einen zusätzlichen Textabstand verfügen, der das Symbol umgibt, und sollte so dicht wie möglich abgeschnitten sein, während die 32x32-Bemaßungen weiterhin beibehalten werden. Hier sind einige gute Beispiele:

![Beispiel-Gliederungssymbole](~/assets/images/icons/sample20x20s.png)

[! Tipp zum Erstellen eines transparenten Symbols]

* Die Farbe muss in RGB "weiß" sein (rot: 255, grün: 255, blau: 255).
* Der gesamte andere Teil des Symbols sollte transparent sein.
* Für die Übergabe muss das kleine Symbol vollständig transparent sein, mit einem Alphakanalwert von 0 – ein beliebiger anderer Wert ist ein Fehler.

Angenommen, Ihr Unternehmen ist contoso. Sie möchten zwei Symbole übermitteln:

![Symbol Showcase](~/assets/images/framework/framework_submit_icon.png)

Hier erfahren Sie, wie die Symbole auf der Benutzeroberfläche angezeigt werden:

#### <a name="bot-and-chiclet-in-channel-view"></a>Bot-und chiclet in der Kanalansicht

![Bot-und chiclet-UX](~/assets/images/icons/botandchiclet.png)

#### <a name="flyout"></a>Flyout

![Beispiel für Contoso-Flyout](~/assets/images/icons/flyout.png)

#### <a name="app-bar-and-home-screen"></a>App-Leiste und Startbildschirm

![Beispiel für Contoso-App-Leiste Homescreen](~/assets/images/icons/appbarhomescreen.png)
