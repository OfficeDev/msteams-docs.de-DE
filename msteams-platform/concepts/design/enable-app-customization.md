---
title: Aktivieren der App-Anpassung und Blockieren von Apps, bis der Administrator dies zulässt
author: heath-hamilton
description: In diesem Modul erfahren Sie, wie Teams-Administratoren Ihre Teams-App für ihre Organisation anpassen und die Teams-App ausblenden können, bis der Administrator dies genehmigt.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 7d71e341bd1613e9efe6c900f29e1bd340006b49
ms.sourcegitcommit: d92e14fad6567fe91fd52ee6c213836740316683
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2022
ms.locfileid: "67604954"
---
# <a name="enable-app-customization-and-block-apps-till-admin-allows"></a>Aktivieren der App-Anpassung und Blockieren von Apps, bis der Administrator dies zulässt

Mit Microsoft Teams können Administratoren die Teams-App anpassen, um die Store-Erfahrung zu verbessern und das Branding ihrer Organisation einzuhalten. Ein App-Entwickler kann zulassen, dass seine App von einem Teams-Administrator angepasst wird. Weitere Informationen finden [Sie unter Anpassen von Apps im Teams Admin Center](/MicrosoftTeams/customize-apps).

## <a name="enable-customization-for-your-microsoft-teams-app"></a>Aktivieren der Anpassung für Ihre Microsoft Teams-App

Sie können Kunden erlauben, einige Aspekte Ihrer Microsoft Teams-App im Teams Admin Center anzupassen. Dieses Feature wird nur für Apps unterstützt, die im Teams Store veröffentlicht wurden. Quergeladene Apps und Apps, die für eine Organisation veröffentlicht wurden, können nicht angepasst werden.

Einige mögliche Beispiele für dieses Feature sind:

* Ändern der Akzentfarbe der App, um sie an die Marke einer Organisation anzupassen.
* Aktualisieren des App-Namens von *Contoso* zu *Contoso-Agent*, das ist der Name, den Benutzer in der Organisation sehen werden.
(Hinweis: Benutzer, die einen Connector zu einem Chat oder Kanal hinzufügen, sehen weiterhin den ursprünglichen App-Namen *Contoso*.)

Sie können dieses Feature aktivieren, indem Sie die App-Eigenschaften definieren, die Ihre Kunden ab Version 1.11 [im Abschnitt im Teams-App-Manifest anpassen können.`configurableProperties`](/microsoftteams/platform/resources/schema/manifest-schema#configurableproperties) Dies kann im [Entwicklerportal für Teams](https://dev.teams.microsoft.com/home) erfolgen, wenn Sie sich entschieden haben, das Entwicklerportal zum Bearbeiten des Manifests Ihrer App zu verwenden.

> [!IMPORTANT]
> Sie können dieses Feature während der Entwicklung nicht testen. App-Anpassungen werden beim Querladen oder Veröffentlichen im App-Katalog einer Organisation nicht unterstützt.

### <a name="user-considerations"></a>Überlegungen zum Benutzer

Stellen Sie Richtlinien für Kunden (insbesondere Teams Administratoren) bereit, die Ihre App anpassen möchten. Weitere Informationen finden Sie unter [Apps in Teams anpassen](/MicrosoftTeams/customize-apps).

## <a name="block-apps-by-default-for-users-until-an-admin-approves"></a>Standardmäßige Sperrung von Apps für Benutzer, bis ein Administrator dies genehmigt

Um die Erfahrung mit der Teams-App zu verbessern, können Sie eine App standardmäßig vor Benutzern ausblenden, bis der Administrator das Einblenden der App zulässt. Beispielsweise hat Contoso Electronics eine Helpdesk-App für Teams erstellt. Um eine angemessene Funktion der App zu ermöglichen, möchte Contoso Electronics, dass die Kunden zuerst bestimmte Eigenschaften der App einrichten. Die App ist standardmäßig ausgeblendet und steht Benutzern erst zur Verfügung, nachdem der Administrator sie zulässt.

Um die App auszublenden, legen Sie in der App-Manifestdatei die Eigenschaft `defaultBlockUntilAdminAction` auf `true` fest. Wenn die Eigenschaft auf `true`Teams Admin Center > **Apps verwalten** festgelegt ist, wird **Vom Herausgeber blockiert** im **Status** der App angezeigt:

:::image type="content" source="../../assets/images/manage-apps-status.png" alt-text="Der Screenshot ist ein Beispiel für eine vom Herausgeber blockierte App." lightbox="../../assets/images/manage-apps-status-expanded.png":::

Der Administrator erhält eine Aufforderung, Aktionen durchzuführen, bevor ein Benutzer auf die App zugreifen kann. Unter **Apps verwalten** können die Administratoren **Zulassen** auswählen, um die App mit dem Status **Vom Herausgeber blockiert** zuzulassen:

:::image type="content" source="../../assets/images/manage-apps-allow.png" alt-text="Der Screenshot ist ein Beispiel, in dem die Option &quot;Zulassen&quot; für die vom Herausgeber blockierte App angezeigt wird." lightbox="../../assets/images/manage-apps-allow-expanded.png":::

Wenn die App standardmäßig nicht ausgeblendet werden soll, können Sie die Eigenschaft `defaultBlockUntilAdminAction` auf `false` aktualisieren. Wenn die neue Version der App genehmigt wird, ist die App standardmäßig zulässig, solange der Administrator keine explizite Aktion ausgeführt hat.

> [!NOTE]
> Für Branchen-Apps wird dies `defaultBlockUntilAdminAction` nicht unterstützt. Die App wird nicht blockiert, wenn Sie eine Branchen-App mit dieser Eigenschaft hochladen.

## <a name="see-also"></a>Siehe auch

* [App-Manifestschema](/microsoftteams/platform/resources/schema/manifest-schema)
* [Anpassen von Apps im Teams-Admin Center](/MicrosoftTeams/customize-apps)
