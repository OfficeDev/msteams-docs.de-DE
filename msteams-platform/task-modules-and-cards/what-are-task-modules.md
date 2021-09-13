---
title: Aufgabenmodule
author: surbhigupta
description: Hinzufügen modaler Popup-Oberflächen zum Sammeln oder Anzeigen von Informationen für Ihre Benutzer aus Ihren Microsoft Teams-Apps
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a82552f43456aa1ddee0b68f13a8c5435165ed64
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156751"
---
# <a name="task-modules"></a>Aufgabenmodule

Mit Aufgabenmodulen können Sie modale Popupfunktionen in Ihrer Teams-Anwendung erstellen. Im Popup können Sie Folgendes ausführen:

* Führen Sie Ihren eigenen benutzerdefinierten HTML- oder JavaScript-Code aus.
* Zeigen Sie ein `<iframe>` -basiertes Widget an, z. B. ein YouTube- oder Microsoft Stream-Video.
* Zeigt eine [adaptive Karte](/adaptive-cards/)an.

Aufgabenmodule eignen sich zum Initiieren und Abschließen von Aufgaben oder zum Anzeigen umfangreicher Informationen, z. B. Videos oder Power Business Intelligence (BI)-Dashboards. Eine Popupoberfläche ist für Benutzer, die Aufgaben initiieren und ausführen, im Vergleich zu einer Registerkarte oder einer unterhaltungsbasierten Bot-Erfahrung oft natürlicher.

Aufgabenmodule basieren auf der Grundlage Microsoft Teams Registerkarten. Sie sind im Wesentlichen eine Registerkarte in einem Popupfenster. Sie verwenden das gleiche SDK, wenn Sie also eine Registerkarte erstellt haben, sind Sie bereits mit dem Erstellen eines Aufgabenmoduls vertraut.

Aufgabenmodule können auf drei Arten aufgerufen werden:

* Kanal- oder persönliche Registerkarten: Mit dem Microsoft Teams Tabs SDK können Sie Aufgabenmodule über Schaltflächen, Links oder Menüs auf Ihrer Registerkarte aufrufen. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* Bots: Verwenden von Schaltflächen auf [Karten,](~/task-modules-and-cards/cards/cards-reference.md) die von Ihrem Bot gesendet werden. Dies ist nützlich, wenn Nicht-Benutzer in einem Kanal sehen müssen, was Sie mit einem Bot tun. Wenn Benutzer beispielsweise auf eine Umfrage in einem Kanal antworten, ist es nicht sinnvoll, einen Datensatz zu sehen, der erstellt wird. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen aus Teams Bots.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* Außerhalb von Teams von einem Deep-Link: Sie können auch URLs erstellen, um ein Aufgabenmodul von überall aus aufzurufen. Weitere Informationen finden Sie unter ["Deep Link"-Syntax des Aufgabenmoduls.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax)

## <a name="components-of-a-task-module"></a>Komponenten eines Aufgabenmoduls

So sieht ein Aufgabenmodul aus, wenn es von einem Bot aufgerufen wird:

![Beispiel für ein Aufgabenmodul](~/assets/images/task-module/task-module-example.png)

Ein Aufgabenmodul enthält Folgendes, wie in der vorherigen Abbildung dargestellt:

1. [ `color` Das Symbol](~/resources/schema/manifest-schema.md#icons)Ihrer App.
2. Der [ `short` Name](~/resources/schema/manifest-schema.md#name)Ihrer App.
3. Der Titel des Aufgabenmoduls, der in der `title` Eigenschaft des [TaskInfo -Objekts](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object)angegeben ist.
4. Die Schaltfläche zum Schließen oder Abbrechen des Aufgabenmoduls. Wenn der Benutzer diese Schaltfläche auswählt, empfängt Ihre App ein `err` Ereignis. Weitere Informationen finden Sie unter [Beispiel zum Übermitteln des Ergebnisses eines Aufgabenmoduls.](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module)

    > [!NOTE]
    > Es ist derzeit nicht möglich, das Ereignis zu `err` erkennen, wenn ein Aufgabenmodul von einem Bot aufgerufen wird.

5. Das blaue Rechteck ist der Ort, an dem Ihre Webseite angezeigt wird, wenn Sie Ihre eigene Webseite mithilfe der `url` Eigenschaft des [TaskInfo -Objekts](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object)laden. Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-sizing)
6. Wenn Sie eine adaptive Karte mithilfe der `card` Eigenschaft des [TaskInfo -Objekts](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) anzeigen, wird der Abstand für Sie hinzugefügt. Weitere Informationen finden Sie unter [Aufgabenmodul-CSS für HTML- oder JavaScript-Aufgabenmodule.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-css-for-html-or-javascript-task-modules)
7. Schaltflächen für adaptive Karten werden gerendert, nachdem Sie **"Registrieren"** ausgewählt haben. Wenn Sie Ihre eigene Seite verwenden, erstellen Sie Ihre eigenen Schaltflächen.

## <a name="see-also"></a>Siehe auch

[Karten](~/task-modules-and-cards/what-are-cards.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aufrufen und Schließen von Aufgabenmodulen](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
