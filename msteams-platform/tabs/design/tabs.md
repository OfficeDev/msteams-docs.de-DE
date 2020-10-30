---
title: Entwurfsrichtlinien für Registerkarten
description: Beschreibt die Richtlinien zum Erstellen von Registerkarten für Inhalt und Zusammenarbeit.
keywords: Teams Design Guidelines Reference Framework Registerkartenkonfiguration Kanal Registerkarte statische Registerkarte einfache Registerkarte Designteams Registerkarte
ms.openlocfilehash: 7636159e26a4000efb1d89dd8e9921a91cb5aa39
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796211"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a>Inhalte und Unterhaltungen auf einmal mithilfe von Registerkarten

> [!Important]
> **Registerkarten auf mobilen Clients**
>
> Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](./tabs-mobile.md) , wenn Sie Ihre Registerkarten erstellen. Wenn Ihre Registerkarte die Authentifizierung verwendet, müssen Sie Ihr Microsoft Teams-JavaScript-SDK auf Version 1.4.1 oder höher aktualisieren, oder die Authentifizierung schlägt fehl.
>
> **Registerkarten für Kanal/Gruppe (konfigurierbar) auf mobilen Geräten:**
>
> * Mobile Clients zeigen nur konfigurierbare Registerkarten mit einem Wert für an `websiteUrl` . Wenn die Registerkarte auf den mobilen Teams-Clients angezeigt werden soll, müssen Sie den Wert von festlegen `websiteUrl` .
> * Das standardmäßig geöffnete Verhalten auf mobilen Geräten ist das Öffnen außerhalb von Browser mithilfe von `websiteUrl` . Wenn Sie für apps, die im öffentlichen APP-Speicher veröffentlicht werden, die Kanal Registerkarte standardmäßig in Microsoft Teams öffnen möchten, befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md), und wenden Sie sich an Ihren Supportmitarbeiter, um eine weiße Liste zu fordern.

Registerkarten sind Ansichtsbilder, die Sie zum Freigeben von Inhalten, halten von Unterhaltungen und Hosten von Drittanbieterdiensten verwenden können, die alle innerhalb des organischen Workflows eines Teams liegen. Wenn Sie eine Registerkarte in Microsoft Teams erstellen, wird Ihre Webanwendungs-Front-und-Mitte platziert, wo Sie leicht von wichtigen Unterhaltungen aus zugänglich ist.

## <a name="guidelines"></a>Anleitungen

Auf einer Registerkarte "gut" sollten die folgenden Merkmale angezeigt werden:

### <a name="focused-functionality"></a>Fokussierte Funktionalität

Registerkarten funktionieren am besten, wenn Sie erstellt werden, um eine bestimmte Anforderung zu erfüllen. Konzentrieren Sie sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge der Daten, die für den Kanal relevant ist, in dem sich die Registerkarte befindet.

### <a name="reduced-chrome"></a>Einfach halten

Vermeiden Sie es, auf einer Registerkarte mehrere Panels zu erstellen, Navigationsebenen hinzuzufügen oder zu fordern, dass Benutzer auf einer Registerkarte sowohl vertikal als auch horizontal scrollen. Versuchen Sie also, keine Registerkarten auf Ihrer Registerkarte zu haben.

### <a name="integration"></a>Integration

