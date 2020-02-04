---
title: Erstellen eines Bots
description: Beschreibt das Erstellen von Bots in Microsoft Teams
keywords: Erstellen von Teams-Bots
ms.date: 12/07/2018
ms.openlocfilehash: cb2d0974baf1d36a4acf077c219eb12449a5721a
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674129"
---
# <a name="create-a-bot"></a>Erstellen eines Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Alle Bots, die mit dem Microsoft bot Framework erstellt wurden, sind konfiguriert und können in Microsoft Teams verwendet werden.

In der [bot-Framework-Dokumentation](/azure/bot-service/?view=azure-bot-service-3.0) finden Sie allgemeine Informationen zu Bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Erstellen eines bot für Microsoft Teams

*Teams App Studio* ist ein Tool, mit dem Sie Ihren bot erstellen können, und ein App-Paket, das auf Ihren bot verweist. Es enthält auch eine Reaktions Steuerungs Bibliothek und konfigurierbare Beispiele für Karten. Weitere Informationen finden Sie unter [Erste Schritte mit Microsoft Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). In den folgenden Schritten wird davon ausgegangen, dass Sie den bot und nicht die Verwendung von *Teams App Studio*manuell konfigurieren.

1. Erstellen Sie den Bot mithilfe dieses Links https://dev.botframework.com/bots/new:. **Stellen Sie sicher, dass Sie Microsoft Teams als Kanal aus der Liste der vorgestellten Kanäle hinzufügen, nachdem Sie Ihren bot erstellt haben.** Fühlen Sie sich frei, jede von Ihnen generierte Microsoft-App-ID wiederzuverwenden, wenn Sie Ihr App-Paket/Manifest bereits erstellt haben.

   ![Seite "bot Framework-Registrierung"](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Wenn Sie Ihren bot in Azure nicht erstellen möchten, **müssen** Sie diesen Link verwenden, um einen neuen bot zu erstellen: https://dev.botframework.com/bots/new. Wenn Sie stattdessen im bot-Framework-Portal auf die Schaltfläche *Create a bot* klicken, [Erstellen Sie stattdessen Ihren bot in Microsoft Azure](#bots-and-microsoft-azure) .

2. Erstellen Sie den Bot mithilfe des [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Pakets, des [botbuilder-Teams NPM-](https://www.npmjs.com/package/botbuilder-teams) Pakets oder der [bot Connector-API](https://docs.microsoft.com/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Testen Sie den Bot mithilfe des [bot Framework-Emulators](https://docs.microsoft.com/bot-framework/debug-bots-emulator).

4. Stellen Sie den bot für einen clouddienst bereit, beispielsweise [Microsoft Azure](https://azure.microsoft.com/). Alternativ können Sie Ihre APP lokal ausführen und einen Tunnel Dienst wie [ngrok](https://ngrok.com) verwenden, um einen https://-Endpunkt für Ihren bot anzuzeigen, `https://45az0eb1.ngrok.io/api/messages`beispielsweise.

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots und Microsoft Azure
> Seit Dezember 2017 ist das bot-Framework-Portal für die Registrierung von Bots in Microsoft Azure optimiert. Hier sind einige Dinge, die Sie kennen sollten:
>
> * Der Microsoft Teams-Kanal für Bots, die in Azure registriert sind, ist kostenlos. Nachrichten, die über den Teams-Kanal gesendet werden, werden nicht auf die verbrauchten Nachrichten für den bot gezählt.
> * Obwohl es möglich ist, [einen neuen bot-Framework-bot](https://dev.botframework.com/bots/new) ohne Verwendung von Azure zu erstellen, müssen Siehttps://dev.botframework.com/bots/new)diese URL verwenden (, die nicht mehr im bot-Framework-Portal verfügbar gemacht wird.
> * Wenn Sie die Eigenschaften eines vorhandenen bot in der [Liste Ihrer Bots im bot-Framework](https://dev.botframework.com/bots) wie seinen "Messaging Endpoint" Bearbeiten, was bei der ersten Entwicklung eines bot üblich ist, insbesondere wenn Sie [ngrok](https://ngrok.com)verwenden, wird die Spalte "Migrationsstatus" und eine blaue "migrieren"-Schaltfläche angezeigt, die Sie in das Microsoft Azure Portal einführt. Klicken Sie nicht auf die Schaltfläche "migrieren", es sei denn, Sie möchten dies tun; Klicken Sie stattdessen auf den Namen des bot, und Sie können seine Eigenschaften bearbeiten:</br>
   ![Eigenschaften von bot bearbeiten](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Wenn Sie Ihren bot mit Microsoft Azure registrieren, muss Ihr bot-Code nicht auf Microsoft Azure *gehostet* werden.
> * Wenn Sie einen bot über Microsoft Azure Portal registrieren, benötigen Sie ein Microsoft Azure Konto. Sie können [eine kostenlos erstellen](https://azure.microsoft.com/free/). Um Ihre Identität zu überprüfen, wenn Sie eine erstellen, müssen Sie eine Kreditkarte angeben, aber es wird nicht aufgeladen werden; Es ist immer kostenlos, Bots mit Microsoft Teams zu erstellen und zu verwenden.
> * Sie können jetzt APP Studio zum Registrieren/Aktualisieren von App-und bot-Informationen direkt in Microsoft Teams verwenden. Sie müssen nur das Microsoft Azure-Portal zum Hinzufügen/Konfigurieren anderer bot-Framework-Kanäle wie Direktverbindung, Chat, Skype und Facebook-Messenger verwenden.
