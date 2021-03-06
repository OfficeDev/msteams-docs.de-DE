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
# <a name="choose-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Auswählen eines Setups zum Testen und Debuggen ihrer Microsoft Teams App

Microsoft Teams apps enthalten eine oder mehrere Funktionen, und die Möglichkeiten zum Ausführen oder sogar Hosten sind unterschiedlich. Verwenden Sie zum Debuggen eine der folgenden Möglichkeiten:

* **Rein lokal:** Für Bots können Sie Ihre Erfahrung im Bot-Emulator testen. Für andere Inhalte können Sie lokal in Ihrem Browser und Adressinhalt über ausgeführt `http://localhost` werden.
* **Lokal gehostet in Teams:** Dazu gehört das lokale Ausführen [](~/concepts/build-and-test/apps-package.md) der App in Tunnelsoftware und das Erstellen eines Pakets zum Hochladen [in](~/concepts/deploy-and-publish/apps-upload.md) Teams. Auf diese Weise können Sie Ihre App ganz einfach im Client ausführen Teams debuggen.
* **Cloudhosting in Teams:** Dadurch wird die Unterstützung auf Produktionsebene für eine Teams simuliert. Es umfasst das Hochladen Ihrer Lösung auf Ihren extern [](~/concepts/build-and-test/apps-package.md) zugänglichen Server oder Cloudanbieter ihrer Wahl und das Erstellen eines Pakets zum Hochladen [in](~/concepts/deploy-and-publish/apps-upload.md) Teams.

Führen Sie die Erfahrung auf Ihrem eigenen Computer für rein lokale oder lokale Tests Teams aus. Auf diese Art können Sie in Ihrer integrierten Entwicklungsumgebung kompilieren und ausführen und techniken wie Haltepunkte und Schrittdebude nutzen. 

> [!NOTE]
> Für Das Debuggen und Testen im Produktionsmaßstab wird empfohlen, dass Sie Ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung über Ihre eigenen Prozesse unterstützen können.

Verwenden Sie mehrere Manifeste und Pakete, um die Trennung zwischen Produktions- und Entwicklungsdiensten aufrecht zu erhalten. Sie können beispielsweise separate Entwicklungs- und Produktionsbots registrieren und geeignete Pakete erstellen, um sie in Ihrer Testumgebung hochzuladen. Es wird auch empfohlen, Ihr Produktionspaket hochzuladen und zu testen, bevor Sie Ihre App zur Veröffentlichung im App Store oder zur Verteilung an Kunden übermitteln.

## <a name="purely-local"></a>Rein lokal

> [!NOTE]
> Wenn Sie den Bot lokal ausführen, erhalten Sie keinen Zugriff auf Teams-App-Funktionalität oder Teams bot-spezifische Funktionen wie Dienstplananrufe und andere kanalspezifische Funktionen. Darüber hinaus sind einige Funktionen vom Bot Framework im Bot-Emulator zulässig, die möglicherweise nicht funktionieren, wenn sie in Microsoft Teams.

Ihr Bot kann im Bot-Emulator ausgeführt werden. Auf diese Weise können Sie einige der Kernlogik des Bots testen, ein grobes Layout von Nachrichten anzeigen und einfache Tests durchführen. Im Folgenden finden Sie die folgenden Schritte:

1. Führen Sie den Code lokal aus.
2. Starten Sie den Bot-Emulator, und legen Sie die URL bereit:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Lassen Sie die Microsoft-App-ID und das Microsoft-App-Kennwort leer, um den Standardumgebungsvariablen zu entsprechen.

## <a name="locally-hosted"></a>Lokal gehostet

Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die zugegriffen wird, über HTTPS-Endpunkte öffentlich verfügbar sein. Damit Ihre App innerhalb von Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder unsere lokale ausgeführte Instanz extern zugänglich machen. Letzteres können wir mit Tunnelsoftware tun.

Obwohl Sie ein beliebiges Tool ihrer Wahl verwenden können, verwenden und empfehlen wir [ngrok](https://ngrok.com/download), das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen. 

**So richten Sie ngrok in Vorbereitung auf die lokale Ausführung ihrer Microsoft Teams ein**

1. Wechseln Sie zu dem Verzeichnis, in dem ngrok.exe in einer Terminalanwendung installiert haben. Sie können sie als Pfadvariable hinzufügen, um diesen Schritt zu vermeiden.
2. Führen Sie beispielsweise `ngrok http 3978 --host-header=localhost:3978` aus, oder ersetzen Sie die Portnummer nach Bedarf.
   Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port auflisten zu können. Im Gegenzug erhalten Sie eine extern adressierbare URL, die solange gültig ist, wie ngrok ausgeführt wird.

> [!NOTE]
> Wenn Sie ngrok beenden und neu starten, ändert sich die URL.

Um ngrok in Ihrem Projekt basierend auf den von Ihnen verwendeten Funktionen zu verwenden, müssen Sie alle URL-Verweise in Code, Konfiguration und manifest.json-Datei ersetzen, um diesen URL-Endpunkt zu verwenden.

Aktualisieren Sie für bots, die im Microsoft Bot Framework registriert sind, den Messagingendpunkt des Bots so, dass er diesen neuen ngrok-Endpunkt verwendet. Beispiel: `https://2d1224fb.ngrok.io/api/messages`. Sie können überprüfen, ob ngrok funktioniert, indem Sie die Botantwort im Testchatfenster des Bot Framework-Portals testen. Wie der Emulator ermöglicht auch dieser Test nicht den Zugriff Teams spezifischen Funktionen.

> [!NOTE]
> Zum Aktualisieren des Messagingendpunkts für einen Bot müssen Sie das Bot Framework verwenden. Wählen Sie Ihren Bot in [Ihrer Liste der Bots in Bot Framework aus.](https://dev.botframework.com/bots) Sie müssen Ihren Bot nicht zu einem Microsoft Azure. Sie können Ihren Messagingendpunkt auch über [App Studio aktualisieren.](~/concepts/build-and-test/app-studio-overview.md)

## <a name="cloud-hosted"></a>In der Cloud gehostet

Sie können einen beliebigen extern adressierbaren Dienst verwenden, um Ihren Entwicklungs- und Produktionscode und deren HTTPS-Endpunkte zu hosten. Es wird nicht erwartet, dass sich Ihre Funktionen auf demselben Dienst befinden. Wir benötigen den Zugriff auf alle Domänen von Ihren Microsoft Teams, die im Objekt [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) in der Datei aufgeführt `manifest.json` sind.

> [!NOTE]
> Um eine sichere Umgebung sicherzustellen, sollten Sie explizit die genaue Domäne und unterdomänen, auf die Sie verweisen, und diese Domänen müssen sich in Ihrem Steuerelement befinden. Wird beispielsweise `*.azurewebsites.net` nicht empfohlen, wird `contoso.azurewebsites.net` jedoch empfohlen.

## <a name="load-and-run-your-experience"></a>Laden und Ausführen Der Benutzererfahrung

Zum Laden und Ausführen Der Benutzererfahrung innerhalb Microsoft Teams müssen Sie ein Paket erstellen und in Teams. Weitere Informationen finden Sie unter:

* [Erstellen Sie das Paket für Microsoft Teams App](~/concepts/build-and-test/apps-package.md).
* [Hochladen App in Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"] 
> [Hinzufügen von Testdaten zu Ihrer Umgebung](~/concepts/build-and-test/test-data.md)

