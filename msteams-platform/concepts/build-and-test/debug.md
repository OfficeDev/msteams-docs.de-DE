---
title: Auswählen eines Setups zum Testen und Debuggen Ihrer App
description: Beschreibt Optionen zum Testen und Debuggen Microsoft Teams Apps in einer lokalen und in der Cloud gehosteten Umgebung.
keywords: Teams führen Debug-Apps lokal in der Cloud gehosteten Host aus
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: eddcd41a7bebae183df079bc5dfe67deed65056e
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355706"
---
# <a name="choose-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Auswählen eines Setups zum Testen und Debuggen Ihrer Microsoft Teams-App

Microsoft Teams Apps eine oder mehrere Funktionen enthalten, und die Möglichkeiten zum Ausführen oder sogar Hosten unterscheiden sich. Verwenden Sie für das Debuggen eine der folgenden Methoden:

* **Rein lokal**: Für Bots können Sie Ihre Erfahrung im Bot-Emulator testen. Für andere Inhalte können Sie lokal in Ihrem Browser ausführen und Inhalte über `http://localhost`.
* **Lokal in Teams gehostet**: Dies umfasst das lokale Ausführen der App in Tunnelsoftware und [das Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) zum [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams. Auf diese Weise können Sie Ihre App einfach im Teams-Client ausführen und debuggen.
* **In der Cloud gehostet in Teams**: Dadurch wird die Unterstützung auf Produktionsebene für eine Teams App simuliert. Dazu gehört das Hochladen Ihrer Lösung auf Ihren extern zugänglichen Server oder Cloudanbieter Ihrer Wahl und das [Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) zum [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams.

Führen Sie die Benutzeroberfläche von Ihrem eigenen Computer aus, um rein lokale oder lokale Teams zu testen. Auf diese Weise können Sie in Ihrer integrierten Entwicklungsumgebung kompilieren und ausführen und alle Techniken nutzen, z. B. Haltepunkte und Schrittdebugging.

> [!NOTE]
> Für Debuggen und Tests im Produktionsmaßstab empfehlen wir, dass Sie Ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung über Ihre eigenen Prozesse unterstützen können.

Verwenden Sie mehrere Manifeste und Pakete, um die Trennung zwischen Produktions- und Entwicklungsdiensten aufrechtzuerhalten. Sie können beispielsweise separate Entwicklungs- und Produktionsbots registrieren und entsprechende Pakete erstellen, um sie in Ihre Testumgebung hochzuladen. Wir empfehlen außerdem, Ihr Produktionspaket hochzuladen und zu testen, bevor Sie Ihre App für die Veröffentlichung in unserem App Store oder für die Verteilung an Kunden übermitteln.

## <a name="purely-local"></a>Rein lokal

> [!NOTE]
> Wenn Sie den Bot lokal ausführen, erhalten Sie keinen Zugriff auf Teams App-Funktionalität oder Teams-spezifischen Bot-Funktionen wie Listenaufrufe und andere kanalspezifische Funktionen. Darüber hinaus sind einige Funktionen vom Bot Framework im Bot-Emulator zulässig, die möglicherweise nicht funktionieren, wenn sie in Microsoft Teams ausgeführt werden.

Ihr Bot kann innerhalb des Bot-Emulator ausgeführt werden. Auf diese Weise können Sie einige der Kernlogik des Bots testen, ein grobes Layout von Nachrichten anzeigen und einfache Tests durchführen. Führen Sie die folgenden Schritte aus:

1. Führen Sie den Code lokal aus.
2. Starten Sie die Bot-Emulator, und legen Sie die URL fest:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Lassen Sie die Microsoft-App-ID und das Microsoft-App-Kennwort leer, um den Standardumgebungsvariablen zu entsprechen.

## <a name="locally-hosted"></a>Lokal gehostet

Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die es zugreift, über HTTPS-Endpunkte öffentlich verfügbar sein. Damit Ihre App in Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder die lokale ausgeführte Instanz extern zugänglich machen. Letzteres ist mit Tunnelsoftware möglich.

Obwohl Sie ein beliebiges Tool verwenden können, wird [ngrok](https://ngrok.com/download) verwendet und empfohlen, das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen.

Führen Sie die folgenden Schritte aus, um ngrok in Vorbereitung auf die lokale Ausführung Ihrer Microsoft Teams-App einzurichten:

1. Wechseln Sie zu dem Verzeichnis, in dem Sie ngrok.exe in einer Terminalanwendung installiert haben. Sie können sie als Pfadvariable hinzufügen, um diesen Schritt zu vermeiden.
2. Führen Sie z. B. die Portnummer aus, `ngrok http 3978 --host-header=localhost:3978`oder ersetzen Sie sie nach Bedarf.
   Dadurch wird ngrok gestartet, um eine Liste auf dem von Ihnen angegebenen Port zu erstellen. Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL.

Um ngrok in Ihrem Projekt basierend auf den von Ihnen verwendeten Funktionen zu verwenden, müssen Sie alle URL-Verweise in Ihrer Code-, Konfigurations- und manifest.json-Datei ersetzen, um diesen URL-Endpunkt zu verwenden.

Aktualisieren Sie für bots, die im Microsoft Bot Framework registriert sind, den Messaging-Endpunkt des Bots, um diesen neuen ngrok-Endpunkt zu verwenden. Beispiel: `https://2d1224fb.ngrok.io/api/messages`. Sie können überprüfen, ob ngrok funktioniert, indem Sie die Botantwort im Chatfenster "Test" des Bot Framework-Portals testen. Wie der Emulator ermöglicht ihnen dieser Test auch hier nicht den Zugriff auf Teams-spezifische Funktionalität.

> [!NOTE]
> Um den Messaging-Endpunkt für einen Bot zu aktualisieren, müssen Sie das Bot Framework verwenden. Wählen Sie Ihren Bot in [Ihrer Liste der Bots im Bot Framework](https://dev.botframework.com/bots) aus. Sie müssen Ihren Bot nicht zu Microsoft Azure migrieren. Sie können Ihren Messaging-Endpunkt auch über [App Studio](~/concepts/build-and-test/app-studio-overview.md) aktualisieren.

## <a name="cloud-hosted"></a>In der Cloud gehostet

Sie können einen beliebigen extern adressierbaren Dienst verwenden, um Ihren Entwicklungs- und Produktionscode und deren HTTPS-Endpunkte zu hosten. Es wird nicht erwartet, dass Sich Ihre Funktionen auf demselben Dienst befinden. Es ist erforderlich, dass von Ihren Microsoft Teams Apps, die im Objekt in der [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) `manifest.json` Datei aufgeführt sind, auf alle Domänen zugegriffen werden kann.

> [!NOTE]
> Um eine sichere Umgebung zu gewährleisten, geben Sie die genaue Domäne und die Unterdomänen an, auf die Sie verweisen, und diese Domänen müssen sich in Ihrem Steuerelement befinden. Wird beispielsweise `*.azurewebsites.net` nicht empfohlen, wird jedoch `contoso.azurewebsites.net` empfohlen.

## <a name="load-and-run-your-experience"></a>Laden und Ausführen der Benutzeroberfläche

Um Ihre Oberfläche in Microsoft Teams zu laden und auszuführen, müssen Sie ein Paket erstellen und in Teams hochladen. Weitere Informationen finden Sie unter:

* [Erstellen Sie das Paket für Ihre Microsoft Teams-App](~/concepts/build-and-test/apps-package.md).
* [Hochladen Sie Ihre App in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Hinzufügen von Testdaten zu Ihrer Umgebung](~/concepts/build-and-test/test-data.md)

## <a name="see-also"></a>Siehe auch

[Testen und debuggen Sie Ihren Bot lokal](../../bots/how-to/debug/locally-with-an-ide.md#test-and-debug-your-bot-locally)
