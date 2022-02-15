---
title: Erstellen eines Bots
description: Beschreibt, wie Bots in Microsoft Teams
ms.topic: how-to
keywords: Erstellen von Teams-Bots
ms.localizationpriority: medium
ms.date: 12/07/2018
ms.openlocfilehash: 6c95055b6e053c4319810acb8923ea3f3178f3b9
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821409"
---
# <a name="create-a-bot"></a>Erstellen eines Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Alle Bots, die mithilfe der Microsoft Bot Framework erstellt wurden, sind konfiguriert und können in Microsoft Teams verwendet werden.

Weitere Informationen finden Sie in der [Bot Framework-Dokumentation](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) für allgemeine Informationen zu Bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

**Teams App Studio** ist ein Tool, mit dem Sie Ihren Bot erstellen können, und ein App-Paket, das auf Ihren Bot verweist. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Weitere Informationen finden Sie unter ["Erste Schritte mit Teams App Studio](~/concepts/build-and-test/app-studio-overview.md)". Bei den folgenden Schritten wird davon ausgegangen, dass Sie Ihren Bot manuell konfigurieren und **nicht Teams App Studio** verwenden:

1. Erstellen Sie den Bot über diesen Link: https://dev.botframework.com/bots/new. **Achten Sie darauf, dass Sie Microsoft Teams nach der Erstellung Ihres Bots aus der Liste der empfohlenen Kanäle als Kanal hinzufügen.** Sie können eine von Ihnen generierte Microsoft-App-ID wiederverwenden, wenn Sie Ihr App-Paket/-Manifest bereits erstellt haben.

   ![Bot Framework-Registrierungsseite](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Wenn Sie Ihren Bot nicht in Azure erstellen möchten, **müssen** Sie diesen Link verwenden, um einen neuen Bot zu erstellen: https://dev.botframework.com/bots/new. Wenn Sie stattdessen im Bot Framework-Portal auf den **Bot** erstellen klicken, erstellen Sie [ihren Bot stattdessen in Microsoft Azure](#bots-and-microsoft-azure).

2. Erstellen Sie den Bot mit dem [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket, dem [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) oder der [Bot Connector-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Testen Sie den Bot mithilfe der [Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Stellen Sie den Bot für einen Clouddienst bereit, z. [B. Microsoft Azure](https://azure.microsoft.com/). Alternativ können Sie Ihre App lokal ausführen und einen Tunneldienst wie [ngrok](https://ngrok.com) verwenden, um einen https:// Endpunkt für Ihren Bot verfügbar zu machen, z `https://45az0eb1.ngrok.io/api/messages`. B. .

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots und Microsoft Azure
> Ab Dezember 2017 ist das Bot Framework-Portal für die Registrierung von Bots in Microsoft Azure optimiert. Hier sind einige weitere Punkte, die Sie wissen sollten:
>
> * Der Microsoft Teams-Kanal für in Azure registrierte Bots ist kostenlos. Nachrichten, die über den Teams Kanal gesendet werden, werden nicht in die verbrauchten Nachrichten für den Bot gezählt.
> * Es ist zwar möglich, [einen neuen Bot Framework-Bot zu erstellen](https://dev.botframework.com/bots/new) , ohne Azure zu verwenden, Sie müssen jedoch diese URL verwenden (https://dev.botframework.com/bots/new)die nicht mehr im Bot Framework-Portal verfügbar gemacht wird.
> * Wenn Sie die Eigenschaften eines vorhandenen [Bots in der Liste Ihrer Bots im Bot Framework](https://dev.botframework.com/bots) bearbeiten, z. B. den "Messaging-Endpunkt", der beim ersten Entwickeln eines Bots häufig vorkommt, insbesondere wenn Sie [ngrok](https://ngrok.com) verwenden, werden die Spalte "Migrationsstatus" und eine blaue Schaltfläche "Migrieren" angezeigt, die Sie in das Microsoft Azure Portal führt. Klicken Sie nicht auf die Schaltfläche "Migrieren", es sei denn, Sie möchten dies tun. Klicken Sie stattdessen auf den Namen des Bots, und Sie können seine Eigenschaften bearbeiten:</br>
   ![Bearbeiten von Bot-Eigenschaften](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Wenn Sie Ihren Bot mit Microsoft Azure registrieren, muss Ihr Botcode nicht auf Microsoft Azure *gehostet* werden.
> * Wenn Sie einen Bot über das Azure-Portal registrieren, benötigen Sie ein Microsoft Azure Konto. Sie können [kostenlos ein Konto erstellen](https://azure.microsoft.com/free/). Um Ihre Identität beim Erstellen zu überprüfen, müssen Sie eine Kreditkarte angeben, die jedoch nicht in Rechnung gestellt wird. Es ist immer kostenlos, Bots mit Microsoft Teams zu erstellen und zu verwenden.
> * Sie können jetzt App Studio verwenden, um App- und Bot-Informationen direkt in Microsoft Teams zu registrieren/zu aktualisieren. Sie müssen das Azure-Portal nur zum Hinzufügen oder Konfigurieren anderer Bot Framework-Kanäle wie Direct Line, Web Chat, Skype und Facebook Messenger verwenden.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).