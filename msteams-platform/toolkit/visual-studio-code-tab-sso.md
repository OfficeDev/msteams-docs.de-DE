---
title: Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen einer Registerkarte, die einmaliges Anmelden unterstützt, und Microsoft Graph aufruft direkt innerhalb Visual Studio Code mit dem Microsoft Teams Toolkit
keywords: Registerkarten des visual studio code toolkits sso graph authentication Azure identity platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 2ef409a45b92240cced09d2d77793af33945589e
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721815"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten

> [!IMPORTANT]
> **Dieses Dokument bezieht sich auf eine alte Version von Teams Toolkit**
>
> Wenn Sie aktuelle Informationen erhalten, lesen Sie [die](../get-started/prerequisites.md) Voraussetzungen, und folgen Sie einem der neueren Lernprogramme.

Mit Microsoft Teams Toolkit können Sie die einmalige Anmeldung (Single Sign-On, SSO)-Authentifizierung für Registerkarten-Apps direkt innerhalb Visual Studio Code. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Microsoft Identity Platform Registrierung im Azure-Portal.

## <a name="get-started--create-a-project"></a>Erste Schritte – Erstellen eines Projekts

1. Erstellen Sie ein neues Projekt im Toolkit.
1. Wählen Sie tab als Den Typ der Erweiterung aus, den Sie erstellen möchten.
1. Wählen Sie die Option aus, um SSO zu unterstützen.

> [!TIP]
> Nach der Installation sollte das Teams Toolkit in der Visual Studio Code angezeigt werden. Wenn nicht, klicken Sie mit der  rechten Maustaste in der Aktivitätsleiste, und wählen Microsoft Teams, um das Toolkit für den einfachen Zugriff anheften.

## <a name="configure-your-project"></a>Konfigurieren Ihres Projekts

1. Um SSO innerhalb Teams zu aktivieren, muss Ihre App über eine Azure-App-Registrierungsressource verfügen. Das Teams Toolkit stellt die App-Registrierung in Ihrem Namen zur Bereitstellung.
1. Geben Sie die URL ein, in der Ihre App gehostet wird, und wählen Sie als **Nächstes aus.** Ihre App-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.
1. Die Konfigurationsdetails der App-Registrierung werden in den Dateien im Quellcode Ihres `.env` Projekts gespeichert.

Wenn Sie mehr darüber erfahren möchten, wie Ihre Azure-App-Registrierung bereitgestellt wird, lesen Sie unsere Unterstützung für einmaliges Anmelden [(Single Sign-On, SSO)](../tabs/how-to/authentication/auth-aad-sso.md) für die Registerkartendokumentation. 

> [!TIP]
> Sie müssen zu **Azure App-Registrierungen** wechseln und Ihren *API-URI aktualisieren* und *URLs* umleiten, wenn Sie diese URL ändern.

## <a name="run-your-project"></a>Ausführen des Projekts

1. Wählen **Sie npm install** aus dem Ordner `api-server` aus. Starten Sie **dann npm.**
1. Wählen **Sie npm install** aus dem Ordner `.src` aus. Starten Sie **dann npm.**
1. Wenn Sie einen Tunneldienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit dem entspricht, was Sie im Assistenten zum Erstellen des Projekts eingegeben haben. Andern falls nicht, müssen Sie Ihren _API-URI_ aktualisieren und _die URL_ in der app-Registrierung umleiten, die in Azure erstellt wurde.
1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Code Fensters.
1. Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen anzeigen.**
1. Sie können auch die Tastenkombination **STRG+Umschalt+D verwenden.**

> [!TIP]
> Möglicherweise wird der Dialog zur App-Installation im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind. Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.

## <a name="see-also"></a>Siehe auch

[Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](visual-studio-code-overview.md)
