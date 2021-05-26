---
title: Together Mode in Teams
description: Arbeiten mit dem Gemeinsamen Modus
ms.topic: conceptual
ms.openlocfilehash: 1620e01ef1825ec43e94614ff8ea355e764e10e0
ms.sourcegitcommit: 1cc1516e71441f6f3f82b35868e21ba9933333cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52651740"
---
# <a name="together-mode-in-teams"></a>Together Mode in Teams

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Microsoft Teams Der Modus "Zusammen" bietet eine immersive und ansprechende Besprechungsumgebung, die Personen zusammen bringt und sie ermutigt, ihr Video zu aktivieren. Es kombiniert Teilnehmer digital zu einer einzelnen virtuellen Szene und platziert ihre Videostreams an vordefinierten, vom Szenenersteller entworfenen und festgelegten Sitzen.

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

Eine Szene im Gemeinsamen Modus ist ein Artefakt, das vom Szenenentwickler mit dem Microsoft Scene Studio erstellt wurde. In einer konzipierten Szeneneinstellung verfügen die Teilnehmer über festgelegte Plätze mit Videostreams, die in diesen Sitzen gerendert werden.

> [!NOTE]
> Nur Szenen-Apps werden empfohlen, da die Kauferfahrung für solche Apps nahtloser ist.

Der folgende Prozess bietet eine Übersicht zum Erstellen einer Nur-Szene-App:

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Nur Szenen-App erstellen" border="false":::

> [!NOTE]
> * Eine Nur-Szene-App ist immer noch eine App in Microsoft Teams. Das Scene Studio verarbeitet die Erstellung von App-Paketen im Hintergrund.
> * Mehrere Szenen in einem einzelnen App-Paket werden benutzern als flache Liste von Szenen angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen über grundlegende Kenntnisse der folgenden Funktionen verfügen, um den Gemeinsamen Modus verwenden zu können:

* Definition von Szene und Sitzen in einer Szene.
* Verfügen Sie über ein Microsoft Developer-Konto, und machen Sie sich mit Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) und App Studio vertraut.
* [Konzept des Querladens von Apps](../concepts/deploy-and-publish/apps-upload.md).
* Stellen Sie sicher, dass  der Administrator die Berechtigung zum Hochladen einer benutzerdefinierten App und zum Auswählen aller Filter im Rahmen von App-Setup- bzw. Besprechungsrichtlinien erteilt hat.

## <a name="best-practices"></a>Bewährte Methoden

Berücksichtigen Sie vor dem Erstellen einer Szene Folgendes, um eine nahtlose Szenenbildung zu ermöglichen:

* Stellen Sie sicher, dass alle Bilder im PNG-Format vorliegen.
* Stellen Sie sicher, dass das endgültige Paket mit allen zusammen 1920 x 1080 Bildern nicht die Auflösung von 1920 x 1080 überschreiten darf.

    > [!NOTE]
    > Die Auflösung ist eine gleichmäßige Zahl. Dies ist eine Voraussetzung dafür, dass Szenen erfolgreich beleuchtet werden.

* Stellen Sie sicher, dass die maximale Szenengröße 10 MB beträgt.
* Stellen Sie sicher, dass die maximale Größe jedes Bilds 5 MB beträgt.

    > [!NOTE]
    > * Eine Szene ist eine Sammlung mehrerer Bilder. Der Grenzwert gilt für jedes einzelne Bild.
    > * Die einzelne Bildauflösung muss auch eine gleichmäßige Zahl sein.
  
* Stellen Sie sicher, dass **das Kontrollkästchen Transparent** aktiviert ist, wenn das Bild transparent ist. Dieses Kontrollkästchen ist im rechten Bereich verfügbar, wenn ein Bild ausgewählt ist.

    > [!NOTE]
    > Überlappende Bilder müssen als **Transparent gekennzeichnet** werden, um anzuzeigen, dass es sich um überlappende Bilder in der Szene handelt.

## <a name="build-a-scene-using-the-scene-studio"></a>Erstellen einer Szene mithilfe des Szenenstudios

