---
title: Erstellen eines Bots
description: Beschreibt das Erstellen von Bots in Microsoft Teams
ms.topic: how-to
keywords: Erstellung von Teams-Bots
localization_priority: Normal
ms.date: 12/07/2018
ms.openlocfilehash: 67aa3e2cfd1950dced84785a9f6f35cfd4d5ff85
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566775"
---
# <a name="create-a-bot"></a>Erstellen eines Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Alle bots, die mit dem Microsoft Bot Framework erstellt wurden, sind konfiguriert und können in Microsoft Teams.

Weitere Informationen finden Sie unter [Bot Framework Documentation](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) für allgemeine Informationen zu Bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

**Teams App Studio ist** ein Tool, mit dem Sie Ihren Bot erstellen können, und ein App-Paket, das auf Ihren Bot verweist. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Weitere Informationen finden Sie unter [Erste Schritte mit Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). Bei den folgenden Schritten wird davon ausgegangen, dass Sie den Bot handkonfigurieren und nicht **Teams App Studio verwenden:**

1. Erstellen Sie den Bot über diesen Link: https://dev.botframework.com/bots/new . **Achten Sie darauf, dass Sie Microsoft Teams nach der Erstellung Ihres Bots aus der Liste der empfohlenen Kanäle als Kanal hinzufügen.** Sie können eine von Ihnen generierte Microsoft-App-ID wiederverwenden, wenn Sie Ihr App-Paket/-Manifest bereits erstellt haben.

   ![Bot Framework-Registrierungsseite](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Wenn Sie Ihren Bot nicht in Azure erstellen möchten, **müssen** Sie diesen Link verwenden, um einen neuen Bot zu erstellen: https://dev.botframework.com/bots/new . Wenn Sie stattdessen  im Bot Framework-Portal auf den Bot erstellen klicken, erstellen Sie ihren Bot [in Microsoft Azure.](#bots-and-microsoft-azure)

2. Erstellen Sie den Bot mithilfe des [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Pakets, des [Bot Framework SDK](https://github.com/microsoft/botframework-sdk)oder der Bot [Connector-API.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)

3. Testen Sie den Bot mithilfe [der Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Stellen Sie den Bot in einem Clouddienst wie z. B. [Microsoft Azure.](https://azure.microsoft.com/) Alternativ können Sie Ihre App lokal ausführen und einen Tunneldienst wie [ngrok](https://ngrok.com) verwenden, um einen https:// für Ihren Bot verfügbar zu machen, z. B. `https://45az0eb1.ngrok.io/api/messages` .

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots und Microsoft Azure
> Ab Dezember 2017 ist das Bot Framework-Portal für die Registrierung von Bots in Microsoft Azure. Hier sind einige weitere Punkte, die Sie wissen sollten:
>
> * Der Microsoft Teams-Kanal für in Azure registrierte Bots ist kostenlos. Nachrichten, die über den Teams gesendet werden, zählen nicht zu den verbrauchten Nachrichten für den Bot.
> * Obwohl es möglich ist, einen neuen [Bot Framework-Bot](https://dev.botframework.com/bots/new) ohne Azure zu erstellen, müssen Sie diese URL ( verwenden, die nicht mehr im Bot Framework-Portal https://dev.botframework.com/bots/new) verfügbar ist.
> * Wenn Sie die Eigenschaften eines vorhandenen Bots in der Liste Ihrer [Bots in Bot Framework](https://dev.botframework.com/bots) bearbeiten, z. B. den "Messagingendpunkt", der bei der ersten Entwicklung eines Bots üblich ist, insbesondere wenn Sie ngrok verwenden, werden die Spalte "Migrationsstatus" und eine blaue Schaltfläche "Migrieren" angezeigt, die Sie in das Microsoft Azure-Portal einf?ngt. [](https://ngrok.com) Klicken Sie nicht auf die Schaltfläche "Migrieren", es sei denn, Sie möchten dies tun. Klicken Sie stattdessen auf den Namen des Bots, und Sie können seine Eigenschaften bearbeiten:</br>
   ![Bearbeiten von Bot-Eigenschaften](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Wenn Sie Ihren Bot mithilfe von Microsoft Azure registrieren, muss Ihr Botcode nicht *auf* einer Microsoft Azure.
> * Wenn Sie einen Bot über das Microsoft Azure-Portal registrieren, müssen Sie über ein Microsoft Azure-Konto verfügen. Sie können [kostenlos ein Konto erstellen](https://azure.microsoft.com/free/). Um Ihre Identität zu überprüfen, wenn Sie eine erstellen, müssen Sie eine Kreditkarte bereitstellen, sie wird jedoch nicht belastet. Es ist immer kostenlos, Bots mit Microsoft Teams.
> * Sie können app Studio jetzt verwenden, um App- und Botinformationen direkt innerhalb der App zu registrieren Microsoft Teams. Sie müssen nur das Microsoft Azure-Portal zum Hinzufügen oder Konfigurieren anderer Bot Framework-Kanäle wie Direct Line, Web Chat, Skype und Facebook Messenger verwenden.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).