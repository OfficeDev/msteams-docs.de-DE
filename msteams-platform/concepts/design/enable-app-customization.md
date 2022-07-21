---
title: Anpassen Ihrer Teams-App
author: heath-hamilton
description: In diesem Modul erfahren Sie, wie Teams-Administratoren Ihre Teams-App für ihre Organisation anpassen und die Teams-App ausblenden können, bis der Administrator dies genehmigt.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 0a7a98c5d981f35bc60a6099873a445b45caa071
ms.sourcegitcommit: 4ba6392eced76ba6baeb6d6dd9ba426ebf4ab24f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2022
ms.locfileid: "66919823"
---
# <a name="customize-your-teams-app"></a>Anpassen Ihrer Teams-App

## <a name="enable-your-microsoft-teams-app-to-be-customized"></a>Aktivieren der Anpassung Ihrer Microsoft Teams-App

Sie können Kunden erlauben, einige Aspekte Ihrer Microsoft Teams-App im Teams Admin Center anzupassen. Dieses Feature wird nur für Apps unterstützt, die im Teams Store veröffentlicht wurden. Quergeladene Apps und Apps, die für eine Organisation veröffentlicht wurden, können nicht angepasst werden.

Einige mögliche Beispiele für dieses Feature sind:

* Ändern der Akzentfarbe der App, um sie an die Marke einer Organisation anzupassen.
* Aktualisieren des App-Namens von *Contoso* zu *Contoso-Agent*, das ist der Name, den Benutzer in der Organisation sehen werden. (Hinweis: Benutzer, die einen Connector zu einem Chat oder Kanal hinzufügen, sehen weiterhin den ursprünglichen App-Namen *Contoso*.)

Sie können dieses Feature aktivieren, indem Sie die App-Eigenschaften definieren, die Ihre Kunden ab Version 1.11 [im Abschnitt im Teams-App-Manifest anpassen können.`configurableProperties`](/microsoftteams/platform/resources/schema/manifest-schema#configurableproperties) Dies kann im [Entwicklerportal für Teams](https://dev.teams.microsoft.com/home) erfolgen, wenn Sie sich entschieden haben, das Entwicklerportal zum Bearbeiten des Manifests Ihrer App zu verwenden.

### <a name="test-your-app"></a>Testen eigener Apps

Sie können dieses Feature während der Entwicklung nicht testen. App-Anpassungen werden beim Querladen oder Veröffentlichen im App-Katalog einer Organisation nicht unterstützt.

### <a name="user-considerations"></a>Überlegungen zum Benutzer

Stellen Sie Richtlinien für Kunden (insbesondere Teams Administratoren) bereit, die Ihre App anpassen möchten. Weitere Informationen finden Sie unter [Apps in Teams anpassen](/MicrosoftTeams/customize-apps).

## <a name="hide-teams-app-until-admin-approves"></a>Teams-App bis zur Zustimmung des Administrators ausblenden

Um die Erfahrung mit der Teams-App zu verbessern, können Sie eine App standardmäßig vor Benutzern ausblenden, bis der Administrator das Einblenden der App zulässt. Beispielsweise hat Contoso Electronics eine Helpdesk-App für Teams erstellt. Um eine angemessene Funktion der App zu ermöglichen, möchte Contoso Electronics, dass die Kunden zuerst bestimmte Eigenschaften der App einrichten. Die App ist standardmäßig ausgeblendet und steht Benutzern erst zur Verfügung, nachdem der Administrator sie zulässt.

> [!NOTE]
> Teams Store hat sich weiterentwickelt:
> 
> Zuvor wurden die BRANCHEN-Apps durch Auswahl der Ellipsen auf der Kachel aktualisiert. Mit der aktualisierten Teams Store-Oberfläche können Sie jetzt die branchenspezifischen Apps aktualisieren, indem Sie sich beim [Teams Admin Center](https://admin.teams.microsoft.com)anmelden.

Um die App auszublenden, legen Sie in der App-Manifestdatei die Eigenschaft `defaultBlockUntilAdminAction` auf `true` fest. Wenn die Eigenschaft auf `true`Teams Admin Center > **Apps verwalten** festgelegt ist, wird **Vom Herausgeber blockiert** im **Status** der App angezeigt:

:::image type="content" source="../../assets/images/apps-in-meetings/manageappsblockedapps.png" alt-text="Vom Herausgeber blockierte Apps verwalten.":::

Der Administrator erhält eine Aufforderung, Aktionen durchzuführen, bevor ein Benutzer auf die App zugreifen kann. Unter **Apps verwalten** können die Administratoren **Zulassen** auswählen, um die App mit dem Status **Vom Herausgeber blockiert** zuzulassen:

![Verwalten von Apps](../../assets/images/apps-in-meetings/manageapp.png)

Wenn die App standardmäßig nicht ausgeblendet werden soll, können Sie die Eigenschaft `defaultBlockUntilAdminAction` auf `false` aktualisieren. Wenn die neue Version der App genehmigt wird, ist die App standardmäßig zulässig, solange der Administrator keine explizite Aktion ausgeführt hat.

> [!NOTE]
> `defaultBlockUntilAdminAction` wird für Branchen-Apps nicht unterstützt. Wenn Sie eine Branchen-App mit dieser Eigenschaft hochladen, wird die App nicht blockiert.

## <a name="see-also"></a>Siehe auch

* [App-Manifestschema](/microsoftteams/platform/resources/schema/manifest-schema)
* [Anpassen von Apps im Teams-Admin Center](/MicrosoftTeams/customize-apps)
