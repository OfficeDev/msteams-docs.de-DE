---
title: Entwurfsrichtlinien für Registerkarten
description: Beschreibt die Richtlinien zum Erstellen von Registerkarten für Inhalt und Zusammenarbeit.
keywords: Teams-Entwurfsrichtlinien Referenz-Framework-Registerkartenkonfiguration
ms.openlocfilehash: adf86678a42e2267af00734e1ef85efced882488
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674060"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a>Inhalte und Unterhaltungen auf einmal mithilfe von Registerkarten

> [!Important]
> **Registerkarten auf mobilen Clients**
>
> Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) , wenn Sie Ihre Registerkarten erstellen. Wenn Ihre Registerkarte die Authentifizierung verwendet, müssen Sie Ihr Microsoft Teams-JavaScript-SDK auf Version 1.4.1 oder höher aktualisieren, oder die Authentifizierung schlägt fehl.
>
> **Persönliche Registerkarten (statisch) auf mobilen Geräten:**
>
> * Statische Registerkarten (persönliche APP) stehen in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)zur Verfügung.
> * Stellen Sie beim Erstellen der statischen Registerkarten sicher, dass Sie den [Anweisungen für Tabs auf mobilen](~/tabs/design/tabs-mobile.md)
>
> **Registerkarten für Kanal/Gruppe (konfigurierbar) auf mobilen Geräten:**
>
> * Mobile Clients zeigen nur Registerkarten mit einem Wert für `websiteUrl`an. Wenn die Registerkarte auf den mobilen Teams-Clients angezeigt werden soll, müssen Sie den Wert von `websiteUrl`festlegen.
> * Das standardmäßig geöffnete Verhalten auf mobilen Geräten ist das `websiteUrl`öffnen außerhalb von Browser mithilfe von. Wenn Sie für apps, die im öffentlichen APP-Speicher veröffentlicht werden, die Kanal Registerkarte standardmäßig in Microsoft Teams öffnen möchten, befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md), und wenden Sie sich an Ihren Supportmitarbeiter, um eine weiße Liste zu fordern.

Registerkarten sind Ansichtsbilder, die Sie zum Freigeben von Inhalten, halten von Unterhaltungen und Hosten von Drittanbieterdiensten verwenden können, die alle innerhalb des organischen Workflows eines Teams liegen. Wenn Sie eine Registerkarte in Microsoft Teams erstellen, wird Ihre Webanwendungs-Front-und-Mitte platziert, wo Sie leicht von wichtigen Unterhaltungen aus zugänglich ist.

## <a name="guidelines"></a>Anleitungen

Auf einer Registerkarte "gut" sollten die folgenden Merkmale angezeigt werden:

### <a name="focused-functionality"></a>Fokussierte Funktionalität

Registerkarten funktionieren am besten, wenn Sie erstellt werden, um eine bestimmte Anforderung zu erfüllen. Konzentrieren Sie sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge der Daten, die für den Kanal relevant ist, in dem sich die Registerkarte befindet.

### <a name="reduced-chrome"></a>Reduziertes Chrom

Vermeiden Sie es, mehrere Bereiche auf einer Registerkarte zu erstellen, Navigationsebenen hinzuzufügen oder Benutzer zu verpflichten, sowohl vertikal als auch horizontal in einer Registerkarte zu scrollen. In anderen Worten: versuchen Sie nicht, Registerkarten auf Ihrer Registerkarte zu haben.

> [!TIP]
> Vermeiden Sie es, mehrere Bereiche auf einer Registerkarte zu erstellen, Navigationsebenen hinzuzufügen oder Benutzer zu verpflichten, sowohl vertikal als auch horizontal in einer Registerkarte zu scrollen.

### <a name="integration"></a>Integration

Hier finden Sie Möglichkeiten, Benutzer über die Tab-Aktivität zu informieren, indem Sie beispielsweise Karten für eine Unterhaltung veröffentlichen.

### <a name="conversational"></a>Gesprächs

Finden Sie eine Möglichkeit, um eine Unterhaltung um eine Registerkarte zu erleichtern. Dadurch wird sichergestellt, dass Unterhaltungen auf dem Inhalt, den Daten oder dem Prozess zur Hand stehen.

### <a name="streamlined-access"></a>Optimierter Zugriff

Stellen Sie sicher, dass Sie den richtigen Personen zum richtigen Zeitpunkt Zugriff gewähren. Wenn Sie Ihren Anmeldeprozess einfach halten, können Sie keine Barrieren für Beiträge und Zusammenarbeit schaffen.

