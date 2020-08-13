---
title: Debuggen Ihrer Teams-App
description: Beschreibt die Schritte, die zum Ausführen und Debuggen von Microsoft Teams-apps unternommen werden müssen.
keywords: Teams führen Debug-Apps aus
ms.topic: conceptual
ms.openlocfilehash: 913306bd24a55797e72396a031d917ec99c43bb9
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652029"
---
# <a name="debugging-your-teams-app"></a>Debuggen Ihrer Teams-App

Microsoft Teams-Apps können eine oder mehrere Funktionen enthalten, und die Möglichkeiten zum Ausführen oder sogar hosten können unterschiedlich sein. Wenn es um das Debugging geht, haben wir im allgemeinen folgende Möglichkeiten, um Ihre Microsoft Teams-App auszuführen:

* **Rein lokal** &emsp; Für Bots können Sie Ihre Erfahrung im bot-Emulator testen. Für andere Inhalte können Sie lokal in Ihrem Browser ausführen und Inhalte über `http://localhost` .
* **Lokal gehostet in Microsoft Teams** &emsp; Dies umfasst das lokale Ausführen mit Tunneling-Software und das [Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) , das in Teams [hochgeladen](~/concepts/deploy-and-publish/apps-upload.md) werden soll. Auf diese Weise können Sie Ihre APP im Microsoft Teams-Client ganz einfach ausführen und Debuggen.
* **In Teams in der Cloud gehostet** Dadurch wird die Unterstützung einer Teams-App auf Produktionsebene wirklich simuliert (oder ist dies auch). Es umfasst das Hochladen Ihrer Lösung auf Ihren extern zugänglichen Server oder Cloud-Anbieter Ihrer Wahl (Wir empfehlen natürlich Azure) und das [Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) , das in Teams [hochgeladen](~/concepts/deploy-and-publish/apps-upload.md) werden soll.

Für rein lokale oder lokale Test Teams führen Sie die Benutzeroberfläche auf Ihrem eigenen Computer aus. Auf diese Weise können Sie tatsächlich in Ihrer IDE kompilieren und ausführen und diese Techniken wie Haltepunkte und das schrittweise Debuggen vollständig nutzen. Für das Debuggen und Testen im Produktionsumfang empfehlen wir, dass Sie Ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung über eigene Prozesse unterstützen können.

Im Allgemeinen wird empfohlen, dass Sie mehrere Manifeste und Pakete verwenden, damit Sie die Trennung zwischen Produktions-und Entwicklungsdiensten aufrecht erhalten können. Sie können beispielsweise getrennte Entwicklungs-und Produktions-Bots registrieren und entsprechende Pakete erstellen, um diese in Ihre Testumgebung hochzuladen. Außerdem empfehlen wir Ihnen, Ihr Produktionspaket hochzuladen und zu testen, bevor Sie Ihre APP für die Veröffentlichung in unserem App Store übermitteln oder an Kunden verteilen.

## <a name="purely-local"></a>Rein lokal

> [!NOTE]
> Wenn Sie auf diese Weise vorgehen, erhalten Sie keinen Zugriff auf die APP-Funktionen von Teams oder Teams-spezifische bot-Funktionen wie Dienstplan Aufrufe und andere kanalspezifische Funktionen. Darüber hinaus sind einige Funktionen möglicherweise durch das bot-Framework im bot-Emulator zulässig, der bei der Ausführung in Microsoft Teams möglicherweise nicht funktioniert.

Ihr Bot kann innerhalb des bot-Emulators ausgeführt werden. Auf diese Weise können Sie einige der Kern Logik des bot testen, ein grobes Layout von Nachrichten sehen und einfache Tests durchführen. Die Schritte sind hier aufgeführt:

* Lokal ausführen des Codes
* Starten Sie den bot-Emulator, und legen Sie die URL fest:
  * Node.js: `http://localhost:3978/api/messages`
  * .NET/C#: `http://localhost:3979/api/messages`
* Lassen Sie die Microsoft App-ID und das Microsoft App-Kennwort leer, damit Sie den Standard Umgebungsvariablen entsprechen.

## <a name="locally-hosted"></a>Lokal gehostet

