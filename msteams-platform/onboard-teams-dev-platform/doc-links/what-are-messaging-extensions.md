---
title: Was sind Messaging-Erweiterungen?
author: clearab
description: Eine Übersicht über Messaging-Erweiterungen auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3e80c965fb8cb2c4da2af6f6bf0709e7c8bd1d88
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652000"
---
# <a name="what-are-messaging-extensions"></a>Was sind Messaging-Erweiterungen?

Messaging-Erweiterungen ermöglichen Benutzern die Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client. Sie können Aktionen in einem externen System aus dem Bereich zum Verfassen von Nachrichten, dem Befehlsfeld oder direkt aus einer Nachricht durchsuchen oder initiieren. Sie können dann die Ergebnisse dieser Interaktion an den Microsoft Teams-Client zurücksenden, normalerweise in Form einer reich formatierten Karte.

Der folgende Screenshot zeigt die Orte, von denen aus Messaging Erweiterungen aufgerufen werden können.

![Speicherorte für Messaging Erweiterungs Aufrufe](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="user-scenarios"></a>Benutzerszenarien

**Szenario:** Ich benötige ein externes System, um etwas zu tun, und ich möchte, dass das Ergebnis der Aktion an meine Unterhaltung zurückgesendet wird. \
**Beispiel:** Reservieren Sie eine Ressource, und lassen Sie den Kanal wissen, für welchen Tag/welche Zeit Sie ihn reserviert haben.

**Szenario:** Ich muss etwas in einem externen System finden, und ich möchte die Ergebnisse mit meiner Unterhaltung teilen. \
**Beispiel:**  Suchen Sie in Azure DevOps nach einer Arbeitsaufgabe, und teilen Sie Sie mit der Gruppe als Adaptive Karte.

**Szenario:** Ich muss eine komplexe Aufgabe mit mehreren Schritten (oder vielen Informationen) in einem externen System ausführen, und die Ergebnisse sollten für eine Unterhaltung freigegeben werden. \
**Beispiel:** Erstellen Sie einen Fehler in Ihrem Tracking System basierend auf einer Microsoft Teams-Nachricht, weisen Sie diesen Fehler Bob zu, und senden Sie dann eine Karte an den Unterhaltungsthread mit den Details des Fehlers.

## <a name="how-do-messaging-extensions-work"></a>Wie funktionieren Messaging-Erweiterungen?

Eine Messaging Erweiterung besteht aus einem Webdienst, den Sie hosten, und dem App-Manifest, das definiert, wo Ihr Webdienst aus dem Microsoft Teams-Client aufgerufen werden kann. Sie nutzen das Messaging-Schema und das sichere Kommunikationsprotokoll des Bot-Frameworks, so dass Sie Ihren Webdienst auch als Bot im Bot-Framework registrieren müssen. Sie können den Webdienst zwar vollständig manuell erstellen, aber es wird empfohlen, dass Sie das [bot Framework SDK](https://github.com/microsoft/botframework) nutzen, um das Arbeiten mit dem Protokoll zu vereinfachen.

Im App-Manifest für Ihre Microsoft Teams-app definieren Sie eine einzelne Messaging Erweiterung mit bis zu zehn unterschiedlichen Befehlen. Jeder Befehl definiert einen Typ (Aktion oder Suche) und die Speicherorte im Client, aus dem er aufgerufen werden kann (Verfassen des Nachrichtenbereichs, der Befehlsleiste und/oder der Nachricht). Nachdem der Webdienst aufgerufen wurde, erhält er eine HTTPS-Nachricht mit einer JSON-Nutzlast einschließlich aller relevanten Informationen. Sie Antworten mit einer JSON-Nutzlast, sodass der Microsoft Teams-Client wissen kann, welche Interaktion als nächstes aktiviert werden soll.

## <a name="types-of-messaging-extensions"></a>Typen von Messaging Erweiterungen

Der Typ des Messaging Erweiterungs Befehls definiert die Benutzeroberflächenelemente und Interaktions Flüsse, die Ihrem Webdienst zur Verfügung stehen. Einige Interaktionen, wie Authentifizierung und Konfiguration, stehen für beide Befehlstypen zur Verfügung.

### <a name="action-commands"></a>Aktionsbefehle

Mit Aktions Befehlen können Sie Ihren Benutzern ein modales Popup-Fenster zum Erfassen oder Anzeigen von Informationen präsentieren. Wenn Sie das Formular übermitteln, kann Ihr Webdienst Antworten, indem er eine Nachricht direkt in die Unterhaltung einfügt, oder indem er eine Nachricht in den Bereich zum Verfassen von Nachrichten einfügt und es dem Benutzer ermöglicht, die Nachricht zu übermitteln. Sie können sogar mehrere Formulare für komplexere Workflows miteinander verketten.

Sie können aus dem Bereich zum Verfassen von Nachrichten, dem Befehlsfeld oder aus einer Nachricht ausgelöst werden. Wenn Sie aus einer Nachricht aufgerufen wird, enthält die anfängliche JSON-Nutzlast, die an Ihren bot gesendet wird, die gesamte Nachricht, von der Sie aufgerufen wurde.

![Befehls Aufgabenmodul für Messaging Erweiterungsaktionen](~/assets/images/task-module.png)

### <a name="search-commands"></a>Suchbefehle

Suchbefehle ermöglichen es Ihren Benutzern, ein externes System nach Informationen zu durchsuchen (entweder manuell über ein Suchfeld oder durch Einfügen eines Links zu einer überwachten Domäne in den Nachrichtenbereich „Verfassen“) und anschließend die Ergebnisse der Suche in eine Nachricht einzufügen. Im einfachsten Suchbefehlsfluss enthält die anfängliche „invoke“-Nachricht die vom Benutzer übermittelte Suchzeichenfolge. Sie antworten mit einer Liste von Karten und Kartenvorschauen. Der Microsoft Teams-Client rendert die Kartenvorschau in einer Liste, aus der der Endbenutzer auswählen kann. Wenn der Benutzer eine Karte auswählt, wird sie in voller Größe in den Nachrichtenbereich „Verfassen“ eingefügt.

Sie können aus dem Nachrichtenbereich "Verfassen" oder aus dem Befehlsfeld ausgelöst werden. Im Gegensatz zu Aktions Befehlen können Sie nicht aus einer Nachricht ausgelöst werden.

![Suchbefehl für Messaging Erweiterung](~/assets/images/search-extension.png)

### <a name="link-unfurling"></a>Entfalten von Links

Sie können den Dienst auch aufrufen, wenn eine URL im Bereich zum Verfassen von Nachrichten eingefügt wird. Mit dieser Funktion, die als **Link-Entfaltung**bezeichnet wird, können Sie abonnieren, um einen Aufruf zu erhalten, wenn URLs, die eine bestimmte Domäne enthalten, in den Bereich zum Verfassen von Nachrichten eingefügt werden. Ihr Webdienst kann die URL in eine detaillierte Karte "aufteilen" und bietet mehr Informationen als die standardmäßige Website-Vorschau Karte. Sie können sogar Schaltflächen hinzufügen, damit Benutzeraktionen ausführen können, ohne Teams zu verlassen.

## <a name="get-started"></a>Erste Schritte

Können Sie mit dem Erstellen beginnen? Versuchen Sie es mit einem unserer Schnellstarts:

### <a name="c"></a>C#
* [Messaging-Erweiterung mit Aktions basierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
* [Messaging-Erweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)

### <a name="javascript"></a>JavaScript
* [Messaging-Erweiterung mit Aktions basierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
* [Messaging-Erweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

## <a name="learn-more"></a>Weitere Informationen

* [Erstellen einer Nachrichten-Erweiterung](~/messaging-extensions/how-to/create-messaging-extension.md)
* [Aktions-Messaging-Erweiterungs Befehl definieren](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Definieren des Befehls für die Suchnachrichten Erweiterung](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Planen Ihrer APP](../../concepts/extensibility-points.md)
* [Erstellen Ihrer APP](../../concepts/building-an-app.md)
* [Veröffentlichen Ihrer APP](../../concepts/deploy-and-publish/overview.md)
