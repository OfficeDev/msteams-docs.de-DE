---
title: Hinzufügen von Power Virtual Agents-Chatbot zu Teams
author: laujan
description: Integrieren eines Power Virtual Agents-Chatbots in die Teams-Plattform
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 6103e3b58d7283eab6e9a9932f6dc7778d6fc697
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697095"
---
# <a name="integrate-a-power-virtual-agents-chatbot-with-microsoft-teams"></a>Integrieren eines Power Virtual Agents-Chatbots in Microsoft Teams

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist eine ohne Code geführte grafische Benutzeroberflächenlösung, mit der jedes Mitglied Ihres Teams umfassende, unterhaltungsgesteuerte Chatbots erstellen kann, die problemlos in die Teams-Plattform integriert werden können. Alle inhalte, die in Power Virtual Agents erstellt wurden, werden natürlich in Teams- und Power Virtual Agents-Bots gerendert, die mit Benutzern im systemeigenen Teams-Chatbereich interagieren. Ihre IT-Administratoren, Geschäftsanalysten, Domänenspezialisten und erfahrenen App-Entwickler können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten, einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren zu müssen.  *Weitere* [Informationen finden Sie unter Create a chatbot for Teams with Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).

> [!NOTE]
> Durch das Hinzufügen Ihres Chatbots zu Microsoft Teams werden einige Daten, z. B. Botinhalte und Chatinhalte für Endbenutzer, für Microsoft Teams freigegeben (d. h., Ihre Daten werden außerhalb der Compliance- und geografischen oder regionalen Grenzen Ihrer Organisation [fließen).](/power-virtual-agents/data-location) <br/>
> Weitere Informationen finden Sie unter [Sicherheit und Compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="make-your-chatbot-available-in-teams-via-the-power-virtual-agents-portal"></a>Machen Sie Ihren Chatbot über das Power Virtual Agents-Portal in Teams verfügbar

1. **Veröffentlichen Sie die neuesten Botinhalte**.  Nachdem Sie einen Chatbot im [Power Virtual Agents-Portal](https://powervirtualagents.microsoft.com)erstellt haben, müssen Sie Ihren Bot mindestens einmal veröffentlichen, bevor Teams-Benutzer mit ihm interagieren können. Weitere [Informationen finden Sie unter Publish the latest bot content](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

![Veröffentlichen im Power Virtual Agents-Portal](../../assets/images/pva-publish.png)

2. **Konfigurieren Des Teams-Kanals**. Nach der Veröffentlichung ihres Bots können Sie den Teams-Kanal hinzufügen, um den Bot für Teams-Benutzer verfügbar zu machen.

![Kanäle im Power Virtual Agents-Portal](../../assets/images/pva-channels.png)

3. **Generieren Sie eine App-ID für Ihren Chatbot**.  Wenn der Teams-Kanal ihrem Chatbot erfolgreich hinzugefügt wurde, wird im Dialogfeld eine **App-ID** generiert. Die App-ID ist ein eindeutiger von Microsoft generierter Bezeichner für Ihren Bot.  Kopieren und speichern Sie die App-ID – Sie benötigen sie später, um ein App-Paket für Teams zu erstellen.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Hinzufügen ihres Bots zu Teams mithilfe von App Studio

Wenn [das Hochladen benutzerdefinierter](/microsoftteams/admin-settings) Apps in Ihrer Teams-Instanz aktiviert ist, können Sie Teams App Studio verwenden, um Ihren Chatbot direkt hochzuladen und sofort mit der Verwendung zu beginnen. Wenn Sie Ihren Chatbot freigeben möchten, können Sie anfordern, dass Ihr Administrator Ihren Bot im Mandanten-App-Katalog verfügbar macht, oder Sie können andere Ihr App-Paket senden und ihn bitten, es unabhängig hochzuladen.

1. **Installieren von App Studio in Teams**. App Studio ist eine Teams-App, die Sie im Teams Store installieren können, wodurch die Erstellung und Registrierung Ihres Bots in Teams vereinfacht wird: 

  * Wählen Sie das App Store-Symbol unten in der linken Navigationsleiste in Ihrer Teams-Instanz aus, und suchen Sie **nach App Studio**.
>

&emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="/msteams-docs/msteams-platform/assets/images/get-started/app-studio-store.png"/>   

  * Wählen Sie **die Kachel App Studio** aus, und klicken Sie im Popupdialogfeld auf Installieren. 
>
&emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

2. **Erstellen Sie das Teams-App-Manifest in App Studio**.  Bots in Teams werden durch eine App-Manifestdatei (App Manifest, JSON) definiert, die grundlegende Informationen zu Ihrem Bot und dessen Funktionen enthält. Wählen **Sie in App Studio** manifest **editor** Create a new   =>  **app aus.**
3. **Fügen Sie Ihre Botdetails hinzu.** Eine vollständige Beschreibung der einzelnen Felds finden Sie unter [Manifestschemadefinition](../../resources/schema/manifest-schema.md). Stellen Sie sicher, dass sie alle erforderlichen Felder ausfüllen.
4. **Richten Sie Ihren Bot ein.** Navigieren Sie zur **Registerkarte Bots,** wählen Sie die **Schaltfläche Setup** aus, wählen **Sie Vorhandener Bot** aus, und geben Sie Ihren Botnamen ein.
5. **Fügen Sie Ihre App-ID hinzu.** Navigieren Sie **zu Verbinden mit einer anderen Bot-ID,** und fügen Sie die **App-ID ein, die** Sie zuvor kopiert haben. Wählen Sie unter Bereich **Personal aus,** und wählen Sie dann **Speichern aus.**
6. **Fügen Sie gültige Domänen für Ihren Bot hinzu.**  Dieser Schritt ist nur erforderlich, wenn der Bot die Anmeldung des Benutzers erfordert. Navigieren Sie **zu Domänen und Berechtigungen,** und geben Sie im Feld **Gültige Domänen** Folgendes ein:

```bash
token.botframework.com
```

7.  **Testen und verteilen Sie Ihren Bot.** Wählen Sie die **Registerkarte Testen und Verteilen** aus, und wählen Sie **Installieren** aus, um Ihren Bot direkt zu Ihrer Teams-Instanz hinzuzufügen. Optional können Sie Ihr fertiges App-Paket herunterladen, um es für Teams-Benutzer frei zu machen, oder es Ihrem Administrator zur Verfügung stellen, um Ihren Bot im Mandanten-App-Katalog verfügbar zu machen.
8. **Starten Sie einen Chat**. Der Setupprozess zum Hinzufügen Ihres Power Virtual Agents-Chatbots zu Teams ist abgeschlossen. Sie können jetzt eine Unterhaltung mit Ihrem Bot in einem persönlichen Chat starten.

> [!div class="nextstepaction"]
> [Weitere Informationen: Veröffentlichen Ihres Power Virtual Agents-Bots](/power-virtual-agents/publication-fundamentals-publish-channels)
