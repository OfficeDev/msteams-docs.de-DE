---
title: Szenen im benutzerdefinierten Modus "Zusammen"
description: Arbeiten mit benutzerdefinierten Szenen im Zusammen-Modus
ms.topic: conceptual
ms.openlocfilehash: d19f99ab55654eab03d56de8a001484bb518a7f2
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345269"
---
# <a name="custom-together-mode-scenes-in-teams"></a>Benutzerdefinierte Zusammen-Modus-Szenen

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Szenen im benutzerdefinierten Zusammen-Modus in Microsoft Teams bieten eine immersive und ansprechende Besprechungsumgebung, die Personen zusammenführt und sie dazu auffordert, ihr Video zu aktivieren. Sie kombiniert Teilnehmer digital in einer einzelnen virtuellen Szene und platziert ihre Videostreams in vordefinierten Arbeitsplätzen, die vom Szenenersteller entworfen und behoben wurden.

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

Eine Szene in benutzerdefinierten Szenen im Gemeinsamen Modus ist ein Artefakt, das vom Szenenentwickler mithilfe des Microsoft Scene Studio erstellt wurde. In einer eingestellten Szeneneinstellung haben die Teilnehmer Arbeitsplätze mit Videostreams festgelegt, die auf diesen Arbeitsplätzen gerendert werden.

> [!NOTE]
> Apps nur für Szenen werden empfohlen, da die Kauferfahrung für solche Apps nahtloser ist.

Der folgende Prozess bietet eine Übersicht zum Erstellen einer Nur-Szene-App:

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Nur-Szene-App erstellen" border="false":::

> [!NOTE]
> * Eine Nur-Szene-App ist immer noch eine App in Microsoft Teams. Das Szenenstudio verarbeitet die Erstellung des App-Pakets im Hintergrund.
> * Mehrere Szenen in einem einzelnen App-Paket werden Benutzern als flache Liste von Szenen angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen über grundlegende Kenntnisse der folgenden Punkte verfügen, um benutzerdefinierte Szenen im Zusammen-Modus verwenden zu können:

* Definition der Szene und der Arbeitsplätze in einer Szene.
* Besitzen Sie ein Microsoft Developer-Konto, und machen Sie sich mit dem Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) und App Studio vertraut.
* [Konzept des Querladens von Apps.](../concepts/deploy-and-publish/apps-upload.md)
* Stellen Sie sicher, dass der Administrator die Berechtigung zum [**Hochladen einer benutzerdefinierten App**](../concepts/deploy-and-publish/apps-upload.md) und zum Auswählen aller Filter im Rahmen der App-Setup- bzw. Besprechungsrichtlinien erteilt hat.

## <a name="best-practices"></a>Bewährte Methoden

Berücksichtigen Sie vor dem Erstellen einer Szene Folgendes, um eine nahtlose Szenenerstellung zu ermöglichen:

* Stellen Sie sicher, dass alle Bilder im PNG-Format vorliegen.
* Stellen Sie sicher, dass das endgültige Paket mit allen zusammen zusammengestellten Bildern die Auflösung von 1920 x 1080 nicht überschreiten darf.

    > [!NOTE]
    > Die Auflösung ist eine gerade Zahl. Dies ist eine Voraussetzung dafür, dass Szenen erfolgreich beleuchtet werden.

* Stellen Sie sicher, dass die maximale Szenengröße 10 MB beträgt.
* Stellen Sie sicher, dass die maximale Größe jedes Bilds 5 MB beträgt.

    > [!NOTE]
    > * Eine Szene ist eine Sammlung mehrerer Bilder. Der Grenzwert gilt für jedes einzelne Bild.
    > * Die individuelle Bildauflösung muss auch eine gerade Zahl sein.
  
* Stellen Sie sicher, dass das **Kontrollkästchen Transparent** aktiviert ist, wenn das Bild transparent ist. Dieses Kontrollkästchen ist im rechten Bereich verfügbar, wenn ein Bild ausgewählt ist.

    > [!NOTE]
    > Überlappende Bilder müssen als **transparent** markiert werden, um anzuzeigen, dass es sich um überlappende Bilder in der Szene handelt.

## <a name="build-a-scene-using-the-scene-studio"></a>Erstellen einer Szene mithilfe des Szenenstudios

