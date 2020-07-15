---
title: Erstellen einer APP für Microsoft Teams
author: clearab
description: Verstehen Sie den typischen Prozess für das Erstellen einer APP für Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 748b5cf6c6bc1bf51c1f647348012057627d2679
ms.sourcegitcommit: d0ca6a4856ffd03d197d47338e633126723fa78a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "45137647"
---
# <a name="building-an-app-for-microsoft-teams"></a>Erstellen einer APP für Microsoft Teams

> [!NOTE] 
> Sie möchten schnell loslegen? Sie können Teams-apps mit dem [Microsoft Teams-Toolkit und Visual Studio Code](../toolkit/visual-studio-code-overview.md)erstellen.

Das Erstellen und Verteilen einer App, die auf der Microsoft Teams-Plattform erstellt wurde, beinhaltet auch die Entscheidung dahingehend, was erstellt werden soll, den Aufbau Ihrer Webdienste, das Erstellen eines App-Pakets und das Verteilen dieses Pakets an die Zielgruppe Ihrer Endbenutzer. Die Entscheidung darüber, wer auf Ihre App zugreifen und diese installieren kann, liegt bei den Administratoren einer Organisation. Hingegen ist es Aufgabe Ihrer Benutzer, Ihre App in einem bestimmten Kontext zu installieren.

## <a name="design-a-great-app"></a>Entwerfen einer tollen App

Der wichtigste Schritt bei der Erstellung einer erfolgreichen App für Microsoft Teams ist die Auswahl der richtigen Kombination an Erweiterungspunkten und der Benutzeroberflächenelemente, die genutzt werden. Manchmal ist dies eine ziemlich einfache Entscheidung, aber für komplexere apps sollten Sie viel Zeit damit verbringen, das Problem zu verstehen, das Sie mit Ihrer APP lösen möchten, und Ihre Lösung auf die verschiedenen Arten abzubilden, mit denen Benutzer mit Ihrer APP im Microsoft Teams-Client interagieren können. Unterschätzen Sie nicht die Bedeutung von Kontext und Umfang! Ein Unterhaltungs-Bot, der in einem 1:1-Chat sehr gut funktioniert, ist möglicherweise für einen Gruppen- oder Kanalchat völlig ungeeignet.

1. Verstehen Sie zunächst [die Microsoft Teams-Client Erweiterungspunkte und Benutzeroberflächenelemente, die](~/concepts/extensibility-points.md) für Ihre app verfügbar sind.

2. Stellen Sie anschließend sicher, dass Sie [Ihre Anwendungsfälle verstehen](~/concepts/design/understand-use-cases.md).

3. [Ordnen Sie schließlich ihre Anwendungsfälle den Features der Microsoft Teams-Plattform zu](~/concepts/design/map-use-cases.md).

Nachdem Sie sich für die Erweiterungspunkte und Features entschieden haben, die Ihre APP nutzen wird, sollten Sie diese Interaktionen überdenken. Je nach Design Ihrer APP sollten Sie sich Folgendes ansehen:

* [Entwerfen großer Registerkarten](~/tabs/design/tabs.md)
* [Entwerfen nützlicher Unterhaltungs Bots](~/bots/design/bots.md)

## <a name="prepare-your-environment"></a>Vorbereiten der Umgebung

