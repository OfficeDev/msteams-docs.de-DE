---
title: Auswählen eines Setups zum Testen und Debuggen Ihrer App
description: Beschreibt Optionen zum Testen und Debuggen von Microsoft Teams-Apps.
keywords: Teams führen Debug-Apps aus
ms.topic: conceptual
ms.openlocfilehash: ea851a0d3ecf3ec87093bcc095050190a282c25e
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797799"
---
# <a name="choosing-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Auswählen eines Setups zum Testen und Debuggen Ihrer Microsoft Teams-App

Microsoft Teams apps can contain one or more capabilities, and the ways to run or even host them may be different. Wenn es um das Debuggen geht, haben wir im Allgemeinen die folgenden Möglichkeiten, Ihre Microsoft Teams-App auszuführen:

* **Rein lokal** &emsp; Für Bots können Sie Ihre Erfahrung im Bot Emulator testen. Für andere Inhalte können Sie lokal in Ihrem Browser ausführen und Inhalte über `http://localhost` adressieren.
* **Lokal gehostet in Teams** &emsp; Dies umfasst die lokale Ausführung mit Tunnelsoftware und [das Erstellen eines Pakets zum](~/concepts/build-and-test/apps-package.md) [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams. Auf diese Weise können Sie Ihre App ganz einfach im Teams-Client ausführen und debuggen.
* **In der Cloud gehostet, in Teams** Dies simuliert (oder ist) die Unterstützung auf Produktionsebene für eine Teams-App. Es umfasst das Hochladen Ihrer Lösung auf Ihren extern zugänglichen Server oder Cloudanbieter Ihrer Wahl (wir empfehlen Natürlich Azure) und das Erstellen eines Pakets, das in Teams [hochgeladen](~/concepts/deploy-and-publish/apps-upload.md) werden soll. [](~/concepts/build-and-test/apps-package.md)

Für rein lokale oder lokale Teams-Tests führen Sie die Erfahrung auf Ihrem eigenen Computer aus. Auf diese Weise können Sie in Ihrer IDE kompilieren und ausführen und von techniken wie Haltepunkten und Schrittweisem Debuggen profitieren. Für Das Debuggen und Testen im Produktionsmaßstab wird empfohlen, dass Sie ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung über Ihre eigenen Prozesse unterstützen können.

Im Allgemeinen wird empfohlen, mehrere Manifeste und Pakete zu verwenden, damit Sie die Trennung zwischen Produktions- und Entwicklungsdiensten beibehalten können. Beispielsweise können Sie separate Entwicklungs- und Produktionsbots registrieren und entsprechende Pakete erstellen, um sie in Ihre Testumgebung hochzuladen. Es wird außerdem empfohlen, das Produktionspaket hochzuladen und zu testen, bevor Sie Ihre App zur Veröffentlichung in unserem App Store übermitteln oder an Kunden verteilen.

## <a name="purely-local"></a>Rein lokal

> [!NOTE]
> Wenn Sie diese Methode ausführen, erhalten Sie keinen Zugriff auf die Funktionen der Teams-App oder Teams-spezifische Botfunktionen wie Dienstplanaufrufe und andere kanalspezifische Funktionen. Darüber hinaus sind einige Funktionen möglicherweise vom Bot Framework im Bot Emulator zulässig, die möglicherweise nicht funktionieren, wenn sie in Microsoft Teams ausgeführt werden.

Ihr Bot kann innerhalb des Bot emulators ausgeführt werden. Auf diese Weise können Sie einige der Kernlogik des Bots testen, ein grobes Layout von Nachrichten anzeigen und einfache Tests durchführen. Die Schritte sind hier aufgeführt:

* Ausführen des Codes lokal
* Starten Sie den Bot-Emulator, und legen Sie die URL bereit:
  * Node.js: `http://localhost:3978/api/messages`
  * .NET/C#: `http://localhost:3979/api/messages`
* Lassen Sie die Microsoft-App-ID und das Microsoft-App-Kennwort leer, um den Standardumgebungsvariablen zu entsprechen.

## <a name="locally-hosted"></a>Lokal gehostet

Da Es sich bei Microsoft Teams um ein vollständig cloudbasiertes Produkt handelt, müssen alle Dienste, auf die es zu zugegriffen wird, über die HTTPS-Endpunkte öffentlich verfügbar sein. Damit Ihre App in Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder die lokale ausgeführte Instanz extern zugänglich machen. Letzteres können wir mit Tunnelsoftware tun.

Obwohl Sie ein beliebiges Tool verwenden können, wird [ngrok](https://ngrok.com/download)verwendet und empfohlen, das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen. So richten Sie ngrok als Vorbereitung für die lokale Ausführung Ihrer Microsoft Teams-App ein:

* Wechseln Sie in einer Terminalanwendung zu dem Verzeichnis, in dem sie ngrok.exe haben. Sie können sie als Pfadvariable hinzufügen, um diesen Schritt zu vermeiden.
* Führen Sie z. B. `ngrok http 3978 --host-header=localhost:3978` die Portnummer aus, oder ersetzen Sie die Portnummer nach Bedarf.

Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port abzuhören. Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL.

Um ngrok in Ihrem Projekt zu verwenden, und je nach den verwendeten Funktionen müssen Sie alle URL-Verweise in Ihrem Code, Ihrer Konfiguration und/oder ihrer manifest.json-Datei ersetzen, um diesen URL-Endpunkt zu verwenden.

Aktualisieren Sie beispielsweise für Bots, die im Microsoft Bot Framework registriert sind, den Messagingendpunkt des Bots so, dass er diesen neuen ngrok-Endpunkt verwendet. Beispiel: `https://2d1224fb.ngrok.io/api/messages`. Sie können überprüfen, ob ngrok funktioniert, indem Sie die Botantwort im Testchatfenster des Bot-Framework-Portals testen. (Wie der Emulator lässt dieser Test auch hier keinen Zugriff auf Teams-spezifische Funktionen zu.)

> [!NOTE]
> Um den Nachrichtenendpunkt für einen Bot zu aktualisieren, müssen Sie das Bot Framework verwenden. Klicken Sie auf Ihren Bot in [Ihrer Liste der Bots im Bot Framework.](https://dev.botframework.com/bots) Sie müssen Ihren Bot nicht zu Microsoft Azure migrieren. Sie können Ihren Messagingendpunkt auch über [App Studio aktualisieren.](~/concepts/build-and-test/app-studio-overview.md)

## <a name="cloud-hosted"></a>In der Cloud gehostet

Sie können jeden extern adressierbaren Dienst verwenden, um Ihren Entwicklungs- und Produktionscode und deren HTTPS-Endpunkte zu hosten. Es ist nicht zu erwarten, dass sich Ihre Funktionen auf demselben Dienst befinden. Es ist erforderlich, dass alle Domänen, auf die von Ihren Microsoft Teams-Apps aus zugegriffen wird, im Objekt in der Datei [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) manifest.jswerden.

> [!NOTE]
> Um eine sichere Umgebung zu gewährleisten, sollten Sie die genauen Domänen und Unterdomänen, auf die Sie verweisen, explizit verwenden, und diese Domänen müssen sich in Ihrer Kontrolle befinden. Dies `*.azurewebsites.net` wird beispielsweise nicht empfohlen, aber `contoso.azurewebsites.net` dennoch.

## <a name="loading-and-running"></a>Laden und Ausführen

Im Allgemeinen müssen Sie zum Laden und Ausführen Ihrer Erfahrung in Microsoft Teams ein Paket erstellen und es mithilfe der folgenden Anleitung in Teams hochladen:

* [Erstellen des Pakets für Ihre Microsoft Teams-App](~/concepts/build-and-test/apps-package.md)
* [Hochladen Ihrer App in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md)
