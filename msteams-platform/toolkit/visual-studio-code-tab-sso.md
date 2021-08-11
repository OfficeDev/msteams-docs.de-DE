---
title: Single Sign-On-Authentifizierung mit Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen einer Registerkarte, die einmaliges Anmelden und Microsoft Graph Aufrufe direkt in Visual Studio Code mit dem Microsoft Teams Toolkit unterstützt
keywords: Teams Visual Studio Code Toolkit Registerkarten sso Graph-Authentifizierung Azure Identity Platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 9854ac7dff400a5ef9b4695eab2f1679966043ac5fe5b65a2df5d4c5c7c6da8b
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707407"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Single Sign-On-Authentifizierung mit Teams Toolkit und Visual Studio Code für Registerkarten

> [!IMPORTANT]
> **Dieses Dokument bezieht sich auf eine alte Version von Teams Toolkit.**
>
> Aktuelle Informationen finden Sie unter den [Voraussetzungen,](../get-started/prerequisites.md) und folgen Sie einem der neueren Lernprogramme.

Mit dem Microsoft Teams Toolkit können Sie die SSO-Authentifizierung (Single Sign-On) für Registerkarten-Apps direkt in Visual Studio Code erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform Registrierung im Azure-Portal.

## <a name="get-started--create-a-project"></a>Erste Schritte – Erstellen eines Projekts

1. Erstellen Sie ein neues Projekt im Toolkit.
1. Wählen Sie die Registerkarte als Typ der Erweiterung aus, die Sie erstellen möchten.
1. Wählen Sie die Option zur Unterstützung von SSO aus.

> [!TIP]
> Nach der Installation sollte das Teams Toolkit in der Visual Studio Code Aktivitätsleiste angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitätsleiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einfachen Zugriff zu anheften.

## <a name="configure-your-project"></a>Konfigurieren Ihres Projekts

1. Um SSO innerhalb Teams zu aktivieren, muss Ihre App über eine Azure-App-Registrierungsressource verfügen. Das Teams Toolkit stellt die App-Registrierung in Ihrem Auftrag bereit.
1. Geben Sie die URL ein, unter der Ihre App gehostet wird, und wählen Sie **als Nächstes** aus. Ihre App-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.
1. Die Konfigurationsdetails der App-Registrierung werden in den `.env` Dateien im Quellcode Ihres Projekts gespeichert.

Wenn Sie mehr darüber erfahren möchten, wie Ihre Azure-App-Registrierung bereitgestellt wird, _lesen_  Sie unsere [SSO-Unterstützung (Single Sign-On) für die](../tabs/how-to/authentication/auth-aad-sso.md) Dokumentation zu Registerkarten.

> [!TIP]
> Sie müssen zu **Azure App-Registrierungen** wechseln und Ihren *API-URI* aktualisieren und *URLs umleiten,* wenn Sie diese URL ändern.

## <a name="run-your-project"></a>Ausführen ihres Projekts

1. Wählen Sie **"npm install"** aus dem `api-server` Ordner aus. Dann **npm start**.
1. Wählen Sie **"npm install"** aus dem `.src` Ordner aus. Dann **npm start**.
1. Wenn Sie einen Tunneldienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit dem übereinstimmt, was Sie im Projekterstellungs-Assistenten eingegeben haben. Wenn dies nicht der Fall ist, müssen Sie Ihren _API-URI_ und die _Umleitungs-URL_ in der App-Registrierung aktualisieren, die in Azure erstellt wurde.
1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des fensters Visual Studio Code.
1. Wählen Sie das **Symbol "Ausführen"** aus, um die Ansicht **"Ausführen" und "Debuggen"** anzuzeigen.
1. Sie können auch die Tastenkombination **STRG+UMSCHALT+D** verwenden.

> [!TIP]
> Möglicherweise wird das Dialogfeld "App-Installation" im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind. Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](visual-studio-code-overview.md)
