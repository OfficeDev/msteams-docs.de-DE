---
title: Hinzufügen von Bots zu Microsoft Teams-apps
description: Beschreibt, wie Sie mit der Entwicklung von Bots in Microsoft Teams beginnen.
keywords: Teams-Bots-Entwicklung
ms.date: 05/20/2018
ms.openlocfilehash: 0ecb268c34275e958103c9905b2ed1f0858cafda
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674116"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Hinzufügen von Bots zu Microsoft Teams-apps

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Erstellen und verbinden Sie intelligente Bots, um mit Microsoft Teams-Benutzern auf natürliche Weise über Chat zu interagieren. Oder geben Sie einen einfachen befehlsbasierten bot an, der als "Befehlszeilenschnittstelle" für ihre umfassendere Teams-App-Umgebung verwendet werden kann. Sie können einen nur-Benachrichtigungs-bot erstellen, mit dem Informationen, die für Ihre Benutzer relevant sind, direkt in einem Kanal oder einer direkten Nachricht an Sie weitergeleitet werden können. Sie können sogar Ihren vorhandenen bot Framework-basierten bot und Hinzufügen von Teams-spezifischer Unterstützung, damit Ihre Erfahrung glänzen zu bringen.

![Beispiel eines bot zur Unterstützung eines Benutzers](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>Was Sie wissen müssen: Bots

Ein Bot wird wie jedes andere Teammitglied angezeigt, mit dem Sie in einer Unterhaltung interagieren, es sei denn, es verfügt über ein hexagonales Avatar-Symbol und ist immer online.

Ein bot verhält sich je nach Art der Unterhaltung, an der es beteiligt ist, anders. Bots in Microsoft Teams unterstützen verschiedene Arten von Unterhaltungen (als Bereiche im [App-Manifest](~/resources/schema/manifest-schema.md)bezeichnet).

* `teams`Auch Kanal Unterhaltungen genannt
* `personal`Unterhaltungen zwischen einem bot und einem einzelnen Benutzer
* `groupChat`Eine Unterhaltung zwischen einem bot und 2 oder mehr Benutzern

Weitere Informationen finden Sie unter [Gespräch mit einem Microsoft Teams-bot](~/resources/bot-v3/bot-conversations/bots-conversations.md) .

Mit Microsoft Teams-Apps können Sie den bot zum Star ihrer Erfahrung machen oder einfach nur einen Helfer. Bots werden als Teil ihres umfassenden App-Pakets verteilt, das andere Funktionen wie [Tabs](~/tabs/what-are-tabs.md) oder Messaging- [Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md)umfassen kann.

## <a name="bot-apis"></a>Bot-APIs

Microsoft Teams unterstützt den Großteil des [Microsoft bot-Frameworks](https://dev.botframework.com/). (Wenn Sie bereits einen bot haben, der auf dem bot-Framework basiert, können Sie ihn ganz einfach an die Arbeit in Microsoft Teams anpassen.) Es wird empfohlen, dass Sie entweder C# oder Node. js verwenden, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools)nutzen zu können. Diese Pakete erweitern die grundlegenden Klassen und Methoden von bot Builder SDK:

* Verwenden spezieller Kartentypen wie der Office 365-Verbindungskarte
* Verwenden und Festlegen von Team spezifischen Kanaldaten zu Aktivitäten
* Verarbeiten von Messaging Erweiterungsanforderungen

Die SDK-Erweiterungen installieren Abhängigkeiten, einschließlich des bot Builder SDK.

* **.Net** Um die Microsoft Teams-Erweiterungen für das bot Builder SDK für .net zu verwenden, installieren Sie das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket in Ihrem Visual Studio-Projekt.
* **Node. js** um die Microsoft Teams-Erweiterungen für das bot Builder SDK für Node. js zu verwenden, fügen Sie das [botbuilder-Teams NPM-](https://www.npmjs.com/package/botbuilder-teams) Paket hinzu.
* **Quell Code** Den vollständigen Quellcode für die Erweiterungen finden Sie im [BotBuilder-verläuft](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams) Repo auf GitHub.

> [!IMPORTANT]
> Sie können Teams-apps in jeder anderen webprogrammier Technologie entwickeln und die [bot-Framework-Rest-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die gesamte tokenbehandlung selbst durchführen.

*Teams App Studio* unterstützt Sie beim Erstellen und Konfigurieren Ihres App-Manifests und kann Ihren bot-Framework-bot für Sie erstellen. Es enthält auch eine Reaktions Steuerungs Bibliothek und einen interaktiven Kartengenerator.

## <a name="outgoing-webhooks"></a>Ausgehende webhooks

Mit ausgehenden webhooks können Sie einen einfachen bot für die grundlegende Interaktion erstellen, wie das Starten eines Workflows oder andere einfache Befehle, die Sie möglicherweise benötigen. Ausgehende webhooks Leben nur in dem Team, in dem Sie Sie erstellen, und sind für einfache Prozesse bestimmt, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie unter [ausgehende webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md) .

## <a name="build-a-great-teams-bot"></a>Erstellen eines großen Teams-bot

Die folgenden Themen führen Sie durch den Prozess der Erstellung eines großen bot für Teams.

* [Erstellen eines bot](~/resources/bot-v3/bots-create.md): nutzen Sie die hervorragende Tools, Dokumentation und Community, die das bot-Framework-Team bereitgestellt hat.
* [Sprechen Sie mit Ihrem bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): Fügen Sie grundlegenden Unterhaltungs Fluss hinzu und nutzen Sie kanalspezifische Funktionen. Wenn Sie in .net oder Node. js entwickeln, verwenden Sie unsere Erweiterungen für das bot Builder SDK, um Ihre Arbeit zu vereinfachen.
* [Verwenden von Karten in Ihrem bot](~/resources/bot-v3/bots-cards.md) Entwerfen von Karten zur Kommunikation und Annahme von Benutzerreaktionen.
* [Reagieren Sie auf bot-Ereignisse](~/resources/bot-v3/bots-notifications.md).
* [Nur-Benachrichtigungs-Bots](~/resources/bot-v3/bots-notification-only.md) Verwenden von Bots zum Senden von Benachrichtigungen für Ihre APP.
* [Kontext abrufen](~/resources/bot-v3/bots-context.md) Informationen zum Benutzer abrufen.
* [Bot-Menüs](~/resources/bot-v3/bots-menus.md) Verwenden von Menüs in Bots.
* [Bots und Dateien](~/resources/bot-v3/bots-files.md) Senden und empfangen von Dateien von Bots.
* [Verwenden von Tabs mit Bots](~/resources/bot-v3/bots-with-tabs.md) Erstellen von Registerkarten und Bots zusammenarbeiten.
* [Testen Sie Ihren bot](~/resources/bot-v3/bots-test.md): Fügen Sie Ihren bot für persönliche oder Team Unterhaltungen hinzu, um ihn in Aktion zu sehen.
