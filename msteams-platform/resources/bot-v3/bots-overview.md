---
title: Hinzufügen von Bots zu Microsoft Teams Apps
description: Beschreibt, wie Sie mit der Entwicklung von Bots in Microsoft Teams beginnen
ms.topic: conceptual
keywords: Teams Bots Entwicklung
localization_priority: Normal
ms.date: 05/20/2018
ms.openlocfilehash: 674576efccb2916b8a82ae27310d8fe49909a782
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566754"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Hinzufügen von Bots zu Microsoft Teams Apps

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Erstellen und verbinden Sie intelligente Bots, um mit Microsoft Teams Benutzer natürlich durch Chat zu interagieren. Oder stellen Sie einen einfachen befehlsbasierten Bot bereit, der als "Befehlszeilen"-Schnittstelle für Ihre breitere Teams App-Erfahrung verwendet werden kann. Sie können einen reinen Benachrichtigungsbot erstellen, der Informationen, die für Ihre Benutzer relevant sind, direkt an sie in einem Kanal oder einer direkten Nachricht weiterleiten kann. Sie können sogar Ihren vorhandenen Bot Framework-basierten Bot mitbringen und Teams-spezifische Unterstützung hinzufügen, damit Ihre Erfahrung glänzt.

![Beispiel für einen Bot, der einem Benutzer hilft](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>Was Sie wissen müssen: Bots

Ein Bot erscheint wie jedes andere Teammitglied, mit dem Sie in einer Unterhaltung interagieren, außer dass er ein sechseckiges Avatarsymbol hat und immer online ist.

Ein Bot verhält sich unterschiedlich, je nachdem, in welcher Art von Gespräch er verwickelt ist. Bots in Teams unterstützen verschiedene Arten von Unterhaltungen, die als Bereiche im [App-Manifest](~/resources/schema/manifest-schema.md)bezeichnet werden.

* `teams` Auch Kanalunterhaltungen genannt.
* `personal` Gespräche zwischen einem Bot und einem einzelnen Benutzer.
* `groupChat` Eine Unterhaltung zwischen einem Bot und zwei oder mehr Benutzern.

Weitere Informationen finden Sie unter [Führen einer Unterhaltung mit einem Microsoft Teams Bot](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Mit Microsoft Teams Apps können Sie den Bot zum Star Ihrer Erfahrung machen, oder einfach nur zu einem Helfer. Bots werden als Teil Ihres umfassenderen App-Pakets verteilt, das andere Funktionen wie [Registerkarten](~/tabs/what-are-tabs.md) oder [Messagingerweiterungen](~/messaging-extensions/what-are-messaging-extensions.md)enthalten kann.

## <a name="bot-apis"></a>Bot-APIs

Microsoft Teams unterstützt den größten Teil der [Microsoft Bot Framework](https://dev.botframework.com/). (Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn ganz einfach an die Arbeit in Microsoft Teams anpassen.) Wir empfehlen Ihnen, entweder C- oder Node.js zu verwenden, um die Vorteile unserer [SDKs](/microsoftteams/platform/#pivot=sdk-tools)zu nutzen. Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs:

* Verwenden von speziellen Kartentypen wie der Office 365 Connector-Karte.
* Verbrauchen und Festlegen Teams-spezifischer Kanaldaten für Aktivitäten.
* Verarbeiten von Messagingerweiterungsanforderungen.

Die SDK-Erweiterungen installieren Abhängigkeiten, einschließlich des Bot Builder SDK.

* **.NET** Um die Microsoft Teams Erweiterungen für das Bot Builder SDK für .NET zu verwenden, installieren Sie das [NuGet-Paket Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) in Ihrem Visual Studio-Projekt. Für Node.js Entwicklung wurde die BotBuilder for Microsoft Teams-Funktionalität ab v4.6 in das [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) integriert.

> [!IMPORTANT]
> Sie können Teams-Apps in jeder anderen Web-Programmiertechnologie entwickeln und die [Bot Framework REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die gesamte Tokenverarbeitung selbst durchführen.

*Teams App Studio* hilft Ihnen, Ihr App-Manifest zu erstellen und zu konfigurieren, und kann Ihren Bot Framework-Bot für Sie erstellen. Es enthält auch eine React-Steuerungsbibliothek sowie einen Generator für interaktive Karten.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen es Ihnen, einen einfachen Bot für grundlegende Interaktion zu erstellen, wie z. B. das Starten eines Workflows oder andere einfache Befehle, die Sie benötigen. Ausgehende Webhooks leben nur in dem Team, in dem Sie sie erstellen, und sind für einfache Prozesse gedacht, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie unter [Ausgehende Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="build-a-great-teams-bot"></a>Erstellen Sie eine große Teams Bot

Die folgenden Themen führen Sie durch den Prozess der Erstellung eines großartigen Bots für Teams:

* [Erstellen Sie einen Bot:](~/resources/bot-v3/bots-create.md)Nutzen Sie die großartigen Tools, die Dokumentation und die Community, die vom Bot Framework-Team bereitgestellt werden.
* [Sprechen Sie mit Ihrem Bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): Fügen Sie grundlegende Konversationsfluss und nutzen Sie kanalspezifische Funktionalität. Wenn Sie in .NET oder Node.js entwickeln, verwenden Sie unsere Erweiterungen für das Bot Builder SDK, um Ihre Arbeit zu vereinfachen.
* [Verwenden von Karten in Ihrem Bot](~/resources/bot-v3/bots-cards.md): Entwerfen Sie Karten, um zu kommunizieren und Benutzerreaktionen zu akzeptieren.
* [Reagieren auf Bot-Ereignisse](~/resources/bot-v3/bots-notifications.md)
* [Nur Benachrichtigungsbots](~/resources/bot-v3/bots-notification-only.md): Verwenden von Bots, um Benachrichtigungen für Ihre App zu senden.
* [Kontext abrufen](~/resources/bot-v3/bots-context.md): Abrufen von Informationen über den Benutzer.
* [Bot-Menüs](~/resources/bot-v3/bots-menus.md): Verwenden von Menüs in Bots.
* [Bots und Dateien](~/resources/bot-v3/bots-files.md): Senden und Empfangen von Dateien von Bots.
* [Verwenden von Tabs mit Bots](~/resources/bot-v3/bots-with-tabs.md): Machen Tabs und Bots zusammenarbeiten.
* [Testen Sie Ihren Bot](~/resources/bot-v3/bots-test.md): Fügen Sie Ihren Bot für persönliche oder Team-Gespräche, um es in Aktion zu sehen.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).