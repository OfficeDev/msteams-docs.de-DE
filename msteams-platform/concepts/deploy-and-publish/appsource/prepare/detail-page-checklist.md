---
title: Erstellen einer tollen App-Detailseite
description: Beschreibt, welche Seite mit den App-Details erforderlich ist
keywords: Veröffentlichen von Office-Veröffentlichungsrichtlinien für Microsoft Teams AppSource Inhalt
ms.openlocfilehash: 4a98cca7b1ddd87d79e38d863fd3868171b7749e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674177"
---
# <a name="build-a-great-app-details-page"></a>Erstellen einer tollen App-Detailseite

Die Detailseite ist der erste Eindruck ihrer app. Jedes Element auf ihrer Detailseite kann verwendet werden, um Ihre Ziel-und Laufwerk Downloads zu vermitteln – berücksichtigen Sie, wie Sie Ihre APP auf einem begrenzten Platz präsentieren möchten. Hier finden Sie einige Tipps und Tricks, mit denen Sie Ihre Benutzer einbinden können, bevor Sie Ihre APP sogar installieren.

> [!NOTE]
> Stellen Sie sicher, dass Ihre APP-Informationen unserem [AppSource-Leitfaden für die Erstellung einer effektiven Store-Auflistung](/office/dev/store/create-effective-office-store-listings)folgen.

## <a name="app-name"></a>App-Name

Der Name einer APP spielt eine wichtige Rolle darin, wie Benutzer Sie im AppSource App Store entdecken. Der Kurzname Ihrer APP wird auf der Detailseite angezeigt.

**Aufgaben:**

* Wählen Sie einen einfachen, einprägsamen Namen aus, der darauf hinweist, was Ihre APP tut.
* Unverwechselbar sein.

**Verbote**

* Verwenden Sie keine generischen Ausdrücke oder Namen, die den vorhandenen APP-Namen ähneln.
* Verwenden Sie nicht "Teams", "Microsoft" oder "App" in Ihrem APP-Namen.
![App Name Store View](~/assets/images/store-detail-page/AppName-02.png)
![App Name appstudio View](~/assets/images/store-detail-page/AppName-01.png)

## <a name="color-icon"></a>Farbsymbol

