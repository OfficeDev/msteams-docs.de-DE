---
title: Referenz zu Entwurfsrichtlinien
description: Beschreibt die Richtlinien für das Entwerfen einer persönlichen app.
keywords: Teams-Entwurfsrichtlinien – Referenzrahmen für persönliche apps
ms.openlocfilehash: f66691234149afa56a6753dd51379c9f2355318e
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455499"
---
# <a name="personal-apps"></a>Persönliche Apps

> [!NOTE]
> Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Microsoft Teams unterstützt. Beachten Sie beim Erstellen von Registerkarten für mobile Plattformen die [Anleitungen für Registerkarten auf mobilen Geräten](../../tabs/design/tabs-mobile.md) .

Eine persönliche APP ist eine Microsoft Teams-Anwendung mit einem persönlichen Bereich.  Als App-Entwickler haben Sie die Möglichkeit, eine Version Ihrer APP bereitzustellen, die sich auf Interaktionen mit einem einzelnen Benutzer konzentriert. Es kann sich um einen [Unterhaltungs bot](../../bots/what-are-bots.md) handeln, der sich mit einem Benutzer oder einer [persönlichen Registerkarte](../../tabs/what-are-tabs.md) , die ein eingebettetes Weberlebnis bereitstellt, in eins-zu-eins-Gesprächen beschäftigt. Mit persönlichen Apps können Benutzer Ihre ausgewählten Inhalte an einer Stelle anzeigen. Im folgenden Screenshot ist Contoso eine persönliche App im Flyout für persönliche apps.

![Bild des Menüs "App-Überlauf"](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a>Anleitungen

Eine persönliche app enthält normalerweise die folgenden Registerkarten:

### <a name="your-tab"></a>Ihre Registerkarte

Hier werden Ihre Benutzer alle Ihre Inhalte sehen. Es ist Ihr persönlicher Raum. Die Registerkarte kann als Liste, als Raster, als Spalten oder als einzelne Leinwand angeordnet werden... Was auch immer am besten für Ihre Anwendung geeignet ist. Weitere Informationen zum Entwerfen effektiver Registerkarten finden Sie unter: [Tabs Design](../../tabs/design/tabs.md).

Da auf dieser Registerkarte Elemente aus mehreren Kanälen angezeigt werden können, sollte jedes Element ein eigenes Team, einen eigenen Kanal und eine eigene Registerkarte anzeigen, damit der Benutzer leicht erkennen kann, woher er stammt.

![Registerkarte "persönliche Vorgänge"](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a>Neuesten

Auf der Registerkarte " **zuletzt** verwendet" kann ein Benutzer alle zuletzt in Ihrer APP angezeigten Elemente durchsuchen. Er wird in chronologischer Reihenfolge (von den meisten bis zuletzt jüngsten) aufgeführt. Durch Klicken auf ein Element in dieser Liste wird der Benutzer zum Kanal und zur Registerkarte des Elements navigiert.

![Registerkarte "zuletzt verwendet"](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a>Alle

Hierbei handelt es sich um eine Liste aller Registerkarten in der Organisation der Person (auf die Sie Zugriff haben, auf jeden Fall). Das heißt, Sie werden überall angezeigt, wo die APP verwendet wird. Wie bei der **letzten** Registerkarte wird der Benutzer durch Auswählen eines Elements in der Liste direkt auf den entsprechenden Kanal und die entsprechende Registerkarte gebracht.

### <a name="bot"></a>Bot

Ein Bot ist nicht erforderlich, ist aber eine großartige Möglichkeit, direkt und privat mit ihren Benutzern zu kommunizieren. Die Benachrichtigung ist eine der wichtigsten Funktionen einer persönlichen APP, und welche bessere Möglichkeit gibt es, als bei der direkten Kommunikation zu Benachrichtigen?

Bots liefern Nachrichten in Form von Karten, die spezifische Informationen (wie eine Warnung, dass neue Inhalte verfügbar sind) oder umfassende Updates (wie eine tägliche to-do-Liste) bereitstellen können. Weitere Informationen zum Entwerfen effektiver Bots finden Sie unter: [bot-Design](../../bots/design/bots.md).

![Bot-Begrüßung](~/assets/images/Personal-apps-Bot.png)

### <a name="help-and-settings"></a>Hilfe und Einstellungen

Mithilfe von Inhalten können Benutzer die Nuancen ihrer App ermitteln. Fügen Sie eine Registerkarte **Einstellungen** hinzu, damit Sie Sie weiter anpassen können.

### <a name="about"></a>Info

Schließen Sie die Registerkarte **Info** ein, um Informationen wie Versionsnummer, Funktionen, Datenschutz und Berechtigungs Links bereitzustellen.

## <a name="best-practices"></a>Bewährte Methoden

### <a name="communicate-directly-with-your-users"></a>Direkte Kommunikation mit ihren Benutzern

Verwenden Sie einen bot, um Benutzer über Änderungen und neue Features zu informieren.

### <a name="customize-your-tabs"></a>Passen Sie Ihre Registerkarten an...

Fühlen Sie sich frei, weitere Registerkarten hinzuzufügen, die Ihre Benutzer bei der Ausführung bestimmter Aufgaben unterstützen sollen.

### <a name="and-make-them-relevant-to-every-user"></a>... und Sie für jeden Benutzer relevant zu machen.

Jede Registerkarte, die Sie in Ihrem App-Manifest deklarieren, ist für alle Benutzer sichtbar. Wenn es sich bei Ihrer persönlichen App beispielsweise um ein Spesen abrechnungstool handelt, das sowohl von Managern als auch von Mitarbeitern verwendet wird, sollte eine **Genehmigungs** Registerkarte Inhalte bereitstellen, die für beide Rollen sinnvoll sind.
