---
title: Entwerfen Ihrer benutzerdefinierten App
author: heath-hamilton
description: Erfahren Sie, wie Sie Microsoft Teams entwerfen. Zu den Ressourcen gehören Microsoft Teams UI Kit, bewährte Methoden, Beispiele und vieles mehr.
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: ab311b6b9b8494308916ef602ee98785ab6de61e
ms.sourcegitcommit: 808a203fb963eeade3a8e32db88d64677e37df7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2021
ms.locfileid: "52304026"
---
# <a name="designing-your-microsoft-teams-app"></a>Entwerfen Ihrer Microsoft Teams App

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Konzeptionelles Bild, in dem Microsoft Teams Entwurfsrichtlinien vorgestellt werden.":::

Unabhängig davon, ob Sie Designer, Produktmanager, Entwickler oder Hersteller sind, die Tools mit niedrigem Code verwenden, können diese Richtlinien Ihnen helfen, schnell die richtigen Entwurfsentscheidungen für Ihre Microsoft Teams treffen.

## <a name="teams-app-design-principles"></a>Teams von App-Designprinzipien

Teams Apps helfen, gemeinsam mehr zu erreichen. Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.

:::row:::
   :::column span="":::

### <a name="collaborative"></a>Zusammenarbeit

Teams Apps helfen, gemeinsam mehr zu erreichen. Verwenden Sie diese Prinzipien, um Ihr Design zu leiten.

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a>Vertrauenswürdig

Die App ist sicher und kompatibel. Benutzer können auf einfache Weise Informationen zum Datenschutz finden.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a>Global inklusive

Personen aller Hintergründe, Fähigkeiten und Disziplinen können die App verwenden. Sie ist kulturell, rassistisch und gesellschaftlich bewusst.

   :::column-end:::
   :::column span="":::

### <a name="light"></a>Niedrig

Die App konzentriert sich auf Kernszenarien, die mit Teams werden.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a>Native oder unterschiedliche

Die App verwendet systemeigene Teams oder Eigene. Es gibt keine Mischung aus Farbschemas, Steuerelementen usw.

   :::column-end:::
   :::column span="":::

### <a name="useful"></a>Nützlich

Die App basiert auf einem Szenario, das personen in einem Teams.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a>Einfach zu verwenden

Die Benutzeroberfläche ist leicht zu verstehen, angenehm in Aussehen und Ton und macht die Benutzer produktiver.

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a>Reaktionsfähig

Die App ist geräte- und bildschirmunabhängig.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a>Barrierefrei

Die App erfüllt Teams Barrierefreiheitsanforderungen in Bezug auf Farbkontrast, Navigationsalternativen und vieles mehr.

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a>Gut beschrieben

Text, Symbole und Bilder machen deutlich, wofür die App steht und wie sie verwendet wird.

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a>Erstellen einer gemeinsamen Erfahrung

Das Entwerfen Teams app ist wie das Entwerfen einer herkömmlichen Web-App – aber auch ein wenig anders. Ein effektives Design hebt die eindeutigen Attribute Ihrer App hervor und passt sich natürlich Teams Features und Kontexten an.

Diese Richtlinien und Ressourcen können Ihnen dabei helfen, dieses Gleichgewicht zu finden. Sie wissen, was Sie beim Entwerfen Ihrer Teams -App (z. B. mehrstufige Navigation auf einer Registerkarte) vermeiden sollten.

## <a name="planning-your-app"></a>Planen Ihrer App

Zum Entwerfen einer qualitativ hochwertigen Teams müssen Sie zunächst wissen, was Ihre App tun soll und wie Sie denken, dass die App von den Personen verwendet wird. Wenn Sie dies noch nicht gemacht haben, nehmen Sie sich etwas Zeit, um Ihre [App ordnungsgemäß zu planen.](../../concepts/extensibility-points.md)

## <a name="design-fundamentals"></a>Grundlegendes zur Gestaltung

