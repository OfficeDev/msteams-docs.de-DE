---
title: Entwerfen Ihrer benutzerdefinierten App
author: heath-hamilton
description: Erfahren Sie, wie Sie Microsoft Teams Apps entwerfen. Zu den Ressourcen gehören das Microsoft Teams UI Kit, Best Practices, Beispiele und mehr.
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 2f21872bd8c37026528ff6fde282e8c433d5e052
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565116"
---
# <a name="designing-your-microsoft-teams-app"></a>Entwerfen Ihrer Microsoft Teams-App

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Konzeptionelles Bild zur Einführung der Microsoft Teams Designrichtlinien.":::

Unabhängig davon, ob Sie Designer, Produktmanager, Entwickler oder Hersteller mit Low-Code-Tools sind, können Diese Richtlinien Ihnen helfen, schnell die richtigen Designentscheidungen für Ihre Microsoft Teams-App zu treffen.

## <a name="teams-app-design-principles"></a>Teams-Design-Prinzipien für Apps

Teams-Apps helfen Menschen, gemeinsam mehr zu erreichen. Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.

:::row:::
   :::column span="":::

### <a name="collaborative"></a>Gemeinsame

Teams-Apps helfen Menschen, gemeinsam mehr zu erreichen. Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a>Vertrauenswürdig

Die App ist sicher und konform. Benutzer können leicht Informationen über den Datenschutz finden.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a>Global inklusive

Personen aller Herkunft, Skillsets und Disziplinen können die App verwenden. Es ist kulturell, rassisch und sozial bewusst.

   :::column-end:::
   :::column span="":::

### <a name="light"></a>Niedrig

Die App konzentriert sich auf Kernszenarien, die mit Teams Workflows verschmelzen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a>Native oder ausgeprägte

Die App verwendet native Teams Designkomponenten oder Ihre eigenen. Es gibt keine Mischung aus Farbschemata, Steuerelementen usw.

   :::column-end:::
   :::column span="":::

### <a name="useful"></a>Nützlich

Die App basiert auf einem Szenario, das Die Menschen in Teams tun müssen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a>Einfach zu bedienen

Die Benutzeroberfläche ist leicht zu verstehen, angenehm in Aussehen und Ton und macht Menschen produktiver.

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a>Reaktionsfähig

Die App ist Geräte- und Bildschirmagnostik.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a>Barrierefrei

Die App erfüllt Teams Barrierefreiheitsanforderungen in Bezug auf Farbkontrast, Navigationsalternativen und mehr.

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a>Gut beschrieben

Text, Symbole und Bilder machen deutlich, wofür die App da ist und wie sie verwendet wird.

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a>Erstellen eines kohäsiven Erlebnisses

Das Entwerfen einer Teams-App ist wie das Entwerfen einer herkömmlichen Web-App – aber auch ein wenig anders. Ein effektives Design hebt die einzigartigen Attribute Ihrer App hervor und passt gleichzeitig auf Teams Features und Kontexte.

Diese Richtlinien und Ressourcen können Ihnen helfen, dieses Gleichgewicht zu erreichen. Sie wissen, was zu tun ist und was Sie beim Entwerfen Ihrer Teams-App vermeiden müssen (z. B. mehrstufige Navigation in einer Registerkarte).

## <a name="planning-your-app"></a>Planen Ihrer App

Um eine hochwertige Teams-App zu entwerfen, müssen Sie zunächst verstehen, was Ihre App tun soll und wie Sie denken, dass die Benutzer sie verwenden werden. Wenn Sie dies noch nicht getan haben, nehmen Sie sich etwas Zeit, um Ihre App ordnungsgemäß zu [planen.](../../concepts/extensibility-points.md)

## <a name="design-fundamentals"></a>Grundlegendes zur Gestaltung

