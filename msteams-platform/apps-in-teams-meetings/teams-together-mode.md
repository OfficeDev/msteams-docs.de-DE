---
title: Szenen im benutzerdefinierten Modus "Zusammen"
description: Arbeiten mit benutzerdefinierten Szenen im Zusammen-Modus
ms.topic: conceptual
ms.openlocfilehash: 32b7cb32eb3f422641dbf28e635e39d978bad002
ms.sourcegitcommit: 68f5411f5989ac706b6a4a7b2884296e145fe7c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2021
ms.locfileid: "58849440"
---
# <a name="custom-together-mode-scenes-in-teams"></a>Benutzerdefinierte Zusammen-Modus-Szenen

Szenen im benutzerdefinierten Zusammen-Modus in Microsoft Teams eine immersive und ansprechende Besprechungsumgebung mit den folgenden Aktionen bereitstellen:

* Bringen Sie Personen zusammen und ermutigen Sie sie, ihr Video zu aktivieren. 
* Kombinieren Sie Teilnehmer digital in einer einzelnen virtuellen Szene. 
* Platzieren Sie die Videostreams der Teilnehmer in vordefinierten Arbeitsplätzen, die vom Szenenersteller entworfen und behoben wurden.

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

In szenen des benutzerdefinierten Zusammen-Modus ist die Szene ein Artefakt. Die Szene wird vom Szenenentwickler mithilfe des Microsoft Scene Studio erstellt. In einer erzwungenen Szeneneinstellung verfügen Die Teilnehmer über Arbeitsplätze mit Videostreams. Die Videos werden auf diesen Arbeitsplätzen gerendert. Nur Szenen-Apps werden empfohlen, da die Benutzeroberfläche für solche Apps klar ist.

Der folgende Prozess bietet eine Übersicht zum Erstellen einer Nur-Szene-App:

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Nur-Szene-App erstellen" border="false":::

Eine Nur-Szene-App ist immer noch eine App in Microsoft Teams. Das Szenenstudio verarbeitet die Erstellung des App-Pakets im Hintergrund. Mehrere Szenen in einem einzelnen App-Paket werden den Benutzern als flache Liste angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen über grundlegende Kenntnisse der folgenden Punkte verfügen, um benutzerdefinierte Szenen im Zusammen-Modus verwenden zu können:

* Definieren der Szene und der Arbeitsplätze in einer Szene.
* Besitzen Sie ein Microsoft Developer-Konto, und machen Sie sich mit dem Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) und App Studio vertraut.
* Verstehen des [Konzepts des Querladens von Apps.](../concepts/deploy-and-publish/apps-upload.md)
* Stellen Sie sicher, dass der Administrator die Berechtigung zum [**Hochladen einer benutzerdefinierten App**](../concepts/deploy-and-publish/apps-upload.md) erteilt hat, und wählen Sie alle Filter im Rahmen der App-Setup- bzw. Besprechungsrichtlinien aus.

## <a name="best-practices"></a>Bewährte Methoden

Berücksichtigen Sie die folgenden Methoden für die Erstellung von Szenen:

* Stellen Sie sicher, dass alle Bilder im PNG-Format vorliegen.
* Stellen Sie sicher, dass das endgültige Paket mit allen zusammen zusammengestellten Bildern die Auflösung von 1920 x 1080 nicht überschreiten darf. Die Auflösung ist eine gerade Zahl. Diese Auflösung ist eine Voraussetzung dafür, dass Szenen erfolgreich angezeigt werden.
* Stellen Sie sicher, dass die maximale Szenengröße 10 MB beträgt.
* Stellen Sie sicher, dass die maximale Größe jedes Bilds 5 MB beträgt. Eine Szene ist eine Sammlung mehrerer Bilder. Der Grenzwert gilt für jedes einzelne Bild.
* Stellen Sie sicher, dass Sie bei Bedarf **"Transparent"** auswählen. Dieses Kontrollkästchen ist im rechten Bereich verfügbar, wenn ein Bild ausgewählt ist. Die überlappenden Bilder müssen als **transparent** markiert werden, um anzuzeigen, dass sie sich in der Szene überlappen.

