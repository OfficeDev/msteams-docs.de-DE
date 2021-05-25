---
title: App-Entwurfsprozess
author: heath-hamilton
description: Erhalten Sie eine allgemeine Vorstellung davon, wie und wann Sie Microsoft-Tools und -Ressourcen verwenden können, um eine effektive Microsoft Teams entwerfen.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 533d386db2aa784fc7de955f92f64d07789f0553
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631307"
---
# <a name="design-process-for-microsoft-teams-apps"></a>Entwurfsprozess für Microsoft Teams Apps

Es gibt mehrere Tools und Ressourcen zum Entwerfen Ihrer Microsoft Teams App. In den folgenden Schritten wird beschrieben, wann und wie Sie diese während des Entwurfs verwenden können. (Einige der Schritte können technisch außerhalb des Entwurfsprozesses liegen, sind jedoch für zusätzlichen Kontext enthalten.)

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagramm, das ein Beispiel für den Teams-App-Entwurfsprozesses zeigt." border="false":::

## <a name="plan-your-app"></a>Planen Ihrer App

Das Entwerfen einer qualitativ hochwertigen Teams erfordert, dass Sie verstehen, was die App tun soll und wie Sie denken, dass die App von den Personen verwendet wird. Bevor Sie mit dem Entwerfen beginnen, beantworten Sie jedoch die folgenden Fragen:

* Wer sind Ihre Benutzer?
* Was ist ihr Problem?
* Wie kann Ihre App ihr Problem lösen?
* Wie oft wird Ihre App verwendet?
* Wie viele Personen verwenden Ihre App?
* Welche Art von Rendite kann Ihre App bieten?

Weitere Informationen finden Sie unter [Verstehen der Anwendungsfälle](~/concepts/design/understand-use-cases.md) Ihrer App und [Zuordnung](~/concepts/design/map-use-cases.md)von Anwendungsfällen zu Teams .

## <a name="get-teams-design-tools"></a>Get Teams design tools

Microsoft stellt Tools bereit, mit deren Unterstützung Das Entwerfen Ihrer Teams erleichtert wird. Es wird dringend empfohlen, das Microsoft Teams UI Kit zu verwenden.

### <a name="get-the-microsoft-teams-ui-kit"></a>Get the Microsoft Teams UI Kit

Das Microsoft Teams UI Kit hilft Ihnen, eine effektive Teams app in kürzester Zeit zu entwickeln. Das Benutzeroberflächenkit enthält alles, was sie in diesen Dokumenten im Zusammenhang mit Teams App-Design und vielem mehr sehen, einschließlich umfangreicher Beispiele und Variationen.

Das Benutzeroberflächenkit verfügt auch über vordefinierte Vorlagen und Komponenten, die Sie nach Bedarf kopieren und ändern können, sodass Sie mehr Zeit mit dem Entwerfen der besten Benutzeroberfläche verbringen können, anstatt sich Gedanken darüber zu machen, wie eine Schaltfläche aussehen soll.

> [!TIP]
> **Ist das Benutzeroberflächenkit für mich?** Wenn Sie eine Rolle beim Erstellen einer Teams haben, ja. Das Erstellen einer Teams-App ist nicht nur designern, sondern auch Produktmanagern, Entwicklern, die IDEs verwenden, und Entwicklern, die mit Low-Code-Tools (z. B. der Microsoft Power Platform) erstellen, hilfreich.