Lernen Sie [die Grundlagen des Teams-App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemas und vieles mehr.

## <a name="basic-fluent-ui-components-for-teams"></a>Grundlegende Komponenten der Fluent-benutzeroberfläche für Teams

Basierend auf der Fluent-Benutzeroberfläche sind dies die [Kernelemente zum Erstellen vertrauter Teams Schnittstellen.](design-teams-app-basic-ui-components.md)

## <a name="ui-templates"></a>Vorlagen für Benutzeroberflächen

Erstellen Sie schnell komplexe Designs mit hoher Genauigkeit mit Vorlagen für [Teams und Workflows](design-teams-app-ui-templates.md).

## <a name="app-capabilities"></a>App-Funktionen

Erfahren Sie, wie Personen apps hinzufügen, Teams verwenden und verwalten, um die einzelnen Funktionen in Ihrem Entwurf zu nutzen.

* [Persönliche Apps](../../concepts/design/personal-apps.md)
* [Tabs](../../tabs/design/tabs.md)
* [Messaging-Erweiterungen](../../messaging-extensions/design/messaging-extension-design.md)
* [Bots](../../bots/design/bots.md)
* [Besprechungserweiterungen](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Aufgabenmodule](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a>App-Anpassung

Erfahren Sie, Teams Administrator die App je nach Bedarf der Organisation anpassen oder neu umbranden kann. Diese Anpassung ist aktiviert, wenn Sie die `configurableProperties` im Manifestschema definieren. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)

> [!NOTE]
> Mithilfe der App-Anpassung können Administratoren das Aussehen und Die-Gefühl der Apps ändern, die über Bots, Messagingerweiterungen, Registerkarten und Connectors geladen werden. Wenn der Administrator Teams den Namen einer App von *Contoso* in *Contoso Agent* anpasst, wird die App benutzern mit dem neuen Namen *Contoso Agent* angezeigt. Beim Hinzufügen eines Connectors zu einem Chat wird in der Liste der Connectors jedoch weiterhin der Name der App als *Contoso angezeigt.*
> 
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)

## <a name="tools-and-samples"></a>Tools und Beispiele

Die folgenden Tools helfen Designern und Entwicklern bei den ersten Schritte:

### <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Entwerfen Sie Teams App mit Benutzeroberflächenkomponenten, Vorlagen und Beispielen, die Sie nach Bedarf ziehen, ablegen und ändern können. Das UI Kit enthält außerdem umfassende Informationen dazu, wie Apps in unterschiedlichen Szenarien aussehen und Teams sollten.

> [!div class="nextstepaction"]
> [Benutzeroberflächenkit (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams Benutzeroberflächenbibliothek

Anzeigen und Testen einzelner Teams benutzeroberflächenvorlagen und zugehörigen Komponenten in Ihrem Browser.

> [!div class="nextstepaction"]
> [Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Teams App-Projekt.

> [!div class="nextstepaction"]
> [Benutzeroberflächenbibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Beispiel-App

Installieren Sie eine Beispiel-App, um zu sehen, wie Benutzeroberflächenvorlagen in Teams aussehen und verhalten.

> [!div class="nextstepaction"]
> [Die Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a>Sonstige Ressourcen

Weitere Informationen finden Sie in einer der folgenden Ressourcen.

### <a name="fluent-ui-documentation"></a>Dokumentation zur Fluent-Benutzeroberfläche

Hier finden Sie Codebeispiele und Implementierungsdetails für die Fluent-UI-basierten Komponenten, die zum Erstellen von Teams verwendet werden.

> [!div class="nextstepaction"]
> [Testen Teams Benutzeroberflächenkomponenten (Fluent UI)](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a>Designer für adaptive Karten

Entwerfen Sie adaptive Karten in unserem webbasierten Tool.

> [!div class="nextstepaction"]
> [Testen des Designers für adaptive Karten](https://adaptivecards.io/designer/)