## <a name="build-a-scene-using-the-scene-studio"></a>Erstellen einer Szene mithilfe des Szenenstudios

Microsoft verfügt über ein Szenenstudio, mit dem Sie Szenen erstellen können. Es ist im [Szenen-Editor](https://dev.teams.microsoft.com/scenes)– Teams Entwicklerportal verfügbar. Dieses Dokument verweist auf Scene Studio im Microsoft Teams Entwicklerportal. Die Benutzeroberfläche und Funktionen sind im App Studio Scene Designer identisch.

Eine Szene im Kontext des Szenenstudios ist ein Artefakt, das die folgenden Elemente enthält:

* Reservierte Arbeitsplätze für Besprechungsorganisatoren und Besprechungsreferenten. Der Referent bezieht sich nicht auf den Benutzer, der aktiv teilt. Es bezieht sich auf die [Besprechungsrolle.](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

* Platz und Bild für jeden Teilnehmer mit einer anpassbaren Breite und Höhe. Für das Bild wird nur das PNG-Format unterstützt.

* XYZ-Koordinaten aller Arbeitsplätze und Bilder.

* Sammlung von Bildern, die als ein einziges Bild getarnt sind.

Die folgende Abbildung zeigt jeden Platz, der als Avatar zum Erstellen der Szenen dargestellt wird:

![Szenenstudio](../assets/images/apps-in-meetings/scene-design-studio.png)

**So erstellen Sie eine Szene mit dem Scene Studio**

1. Wechseln Sie zum [Szenen-Editor – Teams Entwicklerportal.](https://dev.teams.microsoft.com/scenes)

    Alternativ können Sie zum Öffnen von Scene Studio zur Startseite des [Teams Entwicklerportals](https://dev.teams.microsoft.com/home)wechseln:
    * Wählen Sie **"Benutzerdefinierte Szenen für Besprechungen erstellen"** aus.
    * Wählen Sie im linken Abschnitt die Option **"Extras"** und dann im Abschnitt **"Extras"** die Option **"Szenenstudio"** aus.

1. Wählen Sie **im Szenen-Editor** **eine neue Szene erstellen** aus.

1. Geben Sie unter **Szenenname** einen Namen für die Szene ein.

    * Sie können **"Schließen"** auswählen, um zwischen dem Schließen oder erneuten Öffnen des rechten Bereichs zu wechseln.
    * Sie können die Szene mithilfe der Zoomleiste vergrößern oder verkleinern, um eine bessere Ansicht der Szene zu erzielen.

1. Wählen Sie **"Bilder hinzufügen"** aus, um das Bild der Umgebung hinzuzufügen:

    ![Hinzufügen von Bildern zur Umgebung](../assets/images/apps-in-meetings/addimages.png)

    >[!NOTE]
    > * Sie können die [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) herunterladen und Dateien mit den Bildern [SampleApp.zip.](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip)

1. Wählen Sie das Bild aus, das Sie hinzugefügt haben.

1. Wählen Sie im rechten Bereich eine Ausrichtung für das Bild aus, oder verwenden Sie die **Größenänderung,** um die Bildgröße anzupassen:

    ![Ausrichtung für Bilder](../assets/images/apps-in-meetings/image-alignment.png)

1. Wählen Sie einen Bereich außerhalb des Bilds aus.

1. Wählen Sie in der oberen rechten Ecke unter **"Layer"** die Option **"Teilnehmer"** aus.

1. Wählen Sie im Feld "Anzahl der **Teilnehmer"** die Anzahl der Teilnehmer für die Szene aus, und wählen Sie **"Hinzufügen"** aus. Nachdem die Szene ausgeliefert wurde, werden die Avatar-Platzierungen durch die Videostreams des tatsächlichen Teilnehmers ersetzt. Sie können die Bilder der Teilnehmer um die Szene ziehen und an der erforderlichen Position platzieren. Sie können die Größe mithilfe des Größenänderungspfeils ändern.

1. Wählen Sie ein beliebiges Teilnehmerbild aus, und wählen **Sie "Spot zuweisen"** aus, um dem Teilnehmer die Stelle zuzuweisen.

1. Wählen Sie die Rolle **"Besprechungsorganisator"** oder **"Referent"** für den Teilnehmer aus. In einer Besprechung muss einem Teilnehmer die Rolle eines Besprechungsorganisators zugewiesen werden:

    ![Spot zuweisen](../assets/images/apps-in-meetings/assign-spot.png)

1. Wählen Sie **"Speichern"** und **dann "Anzeigen" in Teams** aus, um Ihre Szene schnell in Microsoft Teams zu testen.

    * Wenn Sie **"Ansicht" in Teams** auswählen, wird automatisch eine Microsoft Teams App erstellt, die auf der Seite **"Apps"** im Teams Entwicklerportal angezeigt werden kann.
    * Wenn Sie **"Ansicht" in Teams** auswählen, wird automatisch ein App-Paket erstellt, das hinter der Szene appmanifest.jsist. Sie können über das Menü zu  **Apps** wechseln und auf das automatisch erstellte App-Paket zugreifen.
    * Um eine von Ihnen erstellte Szene zu löschen, wählen Sie die Szene auf der oberen Leiste **löschen** aus.

1. Wählen Sie **in "Ansicht" in Teams** die Option **"Vorschau" in Teams** aus.
1. Wählen Sie im daraufhin angezeigten Dialogfeld **"Hinzufügen"** aus.

    Die Szene wird getestet oder durch Erstellen einer Testbesprechung und Starten benutzerdefinierter Szenen im Zusammen-Modus aufgerufen. Weitere Informationen finden Sie unter [Aktivieren benutzerdefinierter Szenen im Zusammen-Modus:](#activate-custom-together-mode-scenes)

    ![Starten von Szenen im benutzerdefinierten Modus "Zusammen"](../assets/images/apps-in-meetings/launchtogethermode.png)

    Die Szene kann dann in der benutzerdefinierten Szenengalerie für den Zusammen-Modus angezeigt werden.

Optional können Sie im Dropdownmenü **"Speichern"** die Option **"Freigeben"** auswählen. Sie können einen freigabefähigen Link erstellen, um Ihre Szenen für andere Benutzer zu verteilen. Der Benutzer kann den Link öffnen, um die Szene zu installieren und damit zu beginnen.

Nach der Vorschau wird die Szene als App an Teams ausgeliefert, indem die Schritte für die App-Übermittlung ausgeführt werden. Für diesen Schritt ist das App-Paket erforderlich. Das App-Paket unterscheidet sich vom Szenenpaket für die Szene, die entworfen wurde. Das automatisch erstellte App-Paket befindet sich im Abschnitt **"Apps"** im Teams Developer Center.

Optional wird das Szenenpaket abgerufen, indem im Dropdownmenü **"Speichern"** die Option **"Exportieren"** ausgewählt wird. Eine .zip-Datei, d. h. das Szenenpaket, wird heruntergeladen. Das Szenenpaket enthält eine scene.jsund die PNG-Objekte, die zum Erstellen einer Szene verwendet werden. Das Szenenpaket wird auf andere Änderungen überprüft:

![Exportieren einer Szene](../assets/images/apps-in-meetings/build-a-scene.png)

Eine komplexe Szene, die die Z-Achse verwendet, wird im Schritt-für-Schritt-Beispiel für die ersten Schritte veranschaulicht.

## <a name="sample-scenejson"></a>Beispiel scene.json

Scene.jszusammen mit den Bildern zeigen die genaue Position der Arbeitsplätze an. Eine Szene besteht aus Bitmapbildern, Sprites und Rechtecke, in die Teilnehmervideos eingefügt werden. Diese Sprites und Teilnehmerfelder werden in einem Weltkoordinatensystem definiert. Die X-Achse zeigt nach rechts und die Y-Achse nach unten.

Szenen im benutzerdefinierten Zusammen-Modus unterstützen das Vergrößern der aktuellen Teilnehmer. Dieses Feature ist hilfreich für kleine Besprechungen in einer großen Szene. Ein Sprite ist ein statisches Bitmapbild, das in der Welt positioniert ist. Der Z-Wert des Sprite bestimmt die Position des Sprite. Das Rendern beginnt mit dem Sprite mit dem niedrigsten Z-Wert, daher bedeutet ein höherer Z-Wert, dass er näher an der Kamera ist. Jeder Teilnehmer verfügt über einen eigenen Videofeed, der segmentiert ist, sodass nur der Vordergrund gerendert wird.

Der folgende Code ist der scene.jsim Beispiel:

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

Jede Szene hat eine eindeutige ID und einen eindeutigen Namen. Die Szenen-JSON enthält auch Informationen zu allen Ressourcen, die für die Szene verwendet werden. Jede Ressource enthält einen Dateinamen, eine Breite, eine Höhe und eine Position auf der X- und Y-Achse. Entsprechend enthält jeder Arbeitsplatz eine Platz-ID, Breite, Höhe und Position auf der X- und Y-Achse. Die Reihenfolge der Auslastung wird automatisch generiert und gemäß ihrer Präferenz geändert. Die Nummer der Reihenfolge entspricht der Reihenfolge der Personen, die dem Anruf beitreten.

Dies stellt die Reihenfolge dar, in `zOrder` der Bilder und Arbeitsplätze entlang der Z-Achse platziert werden. Es gibt bei Bedarf ein Gefühl von Tiefe oder Partition. Sehen Sie sich das Beispiel für schrittweise erste Schritte an. Im Beispiel wird die `zOrder` .

Nachdem Sie nun die Beispiel-scene.jsdurchlaufen haben, können Sie die benutzerdefinierten Szenen im Zusammen-Modus aktivieren, um szenenaktiviert zu werden.

## <a name="activate-custom-together-mode-scenes"></a>Aktivieren von Szenen im benutzerdefinierten Modus "Zusammen"

Erhalten Sie weitere Informationen dazu, wie sich ein Benutzer mit Szenen in benutzerdefinierten Szenen im Zusammen-Modus beschäftigt.

**So wählen Sie Szenen aus und aktivieren benutzerdefinierte Szenen im Zusammen-Modus**

1. Erstellen sie eine neue Testbesprechung.

    >[!NOTE]
    > Bei Auswahl der **Vorschau** im Szenenstudio wird die Szene als App in Microsoft Teams installiert. Dies ist das Modell, mit dem Entwickler Szenen aus dem Szenenstudio testen und ausprobieren können. Nachdem eine Szene als App ausgeliefert wurde, sehen Benutzer diese Szenen in der Szenengalerie.

1. Wählen  Sie in der Dropdownliste Katalog in der oberen linken Ecke den **Modus Zusammen** aus. Das Dialogfeld **"Auswahl"** wird angezeigt, und die hinzugefügte Szene ist verfügbar.

1. Wählen Sie **"Szene ändern"** aus, um die Standard-Szene zu ändern.

1. Wählen Sie im **Szenenkatalog** die Szene aus, die Sie für Ihre Besprechung verwenden möchten.

    Optional können der Besprechungsorganisator und der Referent die Szene für alle Teilnehmer der Besprechung **ändern.**

    >[!NOTE]
    > Zu jedem Zeitpunkt wird nur eine Szene homogen für die Besprechung verwendet. Wenn ein Referent oder Organisator eine Szene ändert, wird sie für alle geändert. Das Wechseln in oder aus benutzerdefinierten Szenen für den gemeinsamen Modus ist für einzelne Teilnehmer selbst möglich, aber in benutzerdefinierten Szenen im Gemeinsamen Modus haben alle Teilnehmer dieselbe Szene.

1. Wählen Sie **Anwenden** aus. Teams installiert die App für den Benutzer und wendet die Szene an.

## <a name="open-a-custom-together-mode-scenes-scene-package"></a>Öffnen eines benutzerdefinierten Szenenpakets für den Gemeinsamen Modus

Sie können das Szenenpaket, das eine aus dem Szenenstudio abgerufene .zip-Datei ist, für andere Ersteller freigeben, um die Szene weiter zu verbessern. Die Funktion zum **Importieren einer Szene** hilft beim Entpacken eines Szenenpakets, damit der Ersteller die Szene weiter erstellen kann.

![Szenen-ZIP-Datei](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a>Siehe auch

[Apps für Teams Besprechungen](teams-apps-in-meetings.md)
