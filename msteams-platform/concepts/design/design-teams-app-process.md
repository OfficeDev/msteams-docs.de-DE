---
title: App-Entwurfsprozess
author: heath-hamilton
description: Erhalten Sie eine allgemeine Vorstellung davon, wie und wann Sie Microsoft-Tools und -Ressourcen verwenden können, um eine effektive Microsoft Teams-App zu entwerfen.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 34401bf53196601b8836012fa4c96296510472a8
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156938"
---
# <a name="design-process-for-microsoft-teams-apps"></a>Entwurfsprozess für Microsoft Teams-Apps

Es gibt mehrere Tools und Ressourcen zum Entwerfen Ihrer Microsoft Teams-App. In den folgenden Schritten wird beschrieben, wann und wie Sie diese während des Entwurfsprozesses verwenden können. (Einige Schritte befinden sich möglicherweise außerhalb des Entwurfsprozesses, sind aber für zusätzlichen Kontext enthalten.)

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagramm mit einem Beispiel für den Teams App-Entwurfsprozess." border="false":::

## <a name="plan-your-app"></a>Planen Ihrer App

Für das Entwerfen einer qualitativ hochwertigen Teams App müssen Sie wissen, was die App tun soll und wie Sie davon aus gehen, dass Benutzer sie verwenden. Bevor Sie mit dem Entwerfen beginnen, beantworten Sie jedoch die folgenden Fragen:

* Wer sind Ihre Benutzer?
* Was ist ihr Problem?
* Wie kann Ihre App ihr Problem lösen?
* Wie oft wird Ihre App verwendet?
* Wie viele Personen verwenden Ihre App?
* Welche Art von Rendite kann Ihre App bereitstellen?

Weitere Informationen finden Sie unter [Verstehen der Anwendungsfälle Ihrer App](~/concepts/design/understand-use-cases.md) und [Zuordnen von Anwendungsfällen zu Teams.](~/concepts/design/map-use-cases.md)

## <a name="get-teams-design-tools"></a>Abrufen von Teams-Designtools

Microsoft stellt Tools bereit, die das Entwerfen Ihrer Teams-App vereinfachen. Es wird dringend empfohlen, mindestens das Microsoft Teams UI Kit zu verwenden.

### <a name="get-the-microsoft-teams-ui-kit"></a>Abrufen des Microsoft Teams UI Kit

Das Microsoft Teams UI Kit kann Ihnen dabei helfen, in kürzester Zeit eine effektive Teams App zu entwickeln. Das UI-Kit enthält alles, was Sie in diesen Dokumenten im Zusammenhang mit Teams App-Design und vieles mehr sehen, einschließlich umfangreicher Beispiele und Variationen.

Das UI-Kit verfügt auch über vordefinierte Vorlagen und Komponenten, die Sie bei Bedarf kopieren und ändern können, sodass Sie mehr Zeit mit dem Entwerfen der besten Benutzererfahrung verbringen können, anstatt sich Gedanken darüber zu machen, wie eine Schaltfläche aussehen sollte.

> [!TIP]
> **Ist das UI-Kit für mich geeignet?** Wenn Sie an der Erstellung einer Teams App beteiligt sind, ja. Das Erstellen einer Teams-App ist nicht nur für Designer hilfreich, sondern auch für Produktmanager, Entwickler, die IDEs verwenden, und Entwickler, die mit Tools mit wenig Code (z. B. microsoft Power Platform) erstellen.

