---
title: Erstellen eines Bots
description: Beschreibt das Erstellen von Bots in Microsoft Teams
ms.topic: how-to
keywords: Teams Bots Erstellung
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

Alle Bots, die mit dem Microsoft Bot Framework erstellt wurden, sind konfiguriert und bereit, in Microsoft Teams zu arbeiten.

Weitere Informationen finden Sie unter [Bot Framework-Dokumentation](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) für allgemeine Informationen zu Bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

**Teams App Studio** ist ein Tool, das Ihnen beim Erstellen Ihres Bots helfen kann, und ein App-Paket, das auf Ihren Bot verweist. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Weitere Informationen finden Sie unter [Erste Schritte mit Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). Bei den folgenden Schritten wird davon ausgegangen, dass Sie Ihren Bot von Hand konfigurieren und **Teams App Studio** nicht verwenden:

1. Erstellen Sie den Bot mit diesem Link: https://dev.botframework.com/bots/new . **Achten Sie darauf, dass Sie Microsoft Teams nach der Erstellung Ihres Bots aus der Liste der empfohlenen Kanäle als Kanal hinzufügen.** Sie können eine von Ihnen generierte Microsoft-App-ID wiederverwenden, wenn Sie Ihr App-Paket/-Manifest bereits erstellt haben.

   ![Bot Framework-Registrierungsseite](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Wenn Sie Ihren Bot nicht in Azure erstellen möchten, **müssen** Sie diesen Link verwenden, um einen neuen Bot zu erstellen: https://dev.botframework.com/bots/new . Wenn Sie stattdessen im Bot Framework-Portal auf den **Bot-Portal** erstellen klicken, erstellen Sie [stattdessen Ihren Bot in Microsoft Azure.](#bots-and-microsoft-azure)

2. Erstellen Sie den Bot mit dem [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket, dem [Bot Framework SDK](https://github.com/microsoft/botframework-sdk)oder der [Bot Connector-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Testen Sie den Bot mit dem [Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Stellen Sie den Bot in einem Clouddienst bereit, z. B. [Microsoft Azure](https://azure.microsoft.com/). Alternativ können Sie Ihre App lokal ausführen und einen Tunneldienst wie [ngrok](https://ngrok.com) verwenden, um einen https:// Endpunkt für Ihren Bot verfügbar zu machen, z. `https://45az0eb1.ngrok.io/api/messages` B. .

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots und Microsoft Azure
> Seit Dezember 2017 ist das Bot Framework-Portal für die Registrierung von Bots in Microsoft Azure optimiert. Hier sind einige weitere Punkte, die Sie wissen sollten:
>
> * Der Microsoft Teams-Kanal für in Azure registrierte Bots ist kostenlos. Nachrichten, die über den Teams Kanal gesendet werden, werden nicht auf die verbrauchten Nachrichten für den Bot angerechnet.
> * Es ist zwar möglich, [einen neuen Bot Framework-Bot](https://dev.botframework.com/bots/new) ohne Azure zu erstellen, sie müssen jedoch diese URL ( verwenden, https://dev.botframework.com/bots/new) die im Bot Framework-Portal nicht mehr verfügbar gemacht wird.
> * Wenn Sie die Eigenschaften eines vorhandenen Bots in der [Liste Ihrer Bots in Bot Framework](https://dev.botframework.com/bots) bearbeiten, wie z. B. den "Messaging-Endpunkt", der bei der ersten Entwicklung eines Bots üblich ist, insbesondere wenn Sie [ngrok](https://ngrok.com)verwenden, sehen Sie die Spalte "Migrationsstatus" und eine blaue Schaltfläche "Migrieren", die Sie in das Microsoft Azure Portal führt. Klicken Sie nicht auf die Schaltfläche "Migrieren", es sei denn, Sie möchten dies tun. Klicken Sie stattdessen auf den Namen des Bots und Sie können seine Eigenschaften bearbeiten:</br>
   ![Bearbeiten von Bot-Eigenschaften](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Wenn Sie Ihren Bot mit Microsoft Azure registrieren, muss Ihr Bot-Code nicht auf Microsoft Azure *gehostet* werden.
> * Wenn Sie einen Bot über das Microsoft Azure-Portal registrieren, müssen Sie über ein Microsoft Azure-Konto verfügen. Sie können [kostenlos ein Konto erstellen](https://azure.microsoft.com/free/). Um Ihre Identität beim Erstellen zu überprüfen, müssen Sie eine Kreditkarte angeben, die jedoch nicht belastet wird. es ist immer kostenlos, Bots mit Microsoft Teams zu erstellen und zu verwenden.
> * Sie können App Studio jetzt verwenden, um App- und Bot-Informationen direkt in Microsoft Teams zu registrieren/aktualisieren. Sie müssen nur das Microsoft Azure Portal verwenden, um andere Bot Framework-Kanäle wie Direct Line, Web Chat, Skype und Facebook Messenger hinzuzufügen oder zu konfigurieren.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).