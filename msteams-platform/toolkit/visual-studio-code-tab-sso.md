---
title: SSO-Authentifizierung mit Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen einer Registerkarte, die einmaliges Anmelden und Microsoft Graph-Aufrufe direkt in Visual Studio Code unterstützt, mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Code Toolkit Registerkarten Sso Graph-Authentifizierung Azure Identity Platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 38ff0e88cabe5f6cf3b8703fba139a525620ee25
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887583"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>SSO-Authentifizierung mit Teams Toolkit und Visual Studio Code für Registerkarten

> [!IMPORTANT]
> **Dieses Dokument bezieht sich auf eine alte Version des Teams-Toolkits.**
>
> Aktuelle Informationen finden Sie unter den [Voraussetzungen](../get-started/prerequisites.md) , und folgen Sie einem der neueren Lernprogramme.

Mit dem Microsoft Teams-Toolkit können Sie SSO-Authentifizierung (Single Sign-On) für Registerkarten-Apps direkt in Visual Studio Code erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform-Registrierung im Microsoft Azure-Portal.

## <a name="get-started--create-a-project"></a>Erste Schritte – Erstellen eines Projekts

1. Erstellen Sie ein neues Projekt im Toolkit.
1. Wählen Sie die Registerkarte als Typ der Erweiterung aus, die Sie erstellen möchten.
1. Wählen Sie die Option zur Unterstützung von SSO aus.

> [!TIP]
> Nach der Installation sollte das Teams-Toolkit in der Visual Studio Code-Aktivitätsleiste angezeigt werden. Wenn nicht, klicken Sie mit der rechten Maustaste in die Aktivitätsleiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit anzuheften, um einfach darauf zugreifen zu können.

## <a name="configure-your-project"></a>Konfigurieren Ihres Projekts

1. Um SSO in Teams zu aktivieren, muss Ihre App über eine Azure-App-Registrierungsressource verfügen. Das Teams-Toolkit stellt die App-Registrierung in Ihrem Auftrag bereit.
1. Geben Sie die URL ein, unter der Ihre App gehostet wird, und wählen Sie **"Weiter**" aus. Ihre App-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.
1. Die Konfigurationsdetails der App-Registrierung werden in den `.env` Dateien im Quellcode Ihres Projekts gespeichert.

Wenn Sie mehr darüber erfahren möchten, wie Ihre Azure-App-Registrierung bereitgestellt wird, *lesen Sie*  unsere [SSO-Unterstützung (Single Sign-On) für die Dokumentation zu Registerkarten](../tabs/how-to/authentication/tab-sso-overview.md) .

> [!TIP]
> Sie müssen zu **Azure App-Registrierungen** wechseln und Ihren *API-URI* aktualisieren und *URLs umleiten* , wenn Sie diese URL ändern.

## <a name="run-your-project"></a>Ausführen des Projekts

1. Wählen Sie **npm install** aus dem `api-server` Ordner aus. Dann **wird npm gestartet**.
1. Wählen Sie **npm install** aus dem `.src` Ordner aus. Dann **wird npm gestartet**.
1. Wenn Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit dem übereinstimmt, was Sie im Projekterstellungs-Assistenten eingegeben haben. Andernfalls müssen Sie Ihren *API-URI* aktualisieren und die URL in der App-Registrierung *umleiten* , die in Azure erstellt wurde.
1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Code-Fensters.
1. Wählen Sie das Symbol **"Ausführen** " aus, um die Ansicht " **Ausführen und Debuggen** " anzuzeigen.
1. Sie können auch die Tastenkombination **STRG+UMSCHALT+D** verwenden.

> [!TIP]
> Möglicherweise wird der Dialogfeld "App-Installation" im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind. Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.

## <a name="see-also"></a>Siehe auch

[Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](visual-studio-code-overview.md)