Da es sich bei Microsoft Teams um ein vollständig Cloud-basiertes Produkt handelt, müssen alle Dienste, auf die es zugreift, öffentlich über HTTPS-Endpunkte zur Verfügung stehen. Damit Ihre APP in Microsoft Teams funktioniert, müssen Sie daher entweder den Code in der Cloud Ihrer Wahl veröffentlichen oder extern auf unsere lokale Instanz mit externer Ausführung zugreifen können. Letztere können mit Tunneling-Software durchführen.

Obwohl Sie ein beliebiges Tool verwenden können, verwenden und empfehlen wir [ngrok](https://ngrok.com/download), wodurch eine extern adressierbare URL für einen Port erstellt wird, den Sie lokal auf Ihrem Computer öffnen. So richten Sie ngrok in Vorbereitung für die Ausführung Ihrer Microsoft Teams-App lokal ein:

* Wechseln Sie in einer Terminalanwendung in das Verzeichnis, in dem Sie ngrok.exe installiert haben. Möglicherweise möchten Sie es als Path-Variable hinzufügen, um diesen Schritt zu vermeiden.
* Führen Sie beispielsweise aus, `ngrok http 3978 --host-header=localhost:3978` oder ersetzen Sie die Portnummer bei Bedarf.

Dadurch wird ngrok gestartet, um den angegebenen Port abzuhören. Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL.

Wenn Sie ngrok in Ihrem Projekt verwenden möchten, müssen Sie in Abhängigkeit von den von Ihnen verwendeten Funktionen alle URL-Verweise in Ihrem Code, ihrer Konfiguration und/oder manifest.jsin der Datei ersetzen, um diesen URL-Endpunkt zu verwenden.

Aktualisieren Sie beispielsweise für Bots, die im Microsoft bot-Framework registriert sind, den Messaging-Endpunkt des bot, um diesen neuen ngrok-Endpunkt zu verwenden. Beispiel: `https://2d1224fb.ngrok.io/api/messages`. Sie können überprüfen, ob ngrok arbeitet, indem Sie die bot-Antwort im Test Chatfenster des bot-Framework-Portals testen. (Wie beim Emulator können Sie mit diesem Test auch nicht auf Teams-spezifische Funktionen zugreifen.)

> [!NOTE]
> Um den Messaging-Endpunkt für einen bot zu aktualisieren, müssen Sie das bot-Framework verwenden. Klicken Sie in der [Liste der Bots im bot-Framework](https://dev.botframework.com/bots)auf Ihren bot. Sie müssen ihren bot nicht zu Microsoft Azure migrieren. Sie können den Messaging-Endpunkt auch über [App Studio](~/concepts/build-and-test/app-studio-overview.md)aktualisieren.

## <a name="cloud-hosted"></a>In der Cloud gehostet

Sie können einen beliebigen extern adressierbaren Dienst verwenden, um ihren Entwicklungs-und Produktionscode sowie deren HTTPS-Endpunkte zu hosten. Es besteht keine Erwartung, dass sich ihre Funktionen im gleichen Dienst befinden. Es ist erforderlich, dass alle Domänen, auf die über Ihre Microsoft Teams-apps zugegriffen wird, im [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) Objekt im manifest.jsauf Datei aufgeführt sind.

> [!NOTE]
> Um eine sichere Umgebung sicherzustellen, sollten Sie die genaue Domäne und Unterdomänen, auf die Sie verweisen, explizit überprüfen, und diese Domänen müssen sich in Ihrem Steuerelement befinden. Beispielsweise wäre `*.azurewebsites.net` dies nicht empfehlenswert, `contoso.azurewebsites.net` würde dies jedoch tun.

## <a name="loading-and-running"></a>Laden und Ausführung

Im Allgemeinen müssen Sie zum Laden und Ausführen Ihrer Benutzeroberfläche in Microsoft Teams ein Paket erstellen und es mithilfe der folgenden Anleitung in Teams hochladen:

* [Erstellen des Pakets für Ihre Microsoft Teams-App](~/concepts/build-and-test/apps-package.md)
* [Hochladen Ihrer APP in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md)
