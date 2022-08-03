---
title: Entwicklerportal für Teams
description: In diesem Artikel erfahren Sie mehr über das Entwicklerportal und wie Sie eine völlig neue App erstellen und eine vorhandene App im Teams-Entwicklerportal importieren.
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 57274333d37edd166c9c5e7bb9484131a31af904
ms.sourcegitcommit: 990a36fb774e614146444d4adaa2c9bcdb835998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2022
ms.locfileid: "67232308"
---
# <a name="developer-portal-for-teams"></a>Entwicklerportal für Teams

Das <a href="https://dev.teams.microsoft.com" target="_blank">Entwicklerportal für Teams</a> ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps. Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot der Startseite des Entwicklerportals für Teams.":::

> [!NOTE]
>
> * Derzeit ist das Entwicklerportal nicht für Government Community Cloud (GCC),GCC-High- oder Department of Defense (DOD)-Mandanten verfügbar.
> * Sie können jedoch einen regulären Mandanten verwenden, um eine App im Entwicklerportal zu erstellen, die App herunterzuladen und die App mit [Microsoft Graph](/graph/api/teamsapp-publish?view=graph-rest-1.0&tabs=http&preserve-view=true) in eine nationale Cloud hochzuladen. Weitere Informationen finden Sie unter ["Nationale Cloudbereitstellungen"](/graph/deployments).

## <a name="register-an-app"></a>Registrieren einer App

Das Entwicklerportal bietet die folgenden Möglichkeiten zum Registrieren einer Teams-App:

* Erstellen und registrieren Sie eine brandneue App.
* Importieren sie ein vorhandenes App-Paket.

### <a name="create-and-register-a-brand-new-app"></a>Erstellen und Registrieren einer brandneuen App

Mit dem Entwicklerportal können Sie eine völlig neue App erstellen:

1. Melden Sie sich beim [Entwicklerportal](https://dev.teams.microsoft.com) an, und wählen Sie im linken Bereich **"Apps** " aus.

   :::image type="content" source="../../assets/images/tdp/home-page.png" alt-text="Der Screenshot ist ein Beispiel für die Startseite des Entwicklerportals für Teams.":::

1. Wählen Sie **"Neue App** " aus, und geben Sie den Namen der App ein.

   :::image type="content" source="../../assets/images/tdp/enter-app-name-tdp.png" alt-text="Der Screenshot zeigt, wie Sie eine brandneue App im Entwicklerportal für Teams erstellen." lightbox="../../assets/images/tdp/create-new-app-in-tdp.png":::

1. Klicken Sie auf **Hinzufügen**.

Jetzt haben Sie erfolgreich eine brandneue App erstellt, und Sie können alle grundlegenden Informationen der neuen App anzeigen.

:::image type="content" source="../../assets/images/tdp/basic-information-app-tdp.png" alt-text="Der Screenshot ist ein Beispiel, das die grundlegenden Informationen der App zeigt, die Sie im Entwicklerportal für Teams erstellt haben.":::

### <a name="import-an-existing-app"></a>Importieren einer vorhandenen App

Führen Sie die Schritte zum Importieren und Verwalten Ihrer vorhandenen App im Entwicklerportal aus.

1. Wählen Sie im Entwicklerportal im linken Bereich **"Apps** " aus.
1. Wählen Sie **"App importieren**" aus.

   :::image type="content" source="../../assets/images/tdp/import-app.png" alt-text="Der Screenshot zeigt, wie Sie Ihre vorhandene App im Entwicklerportal für Teams importieren, um Ihre Apps zu verwalten.":::

1. Wählen Sie die App-Manifestdatei und dann **"Öffnen**" aus.
1. Wählen Sie **Importieren** aus.

> [!NOTE]
>
> * Das Entwicklerportal erstellt eine eindeutige App-ID und sperrt die ID für Ihre registrierte Teams-App. Sie können keine ID Ihrer Wahl bearbeiten oder angeben, wodurch verhindert wird, dass doppelte App-IDs für mehrere Apps vorhanden sind.
> * Wenn Sie eine App mit dem Microsoft Teams-Toolkit für Visual Studio Code erstellen, können Sie Ihre App im Entwicklerportal verwalten. Weitere Informationen finden Sie unter [Erstellen von Apps mit Teams-Toolkit und Visual Studio-Code](~/toolkit/visual-studio-code-overview.md).
> * Sie können eine vorhandene App, die Sie in App Studio erstellt haben, in das Entwicklerportal importieren.

## <a name="see-also"></a>Siehe auch

[Einschließen eines SaaS-Angebots mit Ihrer Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
