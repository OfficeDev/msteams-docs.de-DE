---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in Microsoft Teams querladen. Das Querladen ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: surbhigupta
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: a9ac73d3c3e41c5c57892273e788855a16642457
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571107"
---
# <a name="upload-your-app-in-microsoft-teams"></a>Hochladen Ihrer App in Microsoft Teams

In den folgenden Szenarien können Sie Microsoft Teams-Apps querladen, ohne sie in Ihrer Organisation oder im Teams Store veröffentlichen zu müssen:

* Sie möchten eine App lokal selbst oder mit anderen Entwicklern testen und debuggen.
* Sie haben eine App für sich selbst erstellt, um einen Workflow zu automatisieren.
* Sie haben eine App für eine kleine Gruppe von Benutzern erstellt, z. B. Ihre Arbeitsgruppe.

> [!IMPORTANT]
> Derzeit sind Querladen-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und Department of Defense (DOD).

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket](~/concepts/build-and-test/apps-package.md) und [überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.
* Aktivieren Sie das [Hochladen einer benutzerdefinierter App](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs zugänglich ist.

## <a name="upload-your-app"></a>Hochladen Ihrer App

Sie können Ihre App in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen, je nachdem, wie Sie den Bereich Ihrer App konfiguriert haben.

1. Melden Sie sich beim Teams-Client mit Ihrem [Microsoft 365-Entwicklungskonto](https://developer.microsoft.com/en-us/microsoft-365/dev-program) an.
1. Wählen Sie **Apps** und dann **Apps** verwalten aus.
1. Wählen Sie **Benutzerdefinierte App hochladen** aus.
1. Wählen Sie die ZIP-Datei Ihres App-Pakets aus.
2. Fügen Sie Ihre App gemäß Ihren Anforderungen zu Teams hinzu:</br>

   a. Wählen Sie **Hinzufügen** aus, um Ihre persönliche App hinzuzufügen.</br>
   b. Verwenden Sie das Dropdownmenü, um Ihre App einem Team oder Chat hinzuzufügen.

![Erstellen einer Teams-App](~/assets/videos/app-teams.gif)

## <a name="troubleshooting"></a>Problembehandlung

Wenn Ihre App nicht quergeladen werden kann oder Probleme beim Hochladen auftreten, versuchen Sie die folgenden Optionen:

1. Stellen Sie sicher, dass Sie alle Anweisungen für [Erstellung Ihres App-Pakets](../../concepts/build-and-test/apps-package.md) befolgt haben.
1. [Überprüfen Sie Ihr App-Paket](https://dev.teams.microsoft.com/appvalidation.html).
1. Stellen Sie sicher, dass Ihr App-Manifest mit dem aktuellen [Schema](../../resources/schema/manifest-schema.md) übereinstimmt.

## <a name="access-your-app"></a>Zugriff auf Ihre App

Teams bietet mehrere Möglichkeiten zum Öffnen von Apps. Weitere Informationen finden Sie unter [Zugriff auf Ihre Apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

## <a name="update-your-app"></a>Aktualisieren Ihrer App

Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widerspiegelt). Sie müssen sie jedoch neu installieren, wenn Sie App-Konfigurationen ändern.

## <a name="remove-your-app"></a>Entfernen Ihrer App

Um Ihre App zu entfernen, klicken Sie mit der rechten Maustaste auf das App-Symbol in Teams, und wählen Sie **Deinstallieren** aus.

> [!NOTE]
>
> * Sie können persönliche Botaktivitäten nicht vollständig entfernen. Wenn Sie die App entfernen und erneut hinzufügen, wird die neue Kommunikation mit dem Bot an die vorherige Konversation mit ihm angefügt.
> * Derzeit können Sie Ihre benutzerdefinierte App nicht in den Teams-Store migrieren. Wenn Sie Ihre App im Teams-Store auflisten möchten, lesen Sie [Veröffentlichung Ihrer App im Microsoft Teams-Store](appsource/publish.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden Ihrer Teams-App](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b)

## <a name="see-also"></a>Siehe auch

* [Konfigurieren der Standardinstallationsoptionen](~/concepts/deploy-and-publish/add-default-install-scope.md)
* [Unterhalt Ihrer veröffentlichte Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
