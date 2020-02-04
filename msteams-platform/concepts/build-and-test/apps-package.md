---
title: Verpacken Ihrer APP
description: Erfahren Sie, wie Sie Ihre APP zum Testen, hochladen und veröffentlichen in Microsoft Teams verpacken.
keywords: Apps für Teams-Verpackungen
ms.topic: conceptual
ms.openlocfilehash: b76041b129e766dba2b401aaac0e12958a4e9b0d
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674451"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Erstellen eines App-Pakets für Ihre Microsoft Teams-App

Apps in Microsoft Teams werden durch eine JSON-Datei für App-Manifeste definiert und in einem App-Paket mit ihren Symbolen gebündelt. Sie benötigen ein App-Paket, um Ihre APP in Microsoft Teams hochzuladen und zu installieren und entweder im App-Katalog ihrer Branche oder in AppSource zu veröffentlichen.

Ein Teams-App-Paket ist eine ZIP-Datei, die Folgendes enthält:

* Eine Manifestdatei mit dem Namen "Manifest. JSON", die Attribute Ihrer APP angibt und auf erforderliche Ressourcen für Ihre Benutzeroberfläche verweist, beispielsweise den Speicherort der Registerkarten-Konfigurationsseite oder die Microsoft App-ID für den bot.
* Ein transparentes "Outline"-Symbol und ein vollständiges "Color"-Symbol. Weitere Informationen finden Sie unter [Icons](#icons) weiter unten in diesem Thema.

## <a name="creating-a-manifest"></a>Erstellen einer Manifestdatei

*Teams App Studio* kann bei der Konfiguration ihres Manifests behilflich sein. Es enthält auch eine Reaktions Steuerungs Bibliothek und konfigurierbare Beispiele für Karten. Siehe [Übersicht über das App-Studio](~/concepts/build-and-test/app-studio-overview.md).

Ihre Manifestdatei muss "Manifest. JSON" genannt werden und sich auf der obersten Ebene des Upload-Pakets befinden. Beachten Sie, dass zuvor erstellte Manifeste und Pakete möglicherweise eine ältere Version des Schemas unterstützen. Für Microsoft Teams-apps und insbesondere AppSource (ehemals Office Store)-Übermittlung müssen Sie das aktuelle [Manifest-Schema](~/resources/schema/manifest-schema.md)verwenden.

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren:
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",`

## <a name="icons"></a>Symbole

> [!Note]
> Wenn Ihre APP eine bot-oder Messaging-Erweiterung enthält, werden die Symbole verwendet, die in Ihre bot-Registrierung im bot-Framework hochgeladen werden.

Microsoft Teams benötigt zwei Symbole für Ihre APP-Erfahrung, die innerhalb des Produkts verwendet werden. Symbole müssen im Paket enthalten sein und über relative Pfade im Manifest referenziert werden. Die maximale Länge jedes Pfads beträgt 2048 Bytes, und das Format des Symbols ist. png.

### <a name="color"></a>color

Das `color` Symbol wird in Microsoft Teams verwendet (in App-und Tab-Galerien, Bots, Flyouts usw.). Dieses Symbol sollte 192x192 Pixel sein. Bei Ihrem Symbol kann es sich um eine beliebige Farbe (oder Farben) handeln, der Hintergrund sollte jedoch ihre Branding-Akzentfarbe sein. Es sollte auch eine kleine Menge von Textabstand um das Symbol verfügen, um das hexagonale Zuschneiden für die bot-Version des Symbols unterzubringen.

### <a name="outline"></a>outline

Das `outline` Symbol wird an diesen Stellen verwendet: die APP-Leiste und die Messaging Erweiterungen, die der Benutzer als Favorit markiert hat. Dieses Symbol muss 32x32 Pixel sein. Das Gliederungssymbol muss nur weiß und Transparenz enthalten (keine anderen Farben). Das Symbol kann weiß mit transparentem Hintergrund oder transparent mit weißem Hintergrund sein. Das Symbol für die Gliederung sollte nicht über einen zusätzlichen Textabstand verfügen, der das Symbol umgibt, und sollte so dicht wie möglich abgeschnitten sein, während die 32x32-Bemaßungen weiterhin beibehalten werden. Hier sind einige gute Beispiele:

![Beispiel-Gliederungssymbole](~/assets/images/icons/sample20x20s.png)

Angenommen, Ihr Unternehmen ist contoso. Sie möchten zwei Symbole übermitteln:

![Symbol Showcase](~/assets/images/framework/framework_submit_icon.png)

Hier erfahren Sie, wie die Symbole auf der Benutzeroberfläche angezeigt werden:

#### <a name="bot-and-chiclet-in-channel-view"></a>Bot-und chiclet in der Kanalansicht

![Bot-und chiclet-UX](~/assets/images/icons/botandchiclet.png)

#### <a name="flyout"></a>Flyout

![Beispiel-Contoso-Symbole](~/assets/images/icons/flyout.png)

#### <a name="app-bar-and-home-screen"></a>App-Leiste und Startbildschirm

![Beispiel-Contoso-Symbole](~/assets/images/icons/appbarhomescreen.png)
