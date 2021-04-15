---
title: Messaging-Erweiterungen
author: clearab
description: Übersicht über Messagingerweiterungen auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2d82202c72584927fc705813151d91510a7f12c9
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696753"
---
# <a name="messaging-extensions"></a>Messaging-Erweiterungen

Messagingerweiterungen ermöglichen benutzern die Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client. Sie können Aktionen in einem externen System aus dem Bereich "Nachricht verfassen", dem Befehlsfeld oder direkt aus einer Nachricht durchsuchen oder initiieren. Sie können die Ergebnisse dieser Interaktion in Form einer reicher formatierten Karte an den Microsoft Teams-Client senden. Dieses Dokument bietet eine Übersicht über die Messagingerweiterung, Aufgaben, die in verschiedenen Szenarien ausgeführt werden, das Arbeiten mit Messagingerweiterungen, Aktions- und Suchbefehlen sowie das Lösen von Verknüpfungen.

In der folgenden Abbildung werden die Speicherorte angezeigt, an denen Messagingerweiterungen aufgerufen werden:

![Messagingerweiterung ruft Speicherorte auf](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="scenarios-where-messaging-extensions-are-used"></a>Szenarien, in denen Messagingerweiterungen verwendet werden

| Szenario | Beispiel |
|:-----------------|:-----------------|
|Sie möchten, dass ein externes System eine Aktion und das Ergebnis der Aktion an Ihre Unterhaltung zurücksennen.|Reservieren Sie eine Ressource, und ermöglichen Sie dem Kanal, den reservierten Zeitfenster zu kennen.|
|Sie möchten etwas in einem externen System finden und die Ergebnisse für die Unterhaltung freigeben.|Suchen Sie nach einer Arbeitsaufgabe in Azure DevOps, und geben Sie sie für die Gruppe als adaptive Karte frei.|
|Sie möchten eine komplexe Aufgabe ausführen, die mehrere Schritte oder viele Informationen in einem externen System enthält, und die Ergebnisse für eine Unterhaltung freigeben.|Erstellen Sie einen Fehler in Ihrem Nachverfolgungssystem basierend auf einer #A0 , weisen Sie ihn Bob zu, und senden Sie eine Karte mit den Details des Fehlers an den Unterhaltungsthread.|

## <a name="understand-how-messaging-extensions-work"></a>Verstehen der Funktionsweise von Messagingerweiterungen

Eine Messagingerweiterung besteht aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, von wo aus Ihr Webdienst im Microsoft Teams-Client aufgerufen wird. Der Webdienst nutzt das Messagingschema und das sichere Kommunikationsprotokoll des Bot Framework, sodass Sie Ihren Webdienst als Bot im Bot Framework registrieren müssen. 

> [!NOTE]
> Obwohl Sie den Webdienst manuell erstellen können, verwenden Sie [bot Framework SDK,](https://github.com/microsoft/botframework) um mit dem Protokoll zu arbeiten.

Im App-Manifest für Microsoft Teams-App wird eine einzelne Messagingerweiterung mit bis zu zehn verschiedenen Befehlen definiert. Jeder Befehl definiert einen Typ, z. B. Aktion oder Suche, und die Speicherorte im Client, von dem aus er aufgerufen wird. Die aufruften Speicherorte sind verfassen Nachrichtenbereich, Befehlsleiste und Nachricht. Beim Aufrufen empfängt der Webdienst eine HTTPS-Nachricht mit einer JSON-Nutzlast, die alle relevanten Informationen enthält. Reagieren Sie mit einer JSON-Nutzlast, sodass der Teams-Client die nächste zu aktivierende Interaktion kennen kann. 

## <a name="types-of-messaging-extension-commands"></a>Typen von Messagingerweiterungsbefehlen

Es gibt zwei Arten von Messagingerweiterungsbefehlen, Aktionsbefehl und Suchbefehl. Der Befehlstyp für die Messagingerweiterung definiert die Benutzeroberflächenelemente und Interaktionsflüsse, die für Ihren Webdienst verfügbar sind. Einige Interaktionen, z. B. Authentifizierung und Konfiguration, sind für beide Befehlstypen verfügbar.

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle werden verwendet, um den Benutzern ein modales Popup zum Sammeln oder Anzeigen von Informationen zu präsentieren. Wenn der Benutzer das Formular übermittelt, antwortet ihr Webdienst, indem er eine Nachricht direkt in die Unterhaltung einfüge oder eine Nachricht in den Bereich verfassen einer Nachricht einfüge. Danach kann der Benutzer die Nachricht übermitteln. Sie können mehrere Formulare für komplexere Workflows verketten.

Die Aktionsbefehle werden aus dem Bereich "Nachricht verfassen", dem Befehlsfeld oder einer Nachricht ausgelöst. Wenn der Befehl über eine Nachricht aufgerufen wird, enthält die anfängliche JSON-Nutzlast, die an Ihren Bot gesendet wurde, die gesamte Nachricht, von der aus er aufgerufen wurde. In der folgenden Abbildung wird das Befehls-Aufgabenmodul für die Messagingerweiterungsaktion angezeigt: Befehlsmodul für Die ![ Messagingerweiterungsaktion](~/assets/images/task-module.png)

### <a name="search-commands"></a>Suchbefehle

Mit Suchbefehlen können Benutzer ein externes System entweder manuell über ein Suchfeld oder durch Einfügen eines Links zu einer überwachten Domäne in den Bereich "Verfassen von Nachrichten" nach Informationen durchsuchen und die Ergebnisse der Suche in eine Nachricht einfügen. Im grundlegendsten Suchbefehlsfluss enthält die anfängliche Aufrufnachricht die Suchzeichenfolge, die der Benutzer übermittelt hat. Sie antworten mit einer Liste von Karten und Kartenvorschauen. Der Teams-Client rendert eine Liste der Kartenvorschauen für den Benutzer. Wenn der Benutzer eine Karte aus der Liste auswählt, wird die Karte in voller Größe in den Bereich Zum Verfassen von Nachrichten eingefügt.

Die Karten werden aus dem Bereich "Nachricht verfassen" oder dem Befehlsfeld ausgelöst und nicht von einer Nachricht ausgelöst. Sie können nicht von einer Nachricht ausgelöst werden.
In der folgenden Abbildung wird das Aufgabenmodul für den Befehlsbefehl für die Nachrichtenerweiterung angezeigt:

![Suchbefehl für Messagingerweiterungen](~/assets/images/search-extension.png)

> [!NOTE]
> Weitere Informationen zu Karten finden Sie unter [Was sind Karten.](../task-modules-and-cards/what-are-cards.md)

## <a name="link-unfurling"></a>Entfalten von Links

Ein Webdienst wird aufgerufen, wenn eine URL im Bereich verfassen von Nachrichten eingegeben wird. Diese Funktion wird als Linkentfurling bezeichnet. Sie können einen Aufruf abonnieren, wenn URLs, die eine bestimmte Domäne enthalten, in den Bereich "Verfassen von Nachrichten" eingedungen werden. Ihr Webdienst kann die URL in einer detaillierten Karte "entfurlen", was mehr Informationen als die Standardvorschaukarte der Website enthält. Sie können Schaltflächen hinzufügen, damit die Benutzer sofort Maßnahmen ergreifen können, ohne den Microsoft Teams-Client zu verlassen.
In den folgenden Bildern wird die Funktion zum Entfingen eines Links angezeigt, wenn ein Link in die Messagingerweiterung einfügbares Feature enthält:
 
![unfurl link](../assets/images/messaging-extension/unfurl-link.png)

![link unfurling](../assets/images/messaging-extension/link-unfurl.gif)


## <a name="see-also"></a>Weitere Informationen

> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Definieren des Befehls für die Aktions-Messaging-Erweiterung](~/messaging-extensions/how-to/action-commands/define-action-command.md)

> [!div class="nextstepaction"]
> [Definieren des Befehls für die Suchnachrichtenerweiterung](~/messaging-extensions/how-to/search-commands/define-search-command.md)
