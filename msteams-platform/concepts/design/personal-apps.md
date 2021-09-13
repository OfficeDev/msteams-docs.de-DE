---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie eine Teams persönliche App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: ae75a79ebc6293b99e7e4db310cfb0545ce5037a
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156931"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Entwerfen Ihrer persönlichen App für Microsoft Teams

Eine persönliche App kann ein Bot, ein privater Arbeitsbereich oder beides sein. Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, in anderen Fällen bietet es dem Benutzer einen Blick auf alles, was ihnen liegt, wenn die App als Registerkarte in mehreren Kanälen konfiguriert wurde.

Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Personen persönliche Apps in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Im Microsoft Teams UI Kit finden Sie umfassende Designrichtlinien für persönliche Apps, einschließlich Elementen, die Sie nach Bedarf abrufen und ändern können. Das UI-Kit enthält auch wichtige Themen wie Barrierefreiheit und dynamische Größenanpassung, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Hinzufügen einer persönlichen App

Benutzer können eine persönliche App aus dem Teams Store oder dem App-Flyout hinzufügen, indem sie auf der linken Seite von Teams das Symbol **"Mehr"** auswählen (siehe das folgende Beispiel).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a>Verwenden einer persönlichen App (privater Arbeitsbereich)

Mit einem privaten Arbeitsbereich können Benutzer App-Inhalte, die für sie von Bedeutung sind, an einem zentralen Ort anzeigen, ohne Teams zu verlassen.