Sie müssen sicherstellen, dass Sie über eine Umgebung verfügen, in der Sie Ihre Teams-App hochladen und testen können. Wenn Sie noch kein O365-Abonnement mit aktivierten Teams haben und die Möglichkeit zum Hochladen von apps darauf haben, können Sie [sich für das O365-Entwicklerprogramm registrieren](https://developer.microsoft.com/microsoft-365/dev-program) , das Ihnen Zugriff auf ein kostenloses Office 365 Abonnement für Entwicklungszwecke bietet.

Weitere Informationen finden Sie unter [Vorbereiten der O365-Umgebung](~/concepts/build-and-test/prepare-your-o365-tenant.md) .

## <a name="build-and-test-your-app"></a>Erstellen und Testen Ihrer App

Das Erstellen und Testen Ihrer APP für Microsoft Teams unterscheidet sich nicht wesentlich von der Erstellung anderer Webanwendungen. Der wichtigste Unterschied besteht darin, dass Sie Ihr App-Manifest in Ihrem App-Paket verwenden müssen, um den Microsoft Teams-Client mit ihren Webdiensten zu verbinden. Jedes Mal, wenn Sie eine Änderung am APP-Manifest vornehmen, müssen Sie Ihr App-Paket erneut hochladen und Ihre APP in Microsoft Teams aktualisieren, indem Sie Sie erneut installieren. Änderungen am Webdienst erfordern jedoch nicht die erneute Installation Ihrer APP im Microsoft Teams-Client.

Wenn Sie Ihre APP anfänglich erstellen, werden Sie regelmäßig sowohl Ihre Webdienste als auch Ihr App-Paket aktualisieren, um die app in der Regel erneut hochzuladen und die APP mehrmals im Microsoft Teams-Client zu installieren (insbesondere beim erstmaligen Einrichten Ihrer APP). Da das, was Sie gerade erstellen, die Notwendigkeit einer Änderung des App-Manifests jedoch stabilisiert, werden Sie in erster Linie Änderungen an Ihrem Webdienst vornehmen.

### <a name="build-your-web-services"></a>Erstellen Ihrer Webdienste

Sobald Sie sich entschieden haben, wie Benutzer mit Ihrer App interagieren werden, ist es an der Zeit, die erforderlichen Webdienste zu erstellen, um die App leistungsfähig zu machen. Je nachdem, was Sie erstellen, werden in Teams verschiedene SDKs, Vorlagen, Codebeispiele und Generatoren bereitgestellt, die Ihnen bei den ersten Schritten helfen, unter anderem:

* Bot-Framework-SDK für [Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) und [Unterhaltungs Bots](~/bots/what-are-bots.md)
* Microsoft Teams JavaScript Client SDK für [Registerkarten](~/tabs/what-are-tabs.md) und andere Inhaltsseiten
* Ein [Generator](~/tutorials/get-started-yeoman.md) für die Erstellung von apps in Node.js
* **Vorschau anzeigen** Eine Gruppe von Open-Source-Steuerelementen für Ihre Webinhalts Seiten – [Fluent-Benutzeroberfläche](https://microsoft.github.io/fluent-ui-react/)
* Ready-for-Production- [App-Vorlagen](~/samples/app-templates.md)
* Verschiedene [Beispiele](~/samples/code-samples.md) , die Ihnen den Einstieg erleichtern

Denken Sie daran, dass Sie Ihre Webdienste derart hosten müssen, dass diese über das Internet öffentlich zugänglich sind (in der Regel in einem Cloud-Dienstanbieter wie Azure) und Ihre Inhalte über HTTPS verfügbar gemacht werden.

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie müssen außerdem ein App-Paket erstellen, das in Microsoft Teams verteilt und installiert werden kann. Das App-Paket beinhaltet zwei Symbole und eine JSON-Manifestdatei, in der die Metadaten für Ihre App, die von Ihrer App verwendeten Erweiterungspunkte sowie die Verweise auf die Dienste, die diese Erweiterungspunkte aktivieren/deaktivieren, beschrieben werden.

Beim Erstellen Ihres App-Paket können Sie wählen, ob Sie dieses manuell erstellen oder App Studio verwenden möchten. Bei App Studio handelt es sich um eine in Teams integrierte App, die Sie beim Gestalten von Teams-Apps unterstützt (sehr Meta-mäßig – ist uns bewusst). App Studio führt Sie durch die Erstellung Ihres App-Manifests und kann Ihnen dabei helfen, Ihren Bot im Bot-Framework zu registrieren. App Studio beinhaltet außerdem einen Karten-Designer, der Sie beim visuellen Erstellen von Karten und Kartenaktionen unterstützt und über den Sie in Teams Beispiele an sich selbst senden können.

## <a name="distributing-your-app"></a>Verteilen Ihrer APP

Sie haben drei Möglichkeiten, [Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/apps-publish.md)je nach Zielgruppe zu verteilen.

* **Teilen Sie Ihr App-Paket direkt.** Sie können Ihr App-Paket direkt für Benutzer freigeben. Dies ist besonders nützlich, wenn Ihre APP auf eine beschränkte Zielgruppe (nur ein paar Teams oder Einzelpersonen) und während der Entwicklung und des Tests Ihrer APP ausgerichtet ist.
  
* **Veröffentlichen Sie Ihre App im App-Katalog. Ihrer Organisation.** Wenn Ihre App sich für eine bestimmte Organisation eignet (oder Sie die App derart angepasst haben, dass diese den spezifischen Anforderungen einer Organisation entspricht), kann ein Mandantenadministrator Ihre App in den App-Katalog der Organisation hochladen. Dadurch steht Ihre App für alle Benutzer in der Organisation zur Verfügung und kann von diesen installiert werden (sie wird allerdings nicht automatisch installiert).
  
* **Veröffentlichen Sie Ihre App im öffentlichen App-Store.** Wenn sich Ihre App für alle Benutzer von Teams, ungeachtet dessen, wo sich diese befinden, eignet, können Sie Ihre App für eine Veröffentlichung im öffentlich zugänglichen App-Store übermitteln. Sie müssen ein sehr strenges Prüfungsverfahren durchlaufen, mit dem sichergestellt werden soll, dass alles bis ins kleinste Detail stimmt und funktioniert.

Beim Verteilen Ihrer App müssen Sie nicht nur die gewünschte Zielgruppe berücksichtigen, sondern auch die geltenden IT-Richtlinien der Organisation, für die Sie Ihre App freigeben möchten. Jede Organisation hat die völlige Kontrolle über die Festlegung, welche Apps in den App-Katalog der Organisation hochgeladen werden sollen und welche Apps aus dem App-Store zur Installation hochgeladen werden dürfen.

### <a name="the-app-you-create-versus-the-app-your-users-install"></a>Die von Ihnen erstellte App im Vergleich zu der APP, die Ihre Benutzer installieren

Ihre APP kann mehrere Erweiterbarkeitspunkte im Teams-Client nutzen und in einer Vielzahl von Bereichen arbeiten. Mit Ihrem App-Paket, das Sie an Benutzer verteilen, werden alle diese als einzelne Entität definiert. Da allerdings alle App-Installationen in Microsoft Teams *kontextspezifisch*sind, wird die Gesamtheit ihrer App möglicherweise nicht immer für alle Benutzer installiert.

Stellen Sie sich beispielsweise vor, dass Ihre APP einen Unterhaltungs-bot enthält, der sowohl in persönlichen als auch in Team Unterhaltungen sowie sowohl auf einer persönlichen als auch auf einer Kanal Registerkarte funktioniert. Wenn Ihre APP installiert ist, wird Sie in einem bestimmten Kontext installiert-wenn ein Benutzer die app in einem Team installiert, haben Sie nicht unbedingt den persönlichen Teil Ihrer APP installiert. Dies kann zunächst etwas verwirrend sein, aber denken Sie daran, nie zu erwarten, dass alle Teile ihrer app in einem bestimmten Kontext installiert und konfiguriert werden.

## <a name="getting-started-tutorials"></a>Lernprogramme für erste Schritte

* [Erstellen einer bot-und Tab-app in C #](~/tutorials/get-started-dotnet-app-studio.md)
* [Erstellen einer bot-und Tab-app in JavaScript/Node.js](~/tutorials/get-started-nodejs-app-studio.md)
* [Erstellen einer App mit dem Yeoman-Generator](~/tutorials/get-started-yeoman.md)
