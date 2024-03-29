---
title: Erstellen eines Bots
description: In diesem Modul erfahren Sie, wie Sie bots mithilfe der Microsoft Bot Framework erstellen und in Microsoft Teams arbeiten können.
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 12/07/2018
ms.openlocfilehash: 66b0557308e2d76332e1a5b0fcba06ac596822c4
ms.sourcegitcommit: 69a45722c5c09477bbff3ba1520e6c81d2d2d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2022
ms.locfileid: "67312100"
---
# <a name="create-a-bot"></a>Erstellen eines Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Alle Bots, die mithilfe der Microsoft Bot Framework erstellt wurden, sind konfiguriert und können in Microsoft Teams verwendet werden.

Weitere Informationen finden Sie in der [Bot Framework-Dokumentation](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) für allgemeine Informationen zu Bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

**Das Teams-Entwicklerportal für Teams** ist ein Tool, mit dem Sie Ihren Bot erstellen können, und ein App-Paket, das auf Ihren Bot verweist. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Weitere Informationen finden Sie unter ["Erste Schritte mit dem Teams Developer Portal für Teams"](~/concepts/build-and-test/teams-developer-portal.md). Bei den folgenden Schritten wird davon ausgegangen, dass Sie ihren Bot manuell konfigurieren und nicht **das Teams Developer Portal für Teams** verwenden:

1. Erstellen Sie den Bot mit Bot [Framework](https://dev.botframework.com/bots/new). **Achten Sie darauf, dass Sie Microsoft Teams nach der Erstellung Ihres Bots aus der Liste der empfohlenen Kanäle als Kanal hinzufügen.** Sie können eine von Ihnen generierte Microsoft-App-ID wiederverwenden, wenn Sie Ihr App-Paket/-Manifest bereits erstellt haben.

   ![Bot Framework-Registrierungsseite](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Wenn Sie Ihren Bot nicht in Azure erstellen möchten, **müssen** Sie diesen Link verwenden, um einen neuen Bot zu erstellen: [Bot Framework](https://dev.botframework.com/bots/new). Wenn Sie stattdessen im Bot Framework-Portal auf " **Bot** erstellen" klicken, [erstellen Sie Ihren Bot stattdessen in Microsoft Azure](#bots-and-microsoft-azure) .

2. Erstellen Sie den Bot mit dem [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket, dem  [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) oder der [Bot Connector-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Testen Sie den Bot mithilfe der [Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Stellen Sie den Bot für einen Clouddienst bereit, z. B. [Microsoft Azure](https://azure.microsoft.com/). Alternativ können Sie Ihre App lokal ausführen und einen Tunneldienst wie [ngrok](https://ngrok.com) verwenden, um einen https:// Endpunkt für Ihren Bot verfügbar zu machen, z `https://45az0eb1.ngrok.io/api/messages`. B. .

> [!NOTE]
>
> ## <a name="bots-and-microsoft-azure"></a>Bots und Microsoft Azure
>
> Seit Dezember 2017 ist das Bot Framework-Portal für die Registrierung von Bots in Microsoft Azure optimiert. Hier sind einige weitere Punkte, die Sie wissen sollten:
>
> * Der Microsoft Teams-Kanal für in Azure registrierte Bots ist kostenlos. Über den Teams-Kanal gesendete Nachrichten zählen nicht zu den verbrauchten Nachrichten für den Bot.
> * Es ist zwar möglich, [einen neuen Bot Framework-Bot zu erstellen](https://dev.botframework.com/bots/new) , ohne Azure zu verwenden, sie müssen jedoch [einen neuen Bot Framework-Bot](https://dev.botframework.com/bots/new) verwenden, der nicht mehr im Bot Framework-Portal verfügbar gemacht wird.
> * Wenn Sie die Eigenschaften eines vorhandenen Bots in der [Liste Ihrer Bots in Bot Framework](https://dev.botframework.com/bots) bearbeiten, z. B. den "Messaging-Endpunkt", der bei der ersten Entwicklung eines Bots üblich ist, insbesondere wenn Sie [ngrok](https://ngrok.com) verwenden, werden die Spalte "Migrationsstatus" und die blaue Schaltfläche "Migrieren" angezeigt, mit der Sie in die Microsoft Azure-Portal gelangen. Klicken Sie nicht auf die Schaltfläche "Migrieren", es sei denn, Sie möchten dies tun. klicken Sie stattdessen auf den Namen des Bots, und Sie können dessen Eigenschaften bearbeiten:</br>
   ![Bearbeiten von Bot-Eigenschaften](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Wenn Sie Ihren Bot mit Microsoft Azure registrieren, muss Ihr Botcode nicht in Microsoft Azure *gehostet* werden.
> * Wenn Sie einen Bot mit Azure-Portal registrieren, müssen Sie über ein Microsoft Azure-Konto verfügen. Sie können [kostenlos ein Konto erstellen](https://azure.microsoft.com/free/). Um Ihre Identität zu überprüfen, wenn Sie eine erstellen, müssen Sie eine Kreditkarte angeben, die jedoch nicht belastet wird. Es ist immer kostenlos, Bots mit Teams zu erstellen und zu verwenden.
> * Sie können jetzt das Entwicklerportal für Teams verwenden, um App- und Bot-Informationen direkt in Teams zu registrieren/zu aktualisieren. Sie müssen die Azure-Portal nur zum Hinzufügen oder Konfigurieren anderer Bot Framework-Kanäle wie Direct Line, Webchat, Skype und Facebook Messenger verwenden.

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