Hier finden Sie Möglichkeiten, Benutzer über die Tab-Aktivität zu informieren, indem Sie einer Unterhaltung [Adaptive Karten](../../task-modules-and-cards/what-are-cards.md#adaptive-cards) senden.

### <a name="conversational"></a>Unterhaltung

Finden Sie eine Möglichkeit, um eine Unterhaltung um eine Registerkarte zu erleichtern. Dadurch wird sichergestellt, dass Unterhaltungen auf dem Inhalt, den Daten oder dem Prozess zur Hand stehen.

### <a name="streamlined-access"></a>Optimierter Zugriff

Stellen Sie sicher, dass Sie den richtigen Personen zum richtigen Zeitpunkt Zugriff gewähren. Wenn Sie Ihren Anmeldeprozess einfach halten, können Sie keine Barrieren für Beiträge und Zusammenarbeit schaffen.

### <a name="responsiveness-to-window-sizing"></a>Reaktionsfähigkeit auf Fenstergröße

Teams können in Fenstergrößen so klein wie 720px verwendet werden, damit sichergestellt ist, dass eine Registerkarte in einem kleinen Fenster nutzbar ist, ist genauso wichtig wie die Benutzerfreundlichkeit bei sehr hohen Auflösungen.

### <a name="flat-navigation"></a>Flache Navigation

Wir bitten Entwickler nicht, Ihr gesamtes Portal einer Registerkarte hinzuzufügen. Die relativ flache Navigation hilft dabei, ein einfacheres Unterhaltungs Modell beizubehalten. In anderen Worten handelt es sich bei der Unterhaltung um eine Liste von Dingen, wie beispielsweise Arbeitsaufgaben mit drei abgelagerten Elementen oder um eine einzelne Sache wie eine spec.

Es gibt inhärente Navigationsprobleme mit der Hierarchie der tiefen Navigation in Thread-Unterhaltungen. Für eine optimale Benutzerfreundlichkeit sollte die Registerkartennavigation auf ein Minimum reduziert und wie folgt gestaltet werden:

> [!div class="checklist"]
>
> * **Öffnet ein Aufgabenmodul wie eine einzelne Arbeitsaufgabe oder Entität** . Dies schließt einen vollständigen Chat aus und ist die beste Option, um den Chat speziell für die Registerkarte und nicht für die unter Entitäten oder Bearbeitungs Erfahrungen zu halten.
>* **Öffnet ein Pseudo Dialogfeld in einem IFRAME** . Wenn Sie mit einem geschirmten Hintergrund verwendet wird, empfiehlt es sich, die hellere Farbe anstelle der Dunkelheit zu verwenden. Die `app-gray-10 at 30%` Transparenz funktioniert gut.
>* **Öffnet eine Browser Seite** .

### <a name="personality"></a>Persönlichkeit

Ihr Tab-Canvas bietet eine großartige Gelegenheit, Ihre Benutzeroberfläche zu Branden. Ihr Logo ist ein wichtiger Bestandteil ihrer Identität und ihrer Verbindung mit ihren Benutzern., stellen Sie daher sicher, dass Sie es einschließen:

> [!div class="checklist"]
>
>* Platzieren Sie Ihr Logo in der linken oder rechten Ecke oder am unteren Rand
> * Halten Sie Ihr Logo klein und unaufdringlich

Unter Einbeziehung ihrer eigenen Farben und Layouts Twill auch Hilfe bei der Kommunikation Persönlichkeit.

> [!TIP]
> Arbeiten Sie mit unserem visuellen Stil, damit Ihr Dienst sich wie ein Teil von Microsoft Teams anfühlt. *Siehe* zum Beispiel Microsoft [Teams-Farben](../../concepts/design/components/color.md)

---

## <a name="tab-layouts"></a>Registerkarten Layouts

[!INCLUDE [Tab layouts](../../includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a>Typen von Registerkarten

[!INCLUDE [Tab types](../../includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a>Höhe der Konfigurationsseiten

>[!IMPORTANT]
>Im September 2018 wurde die Höhe für die Registerkarten- [Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) erhöht, während die Breite unverändert blieb. Wenn Ihre APP für die ältere Größe ausgelegt ist, hat Ihre Registerkarten-Konfigurationsseite sehr viele vertikale Leerzeichen. Ältere Store-Apps, die von dieser Änderung ausgenommen sind, müssen sich nach der Aktualisierung an Microsoft wenden, um die neuen Dimensionen zu erfüllen.

Die Abmessungen der Registerkarten-Konfigurationsseite:


<img width="450px" title="Größen für Konfigurationsregisterkarten" src="~/assets/images/tabs/config-dialog-Contoso2.png" alt="sizes for config tabs" />


### <a name="guidelines-for-tab-configuration-page-format"></a>Richtlinien für das Seitenformat der Registerkartenkonfiguration

* Stützen Sie die minimale Höhe Ihres Inhaltsbereichs auf der Registerkarte Konfigurationsseite auf Grafikelementen mit fester Höhe.
* Berechnen Sie den verfügbaren vertikalen Raum (die Höhe des Inhaltsbereichs auf der Konfigurationsseite) mithilfe von `window.innerHeight` . Dadurch wird die Größe der, in der sich die `<iframe>` Konfigurationsseite befindet, zurückgegeben, die sich in zukünftigen Versionen ändern kann. Wenn Sie diesen Wert verwenden, wird der Inhalt automatisch an zukünftige Änderungen angepasst.
* Zuweisen von vertikalem Abstand zu den Elementen der Variablen Höhe minus was für die Elemente mit fester Höhe benötigt wird.
* Für den *Anmelde* Status vertikal und horizontal zentrieren Sie den Inhalt.
* Wenn Sie ein Hintergrundbild wünschen, benötigen Sie ein neues Bild, das an den Bereich angepasst wird (bevorzugt), oder Sie können das gleiche Bild beibehalten und zwischen folgenden Themen wählen:
  * Ausrichtung an der oberen linken Ecke.
  * Skalieren des Bilds an die Größe

Bei ordnungsgemäßer Größe sollte Ihre Registerkarten-Konfigurationsseite wie folgt aussehen:

<img width="450px" title="Neue Registerkarte "Konfiguration"" src="~/assets/images/tabs/config-dialog-Contoso.png" alt="new config tab"/>

## <a name="best-practices"></a>Bewährte Methoden

### <a name="always-include-a-default-state"></a>Immer einen Standardzustand einschließen

Schließen Sie einen Standardzustand ein, um das Einrichten von Registerkarten zu vereinfachen, auch wenn die Registerkarte konfigurierbar ist.

### <a name="deep-linking"></a>Deep-Verknüpfung

Wann immer möglich, sollten Karten und Bots einen tiefen Link zu umfangreicheren Daten in einer gehosteten RegisterkarteErstellen. Beispielsweise kann eine Karte eine Zusammenfassung der Fehlerdaten anzeigen, aber durch Klicken darauf kann der gesamte Fehler in einer Registerkarte angezeigt werden.

### <a name="naming"></a>Benennungs

In vielen Fällen wird der Name Ihrer APP zu einem großen Registerkartennamen. Sie sollten Ihre Registerkarten jedoch auch entsprechend der von Ihnen bereitgestellten Funktionen benennen.

## <a name="notifications-for-tabs"></a>Benachrichtigungen für Registerkarten

Es gibt zwei Benachrichtigungs Modi für Änderungen an Registerkarten Inhalten:

> [!div class="checklist"]
>
> * **Verwenden Sie die APP-API, um Benutzer über Änderungen zu informieren** . Diese Meldung wird im Aktivitätsfeed des Benutzers und im Deep-Link zur Registerkarte angezeigt. *Weitere Informationen finden Sie unter*  [Erstellen von Deep Links zu Inhalten und Features in Microsoft Teams](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true )
> * **Verwenden Sie einen bot** . Diese Methode wird vor allem bevorzugt, wenn der Tab-Thread gezielt ist. Das Ergebnis ist, dass die Thread-Unterhaltung der Registerkarte als kürzlich aktiviert in die Ansicht verschoben wird. Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.

  Durch das Senden einer Nachricht an einen Tab-Thread wird das Bewusstsein der Aktivität für alle Benutzer erhöht, ohne dass alle Personen explizit benachrichtigt werden. Dies ist die Sensibilisierung ohne Rauschen. Darüber hinaus `@mention`  wird bei bestimmten Benutzern die gleiche Benachrichtigung in Ihren Feed eingefügt, indem Sie Sie direkt mit dem Tab-Thread verbindet.