Microsoft verfügt über ein Szenenstudio, mit dem Sie Szenen erstellen können. Es ist im [Szenen-Editor](https://dev.teams.microsoft.com/scenes)– Teams Entwicklerportal verfügbar.

> [!NOTE]
> Dieses Dokument bezieht sich auf Scene Studio im Microsoft Teams Entwicklerportal. Die Benutzeroberfläche und Funktionen sind im App Studio Scene Designer identisch.

Eine Szene im Kontext des Szenenstudios ist ein Artefakt, das Folgendes enthält:

* Reservierte Arbeitsplätze für Besprechungsorganisatoren und Besprechungsreferenten.

    > [!NOTE]
    > Der Referent bezieht sich nicht auf den Benutzer, der aktiv teilt. Es bezieht sich auf die [Besprechungsrolle.](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

* Platz und Bild für jeden Teilnehmer mit einer anpassbaren Breite und Höhe.

    > [!NOTE]
    > PNG ist das einzige unterstützte Format.

* XYZ-Koordinaten aller Arbeitsplätze und Bilder.
* Sammlung von Bildern, die als ein einziges Bild getarnt sind.

Die Platzabmessungen werden zum Zeichenbereich für das Rendern des Videostreams des Teilnehmers. Die folgende Abbildung zeigt jeden Platz, der als Avatar zum Erstellen von Szenen dargestellt wird:

![Szenenstudio](../assets/images/apps-in-meetings/scene-design-studio.png)

**So erstellen Sie eine Szene mit dem Scene Studio**

1. Wechseln Sie zum [Szenen-Editor – Teams Entwicklerportal.](https://dev.teams.microsoft.com/scenes)

    >[!NOTE]
    > * Um Scene Studio zu öffnen, können Sie zur Startseite von [Teams Entwicklerportal](https://dev.teams.microsoft.com/home) navigieren und **benutzerdefinierte Szenen für Besprechungen** erstellen auswählen.
    > * Um Scene Studio zu öffnen, können Sie zur Startseite von [Teams Entwicklerportal](https://dev.teams.microsoft.com/home)navigieren, im linken Abschnitt die Option **"Extras"** und im Abschnitt **"Extras"** das **Szenenstudio** auswählen.

1. Wählen Sie auf der Seite **"Szenen-Editor"** die Option **"Neue Szene erstellen" aus.**

1. Geben Sie im **Szenenfeld** einen Namen für die Szene ein.

    >[!NOTE]
    > * Sie können **"Schließen"** auswählen, um zwischen dem Schließen oder erneuten Öffnen des rechten Bereichs zu wechseln.
    > * Sie können die Szene mithilfe der Zoomleiste vergrößern oder verkleinern, um eine bessere Ansicht der Szene zu erzielen.

1. Ziehen Sie das Bild in die Umgebung, wie in der folgenden Abbildung dargestellt:

    >[!NOTE]
    > * Sie können die [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) herunterladen und Dateien mit den Bildern [SampleApp.zip.](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip)
    > * Alternativ können Sie der Szene Hintergrundbilder hinzufügen, indem **Sie Bilder hinzufügen.**

    ![Ziehen in die Szene](../assets/images/apps-in-meetings/drag-and-drop-scene.png)

1. Wählen Sie das Bild aus, das Sie platziert haben.

1. Wählen Sie im rechten Bereich eine Ausrichtung für das Bild aus, oder verwenden Sie den Schieberegler **"Größe anpassen",** um die Bildgröße anzupassen.

    ![Ausrichtung für Bilder](../assets/images/apps-in-meetings/image-alignment.png)

1. Wählen Sie einen Bereich außerhalb des Bilds aus.

1. Wählen Sie in der oberen rechten Ecke unter **"Layer"** die Option **"Teilnehmer"** aus.

1. Wählen Sie im Feld "Anzahl der **Teilnehmer"** die Anzahl der Teilnehmer für die Szene aus, und wählen Sie **"Hinzufügen"** aus.

    >[!NOTE]
    > * Nachdem die Szene ausgeliefert wurde, werden die Avatar-Platzierungen durch die Videostreams des tatsächlichen Teilnehmers ersetzt.
    > * Sie können die Teilnehmerbilder um die Szene ziehen und an der erforderlichen Position platzieren und die Größe mithilfe des Größenänderungspfeils ändern.

1. Wählen Sie ein beliebiges Teilnehmerbild aus, und aktivieren Sie das Kontrollkästchen **"Spot zuweisen",** um dem Teilnehmer die Stelle zuzuweisen.

1. Wählen Sie die Rolle **"Besprechungsorganisator"** oder **"Referent"** für den Teilnehmer aus.

    >[!NOTE]
    > In einer Besprechung muss einem Teilnehmer die Rolle eines Besprechungsorganisators zugewiesen werden.

    ![Spot zuweisen](../assets/images/apps-in-meetings/assign-spot.png)

1. Wählen Sie **"Speichern"** und **dann "Ansicht" in Teams** aus, um Ihre Szene in Microsoft Teams schnell zu testen.

    >[!NOTE]
    > * Wenn Sie **"Ansicht" in Teams** auswählen, wird automatisch eine Microsoft Teams App erstellt, die auf der Seite **"Apps"** im Teams Entwicklerportal angezeigt werden kann.
    > * Wenn Sie **"Ansicht" in Teams** auswählen, wird automatisch ein App-Paket erstellt, das hinter der Szene appmanifest.jswird. Wie bereits erwähnt, ist dies abstrahiert, Aber Sie können über das Menü zu **Apps** navigieren, um auf das automatisch erstellte App-Paket zuzugreifen.
    > * Um eine von Ihnen erstellte Szene zu löschen, wählen Sie die Szene auf der oberen Leiste **löschen** aus.

1. Wählen Sie im daraufhin angezeigten Dialogfeld **"Hinzufügen"** aus.

    Sie können die Szene testen oder darauf zugreifen, indem Sie eine Testbesprechung erstellen und benutzerdefinierte Szenen im Gemeinsamen Modus starten. Weitere Informationen finden Sie unter [Aktivieren benutzerdefinierter Szenen für den Zusammen-Modus.](#activate-custom-together-mode-scenes)

    ![Starten von Szenen im benutzerdefinierten Modus "Zusammen"](../assets/images/apps-in-meetings/launchtogethermode.png)

    >[!NOTE]
    > * Die Szene kann in der benutzerdefinierten Szenengalerie für den Zusammen-Modus angezeigt werden.

1. Optional können Sie im Dropdownmenü **"Speichern"** die Option **"Freigeben"** auswählen, um einen freigabefähigen Link zu erstellen, um Ihre Szenen für andere Benutzer einfach zu verteilen. Durch Öffnen dieses Links wird die Szene für den Benutzer installiert, und er kann mit der Verwendung beginnen.

1. Nach der Vorschau kann die Szene als App an Teams ausgeliefert werden, indem Sie zum Abschnitt "Apps" im Teams Developer Center wechseln. Von dort aus können Sie das App-Paket herunterladen oder direkt in Ihrer Organisation veröffentlichen.

    >[!NOTE]
    > Dieser Schritt erfordert das App-Paket, das sich vom Szenenpaket unterscheidet, für die Szene, die entworfen wurde. Das automatisch erstellte App-Paket finden Sie im Abschnitt **"Apps"** im Teams Developer Center.

1. Optional kann das Szenenpaket gespeichert werden, indem Sie im Dropdownmenü **"Speichern"** die Option **"Exportieren"** auswählen. Eine .zip Datei, bei der es sich um das Szenenpaket handelt, wird heruntergeladen.

    ![Exportieren einer Szene](../assets/images/apps-in-meetings/build-a-scene.png)

    >[!NOTE]
    > Das Szenenpaket besteht aus einer scene.jsund den PNG-Ressourcen, die zum Erstellen einer Szene verwendet werden. Das Szenenpaket kann auf andere Änderungen überprüft werden, wie im Beispiel scene.jsim Abschnitt dieses Dokuments beschrieben.

Eine komplexere Szene, die die Z-Achse nutzt, wird im Beispiel für die ersten Schritte veranschaulicht.

## <a name="sample-scenejson"></a>Beispiel scene.json

Scene.jszusammen mit den Bildern gibt die genaue Position der Arbeitsplätze an. Eine Szene besteht aus Bitmapbildern, Sprites und Rechtecke, in die Teilnehmervideos eingefügt werden. Diese Sprites und Teilnehmerfelder werden in einem Weltkoordinatensystem definiert, wobei die X-Achse nach rechts und die Y-Achse nach unten zeigen. Szenen im benutzerdefinierten Zusammen-Modus unterstützen das Vergrößern der aktuellen Teilnehmer. Dies ist hilfreich für kleine Besprechungen in einer großen Szene. Ein Sprite ist ein statisches Bitmapbild, das in der Welt positioniert ist. Der Z-Wert des Sprite bestimmt die Position des Sprite. Das Rendern beginnt mit dem Sprite mit dem niedrigsten Z-Wert, daher bedeutet ein höherer Z-Wert, dass es näher an der Kamera ist. Jeder Teilnehmer verfügt über einen eigenen Videofeed, der so segmentiert ist, dass nur der Vordergrund gerendert wird.

Im Folgenden finden Sie die scene.jsim Beispiel:

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

Jede Szene hat eine eindeutige ID und einen eindeutigen Namen. Die Szenen-JSON enthält auch Informationen zu allen Ressourcen, die für die Szene verwendet werden. Jede Ressource enthält einen Dateinamen, eine Breite, eine Höhe und eine Position auf der X- und Y-Achse. Entsprechend enthält jeder Arbeitsplatz eine Platz-ID, Breite, Höhe und Position auf der X- und Y-Achse. Die Reihenfolge der Auslastung wird automatisch generiert und kann je nach Präferenz geändert werden.

> [!NOTE]
> Die Nummer der Reihenfolge der Benachrichtigung entspricht der Reihenfolge der Personen, die dem Anruf beitreten.

Der ZOrder stellt die Reihenfolge dar, in der Bilder und Arbeitsplätze entlang der Z-Achse platziert werden. In vielen Fällen gibt es bei Bedarf ein Gefühl von Tiefe oder Partition. Weitere Informationen finden Sie im Schritt-für-Schritt-Beispiel für die ersten Schritte. Das Beispiel nutzt zOrder.

Nachdem Sie nun das Beispiel scene.jsweiter durchgegangen sind, können Sie die benutzerdefinierten Szenen im Zusammen-Modus aktivieren, um szenenaktiviert zu werden.

## <a name="activate-custom-together-mode-scenes"></a>Aktivieren von Szenen im benutzerdefinierten Modus "Zusammen"

Hier erhalten Sie End-to-End-Informationen dazu, wie sich ein Endbenutzer mit Szenen in benutzerdefinierten Szenen im Zusammen-Modus beschäftigt.

**So wählen Sie Szenen aus und aktivieren benutzerdefinierte Szenen im Zusammen-Modus**

1. Erstellen sie eine neue Testbesprechung.

    >[!NOTE]
    > Bei Auswahl der **Vorschau** im Szenenstudio wird die Szene als App in Microsoft Teams installiert. Dies ist das Modell, mit dem Entwickler Szenen aus dem Szenenstudio testen und ausprobieren können. Nachdem eine Szene als App ausgeliefert wurde, sehen Benutzer diese Szenen in der Szenengalerie.

1. Wählen  Sie in der Dropdownliste Katalog in der oberen linken Ecke den **Modus Zusammen** aus. Das Dialogfeld **"Auswahl"** wird angezeigt, und die hinzugefügte Szene ist verfügbar.

1. Wählen Sie **"Szene ändern"** aus, um die Standard-Szene zu ändern.

1. Wählen Sie im **Szenenkatalog** die Szene aus, die Sie für Ihre Besprechung verwenden möchten.

1. Optional können der Besprechungsorganisator und der Referent die Szene für alle Teilnehmer der Besprechung **ändern.**

    >[!NOTE]
    > Zu jedem Zeitpunkt kann nur eine Szene homogen für die Besprechung verwendet werden. Wenn ein Referent oder Organisator eine Szene ändert, wird sie für alle geändert. Das Wechseln in oder aus benutzerdefinierten Szenen für den gemeinsamen Modus ist für einzelne Teilnehmer selbst möglich, aber in benutzerdefinierten Szenen im Gemeinsamen Modus haben alle Teilnehmer dieselbe Szene.

1. Wählen Sie **Anwenden** aus. Teams installiert die App für den Benutzer und wendet die Szene an.

## <a name="open-a-custom-together-mode-scenes-scene-package"></a>Öffnen eines benutzerdefinierten Szenenpakets für den Gemeinsamen Modus

Sie können das Szenenpaket, bei dem es sich um eine aus dem Szenenstudio abgerufene .zip datei handelt, für andere Ersteller freigeben, um die Szene weiter zu verbessern. Die Funktion zum **Importieren einer Szene** kann verwendet werden. Mit diesem Tool können Sie ein Szenenpaket entpacken, damit der Ersteller die Szene weiter erstellen kann.

![Szenen-ZIP-Datei](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a>Siehe auch

[Apps für Teams Besprechungen](teams-apps-in-meetings.md)
