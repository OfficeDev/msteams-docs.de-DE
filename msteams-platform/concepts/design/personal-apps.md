---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie eine persönliche Teams-App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 971071be9f345815f5461646d7970efdf05fd5c4
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604990"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Entwerfen Ihrer persönlichen App für Microsoft Teams

Eine persönliche App kann ein bot, ein privater Arbeitsbereich oder beides sein. Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, ein anderes Mal bietet es dem Benutzer eine Vogelperspektive auf alles, was Ihnen gehört, wenn die APP als Registerkarte in mehreren Kanälen konfiguriert wurde.

Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie personenbezogene apps in Microsoft Teams hinzugefügt, verwendet und verwaltet werden können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende persönliche App-Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit. Das UI Kit enthält auch wichtige Themen wie Barrierefreiheit und Anpassungsfähigkeit, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Hinzufügen einer persönlichen App

Sie können eine persönliche App aus dem teamstore (AppSource) oder dem App-Flyout hinzufügen, indem Sie das Symbol **Weitere** auf der linken Seite von Teams auswählen (siehe folgendes Beispiel).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a>Verwenden einer persönlichen app (privater Arbeitsbereich)

Mit einem privaten Arbeitsbereich können Sie für Sie bedeutsame App-Inhalte an einem zentralen Ort anzeigen, ohne Teams zu verlassen.

(Implementierungs Hinweis: der private Arbeitsbereich basiert auf der [*persönlichen Registerkarten*](../../build-your-first-app/build-personal-tab.md) Funktion.)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomie: persönliche app (privater Arbeitsbereich)

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponenten Anatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Attribution**: Ihr App-Logo und Name.|
|B|**Tabs**: bietet Navigation für Ihre persönliche app. Fügen Sie beispielsweise eine Registerkarte **Info** oder **Help** hinzu.|
|C|**Popout-Ansicht**: verschiebt Ihre APP-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.|
|D|**Weiteres Menü**: enthält zusätzliche APP-Informationen und-Optionen. (Sie können **Einstellungen** auch als Registerkarte festlegen.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Tabs**: bietet Navigation für Ihre persönliche app.|
|1 |**iframe**: zeigt den App-Inhalt an.|

### <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Microsoft Teams-Benutzeroberflächenvorlagen, um die Gestaltung Ihrer persönlichen Registerkarte zu unterstützen:

* [List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.
* [Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): ein Aufgaben Gremium, das manchmal als Kanban-Board oder als Swim Lanes bezeichnet wird, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitsaufgaben oder Tickets verwendet werden.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): ein Dashboard ist eine Leinwand mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.
* [Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.
* [Linker NAV](../../concepts/design/design-teams-app-ui-templates.md#left-nav): die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-a-personal-app-bot"></a>Verwenden einer persönlichen app (bot)

Persönliche Apps können einen bot für Einzelgespräche und private Benachrichtigungen umfassen (beispielsweise, wenn ein Kollege einen Kommentar auf Ihrer Zeichenfläche veröffentlicht). Der Bot ist auf einer von Ihnen angegebenen Registerkarte verfügbar.

### <a name="anatomy-personal-app-bot"></a>Anatomie: persönliche app (bot)

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie des persönlichen bot-Komponenten." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Bot-Registerkarte**: Fügen Sie beispielsweise eine Registerkarte **Chat** hinzu, um auf bot-Unterhaltungen und-Benachrichtigungen zuzugreifen.|
|B|**Bot-Nachricht**: Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (beispielsweise eine Adaptive Karte).|
|C|**Feld "Verfassen"**: Eingabefeld zum Senden von Nachrichten an den bot.|

## <a name="best-practices"></a>Bewährte Methoden

### <a name="tab-priority"></a>Tab-Priorität

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte

Bei angepasster Größenanpassung können Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Nicht: Lead mit sekundärem Inhalt oder Metadaten

Wie bei einer standardmäßigen Webanwendung sollte die Tab-Navigation in einer Reihenfolge fortgeschritten sein, die den Sinn der primären Features Ihrer APP erleichtert.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="tab-hierarchy"></a>Tab-Hierarchie

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Do: Registerkarten sollten der gleichen Hierarchie entsprechen und wichtige App-Seiten darstellen

Ihre Registerkarten sollten die primären Features und Inhalte Ihrer APP kategorisieren. Durch die reaktionsschnelle Größenanpassung können Inhalte auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Nicht: unterschiedliche Hierarchieebenen einbeziehen

Ihre Inhalte sollten in einer logischen Reihenfolge weiterentwickelt werden, die es Benutzern ermöglicht, diese zu verstehen. Wenn Sie zwei Registerkarten haben, die eng miteinander verbunden sind, sollten Sie diese in einer Registerkarte kombinieren.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="first-run-experience"></a>Erste Ausführung

#### <a name="do-include-a-first-run-experience"></a>Do: Einschließen einer ersten Ausführung

Es sollte mindestens einen Willkommensbildschirm geben, wenn Sie das erste Mal eine persönliche App verwenden. Beschreiben Sie für Bots, was Ihr bot tun kann, und geben Sie schnell Aktionen an, beispielsweise eine Anmeldeschaltfläche.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a>Nicht: mit einem leeren Bildschirm beginnen

Benutzer können verwechselt werden, wenn nichts angezeigt wird, wenn Sie Ihre APP zum ersten Mal ausführen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="personalized-content"></a>Personalisierter Inhalt

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Do: aggregierter App-Inhalt, der für einen Benutzer relevant ist

Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen bot handelt, werden Inhalte angezeigt, die sich nur auf die Aktivität eines Benutzers in Ihrer APP beziehen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Nicht: Anzeigen von nicht verwandten oder übermäßig großen Inhalten

Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu denen ein Benutzer nicht gehört. Der persönliche bot-Inhalt sollte sich auf das Individuum konzentrieren – nicht auf eine Gruppe.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="complex-app-features"></a>Komplexe App-Features

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Do: Benutzern den Zugriff auf komplexe Features in einem Browser ermöglichen

Ihre APP sollte sich auf Kernaufgaben in Microsoft Teams konzentrieren, aber Sie können die vollständige eigenständige app in einem Browser anzeigen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-include-your-entire-app"></a>Nicht: einschließen der gesamten App

Wenn Sie Ihre APP nicht speziell für Teams erstellt haben, haben Sie wahrscheinlich Features, die in einem Tool für die Zusammenarbeit keinen Sinn ergeben.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

## <a name="manage-a-personal-tab"></a>Verwalten einer persönlichen Registerkarte

Auf der linken Seite der Teams können Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen zu fixieren, zu entfernen und zu konfigurieren.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen app." border="false":::

## <a name="learn-more"></a>Mehr erfahren

Diese anderen Entwurfsrichtlinien können abhängig vom Umfang ihrer persönlichen App hilfreich sein:

* [Entwerfen der Registerkarte](../../tabs/design/tabs.md)
* [Entwerfen von Ihnen bot](../../bots/design/bots.md)

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
