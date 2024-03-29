---
title: Hinzufügen eines Power Virtual Agent-Chatbots
author: surbhigupta
description: Erfahren Sie, wie Sie einen Power Virtual Agents-Chatbot in die Teams-Plattform integrieren, um Unterhaltungs-Chatbots zu erstellen und ihn in Teams zu integrieren.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 310b7d8a5e04259a205763b45cb2d2315c19c72a
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485202"
---
# <a name="add-power-virtual-agents-chatbot"></a>Hinzufügen eines Power Virtual Agent-Chatbots

Power Virtual Agents ist eine codelose, geführte grafische Benutzeroberflächenlösung, die es jedem Mitglied Ihres Teams ermöglicht, umfangreiche, unterhaltungsbezogene Chatbots zu erstellen, die sich einfach in die Teams-Plattform integrieren lassen. Alle in Power Virtual Agents erstellten Inhalte werden natürlich in Teams gerendert. Power Virtual Agents-Bots interagieren mit Benutzern in der nativen Chat-Canvas von Teams. It-Administratoren, Geschäftsanalysten, Domänenspezialisten und erfahrene App-Entwickler können intelligente virtuelle Agents für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten zu müssen. Sie können einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren.

In diesem Dokument erfahren Sie, wie Sie Ihren Chatbot über das Power Virtual Agents-Portal in Teams verfügbar machen und Ihren Bot mithilfe von App Studio zu Teams hinzufügen.

Mit Power Virtual Agents können Sie leistungsstarke Chatbots erstellen, die Fragen beantworten können, die von Ihren Kunden, anderen Mitarbeitern oder Besuchern Ihrer Website oder Ihres Diensts gestellt werden.

Diese Bots können problemlos erstellt werden, ohne dass Data Scientists oder Entwickler benötigt werden müssen.

> [!NOTE]
>
> * Indem Sie Ihren Chatbot zu Microsoft Teams hinzufügen, werden einige der Daten, z. B. Bot-Inhalte und Benutzerchatinhalte, für Teams freigegeben. Dies bedeutet, dass Ihre Daten außerhalb der [Compliance- und geografischen oder regionalen Grenzen Ihrer Organisation](/power-virtual-agents/data-location) fließen. <br/>
> * Sie dürfen mit Microsoft Power Platform erstellte Apps nicht im Teams App Store veröffentlichen. Microsoft Power Platform-Apps können nur im App Store einer Organisation veröffentlicht werden.

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a>Bereitstellen Ihres Chatbots in Teams über das Power Virtual Agents-Portal

Um Ihren Chatbot in Teams über das Power Virtual Agents-Portal verfügbar zu machen, müssen Sie die folgenden Prozessschritte ausführen:

So stellen Sie den Chatbot in Teams zur Verfügung:

1. **Veröffentlichen der neuesten Bot-Inhalte**  
Nachdem Sie einen Chatbot im Power Virtual Agents-Portal erstellt haben, müssen Sie Ihren Bot veröffentlichen, bevor Teams-Benutzer damit interagieren können. Weitere Informationen finden Sie unter [Veröffentlichen der neuesten Bot-Inhalte](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).

   ![Veröffentlichen im Power Virtual Agents-Portal](../../assets/images/pva-publish.png)

1. **Konfigurieren des Teams-Kanals**  
Fügen Sie nach der Veröffentlichung Ihres Bots den Teams-Kanal hinzu, um den Bot für Teams-Benutzer verfügbar zu machen.

   ![Kanäle im Power Virtual Agents-Portal](../../assets/images/pva-channels.png)

1. **Generieren einer App-ID für Ihren Chatbot**  
Nach dem Hinzufügen des Teams-Kanals zu Ihrem Chatbot wird im Dialogfeld eine **App-ID** generiert. Die App-ID ist ein eindeutiger von Microsoft generierter Bezeichner für Ihren Bot. Speichern Sie die App-ID, um ein App-Paket für Teams zu erstellen.

## <a name="add-your-bot-to-teams-using-app-studio"></a>Hinzufügen Ihres Bots zu Teams mitHilfe von App Studio

Wenn [das Hochladen benutzerdefinierter Apps](/microsoftteams/admin-settings) in Ihrer Teams-Instanz aktiviert ist, können Sie Teams App Studio verwenden, um Ihren Chatbot direkt hochzuladen und sofort damit zu beginnen. Um Ihren Chatbot freizugeben, können Sie Ihren Administrator bitten, Ihren Bot im Mandanten-App-Katalog zur Verfügung zu stellen, oder Sie können Ihr App-Paket an andere Personen senden und ihn bitten, es unabhängig hochzuladen.

