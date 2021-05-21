---
title: Hinzufügen von Bots zu Microsoft Teams Apps
description: Beschreibt, wie Sie mit der Entwicklung von Bots in Microsoft Teams
ms.topic: conceptual
keywords: Teams-Bots-Entwicklung
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

Erstellen und verbinden Sie intelligente Bots, um Microsoft Teams benutzer natürlich über Chat zu interagieren. Oder stellen Sie einen einfachen befehlsbasierten Bot bereit, der als "Befehlszeilenschnittstelle" für Ihre umfassendere Teams verwendet werden soll. Sie können einen Nur-Benachrichtigungs-Bot erstellen, der informationen, die für Ihre Benutzer relevant sind, direkt in einem Kanal oder einer direkten Nachricht an sie senden kann. Sie können sogar Ihren vorhandenen Bot Framework-basierten Bot mitbringen und Teams unterstützung hinzufügen, um Ihre Erfahrung zu glänzen.

![Beispiel für einen Bot, der einen Benutzer unterstützt](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>Was Sie wissen müssen: Bots

Ein Bot wird wie jedes andere Teammitglied angezeigt, mit dem Sie in einer Unterhaltung interagieren, mit der Ausnahme, dass er über ein sechseckiges Avatarsymbol verfügt und immer online ist.

Ein Bot verhält sich abhängig von der Art der Unterhaltung, an der er beteiligt ist, unterschiedlich. Bots in Teams unterstützen verschiedene Arten von Unterhaltungen, die als Bereiche im [App-Manifest bezeichnet werden.](~/resources/schema/manifest-schema.md)

* `teams` Wird auch als Kanalunterhaltungen bezeichnet.
* `personal` Unterhaltungen zwischen einem Bot und einem einzelnen Benutzer.
* `groupChat` Eine Unterhaltung zwischen einem Bot und zwei oder mehr Benutzern.

Weitere Informationen finden Sie unter [Führen einer Unterhaltung mit einem Microsoft Teams Bot](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Mit Microsoft Teams Apps können Sie den Bot zum Star Ihrer Erfahrung machen oder einfach nur als Helfer. Bots werden als Teil Ihres umfassenderen App-Pakets verteilt, das andere Funktionen wie [Registerkarten oder](~/tabs/what-are-tabs.md) [Messagingerweiterungen enthalten kann.](~/messaging-extensions/what-are-messaging-extensions.md)

## <a name="bot-apis"></a>Bot-APIs

Microsoft Teams unterstützt die meisten [Microsoft Bot Framework](https://dev.botframework.com/). (Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn ganz einfach an die Arbeit in Microsoft Teams.) Es wird empfohlen, entweder C# oder Node.js zu verwenden, um unsere [SDKs zu nutzen.](/microsoftteams/platform/#pivot=sdk-tools) Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs:

* Verwenden spezieller Kartentypen wie Office 365 Connector-Karte.
* Verwenden und Festlegen Teams spezifischen Kanaldaten zu Aktivitäten.
* Verarbeiten von Messagingerweiterungsanforderungen.

Die SDK-Erweiterungen installieren Abhängigkeiten, einschließlich des Bot Builder SDK.

* **.NET** Um die Microsoft Teams für das Bot Builder SDK für .NET zu verwenden, installieren Sie das [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket in Ihrem Visual Studio Projekt. Für Node.js Entwicklung wurde die BotBuilder für Microsoft Teams ab v4.6 in das [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) integriert.

> [!IMPORTANT]
> Sie können Teams apps in jeder anderen Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die token-Verarbeitung selbst ausführen.

*Teams App Studio* hilft Ihnen beim Erstellen und Konfigurieren Ihres App-Manifests und kann Ihren Bot Framework-Bot für Sie erstellen. Es enthält auch eine React-Steuerungsbibliothek sowie einen Generator für interaktive Karten.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen ihnen das Erstellen eines einfachen Bots für grundlegende Interaktionen, z. B. das Starten eines Workflows oder andere einfache Befehle, die Sie möglicherweise benötigen. Ausgehende Webhooks leben nur in dem Team, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie unter [Ausgehende Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="build-a-great-teams-bot"></a>Erstellen eines großartigen Teams Bots

Die folgenden Themen führen Sie durch den Prozess der Erstellung eines großartigen Bots für Teams:

* [Erstellen eines Bots:](~/resources/bot-v3/bots-create.md)Nutzen Sie die großartigen Tools, Dokumentationen und die Community, die vom Bot Framework-Team bereitgestellt werden.
* [Sprechen Sie mit Ihrem Bot:](~/resources/bot-v3/bot-conversations/bots-conversations.md)Fügen Sie grundlegenden Unterhaltungsfluss hinzu und nutzen Sie kanalspezifische Funktionen. Wenn Sie in .NET oder Node.js entwickeln, verwenden Sie unsere Erweiterungen für das Bot Builder SDK, um Ihre Arbeit zu vereinfachen.
* [Verwenden von Karten in Ihrem Bot:](~/resources/bot-v3/bots-cards.md)Entwerfen Sie Karten, um benutzerantworten zu kommunizieren und zu akzeptieren.
* [Reagieren auf Botereignisse](~/resources/bot-v3/bots-notifications.md)
* [Nur-Benachrichtigungs-Bots:](~/resources/bot-v3/bots-notification-only.md)Verwenden von Bots zum Senden von Benachrichtigungen für Ihre App.
* [Get context](~/resources/bot-v3/bots-context.md): Get information about the user.
* [Bot-Menüs:](~/resources/bot-v3/bots-menus.md)Verwenden von Menüs in Bots.
* [Bots und Dateien:](~/resources/bot-v3/bots-files.md)Senden und Empfangen von Dateien von Bots.
* [Verwenden von Registerkarten mit Bots:](~/resources/bot-v3/bots-with-tabs.md)So arbeiten Registerkarten und Bots zusammen.
* [Test your bot](~/resources/bot-v3/bots-test.md): Add your bot for personal or team conversations to see it in action.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).