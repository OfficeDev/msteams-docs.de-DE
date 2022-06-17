---
title: App-Entwurfsprozess
author: heath-hamilton
description: Erfahren Sie, wie und wann Sie Microsoft-Tools und -Ressourcen verwenden können, um eine effektive Microsoft Teams-App zu entwerfen.
ms.localizationpriority: mediums
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 97ff20e0ffc6cc802c2226cc7767873cd3a25416
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144376"
---
# <a name="design-process-for-microsoft-teams-apps"></a>Entwurfsprozess für Microsoft Teams-Apps

Es gibt mehrere Tools und Ressourcen zum Entwerfen Ihrer Microsoft Teams-App. In den folgenden Schritten wird beschrieben, wann und wie Sie diese während des Entwurfsprozesses verwenden können. (Einige Schritte zählen technisch gesehen möglicherweise nicht zum Entwurfsprozess, werden jedoch als zusätzlicher Kontext aufgeführt.)

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagramm mit einem Beispiel für den Teams-App-Entwurfsprozess" border="false":::

## <a name="plan-your-app"></a>Planen Ihrer App

Beim Entwerfen einer qualitativ hochwertigen Microsoft Teams-App müssen Sie sich darüber klar sein, welche Aufgaben die App erfüllen soll und wie die Benutzer sie voraussichtlich nutzen werden. Bevor Sie mit dem Entwurf beginnen, beantworten Sie die folgenden Fragen:

* Wer sind Ihre Benutzer?
* Was ist deren Problem?
* Wie kann Ihre App das Problem lösen?
* Wie oft wird Ihre App verwendet?
* Wie viele Personen verwenden Ihre App?
* Welche Art von Rendite kann Ihre App bieten?

Weitere Informationen finden Sie unter [Grundlegendes zu den Anwendungsfällen Ihrer App](~/concepts/design/understand-use-cases.md) und [Zuordnen von Anwendungsfällen zu Teams](~/concepts/design/map-use-cases.md).

## <a name="get-teams-design-tools"></a>Abrufen von Teams-Entwurfstools

Microsoft stellt Tools bereit, die das Entwerfen einer Teams-App erleichtern. Es wird dringend empfohlen, zumindest das Microsoft Teams-UI-Kit zu verwenden.

### <a name="get-the-microsoft-teams-ui-kit"></a>Holen Sie sich das Microsoft Teams-UI-Kit

Das Microsoft Teams-UI-Kit kann Ihnen dabei helfen, innerhalb kürzester Zeit eine effektive Teams-App zu entwickeln. Das UI-Kit enthält alles, was Sie in diesen Dokumenten bezüglich des Teams-App-Designs sehen und weitere Informationen, einschließlich umfangreicher Beispiele und Variationen.

Das UI-Kit verfügt auch über vordefinierte Vorlagen und Komponenten, die Sie nach Bedarf kopieren und ändern können, sodass Sie mehr Zeit mit dem Entwurf der besten Benutzeroberfläche verbringen können, anstatt sich Gedanken darüber zu machen, wie eine Schaltfläche aussehen soll.

> [!TIP]
> **Ist das UI-Kit für mich geeignet?** Ja, wenn Sie auf irgendeine Weise an der Erstellung einer Teams-Apps beteiligt sind. Zu verstehen, wie man eine Teams-App erstellt, ist nicht nur für Designer, sondern auch für Produktmanager, Entwickler, die IDEs verwenden, und Entwickler, die mit Tools mit wenig Code (z. B. Microsoft Power Platform) arbeiten, hilfreich.

