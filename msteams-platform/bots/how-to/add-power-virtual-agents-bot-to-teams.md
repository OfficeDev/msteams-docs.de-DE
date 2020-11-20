---
title: Hinzufügen von Power Virtual Agents Chatbot zu Teams
author: laujan
description: Integrieren eines Power Virtual Agents Chatbot in die Teams-Plattform
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 3f877505cb2ef20bbd74d236dc17816df04bbef1
ms.sourcegitcommit: 43e1be9d9e3651ce73a8d2139e44d75550a0ca60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "49366868"
---
# <a name="integrate-a-power-virtual-agents-chatbot-with-microsoft-teams"></a>Integrieren einer Power Virtual Agents Chatbot mit Microsoft Teams

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist eine codelose, geführte grafische Schnittstellenlösung, die es jedem Mitglied Ihres Teams ermöglicht, umfangreiche Unterhaltungs Chatbots zu erstellen, die sich problemlos in die Microsoft Teams-Plattform integrieren lassen. Alle Inhalte, die in Power Virtual Agents erstellt wurden, werden in Microsoft Teams und Power Virtual Agent-Bots mit Benutzern im nativen Chatbereich von Teams gerendert. Ihre IT-Administratoren, Geschäftsanalysten, Domänen Spezialisten und erfahrenen App-Entwickler können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten, einen Webdienst erstellen oder sich direkt im bot-Framework registrieren zu müssen.  *Weitere Informationen finden Sie unter* [Create a Chatbot for Teams with Microsoft Power Virtual Agents](../what-are-bots.md#create-a-chatbot-for-teams-with-microsoft-power-virtual-agents).

> [!NOTE]
> Durch das Hinzufügen Ihrer Chatbot zu Microsoft Teams werden einige Daten, wie bot-und Endbenutzer Chatinhalte, für Microsoft Teams freigegeben (was bedeutet, dass Ihre Daten außerhalb der [Compliance-und geografischen oder regionalen Grenzen Ihrer Organisation](/power-virtual-agents/data-location)fließen werden). <br/>
> Weitere Informationen finden Sie unter [Sicherheit und Compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="make-your-chatbot-available-in-teams-via-the-power-virtual-agents-portal"></a>Stellen Sie Ihre Chatbot in Microsoft Teams über das Portal Power Virtual Agents zur Verfügung.

1. **Veröffentlichen Sie die neuesten bot-Inhalte**.  Nachdem Sie im [Portal Power Virtual Agents](https://powervirtualagents.microsoft.com)ein Chatbot erstellt haben, müssen Sie Ihren bot mindestens einmal veröffentlichen, bevor Microsoft Teams mit dem-Benutzer interagieren können. Weitere Informationen finden Sie unter [Veröffentlichen der neuesten bot-Inhalte](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

![Portal zum Veröffentlichen in Power Virtual Agents](../../assets/images/pva-publish.png)

2. **Konfigurieren des Teams-Kanals**. Nachdem Sie Ihren bot veröffentlicht haben, können Sie den Teams-Kanal hinzufügen, um den bot für Microsoft Teams-Benutzer verfügbar zu machen.

![Kanäle im Portal Power Virtual Agents](../../assets/images/pva-channels.png)

3. **Generieren Sie eine APP-ID für Ihre Chatbot**.  Wenn der Microsoft Teams-Kanal Ihrem Chatbot erfolgreich hinzugefügt wurde, wird im Dialogfeld eine **App-ID** generiert. Die APP-ID ist ein eindeutiger von Microsoft generierter Bezeichner für Ihren bot.  Kopieren und speichern Sie die APP-ID – Sie benötigen Sie später, um ein App-Paket für Microsoft Teams zu erstellen.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Hinzufügen Ihres bot zu Microsoft Teams mithilfe von App Studio

Wenn das [Hochladen benutzerdefinierter apps](/microsoftteams/admin-settings) in Ihrer Teams-Instanz aktiviert ist, können Sie Microsoft Teams App Studio verwenden, um Ihre Chatbot direkt hochzuladen und sofort zu verwenden. Wenn Sie Ihre Chatbot freigeben möchten, können Sie anfordern, dass Ihr Administrator Ihren bot im Mandanten-App-Katalog zur Verfügung stellt, oder Sie können anderen Ihr App-Paket senden und ihn bitten, ihn unabhängig voneinander hochzuladen.

1. **Installieren Sie App Studio in Microsoft Teams**. App Studio ist eine Microsoft Teams-APP, die Sie im Microsoft Teams Store installieren können, die die Erstellung und Registrierung Ihres bot in Microsoft Teams vereinfacht: 

  * Wählen Sie das App Store-Symbol am unteren Rand der linken Navigationsleiste in Ihrer Teams-Instanz aus, und suchen Sie nach **App Studio**.
>

&emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="/msteams-docs/msteams-platform/assets/images/get-started/app-studio-store.png"/>   

  * Wählen Sie die Kachel **App Studio** aus, und wählen Sie im Popupdialogfeld **Installieren** aus.
>
&emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

2. **Erstellen Sie das Teams-App-Manifest in App Studio**.  Bots in Microsoft Teams werden durch eine APP-Manifestdatei (JSON) definiert, die grundlegende Informationen zu Ihrem bot und seinen Funktionen bereitstellt. Erstellen Sie in **App Studio** **Manifest-Editor**   =>  **eine neue APP**.
3. **Fügen Sie Ihre bot-Details hinzu**. Eine vollständige Beschreibung der einzelnen Felder finden Sie unter [Manifest Schema Definition](../../resources/schema/manifest-schema.md). Stellen Sie sicher, dass Sie alle erforderlichen Felder ausfüllen.
4. **Richten Sie Ihren bot ein**. Navigieren Sie zur Registerkarte **Bots** , wählen Sie die Schaltfläche **Setup** , wählen Sie **vorhandenen bot** aus, und geben Sie Ihren bot-Namen ein.
5. **Fügen Sie Ihre APP-ID hinzu**. Navigieren Sie zu **einer anderen bot-ID** , und fügen Sie die **App-ID** ein, die Sie zuvor kopiert haben. Wählen Sie Unterbereich die Option **persönlich** aus, und wählen Sie dann **Speichern** aus.
6. **Fügen Sie gültige Domänen für Ihren bot hinzu**.  Dieser Schritt ist nur erforderlich, wenn sich der Benutzer bei Ihrem bot anmelden muss. Navigieren Sie zu **Domänen und Berechtigungen** , und geben Sie im Feld **gültige Domänen** Folgendes ein:

```bash
token.botframework.com
```

7.  **Testen und verteilen Sie Ihren bot**. Klicken Sie auf die Registerkarte **Test and Distribute** und dann auf **Installieren** , um Ihren bot direkt zu Ihrer Teams-Instanz hinzuzufügen. Optional können Sie Ihr abgeschlossenes App-Paket herunterladen, um Sie für Microsoft Teams-Benutzer freizugeben oder es Ihrem Administrator zur Verfügung zu stellen, damit Ihr bot im Mandanten-App-Katalog verfügbar ist.
8. **Starten Sie einen Chat**. Der Setupprozess für das Hinzufügen Ihrer Power Virtual Agents Chat Bot zu Teams ist abgeschlossen. Sie können jetzt eine Unterhaltung mit Ihrem bot in einem persönlichen Chat starten.

> [!div class="nextstepaction"]
> [Weitere Informationen: veröffentlichen Sie Ihre Power Virtual Agents bot](/power-virtual-agents/publication-fundamentals-publish-channels)
