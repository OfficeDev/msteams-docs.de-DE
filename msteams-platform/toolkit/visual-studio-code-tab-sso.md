---
title: Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen einer Registerkarte, die einmaliges Anmelden und Microsoft Graph-Aufrufe direkt in Visual Studio Code mit dem Microsoft Teams Toolkit unterstützt
keywords: Registerkarten des visual studio code toolkits sso graph authentication Azure identity platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: daf9a1b0bb64fee9584d0f58d749cf2b1ccaa4ef
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018425"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten

Mit dem Microsoft Teams Toolkit können Sie die einmalige Anmeldung (Single Sign-On, SSO)-Authentifizierung für Registerkarten-Apps direkt innerhalb Visual Studio erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform-Registrierung im Azure-Portal.

## <a name="get-started--create-a-project"></a>Erste Schritte – Erstellen eines Projekts

1. Erstellen Sie ein neues Projekt im Toolkit.
1. Wählen Sie tab als Den Typ der Erweiterung aus, den Sie erstellen möchten.
1. Wählen Sie die Option aus, um SSO zu unterstützen.

> [!TIP]
> Nach der Installation sollte das Teams Toolkit in der Visual Studio Code-Aktivitätsleiste angezeigt werden. Wenn nicht, klicken Sie mit der rechten Maustaste in der Aktivitätsleiste, und wählen **Sie Microsoft Teams aus,** um das Toolkit für den einfachen Zugriff anheften.

## <a name="configure-your-project"></a>Konfigurieren Ihres Projekts

1. Um SSO in Teams zu aktivieren, muss Ihre App über eine Azure-App-Registrierungsressource verfügen. Das Teams Toolkit stellt die App-Registrierung in Ihrem Namen zur Bereitstellung.
1. Geben Sie die URL ein, in der Ihre App gehostet wird, und wählen Sie als **Nächstes aus.** Ihre App-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.
1. Die Konfigurationsdetails der App-Registrierung werden in den Dateien im Quellcode Ihres `.env` Projekts gespeichert.

Wenn Sie mehr darüber erfahren möchten, wie Ihre Azure-App-Registrierung bereitgestellt wird, lesen Sie unsere Unterstützung für einmaliges Anmelden [(Single Sign-On, SSO)](../tabs/how-to/authentication/auth-aad-sso.md) für die Registerkartendokumentation. 

> [!TIP]
> Sie müssen zu **Azure App-Registrierungen** wechseln und Ihren *API-URI aktualisieren* und *URLs* umleiten, wenn Sie diese URL ändern.

## <a name="run-your-project"></a>Ausführen des Projekts

1. Wählen **Sie npm install** aus dem Ordner `api-server` aus. Starten Sie **dann npm.**
1. Wählen **Sie npm install** aus dem Ordner `.src` aus. Starten Sie **dann npm.**
1. Wenn Sie einen Tunneldienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit dem entspricht, was Sie im Assistenten zum Erstellen des Projekts eingegeben haben. Andern falls nicht, müssen Sie Ihren _API-URI_ aktualisieren und _die URL_ in der app-Registrierung umleiten, die in Azure erstellt wurde.
1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Codefensters.
1. Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen anzeigen.**
1. Sie können auch die Tastenkombination **STRG+Umschalt+D verwenden.**

> [!TIP]
> Möglicherweise wird der Dialog zur App-Installation im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind. Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.

> [!div class="nextstepaction"]
> [Weitere Informationen: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](visual-studio-code-overview.md)
