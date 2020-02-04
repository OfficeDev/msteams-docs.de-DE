---
title: Entwerfen effektiver Karten
description: Beschreibt die Entwurfsrichtlinien zum Erstellen von Karten.
keywords: Teams-Entwurfsrichtlinien Referenz-Framework-Karten anpassungsfähiges Leichtgewicht
ms.openlocfilehash: 33ee0b59a3a5a1490d6e2106f8532094ed852598
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674522"
---
# <a name="designing-effective-cards"></a>Entwerfen effektiver Karten

Karten sind Aktionen-Snippets von Inhalten, die Sie einer Unterhaltung über einen bot, einen Konnektor oder eine APP hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen können Sie mit Karten mit einer Zielgruppe kommunizieren.

Mit unserem Karten Framework entfällt die Last des Designs einer voll funktionsfähigen UX. Wir haben verschiedene standardmäßige Kartentypen entwickelt, die jeweils in unsere unterstützten Plattformen passen. Dies bedeutet, dass für das Layout vollständig gesorgt ist, und Sie müssen keine unterschiedlichen Karten Iterationen auf Plattformen entwickeln. Stattdessen können Sie sich auf das Einwählen von Inhalten konzentrieren.

---

## <a name="guidelines"></a>Anleitungen

Denken Sie an eine Karte als Antwort auf eine Benutzerfrage oder eine Einstellung. Eine Karte kann auf eine direkte Frage (beispielsweise "wie viele geöffnete Fehler ich habe?") oder auf eine Bedingung (wie "eine Liste mit meinen geöffneten Fehlern an 9 Uhr täglich senden") Antworten.

> [!TIP]
> Die Verwendung eines unserer Standardkarten Typen bedeutet, dass Sie bereits wissen, dass alle Ihre Antworten auf jeder unterstützten Plattform gut gerendert werden.

Eine Karte kann eines der folgenden Elemente enthalten:<br />

[!include[Card anatomy](~/includes/design/card-image-anatomy.html)]

1. **Umschlagtext**: am besten für Chatnachrichten verwendet. Wenn Sie beispielsweise einen bot sagen möchten: "hier ist, was ich gefunden habe!" oder "time for your 1:00 News Digest" ist, wird diese Nachricht am besten im Umschlagtext angezeigt.

   Briefumschlag Text ist eine großartige Möglichkeit, um eine kleine Persönlichkeit in ihren Dienst einzufügen – denken Sie daran, Sie relativ kurz zu halten.

2. **Title**: Ihr Titel ist immer der größte Text auf Ihrer Karte. Es dient auch als "Hook", also versuchen Sie, den Titel kurz zu halten, einprägsam und einfach zu scannen.

3. Unter **Titel**: am besten für Attribution, Slogans oder als sekundäre Direktive verwendet. Diese Komponente wird direkt unter Ihrem Titel angezeigt.

4. **Bild**: Bilder skalieren, um ihren Container anzupassen. Hero Cards haben eine maximale Breite von 420px, Miniaturansichten haben eine maximale Breite von 100px, und Listenansichten ermöglichen nur Bund im Desktopmodus.

5. **Text**: am besten für nur-Text im Textkörper Ihrer Karte verwendet. Die maximale Länge hängt vom ausgewählten Kartentyp ab.

6. **Schaltflächen**: wird am besten zum Öffnen von Webseiten, Registerkarten oder zusätzlichen Chat Inhalten verwendet. Achten Sie darauf, den Text der Schaltfläche kurz zu halten.

   Sie können bis zu 6 Schaltflächen pro Karte einbeziehen, aber wir empfehlen Ihnen hier eine "Less is more"-Philosophie.

7. **Tippen**Sie auf Region: Dies ist der klickable Bereich Ihrer Karte. Die meisten Benutzer möchten automatisch auf Bilder klicken, damit Sie wissen, wo Sie tippen oder klicken sollten.

> [!TIP]
> Es ist nicht erforderlich, jedes Element in jede von Ihnen erstellte Karte einzubeziehen. Lassen Sie Ihre Inhalte ihre Elemente diktieren.

---

## <a name="types-of-cards"></a>Kartentypen

### <a name="hero"></a>Hero

Unsere größte Karte. Eignet sich am besten für Artikel, lange Beschreibungen oder Szenarien, in denen das Bild den größten Teil der Geschichte erzählt.

[!include[Card anatomy](~/includes/design/card-image-hero.html)]

### <a name="thumbnail"></a>Minaturansicht

Kurz und bündig. Diese Karten sind ideal für kurze Antworten, oder wenn Sie mehrere Karten gleichzeitig zurückgeben möchten, sodass der Benutzer aus einer Reihe von Optionen auswählen kann. Wir glauben, dass dies eine großartige Möglichkeit zum Deep Link zu einer anderen Registerkarte oder einem Webdienst ist.

