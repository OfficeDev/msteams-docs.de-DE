---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in Microsoft Teams querladen. Das Querladen ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: surbhigupta
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: ffa7cdb0fabf07254c90590fe94fe2347c35658c
ms.sourcegitcommit: 377a4b712b50a211851aeecc1029414939945390
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68044679"
---
# <a name="upload-your-app-in-teams"></a>Hochladen Ihrer App in Teams

In den folgenden Szenarien können Sie Microsoft Teams-Apps querladen, ohne sie in Ihrer Organisation oder im Teams Store veröffentlichen zu müssen:

* Sie möchten eine App lokal selbst oder mit anderen Entwicklern testen und debuggen.
* Sie haben eine App für sich selbst erstellt, um einen Workflow zu automatisieren.
* Sie haben eine App für eine kleine Gruppe von Benutzern erstellt, z. B. Ihre Arbeitsgruppe.

> [!NOTE]
> Beim mehrfachen Querladen Ihrer Messaging-Erweiterungs-App werden mehr als eine Instanz für Messaging-Erweiterungen angezeigt.

> [!IMPORTANT]
>
> * Derzeit ist das Querladen von Apps nur in Government Community Cloud (GCC) möglich und in GCC-High und Department of Defense (DOD) nicht möglich.
> * Die App-Installation wird nur in der Teams-Desktop-App unterstützt.

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket](~/concepts/build-and-test/apps-package.md) und [überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.
* Aktivieren Sie das [Hochladen einer benutzerdefinierter App](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs zugänglich ist.

## <a name="upload-your-app"></a>Hochladen Ihrer App

Sie können Ihre App in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen, je nachdem, wie Sie den Bereich Ihrer App konfiguriert haben.

1. Melden Sie sich beim Teams-Client mit Ihrem [Microsoft 365-Entwicklungskonto](https://developer.microsoft.com/en-us/microsoft-365/dev-program) an.
1. Wählen Sie **Apps** > **Verwalten Ihrer Apps aus** und **Veröffentlichen einer App**.

    :::image type="content" source="~/assets/images/publish-app/manage-apps.png" alt-text="Einer App veröffentlichen":::

1. Wählen Sie **Benutzerdefinierte App hochladen** aus.

   :::image type="content" source="~/assets/images/publish-app/publish-app.png" alt-text="Benutzerdefinierte App hochladen":::

1. Wählen Sie die ZIP-Datei Ihres App-Pakets aus.
1. Fügen Sie Ihre App gemäß Ihren Anforderungen zu Teams hinzu:</br>

   a. Select **Add** to add your personal app.</br>
   b. Use the dropdown menu to add your app to a Team or chat.

    :::image type="content" source="~/assets/images/publish-app/teams-app-detail.png" alt-text="App-Beschreibung":::

## <a name="troubleshoot"></a>Troubleshooting

Wenn die App nicht quergeladen werden kann oder Probleme beim Hochladen auftreten, überprüfen Sie die folgenden Optionen:

1. Stellen Sie sicher, dass Sie alle Anweisungen zum [Erstellen Ihres App-Pakets](../../concepts/build-and-test/apps-package.md) befolgt haben.
1. [Überprüfen Sie Ihr App-Paket](https://dev.teams.microsoft.com/appvalidation.html).
1. Stellen Sie sicher, dass Ihr App-Manifest mit dem neuesten [Schema](../../resources/schema/manifest-schema.md) übereinstimmt.

## <a name="manage-your-apps"></a>Ihre Apps verwalten

Manage your apps allows users to have a dedicated place to manage, update and remove their apps, permissions, and subscriptions on the Teams client. The users can install the apps from **Manage your apps**.

### <a name="access-your-app"></a>Zugriff auf Ihre App

Führen Sie die folgenden Schritte aus, um über **Verwalten Ihrer Apps** auf Apps zuzugreifen:

1. Wechseln Sie zu **Apps**, und wählen Sie **Verwalten Ihrer Apps** in Teams aus, um die installierten Apps in allen Ihren Kanälen oder zur persönlichen Verwendung in einem Listenformat anzuzeigen.

    :::image type="content" source="~/assets/images/publish-app/manage-apps-list.png" alt-text="Zugriff auf die Liste der Teams-Apps":::

1. Wählen Sie das App-Dropdown aus, um alle Bereiche anzuzeigen, in denen die App installiert ist.

    :::image type="content" source="~/assets/images/publish-app/app-scopes.png" alt-text="Zugreifen auf den Teams-App-Bereich":::

1. Wählen Sie den Bereich der App aus, um zur App in der Kanal- oder der persönlichen Ansicht zu wechseln. Die Liste der Bereiche besteht nur aus dem persönlichen Bereich und dem Teams-Bereich. Apps, die im Gruppenchatbereich installiert sind, werden in dieser Ansicht derzeit nicht angezeigt.

Teams bietet mehrere Möglichkeiten zum Öffnen von Apps. Weitere Informationen finden Sie unter [Zugriff auf Ihre Apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).

### <a name="update-your-app"></a>Aktualisieren Ihrer App

Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widerspiegelt). Sie müssen sie jedoch neu installieren, wenn Sie App-Konfigurationen ändern.

Wenn für Ihre App ein Update verfügbar ist, ist die **Update verfügbar**-Option aktiviert. Führen Sie zum Aktualisieren die folgenden Schritte aus:

1. Wählen Sie **Update verfügbar** aus, um die Aktualisierung anzuzeigen.

     :::image type="content" source="~/assets/images/publish-app/update-available.png" alt-text="Teams-App aktualisieren.":::

1. Wählen Sie **"Aktualisierung anzeigen"** aus. Ein Fenster mit der Option "Aktualisieren" wird angezeigt.
1. Wählen Sie die Schaltfläche **Aktualisieren** aus, um Ihre App zu aktualisieren.

     :::image type="content" source="~/assets/images/publish-app/update-window.png" alt-text="Aktualisieren Sie die Teams-App in der App-Verwaltung.":::

     :::image type="content" source="~/assets/images/publish-app/updated-app.png" alt-text="Aktualisierte App.":::

### <a name="remove-your-app"></a>Entfernen Ihrer App

Führen Sie die folgenden Schritte aus, um die App aus Teams zu entfernen:

1. Finden Sie die App unter **Verwalten Ihrer App**.

1. Wählen Sie &nbsp;:::image type="content" source="~/assets/images/publish-app/bin-icon.png" alt-text="App in Teams entfernen.":::&nbsp; im Bereich der installierten App aus.

    :::image type="content" source="~/assets/images/publish-app/uninstall-from-channel.png" alt-text="Entfernen sie die App in einem Kanal.":::

1. Wählen Sie **Entfernen** aus, um Ihre App zu entfernen.

    :::image type="content" source="~/assets/images/publish-app/remove-app-teams.png" alt-text="Entfernen sie eine App aus Teams.":::

> [!NOTE]
>
> * You can't remove personal bot activity entirely. If you remove the app and add it again, new communication with the bot appends to the previous conversation with it.
> * Derzeit können Sie Ihre benutzerdefinierte App nicht in den Teams-Store migrieren. Wenn Sie Ihre App im Teams-Store auflisten möchten, lesen Sie [Veröffentlichung Ihrer App im Microsoft Teams-Store](appsource/publish.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
>[Apps für Teams-Besprechungen erstellen](../../apps-in-teams-meetings/teams-apps-in-meetings.md)

## <a name="see-also"></a>Siehe auch

* [Konfigurieren der Standardinstallationsoptionen](~/concepts/deploy-and-publish/add-default-install-scope.md)
* [Unterhalt Ihrer veröffentlichte Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)
* [App zum Chatten hinzufügen](/graph/api/chat-post-installedapps)