### <a name="personality"></a>Persönlichkeit

Ihr Tab-Canvas bietet eine gute Gelegenheit, Ihre Benutzeroberfläche zu Branden. Integrieren Sie Ihre eigenen Logos, Farben und Layouts, um Persönlichkeit zu vermitteln.

Ihr Logo ist ein wichtiger Bestandteil ihrer Identität und eine Verbindung mit ihren Benutzern. Achten Sie darauf, Sie einzubeziehen.

* Platzieren Sie Ihr Logo in der linken oder rechten Ecke oder am unteren Rand
* Halten Sie Ihr Logo klein und unaufdringlich

> [!TIP]
> Arbeiten Sie mit unserem visuellen Stil, damit Ihr Dienst sich wie ein Teil von Microsoft Teams anfühlt.

---

## <a name="tab-layouts"></a>Registerkarten Layouts

[!include[Tab layouts](~/includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a>Typen von Registerkarten

[!include[Tab types](~/includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a>Höhe der Konfigurationsseiten

>[!NOTE]
>Im September 2018 wurde die Höhe für die Registerkarten- [Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) erhöht, während die Breite unverändert blieb. Wenn Ihre APP für die ältere Größe ausgelegt ist, hat Ihre Registerkarten-Konfigurationsseite sehr viele vertikale Leerzeichen. Ältere Store-Apps, die von dieser Änderung ausgenommen sind, müssen sich nach der Aktualisierung an Microsoft wenden, um die neuen Dimensionen zu erfüllen.

Die Abmessungen der Registerkarten-Konfigurationsseite:

<img width="450px" title="Größen für Konfigurationsregisterkarten" src="~/assets/images/tabs/config-dialog-Contoso2.png" />

### <a name="guidelines-for-tab-configuration-page-format"></a>Richtlinien für das Seitenformat der Registerkartenkonfiguration

* Stützen Sie die minimale Höhe Ihres Inhaltsbereichs auf der Registerkarte Konfigurationsseite auf Grafikelementen mit fester Höhe.
* Berechnen Sie den verfügbaren vertikalen Raum (die Höhe des Inhaltsbereichs auf der Konfigurations `window.innerHeight`Seite) mithilfe von. Dadurch wird die Größe der, `<iframe>` in der sich die Konfigurationsseite befindet, zurückgegeben, die sich in zukünftigen Versionen ändern kann. Wenn Sie diesen Wert verwenden, wird der Inhalt automatisch an zukünftige Änderungen angepasst.
* Zuweisen von vertikalem Abstand zu den Elementen der Variablen Höhe minus was für die Elemente mit fester Höhe benötigt wird.
* Für den *Anmelde* Status vertikal und horizontal zentrieren Sie den Inhalt.
* Wenn Sie ein Hintergrundbild wünschen, benötigen Sie ein neues Bild, das an den Bereich angepasst wird (bevorzugt), oder Sie können das gleiche Bild beibehalten und zwischen folgenden Themen wählen:
  * Ausrichtung an der oberen linken Ecke.
  * Skalieren des Bilds an die Größe

Bei ordnungsgemäßer Größe sollte Ihre Registerkarten-Konfigurationsseite wie folgt aussehen:

<img width="450px" title="Neue Registerkarte "Konfiguration"" src="~/assets/images/tabs/config-dialog-Contoso.png" />

## <a name="best-practices"></a>Bewährte Methoden

### <a name="always-include-a-default-state"></a>Immer einen Standardzustand einschließen

Schließen Sie einen Standardzustand ein, um das Einrichten von Registerkarten zu vereinfachen, auch wenn die Registerkarte konfigurierbar ist.

### <a name="deep-linking"></a>Deep-Verknüpfung

Wann immer möglich, sollten Karten und Bots einen tiefen Link zu umfangreicheren Daten in einer gehosteten RegisterkarteErstellen. Beispielsweise kann eine Karte eine Zusammenfassung der Fehlerdaten anzeigen, aber durch Klicken darauf kann der gesamte Fehler in einer Registerkarte angezeigt werden.

### <a name="naming"></a>Benennungs

In vielen Fällen kann der Name Ihrer APP einen großen Namen für die Registerkarte bilden. Sie sollten Ihre Registerkarten jedoch entsprechend der von Ihnen bereitgestellten Funktionen benennen.
