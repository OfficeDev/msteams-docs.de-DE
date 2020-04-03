---
title: Erstellen einer APP für Microsoft Teams
author: clearab
description: Verstehen Sie den typischen Prozess für das Erstellen einer APP für Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 7ec67c52f9321579da34c490175f6becc3a8fdfd
ms.sourcegitcommit: 058b7bbd817af5f513e0e018f2ef562dc3086a84
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "43120255"
---
# <a name="building-an-app-for-microsoft-teams"></a>Erstellen einer APP für Microsoft Teams

Das Erstellen und Verteilen einer auf der Microsoft Teams-Plattform erstellten App umfasst die Entscheidung, was erstellt werden soll, Erstellen von Webdiensten, Erstellen eines App-Pakets und verteilen dieses Pakets an die Ziel Endbenutzer. Es ist an den Administratoren eines Unternehmens zu entscheiden, wer auf Ihre App zugreifen und diese installieren kann, und es ist Ihre Benutzer, Ihre APP in einem bestimmten Kontext zu installieren.

## <a name="design-a-great-app"></a>Entwerfen einer tollen App

Der wichtigste Schritt beim Erstellen einer erfolgreichen App für Microsoft Teams ist die Auswahl der richtigen Kombinations Erweiterungspunkte und der Benutzeroberflächenelemente, die Sie nutzen können. Manchmal ist dies eine ziemlich einfache Entscheidung, aber für komplexere apps sollten Sie viel Zeit damit verbringen, das Problem zu verstehen, das Sie mit Ihrer APP lösen möchten, und Ihre Lösung auf die verschiedenen Arten abzubilden, mit denen Benutzer mit Ihrer APP im Microsoft Teams-Client interagieren können. Unterschätzen Sie nicht die Wichtigkeit von Kontext und Bereich! Ein Konversations-bot, der in einem 1:1-Chat sehr gut funktioniert, funktioniert möglicherweise nicht im Rahmen eines Gruppenchats oder einer Kanal Unterhaltung.

1. Verstehen Sie zunächst [die Microsoft Teams-Client Erweiterungspunkte und Benutzeroberflächenelemente, die](~/concepts/extensibility-points.md) für Ihre app verfügbar sind.

2. Stellen Sie anschließend sicher, dass Sie [Ihre Anwendungsfälle verstehen](~/concepts/design/understand-use-cases.md).

3. [Ordnen Sie schließlich ihre Anwendungsfälle den Features der Microsoft Teams-Plattform zu](~/concepts/design/map-use-cases.md).

Nachdem Sie sich für die Erweiterungspunkte und Features entschieden haben, die Ihre APP nutzen wird, sollten Sie diese Interaktionen überdenken. Je nach Design Ihrer APP sollten Sie sich Folgendes ansehen:

* [Entwerfen großer Registerkarten](~/tabs/design/tabs.md)
* [Entwerfen nützlicher Unterhaltungs Bots](~/bots/design/bots.md)

## <a name="prepare-your-environment"></a>Vorbereiten der Umgebung

