---
title: Hinzufügen Power Virtual Agents Chatbot zu Teams
author: laujan
description: Integrieren eines Power Virtual Agents Chatbots in die Teams Plattform
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: bd1528d06f9e9f4ca3a03f167ecb3c537977fb61
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058621"
---
# <a name="add-power-virtual-agents-chatbot"></a>Hinzufügen eines Power Virtual Agent-Chatbots 

Power Virtual Agents ist eine ohne Code geführte grafische Benutzeroberflächenlösung, mit der jedes Mitglied Ihres Teams umfassende chatbots erstellen kann, die sich problemlos in die Teams integrieren lassen. Alle inhalte, die in Power Virtual Agents geschrieben werden, werden natürlich in Teams. Power Virtual Agents Bots interagieren mit Benutzern in der Teams nativen Chat-Canvas. Die IT-Administratoren, Geschäftsanalysten, Domänenspezialisten und erfahrenen App-Entwickler können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten zu müssen. Sie können einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren. 

In diesem Dokument erfahren Sie, wie Sie Ihren Chatbot in Teams über das Power Virtual Agents-Portal verfügbar machen und Ihren Bot mithilfe von App Studio Teams hinzufügen. 

Power Virtual Agents können Sie leistungsstarke Chatbots erstellen, die Fragen beantworten können, die von Ihren Kunden, anderen Mitarbeitern oder Besuchern Ihrer Website oder Ihres Dienstes gestellt werden.

Diese Bots können problemlos erstellt werden, ohne dass Datenforscher oder Entwickler benötigt werden müssen.

> [!NOTE]
> Durch hinzufügen des Chatbots zu Microsoft Teams werden einige der Daten, z. B. Botinhalte und Benutzerchatinhalte, für Microsoft Teams. Das bedeutet, dass Ihre Daten außerhalb der Compliance und der geografischen oder regionalen Grenzen Ihrer [Organisation fließen.](/power-virtual-agents/data-location) <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Machen Sie Ihren Chatbot in Teams über das Power Virtual Agents verfügbar

Um Ihren Chatbot im Teams über das Power Virtual Agents verfügbar zu machen, müssen Sie die folgenden Prozessschritte ausführen:

**So stellen Sie den Chatbot in Teams**

