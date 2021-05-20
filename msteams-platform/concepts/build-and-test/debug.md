---
title: Auswählen eines Setups zum Testen und Debuggen Ihrer App
description: Beschreibt Optionen zum Testen und Debuggen Microsoft Teams Apps
keywords: Teams führen Debug-Apps aus
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 1f11834ad83e8bea7e4114d25d022df2f62c1700
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565158"
---
# <a name="choose-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Wählen Sie ein Setup aus, um Ihre Microsoft Teams-App zu testen und zu debuggen

Microsoft Teams Apps eine oder mehrere Funktionen enthalten und die Möglichkeiten, sie auszuführen oder sogar zu hosten, sind unterschiedlich. Verwenden Sie zum Debuggen eine der folgenden Möglichkeiten:

* **Rein lokal**: Für Bots können Sie Ihre Erfahrung im Bot-Emulator testen. Bei anderen Inhalten können Sie lokal in Ihrem Browser ausgeführt werden und Inhalte über `http://localhost` adressieren.
* **Lokal gehostet in Teams**: Dies beinhaltet das lokale Ausführen der App in Tunneling-Software und das [Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) zum [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams. Auf diese Weise können Sie Ihre App einfach im Teams-Client ausführen und debuggen.
* **Cloud-gehostet in Teams**: Dies simuliert wirklich die Unterstützung auf Produktionsebene für eine Teams-App. Es beinhaltet das Hochladen Ihrer Lösung auf Ihren extern zugänglichen Server oder Cloud-Anbieter Ihrer Wahl und das [Erstellen eines Pakets](~/concepts/build-and-test/apps-package.md) zum [Hochladen](~/concepts/deploy-and-publish/apps-upload.md) in Teams.

Führen Sie die Erfahrung von Ihrem eigenen Computer aus für rein lokale oder lokale Teams Tests aus. Auf diese Weise können Sie in Ihrer integrierten Entwicklungsumgebung kompilieren und ausführen und die Vorteile von Techniken wie Haltepunkten und Schrittdebugging voll ausschöpfen. 

> [!NOTE]
> Für Debugging und Tests im Produktionsmaßstab wird empfohlen, dass Sie Ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung durch Ihre eigenen Prozesse unterstützen können.

Verwenden Sie mehrere Manifeste und Pakete, um die Trennung zwischen Produktions- und Entwicklungsdiensten aufrechtzuerhalten. Sie können z. B. separate Entwicklungs- und Produktionsbots registrieren und geeignete Pakete erstellen, um sie in Ihrer Testumgebung hochzuladen. Wir empfehlen Ihnen auch, Ihr Produktionspaket hochzuladen und zu testen, bevor Sie Ihre App zur Veröffentlichung in unserem App Store oder zur Verteilung an Kunden einreichen.

## <a name="purely-local"></a>Rein lokal

> [!NOTE]
> Wenn Sie den Bot lokal ausführen, haben Sie keinen Zugriff auf Teams App-Funktionalität oder Teams-spezifischen Bot-Funktionen wie Dienstplanaufrufe und andere kanalspezifische Funktionen. Darüber hinaus sind einige Funktionen vom Bot Framework im Bot-Emulator zulässig, die möglicherweise nicht funktionieren, wenn sie in Microsoft Teams ausgeführt werden.

Ihr Bot kann im Bot-Emulator ausgeführt werden. Auf diese Weise können Sie einige der Kernlogik des Bots testen, ein grobes Layout von Nachrichten anzeigen und einfache Tests durchführen. Im Folgenden sind die Schritte:

1. Führen Sie den Code lokal aus.
2. Starten Sie den Bot-Emulator und legen Sie die URL fest:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C:: `http://localhost:3979/api/messages`
3. Lassen Sie die Microsoft-App-ID und das Microsoft-App-Kennwort leer, um den Standardumgebungsvariablen zu entsprechen.

## <a name="locally-hosted"></a>Lokal gehostet

Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die es zugreift, öffentlich mit HTTPS-Endpunkten verfügbar sein. Damit Ihre App innerhalb von Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder unsere lokale ausführungsinstanz extern zugänglich machen. Letzteres können wir mit Tunneling-Software machen.

Obwohl Sie jedes Tool Ihrer Wahl verwenden können, verwenden und empfehlen wir [ngrok](https://ngrok.com/download), das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen. 

**So richten Sie ngrok ein, um Ihre Microsoft Teams App lokal auszuführen**

1. Wechseln Sie zu dem Verzeichnis, in dem Sie ngrok.exe in einer Terminalanwendung installiert haben. Sie können sie als Pfadvariable hinzufügen, um diesen Schritt zu vermeiden.
2. Führen Sie z. B. aus, oder ersetzen Sie `ngrok http 3978 --host-header=localhost:3978` die Portnummer bei Bedarf.
   Dadurch wird ngrok gestartet, um den port aufzulisten, den Sie angeben. Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.

> [!NOTE]
> Wenn Sie ngrok anhalten und neu starten, ändert sich die URL.

Um ngrok in Ihrem Projekt basierend auf den von Ihnen verwendenden Funktionen zu verwenden, müssen Sie alle URL-Verweise in Ihrem Code, Ihrer Konfiguration und manifest.jsin der Datei ersetzen, um diesen URL-Endpunkt zu verwenden.

Für Bots, die im Microsoft Bot Framework registriert sind, aktualisieren Sie den Messaging-Endpunkt des Bots, um diesen neuen ngrok-Endpunkt zu verwenden. Beispiel: `https://2d1224fb.ngrok.io/api/messages`. Sie können überprüfen, ob ngrok funktioniert, indem Sie die Bot-Antwort im Test-Chatfenster des Bot Framework-Portals testen. Wie der Emulator ermöglicht Ihnen dieser Test auch hier keinen Zugriff auf Teams-spezifische Funktionalität.

> [!NOTE]
> Um den Messagingendpunkt für einen Bot zu aktualisieren, müssen Sie das Bot Framework verwenden. Wählen Sie Ihren Bot in [Ihrer Liste der Bots in Bot Framework](https://dev.botframework.com/bots). Sie müssen Ihren Bot nicht nach Microsoft Azure migrieren. Sie können Ihren Messagingendpunkt auch über [App Studio](~/concepts/build-and-test/app-studio-overview.md)aktualisieren.

## <a name="cloud-hosted"></a>In der Cloud gehostet

Sie können jeden extern adressierbaren Dienst verwenden, um Ihren Entwicklungs- und Produktionscode und deren HTTPS-Endpunkte zu hosten. Es wird nicht erwartet, dass sich Ihre Funktionen im selben Dienst befinden. Wir müssen auf alle Domänen von Ihren Microsoft Teams Apps zugreifen, die im Objekt in der Datei aufgeführt [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) `manifest.json` sind.

> [!NOTE]
> Um eine sichere Umgebung zu gewährleisten, sollten Sie die genauen Domänen und Subdomänen, auf die Sie verweisen, explizit anzeigen, und diese Domänen müssen sich in Ihrem Steuerelement befinden. Zum Beispiel `*.azurewebsites.net` wird nicht empfohlen, wird jedoch `contoso.azurewebsites.net` empfohlen.

## <a name="load-and-run-your-experience"></a>Laden und ausführen Sie Ihre Erfahrung

Um Ihre Erfahrung innerhalb Microsoft Teams zu laden und auszuführen, müssen Sie ein Paket erstellen und es in Teams hochladen. Weitere Informationen finden Sie unter:

* [Erstellen Sie das Paket für Ihre Microsoft Teams-App](~/concepts/build-and-test/apps-package.md).
* [Hochladen Sie Ihre App in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"] 
> [Hinzufügen von Testdaten zu Ihrer Umgebung](~/concepts/build-and-test/test-data.md)