[!include[Card anatomy](~/includes/design/card-image-thumbnail.html)]

### <a name="sign-in"></a>Anmelden

Bei einigen Diensten müssen sich Benutzer unabhängig von unserer Authentifizierung anmelden. In diesem Fall würden Sie eine Anmeldekarte vorlegen, bevor der Benutzer eine Verbindung mit Ihrem Dienst herstellen kann.

[!include[Card anatomy](~/includes/design/card-image-signin.html)]

> [!TIP]
> Begrenzen Sie das Vorkommen einer zusätzlichen Anmeldekarte, da Sie eine erhebliche Geschwindigkeits Beule für neue Benutzer darstellen.

---

## <a name="card-collections"></a>Kartensammlungen

Wir haben auch standardmäßige Kartentypen, die am besten verwendet werden, wenn Sie mehrere Teile des inhaltsgleich zeitig oder in schneller Folge präsentieren möchten. Zu diesem Zweck haben wir ein Karussell, einen Digest, eine Liste und eine "Bubble Merge".

### <a name="carousel"></a>Karussell

Am besten geeignet für Artikel, Shopping und Browsen durch Karten.

[!include[Card anatomy](~/includes/design/card-image-carousel.html)]

> [!TIP]
> Das Karussell ist die maximale Höhe der größten Karte. Es wird empfohlen, die gleichen Kartentypen und Inhaltsfelder zu verwenden.

### <a name="digest"></a>Digest

Eignet sich am besten für Nachrichten, Digests und immer dann, wenn der Benutzer mehrere Karten gleichzeitig anzeigen soll. Wir empfehlen die Verwendung von Miniatur Ansichtskarten für Digest.

[!include[Card anatomy](~/includes/design/card-image-digest.html)]

### <a name="lists"></a>Listen

Listen stellen eine hervorragende Möglichkeit dar, einen scannable-Objektsatz in einem der folgenden Szenarien darzustellen. Listen werden am besten für Elemente verwendet, die nicht viele Erklärungen benötigen.

[!include[Card anatomy](~/includes/design/card-image-list.html)]

### <a name="bubble-merge"></a>Blasen Zusammenführung

Einige interessante Effekte können erzielt werden, indem ein Held und mehrere Miniaturansichten schnell hintereinander gesendet werden. Diese Vorgehensweise wird empfohlen, wenn Sie ein Hauptergebnis bereitstellen möchten, aber einige weitere verwandte Elemente enthalten sollen.

[!include[Card anatomy](~/includes/design/card-image-bubble-merge.html)]

---

## <a name="best-practices"></a>Bewährte Methoden

### <a name="keep-the-noise-down"></a>Rauschen nach unten aufbewahren

Es ist ganz einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald die Karten aus dem Blickfeld geraten, werden Sie nicht mehr so nützlich. Versuchen Sie, sich auf das Wesentliche zu beschränken. Dies gilt insbesondere für einen Kanal, in dem Benutzer eine geringere Toleranz für das als "Rauschen" wahrgenommene haben.

### <a name="test-on-mobile"></a>Test auf mobilen Geräten

Mobile Umgebungen sind Platz-und Bandbreitenabhängig, daher sollten Sie vorsichtig sein, wenn Sie überdimensionierte Bilder und große Datensätze in Listen und Karussells einschließen. Außerdem werden Titel breiten und Textlängen auf dem Mobiltelefon abgeschnitten, sodass dies eine andere Sache ist, die Sie im Auge behalten.

### <a name="check-your-graphics"></a>Überprüfen der Grafiken

Grafiken werden skaliert, daher sollten Sie Sie auf allen Plattformen in einer Vorschau anzeigen.

### <a name="avoid-including-text-in-a-graphic"></a>Vermeiden des Einbindens von Text in eine Grafik

Alle Elemente, die von einem Benutzer gelesen werden müssen, sollten in ein Textfeld eingeschlossen werden. Wenn ein Bild dynamisch skaliert wird, kann jeder Text, den Sie einer Grafik hinzufügen, nicht mehr verständlich sein.

### <a name="use-mentions-if-you-want-the-attention-of-specific-users"></a>Verwenden von Erwähnungen, wenn Sie die Aufmerksamkeit bestimmter Benutzer wünschen

> [!NOTE]
> Die Erwähnung der Unterstützung in Cards wird derzeit nur in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) unterstützt.

Erwähnungen sind eine hervorragende Möglichkeit, bestimmte Benutzer in einem Team-oder Gruppenchat zu benachrichtigen. Sie können eine Erwähnung in der Karte in Szenarien wie, eine Aufgabe, die einem Benutzer zugewiesen ist oder Lob an einen Teamkollegen hinzufügen. Hier erfahren Sie, wie Sie in Karten auf der [Seite Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md)Erwähnungen hinzufügen. 
