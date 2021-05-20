---
title: Hochladen Ihre benutzerdefinierte App
description: Erfahren Sie, wie Sie Ihre App in Microsoft Teams. Sideloading ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: 39e94317ceb615ecd7d5481276ffafed5afe5cde
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565193"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Hochladen Ihre App in Microsoft Teams

Sie können Microsoft Teams Apps nebeneinander laden, ohne in Ihrer Organisation oder im Teams-Store veröffentlichen zu müssen. Dies ist in den folgenden Szenarien sinnvoll:

* Sie möchten eine App lokal oder mit anderen Entwicklern testen und debuggen.
* Sie haben eine App nur für sich selbst erstellt. Zum Beispiel, um einen Workflow zu automatisieren.
* Sie haben eine App für eine kleine Gruppe von Benutzern erstellt, z. B. für Ihre Arbeitsgruppe.

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket,](~/concepts/build-and-test/apps-package.md) und [überprüfen Sie es auf](https://dev.teams.microsoft.com/appvalidation.html) Fehler.
* [Aktivieren Sie das hochladen benutzerdefinierter Apps](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs zugänglich ist.

## <a name="upload-your-app"></a>Hochladen Ihrer App

Sie können Ihre App an ein Team, einen Chat, eine Besprechung oder für den persönlichen Gebrauch laden, je nachdem, wie Sie den Umfang Ihrer App konfiguriert haben.

1. Melden Sie sich mit Ihrem [Microsoft 365 Entwicklungskonto](~/build-your-first-app/build-and-run.md#prerequisites)beim Teams-Client an.
1. Wählen Sie **Apps** aus, und wählen Sie **Hochladen eine benutzerdefinierte App** aus.
1. Wählen Sie Ihr App-Paket .zip Datei aus. Ein Installationsdialogfeld wird angezeigt.
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot mit einem Beispiel für ein Teams App-Installationsdialogfeld.":::
1. Fügen Sie Ihre App Teams hinzu.

## <a name="troubleshoot-upload-issues"></a>Behandeln von Problemen beim Hochladen

Wenn Ihre App nicht nebeneinander geladen werden kann, gehen Sie wie folgt vor, bis das Problem behoben ist:

1. Gehen Sie zurück durch die Anweisungen zum [Erstellen Ihres App-Pakets](../../concepts/build-and-test/apps-package.md).
1. [Überprüfen Sie Ihr App-Paket](https://dev.teams.microsoft.com/appvalidation.html) erneut.
1. Stellen Sie sicher, dass Ihr App-Manifest mit dem neuesten [Schema](../../resources/schema/manifest-schema.md)übereinstimmt.

## <a name="access-your-app"></a>Zugriff auf Ihre App

Teams bietet mehrere Möglichkeiten zum Öffnen von Apps. Weitere Informationen finden Sie [unter Zugriff auf Ihre Apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

## <a name="update-your-app"></a>Aktualisieren Sie Ihre App

Sie müssen Ihre App nicht erneut seitlich laden, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widergespiegelt). Sie müssen jedoch neu installieren, wenn Sie App-Konfigurationen ändern.

## <a name="remove-your-app"></a>Entfernen Sie Ihre App

Um Ihre App zu entfernen, klicken Sie mit der rechten Maustaste auf das App-Symbol in Teams und wählen **Sie Deinstallieren** aus.

> [!NOTE]
> Sie können persönliche Bot-Aktivitäten nicht vollständig entfernen. Wenn Sie die App entfernen und erneut hinzufügen, hängt eine neue Kommunikation mit dem Bot an die vorherige Unterhaltung mit ihr an.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden Sie Ihre Teams-App](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
