---
title: Power Virtual Agents Chatbot zu Teams hinzufügen
author: laujan
description: Integration eines Power Virtual Agents Chatbots in die Teams Plattform
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 2a8f9c23eaa1acf2555b91cc4caf8d0f3298c114
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566117"
---
# <a name="add-power-virtual-agents-chatbot"></a>Hinzufügen eines Power Virtual Agent-Chatbots 

Power Virtual Agents ist eine codefreie, geführte grafische Benutzeroberfläche, die es jedem Mitglied Ihres Teams ermöglicht, umfangreiche, konversationsfähige Chatbots zu erstellen, die sich problemlos in die Teams-Plattform integrieren lassen. Alle inhalte, die in Power Virtual Agents erstellt werden, werden auf natürliche Weise in Teams gerendert. Power Virtual Agents Bots interagieren mit Benutzern in der Teams nativen Chat-Canvas. IT-Administratoren, Business Analysten, Domänenspezialisten und erfahrene App-Entwickler können intelligente virtuelle Agenten für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten zu müssen. Sie können einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren. 

Dieses Dokument führt Sie darüber, wie Sie Ihren Chatbot in Teams über das Power Virtual Agents-Portal verfügbar machen und Ihren Bot mit App Studio zu Teams hinzufügen. 

mit Power Virtual Agents können Sie leistungsstarke Chatbots erstellen, die Fragen beantworten können, die von Ihren Kunden, anderen Mitarbeitern oder Besuchern Ihrer Website oder Ihres Dienstes gestellt werden.

Diese Bots können leicht erstellt werden, ohne dass Datenwissenschaftler oder Entwickler benötigt werden.

> [!NOTE]
> Durch das Hinzufügen Ihres Chatbots zu Microsoft Teams werden einige der Daten, wie Bot-Inhalte und Benutzer-Chat-Inhalte, mit Microsoft Teams geteilt. Das bedeutet, dass Ihre Daten außerhalb der [Compliance- und geografischen oder regionalen Grenzen](/power-virtual-agents/data-location)Ihrer Organisation fließen. <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Stellen Sie Ihren Chatbot in Teams über das Power Virtual Agents-Portal zur Verfügung

Um Ihren Chatbot in Teams über das Power Virtual Agents-Portal verfügbar zu machen, müssen Sie die folgenden Prozessschritte ausführen:

**So stellen Sie den Chatbot in Teams**

