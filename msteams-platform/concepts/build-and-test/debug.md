---
title: Auswählen eines Setups zum Testen und Debuggen Ihrer App
description: In diesem Modul lernen Sie Optionen zum Testen und Debuggen von Microsoft Teams-Apps in einer lokalen und in der Cloud gehosteten Umgebung kennen.
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: b064fb4ef06576251a91a4727a84bb4519d4d352
ms.sourcegitcommit: d8183bad448990f7c79b1956a6c9761c27712b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2022
ms.locfileid: "67452353"
---
# <a name="choose-a-test-setup-and-debug-your-teams-app"></a>Auswählen eines Testsetups und Debuggen Ihrer Teams-App

Die Microsoft Teams-Apps enthalten eine oder mehrere Funktionen, und die Möglichkeiten, sie auszuführen oder sogar zu hosten, unterscheiden sich. Verwenden Sie zum Debuggen eine der folgenden Möglichkeiten:

* **Rein lokal**: Für Bots können Sie Ihre Erfahrung im Bot-Emulator testen. Für andere Inhalte können Sie lokal in Ihrem Browser ausführen und Inhalte adressieren durch `http://localhost`.
* **Lokal gehostet in Teams**: Dies umfasst die lokale Ausführung der App in Tunnelsoftware und [das Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) zum [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams. Damit können Sie Ihre App ganz einfach im Teams Client ausführen und debuggen.
* **In der Cloud gehostet in Teams**: Dadurch wird die Unterstützung auf Produktionsebene für eine Teams App simuliert. Es umfasst das Hochladen Ihrer Lösung auf Ihren extern zugänglichen Server oder Cloudanbieter ihrer Wahl und [das Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) zum [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams.

Führen Sie die Benutzeroberfläche auf Ihrem eigenen Computer aus, um rein lokale oder lokale Teams zu testen. Dadurch können Sie in Ihrer integrierten Entwicklungsumgebung kompilieren und ausführen und die vollen Vorteile von Techniken wie Haltepunkten und Schrittdebugging nutzen.

> [!NOTE]
> Für das Debuggen und Testen im Produktionsmaßstab empfehlen wir, dass Sie Ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung über Ihre eigenen Prozesse unterstützen können.

Verwenden Sie mehrere Manifeste und Pakete, um die Trennung zwischen Produktions- und Entwicklungsdiensten aufrechtzuerhalten. Beispielsweise können Sie separate Entwicklungs- und Produktions-Bots registrieren und entsprechende Pakete erstellen, um sie in Ihre Testumgebung hochzuladen. Außerdem empfehlen wir, dass Sie Ihr Produktionspaket hochladen und testen, bevor Sie Ihre App für die Veröffentlichung in unserem App Store oder die Verteilung an Kunden übermitteln.

## <a name="purely-local"></a>Rein lokal

> [!NOTE]
> Wenn Sie den Bot lokal ausführen, erhalten Sie keinen Zugriff auf Teams App-Funktionen oder Teams-spezifischen Bot-Funktionen wie Listenanrufe und andere kanalspezifische Funktionen. Darüber hinaus sind einige Funktionen vom Bot-Framework im Bot-Emulator zulässig, die möglicherweise nicht funktionieren, wenn sie in Teams ausgeführt werden.

Ihr Bot kann innerhalb der Bot-Emulator ausgeführt werden. Dadurch können Sie einige der Kernlogik des Bots testen, ein grobes Layout von Nachrichten anzeigen und einfache Tests durchführen. Im Folgenden sind die Schritte aufgeführt:

1. Führen Sie den Code lokal aus.
2. Starten Sie die Bot-Emulator, und legen Sie die URL fest:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Lassen Sie die Microsoft-App-ID und das Kennwort der Microsoft-App leer, um den Standardumgebungsvariablen zu entsprechen.

## <a name="locally-hosted"></a>Lokal gehostet

Teams ist ein vollständig cloudbasiertes Produkt, es erfordert, dass alle Dienste, auf die es zugreift, über HTTPS-Endpunkte öffentlich verfügbar sind. Damit Ihre App innerhalb Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder unsere lokal ausgeführte Instanz extern zugänglich machen. Letzteres können wir mit Tunneling-Software tun.

Obwohl Sie ein beliebiges Tool Ihrer Wahl verwenden können, wird [ngrok](https://ngrok.com/download) verwendet und empfohlen, wodurch eine extern adressierbare URL für einen Port erstellt wird, den Sie lokal auf Ihrem Computer öffnen.

Führen Sie die folgenden Schritte aus, um ngrok in Vorbereitung auf die lokale Ausführung Ihrer Teams-App einzurichten:

1. Wechseln Sie zu dem Verzeichnis, in dem Sie ngrok.exe in einer Terminalanwendung installiert haben. Möglicherweise möchten Sie sie als Pfadvariable hinzufügen, um diesen Schritt zu vermeiden.
2. Führen Sie z. B. die Portnummer aus, `ngrok http 3978 --host-header=localhost:3978`, oder ersetzen Sie die Portnummer nach Bedarf.
   Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port auflisten zu können. Im Gegenzug erhalten Sie eine extern adressierbare URL, die so lange gültig ist, wie ngrok ausgeführt wird.

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL.

Um ngrok in Ihrem Projekt basierend auf den von Ihnen verwendeten Funktionen zu verwenden, müssen Sie alle URL-Verweise in Ihrer Code-, Konfigurations- und manifest.json-Datei ersetzen, um diesen URL-Endpunkt verwenden zu können.

Für Bots, die im Microsoft Bot Framework registriert sind, aktualisieren Sie den Messaging-Endpunkt des Bots, um diesen neuen ngrok-Endpunkt zu verwenden. Beispiel: `https://2d1224fb.ngrok.io/api/messages`. Sie können überprüfen, ob ngrok funktioniert, indem Sie die Bot-Antwort im Testchatfenster des Bot Framework-Portals testen. Wie der Emulator ermöglicht ihnen dieser Test nicht den Zugriff auf Teams-spezifische Funktionen.

> [!NOTE]
> Um den Messaging-Endpunkt für einen Bot zu aktualisieren, müssen Sie das Bot-Framework verwenden. Wählen Sie Ihren Bot in [Ihrer Liste der Bots in Bot Framework](https://dev.botframework.com/bots) aus. Sie müssen Ihren Bot nicht zu Microsoft Azure migrieren. Sie können Ihren Messaging-Endpunkt auch über das [Entwicklerportal für Teams](~/concepts/build-and-test/teams-developer-portal.md) aktualisieren.

## <a name="cloud-hosted"></a>In der Cloud gehostet

Sie können jeden extern adressierbaren Dienst verwenden, um Ihren Entwicklungs- und Produktionscode und deren HTTPS-Endpunkte zu hosten. Es wird nicht davon ausgegangen, dass sich Ihre Funktionen im selben Dienst befinden. Der Zugriff auf alle Domänen muss über Ihre Teams-Apps erfolgen, die [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) im Objekt in der `manifest.json` Datei aufgeführt sind.

> [!NOTE]
> Um eine sichere Umgebung zu gewährleisten, müssen Sie die genauen Domänen und Unterdomänen, auf die Sie verweisen, explizit angeben, und diese Domänen müssen unter Ihrer Kontrolle stehen. Beispielsweise wird `*.azurewebsites.net` nicht empfohlen, aber `contoso.azurewebsites.net` wird empfohlen.

## <a name="load-and-run-your-experience"></a>Laden und Ausführen der Benutzeroberfläche

Um Ihre Erfahrung in Teams zu laden und auszuführen, müssen Sie ein Paket erstellen und in Teams hochladen. Weitere Informationen finden Sie unter:

* [Microsoft Teams: Erstellen eines App-Pakets für Ihre Microsoft Teams-App](~/concepts/build-and-test/apps-package.md).
* [Hochladen Ihrer App in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Hinzufügen von Testdaten zu Ihrer Umgebung](~/concepts/build-and-test/test-data.md)

## <a name="see-also"></a>Siehe auch

* [Testen und debuggen Sie Ihren Bot lokal mit der IDE](../../bots/how-to/debug/locally-with-an-ide.md#test-and-debug-your-bot-locally-with-ide)
* [Entwicklertools für Microsoft Teams-Registerkarten](../../tabs/how-to/developer-tools.md)
