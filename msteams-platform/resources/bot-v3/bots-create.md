---
title: Erstellen eines Bots
description: Beschreibt, wie Bots in Microsoft Teams erstellt werden
ms.topic: how-to
keywords: Erstellen von Teams-Bots
ms.date: 12/07/2018
ms.openlocfilehash: d7c618adc99f814bd677e919923c4b616f293e17
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014089"
---
# <a name="create-a-bot"></a>Erstellen eines Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Alle Bots, die mit Microsoft Bot Framework erstellt wurden, sind konfiguriert und können in Microsoft Teams verwendet werden.

Allgemeine Informationen zu Bots finden Sie in der [Bot-Framework-Dokumentation.](/azure/bot-service/?view=azure-bot-service-3.0)

## <a name="create-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

*Teams App Studio* ist ein Tool, mit dem Sie Ihren Bot erstellen können, und ein App-Paket, das auf Ihren Bot verweist. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Siehe [Erste Schritte mit Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). Bei den folgenden Schritten wird davon ausgegangen, dass Sie Ihren Bot handkonfigurieren und *nicht Teams App Studio verwenden.*

1. Erstellen Sie den Bot über diesen Link: https://dev.botframework.com/bots/new . **Achten Sie darauf, dass Sie Microsoft Teams nach der Erstellung Ihres Bots aus der Liste der empfohlenen Kanäle als Kanal hinzufügen.** Sie können eine von Ihnen generierte Microsoft-App-ID wiederverwenden, wenn Sie Ihr App-Paket/-Manifest bereits erstellt haben.

   ![Bot Framework-Registrierungsseite](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Wenn Sie Ihren Bot nicht in Azure erstellen möchten, **müssen** Sie diesen Link verwenden, um einen neuen Bot zu erstellen: https://dev.botframework.com/bots/new . Wenn Sie stattdessen  im Bot -Framework-Portal auf die Schaltfläche "Bot erstellen" klicken, erstellen Sie ihren Bot [stattdessen in Microsoft Azure.](#bots-and-microsoft-azure)

2. Erstellen Sie den Bot mit dem [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket, dem [Bot Framework SDK](https://github.com/microsoft/botframework-sdk)oder der Bot [Connector-API.](https://docs.microsoft.com/bot-framework/rest-api/bot-framework-rest-connector-api-reference) *Siehe auch* [Bot Framework-Beispiele.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)

3. Testen Sie den Bot mit dem [Bot Framework-Emulator.](https://docs.microsoft.com/bot-framework/debug-bots-emulator)

4. Stellen Sie den Bot in einem Clouddienst bereit, z. B. [Microsoft Azure.](https://azure.microsoft.com/) Alternativ können Sie Ihre App lokal ausführen und einen Tunnelingdienst wie [ngrok](https://ngrok.com) verwenden, um einen https:// für Ihren Bot verfügbar zu machen, z. B. `https://45az0eb1.ngrok.io/api/messages` .

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots und Microsoft Azure
> Seit Dezember 2017 ist das Bot -Framework-Portal für die Registrierung von Bots in Microsoft Azure optimiert. Hier sind einige weitere Punkte, die Sie wissen sollten:
>
> * Der Microsoft Teams-Kanal für in Azure registrierte Bots ist kostenlos. Über den Kanal "Teams" gesendete Nachrichten werden nicht auf die verbrauchten Nachrichten für den Bot angezählt.
> * Obwohl es möglich ist, einen neuen [Bot-Framework-Bot](https://dev.botframework.com/bots/new) ohne Verwendung von Azure zu erstellen, müssen Sie diese URL ( verwenden, die nicht mehr im https://dev.botframework.com/bots/new) Bot -Framework-Portal verfügbar gemacht wird.
> * Wenn Sie die Eigenschaften eines vorhandenen Bots in der Liste Ihrer [Bots in Bot Framework](https://dev.botframework.com/bots) bearbeiten, z. B. den "Messaging-Endpunkt", der beim ersten Entwickeln eines Bots üblich ist, insbesondere wenn Sie [ngrok](https://ngrok.com)verwenden, sehen Sie die Spalte "Migrationsstatus" und eine blaue Schaltfläche "Migrieren", die Sie in das Microsoft Azure-Portal geleitet. Klicken Sie nur dann auf die Schaltfläche "Migrieren", wenn Sie dies tun möchten. Klicken Sie stattdessen auf den Namen des Bots, und Sie können seine Eigenschaften bearbeiten:</br>
   ![Bearbeiten von Bot-Eigenschaften](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Wenn Sie Ihren Bot mit Microsoft Azure registrieren, muss Ihr Botcode nicht in Microsoft Azure *gehostet* werden.
> * Wenn Sie einen Bot über das Microsoft Azure-Portal registrieren, müssen Sie über ein Microsoft Azure-Konto verfügen. Sie können [kostenlos ein Konto erstellen](https://azure.microsoft.com/free/). Um Ihre Identität beim Erstellen einer Kreditkarte zu überprüfen, müssen Sie eine Kreditkarte bereitstellen, die jedoch nicht belastet wird. Es ist immer frei, Bots mit Microsoft Teams zu erstellen und zu verwenden.
> * Sie können jetzt App Studio verwenden, um App- und Botinformationen direkt in Microsoft Teams zu registrieren/zu aktualisieren. Sie müssen nur das Microsoft Azure-Portal zum Hinzufügen/Konfigurieren anderer Bot -Framework-Kanäle wie Direct Line, Web Chat, Skype und Facebook Messenger verwenden.