1. **Veröffentlichen der neuesten Bot-Inhalte**  
Nachdem Sie einen Chatbot im Power Virtual Agents Portal erstellt haben, müssen Sie Ihren Bot veröffentlichen, bevor Teams Benutzer mit ihm interagieren können. Weitere Informationen finden Sie unter [Veröffentlichen der neuesten Bot-Inhalte](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

   ![Veröffentlichen im Power Virtual Agents Portal](../../assets/images/pva-publish.png)

1. **Konfigurieren des Teams Kanals**  
Nachdem Sie Ihren Bot veröffentlicht haben, fügen Sie den Teams-Kanal hinzu, um den Bot Teams Benutzern zur Verfügung zu stellen.

   ![Kanäle im Power Virtual Agents Portal](../../assets/images/pva-channels.png)

1. **Generieren einer App-ID für Ihren Chatbot**  
Nach dem Hinzufügen des Teams Kanals zu Ihrem Chatbot wird im Dialogfeld eine **App-ID** generiert. Die App-ID ist ein eindeutiger von Microsoft generierter Bezeichner für Ihren Bot. Speichern Sie die App-ID, um ein App-Paket für Teams zu erstellen.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Fügen Sie Ihren Bot mit App Studio zu Teams hinzu

Wenn das [Hochladen benutzerdefinierter Apps](/microsoftteams/admin-settings) in Ihrer Teams-Instanz aktiviert ist, können Sie Teams App Studio verwenden, um Ihren Chatbot direkt hochzuladen und sofort zu verwenden. Um Ihren Chatbot freizugeben, können Sie Ihren Administrator auffordern, Ihren Bot im Mandanten-App-Katalog verfügbar zu machen, oder Sie können Ihr App-Paket an andere senden und sie bitten, es unabhängig hochzuladen.

1. **Installieren von App Studio in Teams**  
App Studio ist eine Teams App. Installieren Sie App Studio aus dem Teams Store, der den Prozess der Boterstellung und -registrierung in Teams vereinfacht: 

   1. Wählen Sie das App Store-Symbol aus Teams Instanz aus, und suchen Sie nach **App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. Wählen Sie die **Kachel App Studio** aus, und wählen Sie im Popup-Dialogfeld installieren aus. 

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Erstellen des Teams-App-Manifests in App Studio**  
Bots in Teams werden durch eine App-Manifest-JSON-Datei definiert, die die grundlegenden Informationen über Ihren Bot und seine Funktionen bereitstellt. Wählen Sie in **App Studio** **den Manifest-Editor** aus, und wählen Sie **eine neue App erstellen** aus.

    ![Erstellen einer neuen App](../../assets/images/get-started/create-new-app.png)

1. **Fügen Sie Ihre Bot-Details hinzu**  
Füllen Sie alle erforderlichen Felder aus. Eine vollständige Beschreibung der einzelnen Felde finden Sie unter [Manifestschemadefinition](../../resources/schema/manifest-schema.md).

    ![Hinzufügen von App-Details](../../assets/images/get-started/add-app-details.png)

1. **Einrichten Ihres Bots** Führen Sie die folgenden Schritte aus, um den Bot einzurichten: 
     1. Öffnen Sie die Registerkarte **Bots.** 
     1. Wählen Sie **Vorhandene**  >  **Bots** einrichten aus und geben Sie den Namen Ihres Bots ein.

   ![Bot-Setup](../../assets/images/get-started/bot-set-up.png) 

   Die folgende Abbildung zeigt, wie Sie einen vorhandenen Bot einrichten:      

   ![bestehende Bot-Einrichtung](../../assets/images/get-started/existing-bot-set-up.png)
       
1. **Hinzufügen Ihrer App-ID**  
Führen Sie die folgenden Schritte aus, um Ihre App-ID hinzuzufügen:  
    1. Wählen Sie **Verbinden einer anderen Bot-ID** aus und fügen Sie die **App-ID ein,** die Sie zuvor kopiert haben. 
    1. Wählen Sie **Bereich**  >    >  **Persönlichespeichern**.

    ![App-ID hinzufügen](../../assets/images/get-started/add-app-id.png)

1. **Hinzufügen gültiger Domänen für Ihren Bot**  
Dieser Schritt ist nur erforderlich, wenn Ihr Bot erfordert, dass sich der Benutzer anmeldet. Wählen Sie **Domänen und Berechtigungen** aus, und geben Sie im Feld Gültige **Domänen** die folgenden Eingaben an:

    ```bash
       token.botframework.com
    ```

1. **Testen und verteilen Sie Ihren Bot**  
Öffnen Sie die Registerkarte **Testen und verteilen,** und wählen Sie **Installieren** aus, um Ihren Bot direkt zu Ihrer Teams-Instanz hinzuzufügen. Alternativ können Sie das fertige App-Paket herunterladen, um es für Teams Benutzer freizugeben, oder es Ihrem Administrator zur Verfügung stellen, um Ihren Bot im Mandanten-App-Katalog verfügbar zu machen.

1. **Starten eines Chats**   
Der Einrichtungsprozess zum Hinzufügen Ihres Power Virtual Agents Chat-Bots zu Teams ist abgeschlossen. Sie können jetzt ein Gespräch mit Ihrem Bot in einem persönlichen Chat beginnen.

## <a name="see-also"></a>Siehe auch

- [Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

- [Erstellen Sie einen Chatbot für Teams mit Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).  

- [Power Virtual Agents Portal](https://powervirtualagents.microsoft.com)

- [Veröffentlichen Sie Ihren Power Virtual Agents-Bot](/power-virtual-agents/publication-fundamentals-publish-channels)

- [Sicherheit und Compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Virtueller Assistent erstellen](~/samples/virtual-assistant.md)

