---
title: Einmalige Anmeldeauthentifizierung mit Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen Sie eine Registerkarte, die Single-Sign-On- und Microsoft-Graph-Anrufe direkt innerhalb Visual Studio Code mit dem Microsoft Teams Toolkit unterstützt
keywords: Teams Visual Studio Code Toolkit Registerkarten sso Graph Authentifizierung Azure-Identitätsplattform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 11e642ce335dae4344f1c730b73763e9172fd76c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566831"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Einmalige Anmeldeauthentifizierung mit Teams Toolkit und Visual Studio Code für Registerkarten

Mit dem Microsoft Teams Toolkit können Sie die SSO-Authentifizierung (Single Sign-On) für Tab-Apps direkt in Visual Studio Code erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform Registrierung im Azure-Portal.

## <a name="get-started--create-a-project"></a>Erste Schritte – Erstellen eines Projekts

1. Erstellen Sie ein neues Projekt im Toolkit.
1. Wählen Sie die Registerkarte als Erweiterungstyp aus, den Sie erstellen möchten.
1. Wählen Sie die Option zur Unterstützung von SSO aus.

> [!TIP]
> Nach der Installation sollte das Teams Toolkit in der Aktivitätsleiste Visual Studio Code angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitätsleiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einen einfachen Zugriff anzuheften.

## <a name="configure-your-project"></a>Konfigurieren Sie Ihr Projekt

1. Um SSO innerhalb Teams zu aktivieren, muss Ihre App über eine Azure-App-Registrierungsressource verfügen. Das Teams Toolkit stellt die App-Registrierung in Ihrem Namen bereit.
1. Geben Sie die URL ein, unter der Ihre App gehostet wird, und wählen Sie **die nächste** aus. Ihre App-Registrierung wird mit der bereitgestellten URL konfiguriert.
1. Die Konfigurationsdetails der App-Registrierung werden in den `.env` Dateien im Quellcode Ihres Projekts gespeichert.

Wenn Sie mehr darüber erfahren möchten, wie Ihre Azure-App-Registrierung bereitgestellt wird, _lesen_ Sie bitte unsere [SSO-Unterstützung (Single Sign-On) für die Dokumentation zu Registerkarten.](../tabs/how-to/authentication/auth-aad-sso.md)

> [!TIP]
> Sie müssen zu **Azure App-Registrierungen** wechseln und Ihren *API-URI* aktualisieren und *URLs umleiten,* wenn Sie diese URL ändern.

## <a name="run-your-project"></a>Führen Sie Ihr Projekt aus

1. Wählen Sie **npm install** aus dem `api-server` Ordner aus. Dann **npm starten**.
1. Wählen Sie **npm install** aus dem `.src` Ordner aus. Dann **npm starten**.
1. Wenn Sie einen Tunneldienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit dem übereinstimmt, was Sie im Projekterstellungs-Assistenten eingegeben haben. Andernfalls müssen Sie Ihren _API-URI_ aktualisieren und die URL in der in Azure erstellten App-Registrierung _umleiten._
1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Code Fensters.
1. Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen** anzuzeigen.
1. Sie können auch die Tastenkombination **Strg+Umschalt+D** verwenden.

> [!TIP]
> Möglicherweise wird der App-Installationsdialog im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind. Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](visual-studio-code-overview.md)