1. **Installieren von App Studio in Teams**  
App Studio ist eine Teams-App. Installieren Sie App Studio aus dem Teams-Store, der die Erstellung und Registrierung von Bots in Teams vereinfacht:

   1. Wählen Sie das App Store-Symbol aus der Teams-Instanz aus, und suchen Sie nach **App Studio**.

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>

   1. Wählen Sie die **App Studio-Kachel** und dann im Popupdialogfeld " **Installieren** " aus.

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. **Erstellen des Teams-App-Manifests in App Studio**  
Bots in Teams werden durch eine JSON-Datei des App-Manifests definiert, die die grundlegenden Informationen zu Ihrem Bot und seinen Funktionen bereitstellt. Wählen Sie in **App Studio** den **Manifest-Editor** und dann **"Neue App erstellen**" aus.

    ![Erstellen einer neuen App](../../assets/images/get-started/create-new-app.png)

1. **Hinzufügen von Bot-Details**  
Füllen Sie alle erforderlichen Felder aus. Eine vollständige Beschreibung der einzelnen Felder finden Sie unter [Manifestschemadefinition](../../resources/schema/manifest-schema.md).

    ![App-Details hinzufügen](../../assets/images/get-started/add-app-details.png)

1. **Einrichten Ihres Bots** Führen Sie zum Einrichten des Bots die folgenden Schritte aus:
     1. Öffnen Sie die Registerkarte **"Bots** ".
     1. Wählen Sie "**Vorhandenen Bot** **einrichten"** >  aus, und geben Sie den Namen Ihres Bots ein.

   ![Bot-Einrichtung](../../assets/images/get-started/bot-set-up.png)

   Die folgende Abbildung zeigt, wie Sie einen vorhandenen Bot einrichten:

   ![Vorhandene Bot-Einrichtung](../../assets/images/get-started/existing-bot-set-up.png)

1. **Hinzufügen Ihrer App-ID**  
Führen Sie die folgenden Schritte aus, um Ihre App-ID hinzuzufügen:  
    1. Wählen Sie **"Mit einer anderen Bot-ID verbinden** " aus, und fügen Sie die zuvor kopierte **App-ID** ein.
    1. Wählen Sie **bereichsbezogenes** > **persönliches** > **Speichern aus**.

    ![App-ID hinzufügen](../../assets/images/get-started/add-app-id.png)

1. **Hinzufügen gültiger Domänen für Ihren Bot**  
Dieser Schritt ist nur erforderlich, wenn ihr Bot die Anmeldung des Benutzers erfordert. Wählen Sie **"Domänen und Berechtigungen** " aus, und geben Sie im Feld **"Gültige Domänen** " die folgende Eingabe ein:

    ```bash
       token.botframework.com
    ```

1. **Testen und Verteilen Ihres Bots**  
Öffnen Sie die Registerkarte **"Testen und verteilen** ", und wählen Sie " **Installieren** " aus, um Ihren Bot direkt zu Ihrer Teams-Instanz hinzuzufügen. Alternativ können Sie das fertige App-Paket herunterladen, um es für Teams-Benutzer freizugeben, oder es Ihrem Administrator bereitstellen, um Ihren Bot im Mandanten-App-Katalog verfügbar zu machen.

1. **Starten eines Chats** Der Einrichtungsprozess zum Hinzufügen Ihres Power Virtual Agents-Chat-Bots zu Teams ist abgeschlossen. Sie können jetzt eine Unterhaltung mit Ihrem Bot in einem persönlichen Chat beginnen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines virtuellen Assistenten](~/samples/virtual-assistant.md)

## <a name="see-also"></a>Siehe auch

* [Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  
* [Erstellen eines Chatbots für Teams mit Microsoft Power Virtual Agents](../bot-features.md#bots-with-power-virtual-agents)
* [Power Virtual Agents-Portal](https://powervirtualagents.microsoft.com)
* [Veröffentlichen Ihres Power Virtual Agents-Bots](/power-virtual-agents/publication-fundamentals-publish-channels)
* [Sicherheit und Compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview)
* [Power Virtual Agents-Bot für Personalwesen](/power-virtual-agents/teams/fundamentals-get-started-teams)
