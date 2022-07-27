---
title: Aufgabenmodule
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie modale Popupoberflächen hinzufügen, um Informationen aus Ihren Microsoft Teams-Apps für Ihre Benutzer zu sammeln oder anzuzeigen.
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 23d6a0f1645fefe66544c755ddb617eba9ea8f3e
ms.sourcegitcommit: 1cda2fd3498a76c09e31ed7fd88175414ad428f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2022
ms.locfileid: "67035296"
---
# <a name="task-modules"></a>Aufgabenmodule

Mit Aufgabenmodulen können Sie modale Pop-up-Erlebnisse in Ihrer Teams-Anwendung erstellen. Im Popup haben Sie folgende Möglichkeiten:

* Führen Sie Ihren eigenen benutzerdefinierten HTML- oder JavaScript-Code aus.
* Zeigen Sie ein webbasiertes `<iframe>`Widget an, z. B. ein YouTube- oder Microsoft Stream-Video.
* Zeigt eine [adaptive Karte an](/adaptive-cards/).

Aufgabenmodule eignen sich zum Initiieren und Abschließen von Aufgaben oder zum Anzeigen umfangreicher Informationen, z. B. Videos oder Power Business Intelligence (BI)-Dashboards. Eine Popup-Erfahrung ist für Benutzer, die Aufgaben initiieren und ausführen, im Vergleich zu einer Registerkarte oder einer unterhaltungsbasierten Bot-Erfahrung oft natürlicher.

Aufgabenmodule bauen auf der Grundlage von Microsoft Teams-Registerkarten auf. Sie sind im Wesentlichen eine Registerkarte in einem Popupfenster. Sie verwenden dasselbe SDK. Wenn Sie also eine Registerkarte erstellt haben, sind Sie bereits mit dem Erstellen eines Aufgabenmoduls vertraut.

Aufgabenmodule können auf drei Arten aufgerufen werden:

* Kanal- oder persönliche Registerkarten: Mithilfe des Microsoft Teams Tabs SDK können Sie Aufgabenmodule über Schaltflächen, Links oder Menüs auf Ihrer Registerkarte aufrufen. Weitere Informationen finden Sie [unter Verwenden von Aufgabenmodulen auf Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md).
* Bots: Verwenden von Schaltflächen auf [Karten](~/task-modules-and-cards/cards/cards-reference.md) , die von Ihrem Bot gesendet wurden. Dies ist nützlich, wenn Sie nicht verlangen, dass jeder in einem Kanal sehen kann, was Sie mit einem Bot tun. Wenn Benutzer beispielsweise auf eine Umfrage in einem Kanal antworten, ist es nicht hilfreich, einen Datensatz dieser Umfrage anzuzeigen, der erstellt wird. Weitere Informationen finden Sie [unter Verwenden von Aufgabenmodulen aus Teams-Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md).
* Außerhalb von Teams über einen Deep-Link: Sie können auch URLs erstellen, um ein Aufgabenmodul von überall aus aufzurufen. Weitere Informationen finden Sie in der [Deep Link-Syntax des Aufgabenmoduls](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax).

## <a name="components-of-a-task-module"></a>Komponenten eines Aufgabenmoduls

So sieht ein Aufgabenmodul aus, wenn es von einem Bot aufgerufen wird:

:::image type="content" source="../assets/images/task-module/task-module-example.png" alt-text="Beispiel für ein Aufgabenmodul":::

Ein Aufgabenmodul enthält Folgendes, wie in der vorherigen Abbildung gezeigt:

1. Das Symbol Ihrer App[`color`](~/resources/schema/manifest-schema.md#icons).
2. Der Name Ihrer App[`short`](~/resources/schema/manifest-schema.md#name).
3. Der Titel des Aufgabenmoduls, der in der `title` Eigenschaft des [TaskInfo-Objekts](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) angegeben ist.
4. Die Schaltfläche zum Schließen oder Abbrechen des Aufgabenmoduls. Wenn der Benutzer diese Schaltfläche auswählt, erhält Ihre App ein `err` Ereignis. Weitere Informationen finden Sie im [Beispiel zum Übermitteln des Ergebnisses eines Aufgabenmoduls](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module).

    > [!NOTE]
    > Es ist derzeit nicht möglich, das `err` Ereignis zu erkennen, wenn ein Aufgabenmodul von einem Bot aufgerufen wird.

5. Im blauen Rechteck wird Ihre Webseite angezeigt, wenn Sie ihre eigene Webseite mithilfe der `url` Eigenschaft des [TaskInfo-Objekts](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) laden. Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-sizing).
6. Wenn Sie eine adaptive Karte mithilfe der `card` Eigenschaft des [TaskInfo-Objekts](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) anzeigen, wird der Abstand für Sie hinzugefügt. Weitere Informationen finden Sie unter [Aufgabenmodul-CSS für HTML- oder JavaScript-Aufgabenmodule](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-css-for-html-or-javascript-task-modules).
7. Schaltflächen für adaptive Karten werden gerendert, nachdem Sie **"Registrieren"** ausgewählt haben. Wenn Sie Ihre eigene Seite verwenden, erstellen Sie Ihre eigenen Schaltflächen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aufrufen und Schließen von Aufgabenmodulen](~/task-modules-and-cards/task-modules/invoking-task-modules.md)

## <a name="see-also"></a>Siehe auch

[Karten](~/task-modules-and-cards/what-are-cards.md)
