---
title: Authentifizierung mit einmaligem Anmelden mit Microsoft Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen Sie eine Registerkarte, die Single-Sign-on-und Microsoft Graph-Aufrufe direkt in Visual Studio Code mit dem Microsoft Teams-Toolkit unterstützt.
keywords: Teams Visual Studio Code Toolkit-Registerkarten SSO-Graph-Authentifizierung Azure Identity Platform
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: fe734143975688cd35c510cd68cd0779a2200a18
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "49477736"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Authentifizierung mit einmaligem Anmelden mit Microsoft Teams Toolkit und Visual Studio Code für Registerkarten

Mit dem Microsoft Teams-Toolkit können Sie die SSO-Authentifizierung (Single Sign-on, einmaliges Anmelden) für Registerkarten-apps direkt in Visual Studio Code erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform-Registrierung im Azure-Portal.

## <a name="get-started--create-a-project"></a>Erste Schritte – Erstellen eines Projekts

1. Erstellen Sie ein neues Projekt im Toolkit.
1. Wählen Sie Tab als den Typ der Erweiterung aus, die Sie erstellen möchten.
1. Wählen Sie die Option zur Unterstützung von SSO aus.

> [!TIP]
> Nach der Installation sollte das Teams-Toolkit in der Leiste Visual Studio Code-Aktivität angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitäts Leiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einfachen Zugriff zu fixieren

## <a name="configure-your-project"></a>Konfigurieren des Projekts

1. Um SSO in Microsoft Teams zu aktivieren, muss Ihre APP über eine Azure-App-Registrierungs Ressource verfügen. Das Teams-Toolkit stellt die APP-Registrierung in Ihrem Namen zur Verfügung.
1. Geben Sie die URL ein, unter der Ihre APP gehostet wird, und wählen Sie **weiter** aus. Ihre APP-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.
1. Die Konfigurationsdetails der APP-Registrierung werden in den `.env` Dateien des Quellcodes Ihres Projekts gespeichert.

Wenn Sie mehr über die Einrichtung ihrer Azure-App-Registrierung erfahren möchten _, lesen Sie bitte unsere_ [Unterstützung für einmaliges Anmelden (Single Sign-on, SSO) für die Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md) Dokumentation.

> [!TIP]
> Sie müssen zu **Azure-App-Registrierungen** wechseln und den *API-URI* aktualisieren und *URLs umleiten* , wenn Sie diese URL ändern.

## <a name="run-your-project"></a>Ausführen des Projekts

1. Wählen Sie **NPM-Installation** aus dem Ordner aus `api-server` . Dann **Starten Sie NPM**.
1. Wählen Sie **NPM-Installation** aus dem Ordner aus `.src` . Dann **Starten Sie NPM**.
1. Wenn Sie einen Tunnel Dienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit den Angaben übereinstimmt, die Sie im Assistenten zum Erstellen von Projekten eingegeben haben. Wenn dies nicht der Fall ist, müssen Sie den _API-URI_ und die _Umleitungs-URL_ in der APP-Registrierung aktualisieren, die in Azure erstellt wurde.
1. Navigieren Sie auf der linken Seite des Visual Studio Code Fensters zur Aktivitäts Leiste.
1. Wählen Sie das Symbol **Ausführen** aus, um die Ansicht **ausführen und Debuggen** anzuzeigen.
1. Sie können auch die Tastenkombination **STRG + UMSCHALT + D** verwenden.

> [!TIP]
> Möglicherweise wird der Dialog "App-Installation" im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind. Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.

> [!div class="nextstepaction"]
> [Weitere Informationen: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code](visual-studio-code-overview.md)
