---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in einem Microsoft Teams. Das Querladen ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: a54068ffd57a5d622cad72267c049cee69b18d58
ms.sourcegitcommit: 2c8b35899dd845acd66f1f927e40d99523c29a91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "52684649"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Hochladen Ihrer App in Microsoft Teams

Sie können apps querladen Microsoft Teams, ohne sie in Ihrer Organisation oder im Teams veröffentlichen zu müssen. Dies ist in den folgenden Szenarien sinnvoll:

* Sie möchten eine App lokal selbst oder mit anderen Entwicklern testen und debuggen.
* Sie haben eine App nur für sich selbst erstellt. Zum Beispiel, um einen Workflow zu automatisieren.
* Sie haben eine App für eine kleine Gruppe von Benutzern, z. B. Ihre Arbeitsgruppe, erstellt.

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket,](~/concepts/build-and-test/apps-package.md) [und überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.
* [Aktivieren Sie das Hochladen benutzerdefinierter](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs darauf zugegriffen werden kann.

## <a name="upload-your-app"></a>Hochladen Ihrer App

Sie können Ihre App in abhängigkeit davon, wie Sie den Bereich Ihrer App konfiguriert haben, in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen.

1. Melden Sie sich beim Teams-Client mit Ihrem [Microsoft 365 an.](~/build-your-first-app/build-and-run.md#prerequisites)
1. Wählen **Sie Apps** und Hochladen eine **benutzerdefinierte App aus.**
1. Wählen Sie Ihr App-.zip aus. Ein Installationsdialogfeld wird angezeigt.
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot mit einem Beispiel für ein Teams-App-Installationsdialogfeld.":::
1. Fügen Sie Ihre App zu Teams.

## <a name="troubleshoot-upload-issues"></a>Behandeln von Problemen beim Hochladen

Wenn ihre App nicht querladen kann, gehen Sie wie folgt vor, bis das Problem behoben ist:

1. Gehen Sie zurück durch die Anweisungen zum [Erstellen Ihres App-Pakets.](../../concepts/build-and-test/apps-package.md)
1. [Überprüfen Sie Ihr App-Paket](https://dev.teams.microsoft.com/appvalidation.html) erneut.
1. Stellen Sie sicher, dass Ihr App-Manifest dem neuesten Schema [entspricht.](../../resources/schema/manifest-schema.md)

## <a name="access-your-app"></a>Zugreifen auf Ihre App

Teams bietet verschiedene Möglichkeiten zum Öffnen von Apps. Weitere Informationen finden Sie unter [Zugreifen auf Ihre Apps in Teams.](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a)

## <a name="update-your-app"></a>Aktualisieren Ihrer App

Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widergespiegelt). Sie müssen jedoch neu installieren, wenn Sie app-Konfigurationen ändern.

## <a name="remove-your-app"></a>Entfernen Ihrer App

Klicken Sie zum Entfernen Ihrer App mit der rechten Maustaste auf das Teams und **wählen Sie Deinstallieren aus.**

> [!NOTE]
> Persönliche Botaktivitäten können nicht vollständig entfernt werden. Wenn Sie die App entfernen und erneut hinzufügen, wird die neue Kommunikation mit dem Bot an die vorherige Unterhaltung angefügt.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden Ihrer Teams App](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
