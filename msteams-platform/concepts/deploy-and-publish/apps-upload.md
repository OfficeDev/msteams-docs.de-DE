---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in Microsoft Teams querladen. Das Querladen ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: bcb5661c4f6d09499700456bc44ce962ac710ea9
ms.sourcegitcommit: 83d67e73427ea1e93bb9aea5a8ca8ae05b68e302
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62430299"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Hochladen Ihrer App in Microsoft Teams

Sie können Microsoft Teams-Apps querladen, ohne sie in Ihrer Organisation oder im Teams-Store veröffentlichen zu müssen. Dies ist in den folgenden Szenarien sinnvoll:

* Sie möchten eine App lokal selbst oder mit anderen Entwicklern testen und debuggen.
* Sie haben eine App nur für sich selbst erstellt. Beispielsweise, um einen Workflow zu automatisieren.
* Sie haben eine App für eine kleine Gruppe von Benutzern erstellt, z. B. Ihre Arbeitsgruppe.

> [!IMPORTANT]
> Derzeit sind Querladen-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und Department of Defense (DOD).

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket](~/concepts/build-and-test/apps-package.md) und [überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.
* Aktivieren Sie das [Hochladen einer benutzerdefinierter App](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs zugänglich ist.

## <a name="upload-your-app"></a>Hochladen Ihrer App

Sie können Ihre App in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen, je nachdem, wie Sie den Bereich Ihrer App konfiguriert haben.

1. Melden Sie sich beim Teams-Client mit Ihrem [Microsoft 365-Entwicklungskonto](~/build-your-first-app/build-and-run.md#prerequisites) an.
1. Wählen Sie **Apps** und dann **Hochladen einer benutzerdefinierten App** aus.
1. Wählen Sie die ZIP-Datei Ihres App-Pakets aus. Ein Installationsdialogfeld wird angezeigt.
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot mit einem Beispiel eines Teams-App-Installationsdialogfelds.":::
1. Fügen Sie Ihre App zu Teams hinzu.

> [!NOTE]
> `onInstallationUpdateActivityAsync()`-Methode wird verwendet, um Microsoft Teams Locale abzurufen, während der Bot zu Microsoft Teams hinzugefügt wird.

## <a name="troubleshoot-upload-issues"></a>Behandeln von Problemen beim Hochladen

Wenn Ihre App nicht quergeladen werden kann, führen Sie die folgenden Schritte aus, bis das Problem behoben ist:

1. Gehen Sie zurück zu den Anweisungen für das [Erstellung Ihres App-Pakets](../../concepts/build-and-test/apps-package.md).
1. [Überprüfen Sie Ihre App-Paket](https://dev.teams.microsoft.com/appvalidation.html) erneut.
1. Stellen Sie sicher, dass Ihr App-Manifest mit dem neuesten [Schema](../../resources/schema/manifest-schema.md) übereinstimmt.

## <a name="access-your-app"></a>Zugriff auf Ihre App

Teams bietet mehrere Möglichkeiten zum Öffnen von Apps. Weitere Informationen finden Sie unter [Zugriff auf Ihre Apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

## <a name="update-your-app"></a>Aktualisieren Ihrer App

Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widerspiegelt). Sie müssen sie jedoch neu installieren, wenn Sie App-Konfigurationen ändern.

## <a name="remove-your-app"></a>Entfernen Ihrer App

Um Ihre App zu entfernen, klicken Sie mit der rechten Maustaste auf das App-Symbol in Teams, und wählen Sie **Deinstallieren** aus.

> [!NOTE]
> Sie können persönliche Botaktivitäten nicht vollständig entfernen. Wenn Sie die App entfernen und erneut hinzufügen, wird die neue Unterhaltung mit dem Bot an die vorherige Unterhaltung mit ihm angefügt.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden Ihrer Teams-App](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)

## <a name="see-also"></a>Siehe auch

* [Konfigurieren der Standardinstallationsoptionen](~/concepts/deploy-and-publish/add-default-install-scope.md)
* [Unterhalt Ihrer veröffentlichte Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
