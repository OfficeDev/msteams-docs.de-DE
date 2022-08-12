---
title: Hinzufügen von Bots zu Microsoft Teams-Apps
description: In diesem Modul erfahren Sie, wie Sie mit der Entwicklung von Bots in Microsoft Teams beginnen und was sind alle Anforderungen zum Hinzufügen eines Bots in Teams
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/20/2018
ms.openlocfilehash: a1563d72ada21810393d7a0118b5a2b94463a27b
ms.sourcegitcommit: 69a45722c5c09477bbff3ba1520e6c81d2d2d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2022
ms.locfileid: "67312212"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Hinzufügen von Bots zu Microsoft Teams-Apps

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Erstellen und verbinden Sie intelligente Bots, um mit Microsoft Teams-Benutzern über chatten zu interagieren. Oder stellen Sie einen einfachen befehlsbasierten Bot bereit, der als "Befehlszeilenschnittstelle" für Ihre umfassendere Teams-App-Erfahrung verwendet werden kann. Sie können einen Nur-Benachrichtigungs-Bot erstellen, der Informationen, die für Ihre Benutzer relevant sind, direkt in einem Kanal oder in einer direkten Nachricht an sie weiterleiten kann. Sie können sogar Ihren vorhandenen Bot Framework-basierten Bot mitbringen und Teams-spezifische Unterstützung hinzufügen, um Ihre Erfahrung zu glänzen.

> [!IMPORTANT]
> Derzeit sind Bots in government Community Cloud (GCC) und GCC-High, aber nicht in Department of Defense (DOD) verfügbar.

:::image type="content" source="../../assets/images/bot_example.png" alt-text="Beispiel für einen Bot, der einen Benutzer unterstützt":::

## <a name="what-you-need-to-know-bots"></a>Was Sie wissen müssen: Bots

Ein Bot erscheint wie jedes andere Teammitglied, mit dem Sie in einer Unterhaltung interagieren, mit der Ausnahme, dass er ein sechseckiges Avatarsymbol aufweist und immer online ist.

Ein Bot verhält sich je nach Art der Unterhaltung, an der er beteiligt ist, unterschiedlich. Bots in Teams unterstützen verschiedene Arten von Unterhaltungen, die im [App-Manifest](~/resources/schema/manifest-schema.md) als Bereiche bezeichnet werden.

* `teams` Wird auch als Kanalunterhaltungen bezeichnet.
* `personal` Unterhaltungen zwischen einem Bot und einem einzelnen Benutzer.
* `groupChat` Eine Unterhaltung zwischen einem Bot und zwei oder mehr Benutzern.

Weitere Informationen finden Sie unter ["Unterhaltung mit einem Microsoft Teams-Bot"](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Mit Teams-Apps können Sie den Bot zum Star Ihrer Erfahrung machen oder einfach nur als Helfer. Bots werden als Teil Ihres umfassenderen App-Pakets verteilt, das andere Funktionen wie [Registerkarten](~/tabs/what-are-tabs.md) oder [Nachrichtenerweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) enthalten kann.

## <a name="bot-apis"></a>Bot-APIs

Teams unterstützt die meisten [Microsoft Bot Framework](https://dev.botframework.com/). (Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn ganz einfach an die Arbeit in Teams anpassen.) Wir empfehlen, entweder C# oder Node.js zu verwenden, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools) zu nutzen. Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs:

* Verwenden spezieller Kartentypen wie der Office 365 Connector-Karte.
* Verwenden und Festlegen von Teams-spezifischen Kanaldaten zu Aktivitäten.
* Verarbeiten von Nachrichtenerweiterungsanforderungen.

Die SDK-Erweiterungen installieren Abhängigkeiten, einschließlich des Bot Builder-SDK.

* **.NET** Um die Microsoft Teams-Erweiterungen für das Bot Builder SDK für .NET zu verwenden, installieren Sie das [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket in Ihrem Visual Studio-Projekt. Für Node.js Entwicklung wurde die BotBuilder für Microsoft Teams-Funktionalität ab Version 4.6 in das [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) integriert.

> [!IMPORTANT]
> Sie können Teams-Apps in jeder anderen Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die gesamte Tokenverarbeitung selbst durchführen.

*Das Entwicklerportal für Teams* hilft Ihnen beim Erstellen und Konfigurieren Ihres App-Manifests und kann Ihren Bot Framework-Bot für Sie erstellen. Es enthält auch eine React-Steuerungsbibliothek sowie einen Generator für interaktive Karten.

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Ausgehende Webhooks ermöglichen es Ihnen, einen einfachen Bot für grundlegende Interaktionen zu erstellen, z. B. das Starten eines Workflows oder andere einfache Befehle, die Sie möglicherweise benötigen. Ausgehende Webhooks leben nur in dem Team, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie [unter ausgehende Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="build-a-great-teams-bot"></a>Erstellen eines großartigen Teams-Bots

Die folgenden Artikel führen Sie durch den Prozess der Erstellung eines großartigen Bots für Teams:

* [Erstellen eines Bots](~/resources/bot-v3/bots-create.md): Nutzen Sie die großartigen Tools, Dokumentationen und Communitys, die vom Bot Framework-Team bereitgestellt werden.
* [Sprechen Sie mit Ihrem Bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): Fügen Sie einfachen Unterhaltungsfluss hinzu, und nutzen Sie kanalspezifische Funktionen. Wenn Sie in .NET oder Node.js entwickeln, verwenden Sie unsere Erweiterungen für das Bot Builder SDK, um Ihre Arbeit zu vereinfachen.
* [Verwenden von Karten in Ihrem Bot](~/resources/bot-v3/bots-cards.md): Entwerfen Sie Karten, um zu kommunizieren und Benutzerantworten zu akzeptieren.
* [Reagieren auf Bot-Ereignisse](~/resources/bot-v3/bots-notifications.md)
* [Nur-Benachrichtigungs-Bots](~/resources/bot-v3/bots-notification-only.md): Verwenden von Bots zum Senden von Benachrichtigungen für Ihre App.
* [Kontext abrufen](~/resources/bot-v3/bots-context.md): Abrufen von Informationen über den Benutzer.
* [Bot-Menüs](~/resources/bot-v3/bots-menus.md): Verwenden von Menüs in Bots.
* [Bots und Dateien](~/resources/bot-v3/bots-files.md): Senden und Empfangen von Dateien von Bots.
* [Verwenden von Registerkarten mit Bots](~/resources/bot-v3/bots-with-tabs.md): Zusammenwirken von Registerkarten und Bots.
* [Testen Sie Ihren Bot](~/resources/bot-v3/bots-test.md): Fügen Sie Ihren Bot für persönliche oder Teamunterhaltungen hinzu, um ihn in Aktion zu sehen.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