Microsoft verfügt über ein Szenenstudio, mit dem Sie Szenen erstellen können. Sie ist im [Szenen-Editor verfügbar– Teams Entwicklerportal](https://dev.teams.microsoft.com/scenes).

> [!NOTE]
> Dieses Dokument bezieht sich auf Scene studio im Microsoft Teams Developer Portal. Die Benutzeroberfläche und die Funktionen sind im App Studio Scene Designer identisch.

Eine Szene im Kontext des Szenenstudios ist ein Artefakt, das Folgendes enthält:

* Reservierte Plätze für Besprechungsorganisatoren und Besprechungsorganisatoren.

    > [!NOTE]
    > Der Presenter bezieht sich nicht auf den Benutzer, der aktiv freigaben möchte. Er bezieht sich auf die [Besprechungsrolle](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

* Platz und Bild für jeden Teilnehmer mit einer anpassbaren Breite und Höhe.

    > [!NOTE]
    > PNG ist das einzige unterstützte Format.

* XYZ-Koordinaten aller Sitze und Bilder.
* Sammlung von Bildern, die als ein Bild getarnt sind.

Die Größe des Platzes wird zum Zeichenbereich für das Rendern des Teilnehmervideostreams. Die folgende Abbildung zeigt jeden Platz, der als Avatar für das Erstellen von Szenen dargestellt wird:

![Szenenstudio](../assets/images/apps-in-meetings/scene-design-studio.png)

**So erstellen Sie eine Szene mithilfe des Szenenstudios**

1. Wechseln Sie [zu Szenen-Editor – Teams Developer Portal](https://dev.teams.microsoft.com/scenes).

    >[!NOTE]
    > * Zum Öffnen von Scene Studio können Sie zur Startseite des [Teams-Entwicklerportals](https://dev.teams.microsoft.com/home) navigieren und benutzerdefinierte Szenen für **Besprechungen erstellen auswählen.**
    > * Zum Öffnen von Scene Studio können Sie zur Startseite von [Teams Developer Portal](https://dev.teams.microsoft.com/home)navigieren, im  linken Abschnitt Tools auswählen und im Abschnitt **Extras** szenenstudio auswählen. 

1. Wählen Sie **auf der** Seite Szenen-Editor die Option Neue Szene **erstellen aus.**

1. Geben Sie **im Feld Szene** einen Namen für die Szene ein.

    >[!NOTE]
    > * Sie können Schließen **auswählen,** um zwischen dem Schließen oder erneuten Öffnen des rechten Bereichs umschalten zu können.
    > * Sie können die Szene mithilfe der Zoomleiste vergrößern oder verkleinern, um eine bessere Ansicht der Szene zu erhalten.

1. Ziehen Sie das Bild in die Umgebung, wie in der folgenden Abbildung dargestellt, und legen Sie es in die Umgebung ab:

    >[!NOTE]
    > * Sie können die dateien [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) [ undSampleApp.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip) mit den Bildern herunterladen.
    > * Alternativ können Sie der Szene Hintergrundbilder hinzufügen, indem **Sie Bilder hinzufügen verwenden.**

    ![Ziehen in die Szene](../assets/images/apps-in-meetings/drag-and-drop-scene.png)

1. Wählen Sie das Bild aus, das Sie platziert haben.

1. Wählen Sie im rechten Bereich eine Ausrichtung für das Bild aus, oder verwenden Sie **den** Schieberegler Größenänderung, um die Bildgröße anzupassen.

    ![Ausrichtung für Bilder](../assets/images/apps-in-meetings/image-alignment.png)

1. Wählen Sie einen Bereich außerhalb des Bilds aus.

1. Wählen Sie in der oberen rechten Ecke unter **Ebenen die** Option **Teilnehmer aus.**

1. Wählen Sie im Feld Anzahl  der Teilnehmer die Anzahl der Teilnehmer für die Szene aus, und wählen Sie **Hinzufügen aus.**

    >[!NOTE]
    > * Nachdem die Szene versendet wurde, werden die Avatarplatzierungen durch die Videostreams des tatsächlichen Teilnehmers ersetzt.
    > * Sie können die Teilnehmerbilder um die Szene ziehen und sie an der erforderlichen Position platzieren und die Größe mithilfe des Größenänderungspfeils ändern.

1. Wählen Sie ein beliebiges Teilnehmerbild aus, und aktivieren Sie das Kontrollkästchen **Spot** zuweisen, um den Spot dem Teilnehmer zuzuordnen.

1. Wählen **Sie die Rolle** "Besprechungsorganisator" oder **"Organisator"** für den Teilnehmer aus.

    >[!NOTE]
    > In einer Besprechung muss einem Teilnehmer die Rolle eines Besprechungsorganisators zugewiesen werden.

    ![Spot zuweisen](../assets/images/apps-in-meetings/assign-spot.png)

1. Wählen **Sie Speichern** aus, und **wählen** Teams ansicht aus, um Ihre Szene in einem Microsoft Teams.

    >[!NOTE]
    > Wenn Sie eine von Ihnen erstellte Szene löschen möchten, wählen **Sie szene löschen in** der oberen Leiste aus.

1. Wählen Sie im Dialogfeld **Ansicht in Teams** vorschau in **Teams** aus.
1. Wählen Sie im angezeigten Dialogfeld Hinzufügen **aus.**

    Die Szene kann getestet oder zugegriffen werden, indem Sie eine Testsitzung erstellen und den Gemeinsamen Modus starten. Weitere Informationen finden Sie unter [Aktivieren des Gemeinsamen Modus](#activate-the-together-mode).

    ![Gemeinsamen Modus starten](../assets/images/apps-in-meetings/launchtogethermode.png)

    >[!NOTE]
    > * Durch **Auswählen der** Vorschau wird automatisch Microsoft Teams App erstellt, die auf der Seite **Apps** im Teams angezeigt werden kann.
    > * Durch **Auswählen der Vorschau** wird automatisch ein App-Paket erstellt, appmanifest.jshinter der Szene angezeigt wird. Wie bereits erwähnt, ist dies abstrahiert, Sie können jedoch auf das automatisch erstellte App-Paket zugreifen, indem Sie über das Menü zu **Apps** navigieren.
    > * Die Szene kann dann im Szenenkatalog für den gemeinsamen Modus angezeigt werden.

1. Optional können Sie  im Dropdownmenü Speichern die Option Freigeben auswählen, um einen freigabebaren Link zu erstellen, um Ihre Szenen für andere Benutzer einfach zu verteilen.  Wenn Sie diesen Link öffnen, wird die Szene für den Benutzer installiert, und er kann mit der Verwendung beginnen.

1. Nach der Vorschau kann die Szene als App an Teams, indem Sie die Schritte für die App-Übermittlung ausführen.

    >[!NOTE]
    > Dieser Schritt erfordert das Vom Szenenpaket unterschiedliche App-Paket für die entworfene Szene. Das automatisch erstellte App-Paket finden Sie im Abschnitt **Apps** im Teams Developer Center.

1. Optional kann das Szenenpaket abgerufen werden, indem  Sie im Dropdownmenü Speichern auf **Exportieren** klicken. Eine .zip, d. h. das Szenenpaket, wird heruntergeladen.

    ![Exportieren einer Szene](../assets/images/apps-in-meetings/build-a-scene.png)

    >[!NOTE]
    > Das Szenenpaket besteht aus einem scene.jsund den PNG-Ressourcen, die zum Erstellen einer Szene verwendet werden. Das Szenenpaket kann für die Einbindung anderer Änderungen überprüft werden, wie im Abschnitt Beispiel scene.jsabschnitt dieses Dokuments beschrieben.

Eine komplexere Szene, die die Z-Achse nutzt, wird im Schrittweisen Beispiel für erste Schritte gezeigt.

## <a name="sample-scenejson"></a>Beispiel scene.json

Scene.jszusammen mit den Bildern geben Sie die genaue Position der Sitze an. Eine Szene besteht aus Bitmapbildern, Sprites und Rechtecken, in die Teilnehmervideos eingefügt werden können. Diese Sprites und Teilnehmerfelder werden in einem Weltkoordinatensystem definiert, bei dem die X-Achse nach rechts und die Y-Achse nach unten zeigt. Der Modus "Zusammen" unterstützt das Vergrößern der aktuellen Teilnehmer. Dies ist für kleine Besprechungen in einer großen Szene hilfreich. Ein sprite ist ein statisches Bitmapbild, das in der Welt positioniert ist. Der Z-Wert des sprite bestimmt die Position des sprite. Das Rendern beginnt mit dem sprite mit dem niedrigsten Z-Wert, sodass ein höherer Z-Wert bedeutet, dass er näher an der Kamera liegt. Jeder Teilnehmer verfügt über einen eigenen Videofeed, der segmentiert ist, sodass nur der Vordergrund gerendert wird.

Nachfolgend finden Sie scene.jsBeispiel:

```json
{
   "protocolVersion": "1.0",
   "id": "A",
   "autoZoom": true,
   "mirrorParticipants ": true,
   "extent":{
      "left":0.0,
      "top":0.0,
      "width":16.0,
      "height":9.0
   },
   "sprites":[
      {
         "filename":"background.png",
         "cx":8.0,
         "cy":4.5,
         "width":16.0,
         "height":9.0,
         "zOrder":0.0,
   "isAlpha":false
      },
      {
         "filename":"table.png",
         "cx":8.0,
         "cy":7.0,
         "width":12.0,
         "height":4.0,
         "zOrder":3.0,
   "isAlpha":true
      },
      {
         "filename":"row0.png",
         "cx":12.0,
         "cy":15.0,
         "width":8.0,
         "height":4.0,
         "zOrder":2.0,
   "isAlpha":true
      }

   ],
   "participants":[
      {
         "cx":5.0,
         "cy":4.0,
         "width":4.0,
         "height":2.25,
         "zOrder":1.0,
         "seatingOrder":0
      },
      {
         "cx":11.0,
         "cy":4.0,
         "width":4.0,
         "height":2.25,
         "zOrder":1.0,
         "seatingOrder":1
      }
   ]
}
```

Jede Szene hat eine eindeutige ID und einen eindeutigen Namen. Das Szenen-JSON enthält außerdem Informationen zu allen ressourcen, die für die Szene verwendet werden. Jede Ressource enthält einen Dateinamen, eine Breite, eine Höhe und eine Position auf der X- und Y-Achse. Entsprechend enthält jeder Sitz eine Sitz-ID, Breite, Höhe und Position auf der X- und Y-Achse. Die Sitzreihenfolge wird automatisch generiert und kann je nach Einstellung geändert werden.

> [!NOTE]
> Die Nummer der Sitzreihenfolge entspricht der Reihenfolge der Personen, die dem Anruf beitreten.

Die zOrder stellt die Reihenfolge dar, in der Bilder und Sitze entlang der Z-Achse platziert werden. In vielen Fällen gibt es ein Gefühl von Tiefe oder Partition, falls erforderlich. Weitere Informationen finden Sie im Schrittweisen Beispiel für erste Schritte. Das Beispiel nutzt die zOrder.

Nachdem Sie die Beispielanwendung scene.jshaben, können Sie den Modus "Zusammen" aktivieren, um an Szenen zu arbeiten.

## <a name="activate-the-together-mode"></a>Aktivieren des Gemeinsamen Modus

Erhalten Sie End-to-End-Informationen darüber, wie sich ein Endbenutzer mit Szenen im Gemeinsamen Modus beschäftigt.

**So wählen Sie Szenen aus, und aktivieren Sie den Gemeinsamen Modus**

1. Erstellen Sie eine neue Testsitzung.

    >[!NOTE]
    > Beim Auswählen **der Vorschau** im Szenenstudio wird die Szene als App in Microsoft Teams. Dies ist das Modell für einen Entwickler, um Szenen aus dem Szenenstudio zu testen und auszuprobieren. Nachdem eine Szene als App versendet wurde, werden diese Szenen im Szenenkatalog angezeigt.

1. Wählen Sie **in** der Dropdownliste Galerie in der oberen linken Ecke zusammen **Modus aus.** Das **Dialogfeld Auswahl** wird angezeigt, und die hinzugefügte Szene ist verfügbar.

1. Wählen **Sie Szene ändern aus,** um die Standardszene zu ändern.

1. Wählen Sie **im Szenenkatalog** die Szene aus, die Sie für Ihre Besprechung verwenden möchten.

1. Optional können der Besprechungsorganisator und der Organisator in der Besprechung den Modus **Alle** Teilnehmer in den Gemeinsamen Modus wechseln auswählen.

    >[!NOTE]
    > Zu jedem Beliebigen Zeitpunkt kann nur eine Szene homogen für die Besprechung verwendet werden. Wenn ein Organisator oder ein Organisator eine Szene ändert, ändert sie sich für alle. Das Wechseln in oder aus dem Gemeinsamen Modus liegt bei einzelnen Teilnehmern, aber im Gemeinsamen Modus haben alle Teilnehmer dieselbe Szene.

1. Wählen Sie **Anwenden** aus. Teams installiert die App für den Benutzer und wendet die Szene an.

## <a name="open-a-together-mode-scene-package"></a>Öffnen eines Szenenpakets für den gemeinsamen Modus

Sie können das Szenenpaket, bei dem es sich um eine .zip, die aus dem Szenenstudio abgerufen wurde, für andere Ersteller freigeben, um die Szene weiter zu verbessern. Die **Funktion "Szene importieren"** kann genutzt werden. Dieses Tool hilft beim Auspacken eines Szenenpakets, damit der Ersteller die Szene weiter erstellt.

![Szenen-ZIP-Datei](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a>Siehe auch

[Apps für Teams Besprechungen](teams-apps-in-meetings.md)
