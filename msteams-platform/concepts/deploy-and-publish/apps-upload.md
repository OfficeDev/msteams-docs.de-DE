---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in Microsoft Teams querladen. Sideloading ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: 86b085f55c66b7ce9937665bdd20b04841344e924610237bf2e592d867d0b632
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708709"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Hochladen Ihrer App in Microsoft Teams

Sie können Microsoft Teams Apps querladen, ohne sie in Ihrer Organisation oder im Teams Store veröffentlichen zu müssen. Dies ist in den folgenden Szenarien sinnvoll:

* Sie möchten eine App lokal oder mit anderen Entwicklern testen und debuggen.
* Sie haben eine App nur für sich selbst erstellt. Beispielsweise zum Automatisieren eines Workflows.
* Sie haben eine App für eine kleine Gruppe von Benutzern erstellt, z. B. Für Ihre Arbeitsgruppe.

> [!IMPORTANT]
> Sideloading-Apps sind derzeit in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und das Verteidigungsministerium (Department of Defense, DOD).

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket,](~/concepts/build-and-test/apps-package.md) und [überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.
* [Aktivieren Sie das hochladen von benutzerdefinierten Apps](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs darauf zugegriffen werden kann.

## <a name="upload-your-app"></a>Hochladen Ihrer App

Sie können Ihre App in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen, je nachdem, wie Sie den App-Bereich konfiguriert haben.

1. Melden Sie sich mit Ihrem [Microsoft 365 Entwicklungskonto](~/build-your-first-app/build-and-run.md#prerequisites)beim Teams-Client an.
1. Wählen Sie **"Apps"** aus, und wählen Sie **Hochladen einer benutzerdefinierten App** aus.
1. Wählen Sie Ihr App-Paket .zip Datei aus. Ein Installationsdialogfeld wird angezeigt.
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot eines Beispiels für ein Dialogfeld für Teams App-Installation.":::
1. Fügen Sie Ihre App zu Teams hinzu.

## <a name="troubleshoot-upload-issues"></a>Behandeln von Problemen beim Hochladen

Wenn ihre App nicht quergeladen werden kann, führen Sie die folgenden Schritte aus, bis das Problem behoben ist:

1. Gehen Sie die Anweisungen zum [Erstellen Ihres App-Pakets](../../concepts/build-and-test/apps-package.md)zurück.
1. [Überprüfen Sie das App-Paket](https://dev.teams.microsoft.com/appvalidation.html) erneut.
1. Stellen Sie sicher, dass Ihr App-Manifest dem aktuellen [Schema](../../resources/schema/manifest-schema.md)entspricht.

## <a name="access-your-app"></a>Zugreifen auf Ihre App

Teams bietet verschiedene Möglichkeiten zum Öffnen von Apps. Weitere Informationen finden Sie unter [Zugreifen auf Ihre Apps in Teams.](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a)

## <a name="update-your-app"></a>Aktualisieren Ihrer App

Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widergespiegelt). Sie müssen jedoch neu installieren, wenn Sie App-Konfigurationen ändern.

## <a name="remove-your-app"></a>Entfernen Ihrer App

Um Ihre App zu entfernen, klicken Sie mit der rechten Maustaste auf das App-Symbol in Teams, und wählen Sie **Deinstallieren** aus.

> [!NOTE]
> Persönliche Bot-Aktivitäten können nicht vollständig entfernt werden. Wenn Sie die App entfernen und erneut hinzufügen, wird eine neue Kommunikation mit dem Bot an die vorherige Unterhaltung mit ihr angefügt.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden Ihrer Teams-App](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