Sie müssen sicherstellen, dass Sie über eine Umgebung verfügen, in der Sie Ihre Teams-App hochladen und testen können. Wenn Sie noch kein O365-Abonnement mit aktivierten Teams haben und die Möglichkeit zum Hochladen von apps darauf haben, können Sie [sich für das O365-Entwicklerprogramm registrieren](https://developer.microsoft.com/microsoft-365/dev-program) , das Ihnen Zugriff auf ein kostenloses Office 365 Abonnement für Entwicklungszwecke bietet.

Weitere Informationen finden Sie unter [Vorbereiten der O365-Umgebung](~/concepts/build-and-test/prepare-your-o365-tenant.md) .

## <a name="build-and-test-your-app"></a>Erstellen und Testen Ihrer APP

Das Erstellen und Testen Ihrer APP für Microsoft Teams unterscheidet sich nicht wesentlich von der Erstellung anderer Webanwendungen. Der wichtigste Unterschied besteht darin, dass Sie Ihr App-Manifest in Ihrem App-Paket verwenden müssen, um den Microsoft Teams-Client mit ihren Webdiensten zu verbinden. Jedes Mal, wenn Sie eine Änderung am APP-Manifest vornehmen, müssen Sie Ihr App-Paket erneut hochladen und Ihre APP in Microsoft Teams aktualisieren, indem Sie Sie erneut installieren. Änderungen am Webdienst erfordern jedoch nicht die erneute Installation Ihrer APP im Microsoft Teams-Client.

Wenn Sie Ihre APP anfänglich erstellen, werden Sie regelmäßig sowohl Ihre Webdienste als auch Ihr App-Paket aktualisieren, um die app in der Regel erneut hochzuladen und die APP mehrmals im Microsoft Teams-Client zu installieren (insbesondere beim erstmaligen Einrichten Ihrer APP). Da das, was Sie gerade erstellen, die Notwendigkeit einer Änderung des App-Manifests jedoch stabilisiert, werden Sie in erster Linie Änderungen an Ihrem Webdienst vornehmen.

### <a name="build-your-web-services"></a>Erstellen von Webdiensten

Nachdem Sie festgelegt haben, wie Benutzer mit Ihrer APP interagieren, müssen Sie die Webdienste erstellen, um Sie zu vernetzen. Je nachdem, was Sie erstellen, bietet Microsoft Teams verschiedene SDKs, Vorlagen, Codebeispiele und Generatoren, die Ihnen den Einstieg erleichtern, einschließlich:

* Bot-Framework-SDK für [Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) und [Unterhaltungs Bots](~/bots/what-are-bots.md)
* Microsoft Teams JavaScript Client SDK für [Registerkarten](~/tabs/what-are-tabs.md) und andere Inhaltsseiten
* Ein Autobauer- [Generator](~/tutorials/get-started-yeoman.md) zum Erstellen von apps in Node. js
* **Vorschau anzeigen** Eine Gruppe von Open-Source-Steuerelementen für Ihre Webinhalts Seiten – [Fluent-Benutzeroberfläche](https://microsoft.github.io/fluent-ui-react/)
* Ready-for-Production- [App-Vorlagen](~/samples/app-templates.md)
* Verschiedene [Beispiele](~/samples/code-samples.md) , die Ihnen den Einstieg erleichtern

Denken Sie daran, dass Sie Ihre Webdienste so hosten müssen, dass Sie über das Internet öffentlich zugänglich sind (in der Regel in einem Anbieter von Cloud-Diensten wie Azure) und ihre Inhalte über HTTPS bereitstellen.

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie müssen außerdem ein App-Paket erstellen, das in Microsoft Teams verteilt und installiert werden kann. Das App-Paket enthält zwei Symbole und eine JSON-Manifestdatei, die die Metadaten für Ihre APP, die Erweiterungspunkte, die Ihre APP verwendet, und Zeiger auf die Dienste, die diese Erweiterungspunkte antreiben, beschreiben.

Wenn Sie Ihr App-Paket erstellen, können Sie es manuell erstellen oder App Studio verwenden, bei dem es sich um eine APP innerhalb von Teams handelt, die Ihnen dabei hilft, Microsoft Teams-Apps (wir wissen, sehr Meta) zu machen. App Studio führt Sie durch das Erstellen Ihres App-Manifests und kann Ihnen helfen, ihren bot mit dem bot-Framework zu registrieren. Es enthält auch einen Karten-Designer, der Ihnen beim visuellen Erstellen von Karten-und Karten Aktionen hilft und Beispiele für sich selbst in Microsoft Teams sendet.

## <a name="distributing-your-app"></a>Verteilen Ihrer APP

Sie haben drei Möglichkeiten, [Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/apps-publish.md)je nach Zielgruppe zu verteilen.

* **Teilen Sie Ihr App-Paket direkt.** Sie können beschließen, Ihr App-Paket direkt für Benutzer freizugeben. Dies ist besonders nützlich, wenn Ihre APP auf eine beschränkte Zielgruppe (nur ein paar Teams oder Einzelpersonen) und während der Entwicklung und des Tests Ihrer APP ausgerichtet ist.
  
* **Veröffentlichen Sie Ihre APP in Ihrem Organisations-App-Katalog.** Wenn Ihre APP für eine bestimmte Organisation gilt (oder wenn Sie Ihre APP so angepasst haben, dass Sie den spezifischen Anforderungen einer Organisation entspricht), kann ein mandantenadministrator Ihre APP in den App-Katalog der Organisation hochladen. Dadurch ist Ihre APP für alle Benutzer in der Organisation verfügbar (wird jedoch nicht automatisch installiert).
  
* **Veröffentlichen Sie Ihre APP im öffentlichen App Store.** Wenn Ihre APP für alle Microsoft Teams-Benutzer überall vorgesehen ist, können Sie Ihre APP zur Veröffentlichung im öffentlichen App Store übermitteln. Sie müssen einen rigorosen Überprüfungsprozess durchlaufen, um sicherzustellen, dass Sie Ihre i-Punkte punktiert haben und Ihr t-gekreuzt haben.

Wenn Sie Ihre APP verteilen, müssen Sie nicht nur die gewünschte Zielgruppe berücksichtigen, sondern auch die IT-Richtlinien in der Organisation, für die Sie Ihre APP freigeben möchten. Jede Organisation verfügt über die vollständige Kontrolle darüber, welche apps in den Organisations-App-Katalog hochgeladen werden und welche apps für die Installation aus dem App Store zur Verfügung stehen.

### <a name="the-app-you-create-versus-the-app-your-users-install"></a>Die von Ihnen erstellte App im Vergleich zu der APP, die Ihre Benutzer installieren

Ihre APP kann mehrere Erweiterbarkeitspunkte im Teams-Client nutzen und in einer Vielzahl von Bereichen arbeiten. Mit Ihrem App-Paket, das Sie an Benutzer verteilen, werden alle diese als einzelne Entität definiert. Da allerdings alle App-Installationen in Microsoft Teams *kontextspezifisch*sind, wird die Gesamtheit ihrer App möglicherweise nicht immer für alle Benutzer installiert.

Stellen Sie sich beispielsweise vor, dass Ihre APP einen Unterhaltungs-bot enthält, der sowohl in persönlichen als auch in Team Unterhaltungen sowie sowohl auf einer persönlichen als auch auf einer Kanal Registerkarte funktioniert. Wenn Ihre APP installiert ist, wird Sie in einem bestimmten Kontext installiert-wenn ein Benutzer die app in einem Team installiert, haben Sie nicht unbedingt den persönlichen Teil Ihrer APP installiert. Dies kann zunächst etwas verwirrend sein, aber denken Sie daran, nie zu erwarten, dass alle Teile ihrer app in einem bestimmten Kontext installiert und konfiguriert werden.

## <a name="get-started-quickly"></a>Schneller Einstieg

Möchten Sie schnell loslegen? Schauen Sie sich eines unserer Lernprogramme für erste Schritte oder einen Schnellstart für ein bestimmtes Platt Form Feature an (das in den einzelnen Featurebereichen der Dokumentation zu finden ist).

Lernprogramme für erste Schritte:

* [Erstellen einer bot-und Tab-app in C #](~/tutorials/get-started-dotnet-app-studio.md)
* [Erstellen einer bot-und Tab-app in JavaScript/Node. js](~/tutorials/get-started-nodejs-app-studio.md)
* [Erstellen einer APP mit dem "landkraft-Generator"](~/tutorials/get-started-yeoman.md)