Erfahren Sie mehr über die [Grundlagen Teams App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemata und mehr.

## <a name="basic-fluent-ui-components-for-teams"></a>Grundlegende Fluent UI-Komponenten für Teams

Basierend auf Fluent UI sind dies die Kernelemente für die [Erstellung vertrauter Teams Schnittstellen](design-teams-app-basic-ui-components.md).

## <a name="ui-templates"></a>Vorlagen für Benutzeroberflächen

Erstellen Sie schnell komplexe, hochauflösende Designs mit [Vorlagen für gängige Teams Anwendungsfälle und Workflows](design-teams-app-ui-templates.md).

## <a name="app-capabilities"></a>App-Funktionen

Verstehen Sie, wie Benutzer Teams Apps hinzufügen, verwenden und verwalten, um die einzelnen Funktionen in Ihrem Entwurf zu nutzen.

* [Persönliche Apps](../../concepts/design/personal-apps.md)
* [Registerkarten](../../tabs/design/tabs.md)
* [Messaging-Erweiterungen](../../messaging-extensions/design/messaging-extension-design.md)
* [Bots](../../bots/design/bots.md)
* [Besprechungserweiterungen](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Aufgabenmodule](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a>App-Anpassung

Erfahren Sie, wie der Teams-Administrator die App basierend auf den Bedarf der Organisation anpassen oder umbenennen kann. Diese Anpassung ist aktiviert, wenn Sie die `configurableProperties` im Manifestschema definieren. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).

> [!NOTE]
> Die App-Anpassung ermöglicht es Administratoren, das Erscheinungsbild der Apps zu ändern, die über Bots, Messagingerweiterungen, Registerkarten und Connectors geladen werden. Wenn der Teams Administrator beispielsweise den Namen einer App von *Contoso* in *Contoso Agent* anpasst, wird die App mit dem neuen Namen *Contoso Agent* für Benutzer angezeigt. Beim Hinzufügen eines Connectors zu einem Chat werden in der Liste jedoch immer noch der Name der App als *Contoso* angezeigt.
> 
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die Sie beim Anpassen Ihrer App befolgen müssen. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).

## <a name="tools-and-samples"></a>Tools und Beispiele

Die folgenden Tools können Designern und Entwicklern den Einstieg erleichtern:

### <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Entwerfen Sie eine Teams-App mit UI-Komponenten, Vorlagen und Beispielen, die Sie nach Bedarf ziehen, ablegen und ändern können. Das UI-Kit enthält außerdem umfassende Informationen darüber, wie Apps in verschiedenen Teams Szenarien aussehen und sich verhalten sollten.

> [!div class="nextstepaction"]
> [Holen Sie sich das UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams UI-Bibliothek

Zeigen Sie einzelne Teams UI-Vorlagen und zugehörigeKomponenten in Ihrem Browser an und testen Sie sie.

> [!div class="nextstepaction"]
> [Testen Sie die UI-Bibliothek (Spielplatz)](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams-App-Projekt.

> [!div class="nextstepaction"]
> [Abrufen der UI-Bibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Beispiel-App

Installieren Sie eine Beispiel-App, um zu sehen, wie UI-Vorlagen in Teams Kontexten aussehen und sich verhalten.

> [!div class="nextstepaction"]
> [Abrufen der Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a>Sonstige Ressourcen

Um mehr zu erfahren, versuchen Sie eine der folgenden Ressourcen:

### <a name="fluent-ui-documentation"></a>Fließende UI-Dokumentation

Hier erhalten Sie Codebeispiele und Implementierungsdetails für die fluent UI-basierten Komponenten, die zum Erstellen Teams-Erlebnisse verwendet werden.

> [!div class="nextstepaction"]
> [Versuchen Sie, Teams UI-Komponenten (Fluent UI) zu verwenden](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a>Adaptive Cards-Designer

Entwerfen Sie Adaptive Cards in unserem webbasierten Tool.

> [!div class="nextstepaction"]
> [Testen Sie den Adaptive Cards-Designer](https://adaptivecards.io/designer/)