Dies ist eines der ersten Elemente, die Benutzern angezeigt werden. Es sollte attraktiv und Blickfang beim Scrollen durch den App Store sein. Stellen Sie sicher, dass es einen guten ersten Eindruck und kommuniziert auch Ihre Marke das Bild und den Zweck. AppSource hat weitere Tipps zum [Erstellen einer konsistenten visuellen Identität](/office/dev/store/create-effective-office-store-listings#create-a-consistent-visual-identity).

![App Icon Store](~/assets/images/store-detail-page/AppIcon-02.png)
![App-Symbol appstudio-Ansicht](~/assets/images/store-detail-page/AppIcon-01.png)

## <a name="outline-icon"></a>Gliederungssymbol

Dies wird in Messaging Erweiterungen verwendet, die vom Benutzer und im linken Navigationsmenü als Favorit gekennzeichnet sind. Stellen Sie sicher, dass Sie einfach und erkennbar ist.

![App-Symbol Gliederungs](~/assets/images/store-detail-page/AppIconOutline-02.png)
![Speicheransicht App-Symbol Gliederung appstudio Ansicht](~/assets/images/store-detail-page/AppIconOutline-01.png)

## <a name="short-description"></a>Kurzbeschreibung

Dies ist eine präzise Zusammenfassung Ihrer APP. Diese soll originell und ansprechend und an Ihre Zielgruppe gerichtet sein. Versuchen Sie im Idealfall, Ihre Lösung und ihren Wert für Ihre Benutzer in einem Satz zu beschreiben.

**Aufgaben:**

* Die wichtigsten Informationen kommen an erster Stelle.
* Schließen Sie Stichwörter ein, nach denen Kunden wahrscheinlich suchen.

**Verbote**

* Wiederholen Sie den Titel nicht.
* Verwenden Sie keine Fachsprache oder spezielle Terminologie – Sie können nicht davon ausgehen, dass die Benutzer wissen, wonach Sie suchen sollen.

![Kurze Beschreibung der Store-Ansicht](~/assets/images/store-detail-page/ShortDescription-02.png)

Hier ist eine Ansicht in [App Studio](https://aka.ms/InstallTeamsAppStudio):

![Kurze Beschreibung appstudio-Ansicht](~/assets/images/store-detail-page/ShortDescription-01.png)

## <a name="long-description"></a>Lange Beschreibung

Dadurch werden die Hauptfeatures der Lösung, die Probleme, die gelöst werden, und die Zielgruppe in einer interessanten Erzählung hervorgehoben. Zeichnen Sie Ihre Zielgruppe mit dem ersten Satz, indem Sie die eindeutigen Features Ihrer APP mitteilen. Ihre Beschreibung muss unter 4000 Zeichen liegen. Beachten Sie, dass die meisten Benutzer nur zwischen 300 und 500 Wörter lesen können.

>[!IMPORTANT]
> Stellen Sie sicher, dass Sie die Beschreibungen, die Sie in Ihrem AppSource-Eintrag geschrieben haben, genau in Ihr Manifest kopieren – die Werte müssen übereinstimmen. In Microsoft Teams werden nur die Beschreibungen verwendet, die Sie im Manifest bereitgestellt haben.

**Aufgaben:**

* Verwenden Sie die [Abschlag Formatierung](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) , um Ihre Beschreibung zu beleuchten.  
* Auflisten von Features, die Leser beim Scannen Ihrer Beschreibung unterstützen.
* Verwenden Sie Active Voice, und sprechen Sie direkt mit Benutzern.
* Verwenden Sie Aufzählungspunkte, um ihre Features aufzulisten.
* Fügen Sie einen Hilfe-oder Support Link hinzu, damit Ihre Benutzer wissen, wie Sie Sie erreichen können, wenn Sie Fragen haben.

**Verbote**

* Stellen Sie nicht zu viele Stichwörter in Ihre Beschreibung ein – Sie lenken ab und helfen der Auffindbarkeit Ihrer APP nicht.

![App Long Description Store-Ansicht](~/assets/images/store-detail-page/LongDescription-02.png)

Hier ist eine Ansicht in [App Studio](https://aka.ms/InstallTeamsAppStudio):

![App Long Description appstudio-Ansicht](~/assets/images/store-detail-page/LongDescription-01.png)

## <a name="screenshots"></a>Screenshots

Die im [Verkäuferdashboard](https://sellerdashboard.microsoft.com/Registration) hochgeladenen Screenshots werden sowohl in [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) als auch in Ihrer APP-Auflistung im Teams-Client angezeigt. Sie bieten eine visuelle Vorschau Ihrer APP zusammen mit Ihrer APP-Beschreibung.
Sie können ein bis fünf Screenshots zur Verfügung stellen, die als PNG-, JPG-oder GIF-Dateien formatiert sind. Screenshots sollten 1366 x 768 Pixel mit einer maximalen Größe von 1024 KB sein.

**Aufgaben:**

* Konzentrieren Sie sich auf die Hervorhebung aller Funktionen Ihrer APP.
* Inhalte sollten Ihre APP genau darstellen.
* Der Text sollte gut ausgefüllt sein, ohne übertrieben zu sein.
* Sie können Ihre Screenshots mit einer Hintergrundfarbe umgeben und Marketinginhalte hinzufügen, die dem [Freshdesk](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) -Beispiel ähneln; Allerdings werden die Dimensionen nicht aus dem Screenshot allein, sondern auch das Gesamtbild.

<img width="800px" title="Freshdesk Screenshot" src="~/assets/images/freshdesk.png" />

**Verbote**

* Zeigen Sie keine bestimmten Geräte wie Telefone oder Laptops an.
* Zeigen Sie keine Chrome/UI außerhalb Ihrer APP an.
* Erfassen Sie keine Teams oder Browser-Benutzeroberfläche in ihren Screenshots.
* Schließen Sie keine Mock-ups ein, die die tatsächliche Benutzeroberfläche Ihrer Apps ungenau widerspiegeln, beispielsweise das Anzeigen Ihrer Website anstelle der Registerkarte "Teams".

Weitere bewährte Methoden *finden Sie unter*: [Crafting Effective AppSource Store Images](/office/dev/store/craft-effective-appsource-store-images).

## <a name="videos"></a>Videos

Wenn ein Bild mehr als tausend Worte sagt, ist ein Video mehr als tausend Bilder Wert. Videos sind die effektivste Möglichkeit, um die Vorteile der Verwendung Ihrer APP zu kommunizieren. Sie wird auf der Seite mit den App-Details vor alle Screenshots gesetzt. Stellen Sie sicher, dass Sie darüber sprechen, wie Ihre APP funktioniert, was damit erreicht werden kann, welche Vorteile die Anwendung hat und wer Sie ist. Denken Sie daran, Ihre Präsentation kurz und bündig zu halten – irgendwo zwischen 30-90 Sekunden.

## <a name="learn-more"></a>Weitere Informationen

[Prüfliste für App-Übermittlung](~/concepts/deploy-and-publish/appsource/publish.md).  
[Erstellen Sie ein App-Paket für Ihre Microsoft Teams-App](~/concepts/build-and-test/apps-package.md).  
[Verwenden Sie das Partner Center, um Ihre Lösung an AppSource zu übermitteln](/office/dev/store/use-partner-center-to-submit-to-appsource).