(Implementierungshinweis: Der private Arbeitsbereich basiert auf der [*persönlichen*](../../build-your-first-app/build-personal-tab.md) Registerkartenfunktion.)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomie: Persönliche App (privater Arbeitsbereich)

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Aufbaukomponente der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Zuordnung:** Ihr App-Name.|
|B|**Registerkarten:** Bietet Navigation für Ihre persönliche App.|
|C|**Mehr Menü:** Enthält zusätzliche App-Optionen und Informationen.|
|D|**Primäre Navigation:** Bietet Navigation zu Ihrer App, andere hauptfunktionen Teams.|

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarten:** Bietet Navigation für Ihre persönliche App.|
|1|**webview:** Zeigt Ihre App-Inhalte an.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Dieses Beispiel zeigt die Aufbaukomponente der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Zuordnung:** Ihr App-Logo und -Name.|
|B|**Registerkarten:** Bietet Navigation für Ihre persönliche App.|
|C|**Popupansicht:** Verschiebt Ihre App-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.|
|D|**Mehr Menü:** Enthält zusätzliche App-Optionen und Informationen. (Alternativ können Sie **Einstellungen** eine Registerkarte erstellen.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Dieses Beispiel zeigt die strukturelle Anatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarten:** Bietet Navigation für Ihre persönliche App.|
|1|**iframe:** Zeigt Ihre App-Inhalte an.|

### <a name="design-with-ui-templates-and-advanced-components"></a>Design mit Benutzeroberflächenvorlagen und erweiterten Komponenten

Verwenden Sie eine der folgenden Teams Vorlagen und Komponenten, um Ihre persönliche Registerkarte zu entwerfen:

* [Liste:](../../concepts/design/design-teams-app-ui-templates.md#list)Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Task Board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als "Tickets Board" oder "Sperre" bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen.
* [Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist eine Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Zustand:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.
* [Linke Navigation:](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Die linke Navigationskomponente kann hilfreich sein, wenn Ihre persönliche App eine Navigation erfordert. Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.

## <a name="use-a-personal-app-bot"></a>Verwenden einer persönlichen App (Bot)

Persönliche Apps können einen Bot für 1:1-Unterhaltungen und private Benachrichtigungen enthalten (z. B. wenn ein Kollege einen Kommentar auf dem Zeichenboard sendet). Benutzer interagieren mit dem Bot auf einer von Ihnen angegebenen Registerkarte.

### <a name="anatomy-personal-app-bot"></a>Anatomie: Persönliche App (Bot)

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Bot-Einstiegspunkt:** Einstiegspunkt für Benutzer, um auf das Bot-Feature in Ihrer persönlichen App zuzugreifen.|
|B|**Schaltfläche "Zurück":** Führt Benutzer zurück zum privaten Arbeitsbereich.|
|C|**Botnachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).|
|D|**Feld "Verfassen":** Eingabefeld zum Senden von Nachrichten an den Bot.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Bot-Registerkarte:** Fügen Sie beispielsweise eine **Chat-Registerkarte** ein, um auf Bot-Unterhaltungen und -Benachrichtigungen zuzugreifen.|
|B|**Botnachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).|
|C|**Feld "Verfassen":** Eingabefeld zum Senden von Nachrichten an den Bot.|

## <a name="manage-a-personal-tab"></a>Verwalten einer persönlichen Registerkarte

Auf der linken Seite von Teams können Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen zu anheften, zu entfernen und zu konfigurieren.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen App." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="tab-priority"></a>Registerkartenpriorität

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte

Bei einer dynamischen Größenanpassung werden Registerkarten auf der rechten Seite möglicherweise abgeschnitten oder nicht mehr angezeigt.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine persönliche App, die den relevantesten Inhalt auf der ersten Registerkarte anzeigt." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Don't: Lead with secondary content or metadata

Wie bei einer standardmäßigen Web-App sollte die Registerkartennavigation in einer Reihenfolge ausgeführt werden, die die wichtigsten Features Ihrer App sinnvoll macht.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel zeigt eine persönliche App, die mit sekundären Inhalten oder Metadaten führt." border="false":::

### <a name="tab-hierarchy"></a>Registerkartenhierarchie

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Do: Registerkarten sollten eine gleiche Hierarchie aufweisen und wichtige App-Seiten darstellen

Ihre Registerkarten sollten die wichtigsten Features und Inhalte Ihrer App kategorisieren. Bei einer dynamischen Größenanpassung werden Inhalte auf der rechten Seite möglicherweise abgeschnitten oder nicht mehr angezeigt.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt eine persönliche App mit Registerkarten gleicher Hierarchie." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Don't: Include different levels of hierarchy

Ihre Inhalte sollten in einer logischen Reihenfolge ausgeführt werden, die den Benutzern dabei hilft, sie zu verstehen. Wenn Sie zwei Registerkarten haben, die eng miteinander verbunden sind, sollten Sie diese in einer Registerkarte kombinieren.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine persönliche App mit unterschiedlichen Hierarchieebenen." border="false":::

### <a name="first-run-experience"></a>Erste Ausführung

#### <a name="do-include-a-first-run-experience"></a>Do: Einschließen einer Benutzeroberfläche für die erstausführung

Bei der ersten Verwendung einer persönlichen App sollte mindestens eine Willkommensseite vorhanden sein. Beschreiben Sie für Bots, was Ihr Bot tun kann, und stellen Sie schnelle Aktionen bereit, z. B. eine Anmeldeschaltfläche.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Das Beispiel zeigt, was bei der ersten Ausführung einer persönlichen App zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Ein weiteres Beispiel zeigt, was bei der ersten Ausführung einer persönlichen App zu tun ist." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a>Don't: Start with a blank screen

Benutzer sind möglicherweise verwirren, wenn beim ersten Ausführen Ihrer App nichts angezeigt wird.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Das Beispiel zeigt, was bei der ersten Ausführung einer persönlichen App nicht zu tun ist." border="false":::

### <a name="personalized-content"></a>Personalisierte Inhalte

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Do: Aggregieren von App-Inhalten, die für einen Benutzer relevant sind

Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen Bot handelt, zeigen Sie Inhalte an, die sich nur auf die Aktivitäten eines Benutzers in Ihrer App beziehen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Das Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Ein weiteres Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Don't: Show unrelated or overly broad content

Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu der ein Benutzer nicht gehört. Persönliche Bot-Inhalte sollten sich auf die Person konzentrieren, nicht auf eine Gruppe.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Das Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Ein weiteres Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

### <a name="complex-app-features"></a>Komplexe App-Features

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Do: Benutzern den Zugriff auf komplexe Features in einem Browser gestatten

Ihre App sollte sich auf kernaufgaben in Teams konzentrieren, Sie können jedoch weiterhin die vollständige eigenständige App in einem Browser anzeigen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt, wie komplexe App-Features mit einer persönlichen App behandelt werden." border="false":::

#### <a name="dont-include-your-entire-app"></a>Don't: Include your entire app

Wenn Sie Ihre App nicht speziell für Teams erstellt haben, verfügen Sie wahrscheinlich über Features, die in einem Tool für die Zusammenarbeit nicht sinnvoll sind.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Das Beispiel zeigt, wie komplexe App-Features nicht mit einer persönlichen App behandelt werden." border="false":::

## <a name="see-also"></a>Siehe auch

Diese anderen Entwurfsrichtlinien können je nach Umfang Ihrer persönlichen App hilfreich sein:

* [Entwerfen der Registerkarte](../../tabs/design/tabs.md)
* [Entwerfen eines Bots](../../bots/design/bots.md)