1. **Veröffentlichen der neuesten Botinhalte**  
Nachdem Sie einen Chatbot im Power Virtual Agents erstellt haben, müssen Sie Ihren Bot veröffentlichen, bevor Teams Benutzer mit ihm interagieren können. Weitere Informationen finden Sie unter [Publish the latest bot content](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

   ![Veröffentlichen im Power Virtual Agents-Portal](../../assets/images/pva-publish.png)

1. **Konfigurieren des Teams Kanals**  
Fügen Sie nach der Veröffentlichung des Bots den Teams hinzu, um den Bot für Teams verfügbar zu machen.

   ![Kanäle im Power Virtual Agents-Portal](../../assets/images/pva-channels.png)

1. **Generieren einer App-ID für Ihren Chatbot**  
Nachdem Sie den Teams ihrem Chatbot hinzugefügt haben, wird im Dialogfeld eine **App-ID** generiert. Die App-ID ist ein eindeutiger von Microsoft generierter Bezeichner für Ihren Bot. Speichern Sie die App-ID, um ein App-Paket für Teams.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Hinzufügen ihres Bots Teams App Studio

Wenn [das Hochladen](/microsoftteams/admin-settings) benutzerdefinierter Apps in Ihrer Teams-Instanz aktiviert ist, können Sie Teams App Studio verwenden, um Ihren Chatbot direkt hochzuladen und sofort mit der Verwendung zu beginnen. Um Ihren Chatbot zu teilen, können Sie Ihren Administrator bitten, Ihren Bot im Mandanten-App-Katalog verfügbar zu machen, oder Sie können Ihr App-Paket an andere senden und ihn bitten, es unabhängig hochzuladen.

1. **Installieren von App Studio in Teams**  
App Studio ist eine Teams App. Installieren Sie App Studio aus dem Teams, der die Erstellung und Registrierung von Bots in den Teams: 

   1. Wählen Sie das App Store-Symbol aus Teams aus, und suchen Sie **nach App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. Wählen Sie **die Kachel App Studio** aus, und wählen Sie **im** Popupdialogfeld Installieren aus.

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Erstellen des Teams-App-Manifests in App Studio**  
Bots in Teams werden durch eine App-Manifest-JSON-Datei definiert, die die grundlegenden Informationen zu Ihrem Bot und seinen Funktionen enthält. Wählen **Sie in App Studio** manifest **editor** aus, und wählen Sie Neue App erstellen **aus.**  
Die folgenden Bildanleitungen zum Erstellen einer neuen App in App Studio:  

   ![Erstellen einer neuen App](../../assets/images/get-started/create-new-app.png)

1. **Hinzufügen von Botdetails**  
Füllen Sie alle erforderlichen Felder aus. Eine vollständige Beschreibung der einzelnen Felds finden Sie unter [Manifestschemadefinition](../../resources/schema/manifest-schema.md).   
Mit den folgenden Bildern können Sie die App-Details hinzufügen:  

   ![Hinzufügen von App-Details](../../assets/images/get-started/add-app-details.png)

1. **Einrichten des Bots** Führen Sie zum Einrichten des Bots die folgenden Schritte aus: 
     1. Öffnen Sie die **Registerkarte Bots.** 
     1. Wählen **Sie**  >  **Vorhandenen Bot einrichten aus,** und geben Sie den Namen Ihres Bots ein.

   Die folgenden Bildanleitungen zum Einrichten eines Bots:    

   ![Bot-Einrichtung](../../assets/images/get-started/bot-set-up.png) 

   Die folgenden Bildanleitungen zum Einrichten eines vorhandenen Bots:      

   ![vorhandene Bot-Einrichtung](../../assets/images/get-started/existing-bot-set-up.png)    
1. **Hinzufügen Ihrer App-ID**  
Führen Sie die folgenden Schritte aus, um Ihre App-ID hinzuzufügen:  
    1. Wählen **Verbinden eine andere Bot-ID aus, und** fügen Sie die **App-ID** ein, die Sie zuvor kopiert haben. 
    1. Wählen **Sie Bereich**  >  **Persönliches Speichern**  >  **aus.**      
Die folgenden Bildanleitungen zum Einrichten eines vorhandenen Bots:    

   ![Hinzufügen der App-ID](../../assets/images/get-started/add-app-id.png)

1. **Hinzufügen gültiger Domänen für Ihren Bot**  
Dieser Schritt ist nur erforderlich, wenn der Bot die Anmeldung des Benutzers erfordert. Wählen **Sie Domänen und Berechtigungen** aus, und geben Sie im Feld **Gültige** Domänen die folgende Eingabe an:

    ```bash
       token.botframework.com
    ```

7.  **Testen und Verteilen des Bots**  
Öffnen **Sie die Registerkarte** Testen und Verteilen, und wählen Sie **Installieren** aus, um Ihren Bot direkt zu Ihrer Teams hinzuzufügen. Alternativ können Sie das fertige App-Paket herunterladen, um es für Teams Benutzer frei zu geben, oder es Ihrem Administrator zur Verfügung stellen, um Ihren Bot im Mandanten-App-Katalog verfügbar zu machen.

8. **Starten eines Chats**   
Der Einrichtungsprozess für das Hinzufügen ihres Power Virtual Agents Chatbots zu Teams ist abgeschlossen. Sie können jetzt eine Unterhaltung mit Ihrem Bot in einem persönlichen Chat starten.

## <a name="see-also"></a>Siehe auch

- [Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

- [Erstellen eines Chatbots für Teams mit Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).  

- [Power Virtual Agents Portal](https://powervirtualagents.microsoft.com)

- [Veröffentlichen ihres Power Virtual Agents Bots](/power-virtual-agents/publication-fundamentals-publish-channels)

- [Sicherheit und Compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines virtuellen Assistenten](~/samples/virtual-assistant.md)