1. Wechseln Sie zur [Seite Microsoft Teams UI Kit -Kits.](https://www.figma.com/community/file/916836509871353159)
1. Wählen Sie **"Duplizieren"** aus, um das UI-Kit zu öffnen. (Möglicherweise müssen Sie zuerst ein Numma-Konto erstellen.)

### <a name="try-the-sample-app"></a>Probieren Sie die Beispiel-App aus

Sie können eine Beispiel-App hochladen, um zu sehen, wie Apps im Teams Client aussehen und sich verhalten sollen.

> [!div class="nextstepaction"]
> [Abrufen der Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a>Lernen Sie Teams Entwurfssystem kennen

Informieren Sie sich ausführlich über die [Grundlagen Teams App-Designs,](design-teams-app-fundamentals.md)einschließlich Layout, Farbschemas und mehr, oder machen Sie sich mit ihnen vertraut.

## <a name="choose-app-capabilities"></a>Auswählen von App-Funktionen

Nach der Planungsphase können Sie ermitteln, welche Teams Funktionen zu den Anwendungsfällen Ihrer App passen. Wenn Sie z. B. proaktiv Personen benachrichtigen möchten, ist ein Bot möglicherweise die richtige Funktion.

Das UI-Kit verfügt über vordefinierte Designs, die ihnen zeigen, wie Benutzer in der Regel jede Funktion hinzufügen, einrichten, verwenden und verwalten. Als Kurzübersicht finden Sie diese Informationen auch in diesen Dokumenten, aber mit dem UI-Kit können Sie eines dieser Designs kopieren und in das Design Ihrer App einfügen.

1. Wechseln Sie im linken Navigationsbereich des UI-Kits zu den **App-Funktionen,** und wählen Sie die gewünschte Funktion für Ihre App aus.
1. Kopieren Sie das, was Sie von dieser Seite benötigen, um Ihre App zu entwerfen.<br />
   Wenn Ihre App beispielsweise die Authentifizierung mit einmaligem Anmelden unterstützt, kopieren Sie das Design, und fügen Sie es ein, um dieses genaue Szenario zu behandeln.

## <a name="design-your-ux-flow"></a>Entwerfen des UX-Flusses

Sobald Sie über ein einfaches App-Design verfügen, können Sie es beliebig ändern und verfeinern, indem Sie Teams UI-Vorlagen und grundlegende Komponenten aus dem UI-Kit kopieren.

### <a name="design-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Benutzeroberflächenvorlagen sind komplexe, präzise Designs für gängige Teams Anwendungsfälle und Workflows. Anstatt von unten nach oben mit grundlegenden Komponenten zu beginnen, empfehlen wir, diese Vorlagen zu verwenden, um den Entwurfsprozess zu vereinfachen und zu beschleunigen.

1. Wechseln Sie im linken Navigationsbereich des UI-Kits zu **UI-Vorlagen.**
1. Kopieren Sie Vorlagen, die für Ihr App-Design sinnvoll sind.<br />
   Wenn Sie beispielsweise eine persönliche App entwerfen, sollten Sie eine Dashboardvorlage verwenden.

### <a name="design-with-basic-ui-components"></a>Design mit einfachen UI-Komponenten

Basierend auf Fluent Ui sind dies die Kernelemente zum Erstellen vertrauter Teams Schnittstellen. Verwenden Sie diese Komponenten, wenn eine UI-Vorlage etwas fehlt, das Sie benötigen, oder Sie Ihre App einfach von Grund auf neu entwerfen möchten.

1. Wechseln Sie im linken Navigationsbereich des UI-Kits zu **grundlegenden UI-Komponenten.**
1. Kopieren Sie die Komponenten, die Sie für Ihr App-Design benötigen (z. B. eine Schaltfläche oder einen Umschalter).

## <a name="implement-your-design"></a>Implementieren Ihres Designs

Das Design ist fertig, und Sie können mit dem Erstellen beginnen. Die folgenden Tools können ihnen helfen, die Front-End-Entwicklung Ihrer App zu vereinfachen.

### <a name="build-with-ui-templates"></a>Erstellen mit Benutzeroberflächenvorlagen

Wenn Sie benutzeroberflächenvorlagen in Ihrem Entwurf verwendet haben, können Sie diese Vorlagen mit der Microsoft Teams BENUTZERoberflächenbibliothek (einer React-Komponentenbibliothek basierend auf Fluent Benutzeroberfläche) implementieren.

Derzeit sind nicht alle im UI-Kit aufgeführten Vorlagen in der Bibliothek verfügbar.

> [!div class="nextstepaction"]
> [Abrufen der Bibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a>Erstellen mit einfachen UI-Komponenten

Nicht anders als in der Entwurfsphase können Sie diese Fluent UI-Komponenten in Ihrem App-Projekt verwenden, wenn eine Benutzeroberflächenvorlage etwas fehlt, das Sie benötigen, oder Sie die App einfach von Grund auf neu erstellen möchten. 

(Hinweis: Wenn Sie etwas fehlendes bemerken oder eine Idee für eine Vorlage haben, sollten Sie einen Beitrag zum Repository der Teams UI-Bibliothek leisten.)

> [!div class="nextstepaction"]
> [Abrufen der Bibliothek (Fluent Benutzeroberfläche)](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a>Überprüfen von Designressourcen

Unabhängig davon, ob Sie gerade mit Ihrer App beginnen oder sich in der Nähe einer produktionsbereiten App befinden, empfehlen wir Ihnen, die folgenden Ressourcen regelmäßig zu überprüfen:

* Microsoft Teams Richtlinien für die **Store-Validierung:** Bietet Standards, nach denen alle Teams Apps suchen sollten, und nicht nur apps, die im Store aufgeführt sind. Weitere Informationen finden Sie in den [Richtlinien.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)
* Bewährte Methoden für das **Entwerfen:** Diese Dokumente und das UI-Kit bieten bewährte Methoden für das Entwerfen von qualitativ hochwertigen Apps. Sehen Sie sich beispielsweise die bewährten Methoden für das [Entwerfen von Bots an.](~/bots/design/bots.md#best-practices)