1. Wechseln Sie zur [seite Microsoft Teams UI Kit Figma](https://www.figma.com/community/file/916836509871353159).
1. Wählen **Sie Duplizieren** aus, um das Ui Kit zu öffnen. (Möglicherweise müssen Sie zuerst ein Feigenma-Konto erstellen.)

### <a name="try-the-sample-app"></a>Testen der Beispiel-App

Sie können eine Beispiel-App hochladen, um zu sehen, wie Apps im Client aussehen und sich Teams verhalten sollen.

> [!div class="nextstepaction"]
> [Die Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a>Informationen Teams Entwurfssystem

Erfahren Sie mehr über die Grundlagen des Teams, einschließlich Layout, Farbschemas und [vielem](design-teams-app-fundamentals.md)mehr, oder machen Sie sich zumindest mit den Grundlagen des App-Designs vertraut.

## <a name="choose-app-capabilities"></a>Auswählen von App-Funktionen

Nach der Planungsphase können Sie bestimmen, welche Teams den Anwendungsfällen Ihrer App passen. Wenn Sie z. B. Personen proaktiv benachrichtigen möchten, ist möglicherweise ein Bot die richtige Funktion.

Das Benutzeroberflächenkit verfügt über vordefinierte Designs, die Ihnen zeigen, wie Benutzer in der Regel jede Funktion hinzufügen, einrichten, verwenden und verwalten. Kurzübersicht: Diese Informationen finden Sie auch in diesen Dokumenten. Mit dem UI Kit können Sie jedoch alle diese Designs kopieren und in das Design Ihrer App einfügen.

1. Wechseln Sie im linken Navigationselement  des Benutzeroberflächenkits zu App-Funktionen, und wählen Sie die funktion aus, die Sie für Ihre App wünschen.
1. Kopieren Sie die benötigten Informationen von dieser Seite, um Ihre App zu entwerfen.<br />
   Wenn Ihre App beispielsweise die Authentifizierung mit einmaligem Anmelden unterstützt, kopieren Und fügen Sie den Entwurf für die Verarbeitung dieses genauen Szenarios ein.

## <a name="design-your-ux-flow"></a>Entwerfen des UX-Fluss

Sobald Sie über ein einfaches App-Design verfügen, können Sie es so weit wie möglich (und schnell) ändern und verfeinern, indem Sie Teams Benutzeroberflächenvorlagen und grundlegende Komponenten aus dem UI Kit kopieren.

### <a name="design-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Ui templates are complex, high-fidelity designs for common Teams use cases and workflows. Anstatt von unten nach oben mit grundlegenden Komponenten zu beginnen, empfehlen wir, diese Vorlagen zu verwenden, um den Entwurfsprozess zu vereinfachen und zu beschleunigen.

1. Wechseln Sie im linken Navigationselement des Benutzeroberflächenkits zu **UI-Vorlagen**.
1. Kopieren Sie Vorlagen, die für Ihr App-Design sinnvoll sind.<br />
   Wenn Sie beispielsweise eine persönliche App entwerfen, sollten Sie eine Dashboardvorlage verwenden.

### <a name="design-with-basic-ui-components"></a>Entwurf mit einfachen Benutzeroberflächenkomponenten

Basierend auf der Fluent-Benutzeroberfläche sind dies die Kernelemente zum Erstellen vertrauter Teams Schnittstellen. Verwenden Sie diese Komponenten, wenn einer Benutzeroberflächenvorlage etwas fehlt, das Sie benötigen, oder Wenn Sie Ihre App einfach neu entwerfen möchten.

1. Wechseln Sie im linken Navigationselement des Benutzeroberflächenkits zu **Grundlegende Benutzeroberflächenkomponenten**.
1. Kopieren Sie die Komponenten, die Sie für Ihr App-Design benötigen (z. B. eine Schaltfläche oder umschalten).

## <a name="implement-your-design"></a>Implementieren Des Entwurfs

Das Design ist fertig, und Sie können mit dem Erstellen beginnen. Die folgenden Tools können die Front-End-Entwicklung Ihrer App vereinfachen.

### <a name="build-with-ui-templates"></a>Erstellen mit Benutzeroberflächenvorlagen

Wenn Sie benutzeroberflächenvorlagen in Ihrem Entwurf verwendet haben, können Sie diese Vorlagen mit der Microsoft Teams-Benutzeroberflächenbibliothek (eine React-Komponentenbibliothek basierend auf der Fluent-Benutzeroberfläche) implementieren.

Derzeit sind nicht alle im UI Kit aufgeführten Vorlagen in der Bibliothek verfügbar.

> [!div class="nextstepaction"]
> [Bibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a>Erstellen mit grundlegenden Benutzeroberflächenkomponenten

Im Gegensatz zur Entwurfsphase können Sie diese Fluent-UI-Komponenten in Ihrem App-Projekt verwenden, wenn eine Benutzeroberflächenvorlage fehlt oder Sie die App einfach von Grund auf neu erstellen möchten. 

(Hinweis: Wenn Sie bemerken, dass etwas fehlt oder sie eine Idee für eine Vorlage haben, sollten Sie einen Beitrag zum Repository Teams Ui Library leisten.)

> [!div class="nextstepaction"]
> [Bibliothek erhalten (Fluent UI)](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a>Überprüfen von Entwurfsressourcen

Unabhängig davon, ob Sie gerade mit Ihrer App beginnen oder in der Nähe einer produktionsbereiten App sind, wird empfohlen, die folgenden Ressourcen regelmäßig zu überprüfen:

* **Microsoft Teams Richtlinien für die** Storeüberprüfung: Stellt Standards zur Verfügung, die alle Teams apps anstreben sollten (nicht nur Apps, die im Store aufgeführt sind). Weitere Informationen finden Sie in den [Richtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).
* **Bewährte Entwurfsmethoden:** Diese Dokumente und das UI Kit bieten bewährte Methoden für das Entwerfen qualitativ hochwertiger Apps. Lesen Sie beispielsweise die [bewährten Methoden für das Entwerfen von Bots](~/bots/design/bots.md#best-practices).
