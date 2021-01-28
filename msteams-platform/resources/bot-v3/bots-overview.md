---
title: Hinzufügen von Bots zu Microsoft Teams-Apps
description: Beschreibt, wie Sie mit der Entwicklung von Bots in Microsoft Teams beginnen
ms.topic: conceptual
keywords: Entwicklung von Teams-Bots
ms.date: 05/20/2018
ms.openlocfilehash: 226340500f59754d603f21b7868eecab38f942af
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014404"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Hinzufügen von Bots zu Microsoft Teams-Apps

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Erstellen und verbinden Sie intelligente Bots für die natürliche Interaktion mit Microsoft Teams-Benutzern über Chat. Oder stellen Sie einen einfachen befehlsbasierten Bot bereit, der als "Befehlszeilenschnittstelle" für Ihre umfassendere Teams-App-Erfahrung verwendet werden soll. Sie können einen Nur-Benachrichtigungs-Bot erstellen, der informationen, die für Ihre Benutzer relevant sind, direkt in einem Kanal oder in einer direkten Nachricht an sie senden kann. Sie können sogar Ihren vorhandenen Bot Framework-basierten Bot mitbringen und Teams-spezifische Unterstützung hinzufügen, um Ihre Erfahrung zu glänzen.

![Beispiel für einen Bot, der einen Benutzer unterstützt](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>Was Sie wissen müssen: Bots

Ein Bot erscheint wie jedes andere Teammitglied, mit dem Sie in einer Unterhaltung interagieren, mit der Ausnahme, dass er ein hexagonales Avatarsymbol hat und immer online ist.

Ein Bot verhält sich anders, je nachdem, an welcher Art von Unterhaltung er beteiligt ist. Bots in Teams unterstützen verschiedene Arten von Unterhaltungen (bereiche im [App-Manifest genannt).](~/resources/schema/manifest-schema.md)

* `teams` Auch Kanalunterhaltungen genannt
* `personal` Unterhaltungen zwischen einem Bot und einem einzelnen Benutzer
* `groupChat` Eine Unterhaltung zwischen einem Bot und zwei oder mehr Benutzern

Weitere [Informationen finden Sie unter "Unterhaltung mit einem Microsoft Teams-Bot".](~/resources/bot-v3/bot-conversations/bots-conversations.md)

Mit Microsoft Teams-Apps können Sie den Bot zum Star Ihrer Erfahrung machen oder einfach nur als Helfer. Bots werden als Teil Ihres umfassenderen App-Pakets verteilt, das andere Funktionen wie [Registerkarten oder](~/tabs/what-are-tabs.md) [Messagingerweiterungen enthalten kann.](~/messaging-extensions/what-are-messaging-extensions.md)

## <a name="bot-apis"></a>Bot-APIs

Microsoft Teams unterstützt den Großteil des [Microsoft Bot Frameworks.](https://dev.botframework.com/) (Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn problemlos an die Arbeit in Microsoft Teams anpassen.) Es wird empfohlen, entweder C# oder Node.js zu verwenden, um unsere [SDKs zu nutzen.](/microsoftteams/platform/#pivot=sdk-tools) Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs:

* Verwenden spezieller Kartentypen wie der Office 365 -Connectorkarte
* Verwenden und Festlegen von Teams-spezifischen Kanaldaten zu Aktivitäten
* Verarbeiten von Messagingerweiterungsanforderungen

Die SDK-Erweiterungen installieren Abhängigkeiten, einschließlich des Bot Builder SDK.

* **.NET** Um die Microsoft Teams-Erweiterungen für das Bot Builder SDK für .NET zu verwenden, installieren Sie das [Microsoft.Bot.Connector.Teams-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) in Visual Studio Projekt. For Node.js development, the BotBuilder for Microsoft Teams functionality has been incorporated into the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) as of v4.6.

*Siehe auch* [Bot Framework-Beispiele.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)

> [!IMPORTANT]
> Sie können Teams-Apps in jeder anderen Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die tokenverarbeitung selbst durchführen.

*Teams App Studio hilft* Ihnen beim Erstellen und Konfigurieren Ihres App-Manifests und kann Ihren Bot-Framework-Bot für Sie erstellen. Es enthält auch eine React-Steuerelementbibliothek und einen interaktiven Karten-Generator.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Mit ausgehenden Webhooks können Sie einen einfachen Bot für grundlegende Interaktionen erstellen, z. B. einen Workflow oder andere einfache Befehle starten, die Sie möglicherweise benötigen. Ausgehende Webhooks befinden sich nur in dem Team, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere [Informationen finden Sie unter ausgehenden Webhooks.](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)

## <a name="build-a-great-teams-bot"></a>Erstellen eines großartigen Teams-Bots

Die folgenden Themen führen Sie durch den Prozess der Erstellung eines großartigen Bots für Teams.

* [Erstellen Sie einen Bot:](~/resources/bot-v3/bots-create.md)Nutzen Sie die großartigen Tools, Dokumentationen und die Community, die vom Bot -Framework-Team bereitgestellt werden.
* [Sprechen Sie mit Ihrem Bot:](~/resources/bot-v3/bot-conversations/bots-conversations.md)Fügen Sie einen einfachen Unterhaltungsfluss hinzu, und nutzen Sie kanalspezifische Funktionen. Wenn Sie in .NET oder Node.js entwickeln, verwenden Sie unsere Erweiterungen für das Bot Builder SDK, um Ihre Arbeit zu vereinfachen.
* [Verwenden von Karten in Ihrem Bot](~/resources/bot-v3/bots-cards.md) Entwerfen Sie Karten, um zu kommunizieren und Benutzerantworten zu akzeptieren.
* [Reagieren sie auf Bot-Ereignisse.](~/resources/bot-v3/bots-notifications.md)
* [Nur-Benachrichtigungs-Bots](~/resources/bot-v3/bots-notification-only.md) Verwenden von Bots zum Senden von Benachrichtigungen für Ihre App.
* [Kontext erhalten](~/resources/bot-v3/bots-context.md) Informationen zum Benutzer erhalten.
* [Botmenüs](~/resources/bot-v3/bots-menus.md) Verwenden von Menüs in Bots.
* [Bots und Dateien](~/resources/bot-v3/bots-files.md) Senden und Empfangen von Dateien von Bots.
* [Verwenden von Registerkarten mit Bots](~/resources/bot-v3/bots-with-tabs.md) Zusammenbringen von Registerkarten und Bots.
* [Testen Sie Ihren Bot:](~/resources/bot-v3/bots-test.md)Fügen Sie Ihren Bot für persönliche unterhaltungen oder Teamunterhaltungen hinzu, um ihn in Aktion zu sehen.