1. Besuchen Sie die [Microsoft Teams-UI-Kit-Figma-Website](https://www.figma.com/community/file/916836509871353159).
1. Wählen Sie **Duplizieren** aus, um das UI-Kit zu öffnen. (Möglicherweise müssen Sie zuerst ein Figma-Konto erstellen.)

### <a name="try-the-sample-app"></a>Testen der Beispiel-App

Sie können eine Beispiel-App hochladen, um zu erfahren, wie Apps im Teams-Client aussehen und sich verhalten sollen.

> [!div class="nextstepaction"]
> [Abrufen der Beispiel-App (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a>Teams-Entwurfssystem kennenlernen

Informieren Sie sich ausführlich über die [Grundlagen des Teams-App-Designs](design-teams-app-fundamentals.md), einschließlich Layout, Farbschemas und mehr, oder machen Sie sich zumindest damit vertraut.

## <a name="choose-app-capabilities"></a>Auswählen von App-Funktionen

Nach der Planungsphase können Sie bestimmen, welche Teams-Funktionen zu den Anwendungsfällen Ihrer App passen. Wenn Sie beispielsweise Personen proaktiv benachrichtigen möchten, stellt möglicherweise ein Bot die richtige Funktion dar.

Das UI-Kit verfügt über vordefinierte Designs, die Ihnen zeigen, wie Benutzer in der Regel jede Funktion hinzufügen, einrichten, verwenden und verwalten. Diese Informationen finden Sie auch in diesen Dokumenten, aber mit dem UI-Kit können Sie jedes dieser Designs kopieren und in das App-Design einfügen.

1. Wechseln Sie im linken Navigationsbereich des UI-Kits zu den **App-Funktionen**, und wählen Sie die gewünschte Funktion für Ihre App aus.
1. Kopieren Sie die benötigten Elemente von dieser Seite, um Ihre App zu entwerfen.<br />
   Wenn Ihre App z. B. die Authentifizierung mit einmaligem Anmelden unterstützt, kopieren Sie das Design und fügen Sie es ein, um genau dieses Szenario abzuwickeln.

## <a name="design-your-ux-flow"></a>Entwerfen des UX-Flusses

Nachdem Sie über ein grundlegendes App-Design verfügen, können Sie es beliebig ändern und verfeinern, indem Sie Teams-UI-Vorlagen und grundlegende Komponenten aus dem UI-Kit kopieren.

### <a name="design-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Benutzeroberflächenvorlagen sind komplexe hochwertige Designs für allgemeine Teams-Anwendungsfälle und -Workflows. Anstatt von Null mit grundlegenden Komponenten zu beginnen, empfehlen wir Ihnen, diese Vorlagen zu verwenden, um den Entwurfsprozess zu vereinfachen und zu beschleunigen.

1. Wechseln Sie im linken Navigationsbereich des UI-Kits zu **UI-Vorlagen**.
1. Kopieren Sie Vorlagen, die für Ihr App-Design sinnvoll sind.<br />
   Wenn Sie z. B. eine persönliche App entwerfen, können Sie eine Dashboardvorlage verwenden.

### <a name="design-with-basic-ui-components"></a>Entwurf mit einfachen UI-Komponenten

Basierend auf der Fluent-Benutzeroberfläche sind dies die Kernelemente zum Erstellen vertrauter Teams-Schnittstellen. Verwenden Sie diese Komponenten, wenn einer Benutzeroberflächenvorlage etwas fehlt, das Sie benötigen, oder wenn Sie Ihre App ganz neu entwerfen möchten.

1. Wechseln Sie im linken Navigationsbereich des UI-Kits zu **Grundlegende Benutzeroberflächenkomponenten**.
1. Kopieren Sie die Komponenten, die Sie für Ihr App-Design benötigen (z. B. eine Schaltfläche oder einen Umschalter).

## <a name="implement-your-design"></a>Implementieren Ihres Designs

Das Design ist fertig, und Sie sind bereit, mit dem Erstellen zu beginnen. Mit den folgenden Tools können Sie die Front-End-Entwicklung Ihrer App vereinfachen.

### <a name="build-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Wenn Sie Benutzeroberflächenvorlagen in Ihrem Entwurf verwendet haben, können Sie diese Vorlagen mit der Microsoft Teams-UI-Bibliothek (einer React-Komponentenbibliothek basierend auf der Fluent-UI) implementieren.

Derzeit sind nicht alle im UI-Kit aufgeführten Vorlagen in der Bibliothek verfügbar.

> [!div class="nextstepaction"]
> [Abrufen der Bibliothek (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a>Erstellen mit grundlegenden UI-Komponenten

Ähnlich wie in der Entwurfsphase können Sie diese Fluent-UI-Komponenten in Ihrem App-Projekt verwenden, wenn einer UI-Vorlage etwas fehlt, das Sie benötigen, oder Sie die App einfach ganz neu erstellen möchten. 

(Hinweis: Wenn Sie feststellen, dass etwas fehlt oder Sie eine Idee für eine Vorlage haben, sollten Sie einen Beitrag zum Teams Benutzeroberflächenbibliothek-Repository hinzufügen.)

> [!div class="nextstepaction"]
> [Abrufen der Bibliothek (Fluent-Benutzeroberfläche)](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a>Überprüfen von Entwurfsressourcen

Unabhängig davon, ob Sie gerade erst mit Ihrer App beginnen oder die App fast produktionsbereiten ist, empfehlen wir Ihnen, die folgenden Ressourcen regelmäßig zu überprüfen:

* **Validierungsrichtlinien für den Microsoft Teams-Store**: Stellt Standards bereit, die von allen Teams-Apps und nicht nur von Apps, die im Store aufgeführt sind, angestrebt werden sollten. Weitere Informationen hierzu finden Sie in den [Richtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).
* **Bewährte Methoden für das Design**: Diese Dokumente und das UI-Kit bieten bewährte Methoden zum Entwerfen qualitativ hochwertiger Apps. Sehen Sie sich beispielsweise die [bewährten Methoden für das Entwerfen von Bots an](~/bots/design/bots.md#best-practices).

## <a name="see-also"></a>Siehe auch

[Entwerfen von Aktivitätsfeed-Benachrichtigungen](~/concepts/design/activity-feed-notifications.md)
