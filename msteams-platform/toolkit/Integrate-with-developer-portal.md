---
title: Integration in das Entwicklerportal im Teams-Toolkit
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie das Entwicklerportal in Teams Toolkit integrieren.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
ms.openlocfilehash: b54e833f5c8292c0b426e859e63d858102860a47
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617224"
---
# <a name="integrate-with-developer-portal"></a>Integration in das Entwicklerportal

Sie können Ihre App im Entwicklerportal im Teams-Toolkit konfigurieren und verwalten.

## <a name="to-publish-app-using-developer-portal"></a>So veröffentlichen Sie die App mithilfe des Entwicklerportals

Mit den folgenden Schritten können Sie Ihre App im Entwicklerportal veröffentlichen:

1. Wählen Sie unter **BEREITSTELLUNG** **das Entwicklerportal für Teams** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/dev-portal-ttk.png" alt-text="Entwicklerportal für Teams":::

   Jetzt wird das Entwicklerportal in einem Browser geöffnet.

1. Melden Sie sich mit dem entsprechenden Konto beim [Entwicklerportal für Teams](https://dev.teams.microsoft.com) an.
1. Importieren Sie Ihr App-Paket in ZIP, und wählen Sie **"App** > **importieren"** aus.
1. Wählen Sie **"Veröffentlichen in Ihrer Organisation veröffentlichen** > " aus.

## <a name="to-update-manifest-file-and-app-package"></a>So aktualisieren Sie die Manifestdatei und das App-Paket

Wenn Änderungen an der Manifestdatei der Microsoft Teams-App vorliegen, können Sie das Manifest aktualisieren und die Microsoft Teams-App erneut veröffentlichen. Um eine Microsoft Teams-App manuell zu veröffentlichen, können Sie das [Entwicklerportal für Microsoft Teams](https://dev.teams.microsoft.com/home) nutzen.

1. Melden Sie sich mit dem entsprechenden Konto beim [Entwicklerportal für Teams](https://dev.teams.microsoft.com) an.
1. Importieren Sie Ihr App-Paket in ZIP, und wählen Sie **"App** > **importieren"** aus.<br>
   Sie müssen die App ersetzen, die Sie zuvor in das Entwicklerportal hochgeladen haben.
1. Um Ihre App zu veröffentlichen, wählen Sie " **Veröffentlichen** > **" in Ihrer Organisation** aus.

Sie können die folgende Konfiguration im Entwicklerportal ausführen:

* **Grundlegende Informationen**: In diesem Abschnitt werden der App-Name, die App-ID, Beschreibungen, Version, Entwicklerinformationen, App-URLs, Anwendungs-ID (Client-ID) und Microsoft Partner Network-ID angezeigt und können sie bearbeiten.
* **Branding**: Auf dieser Seite werden die App-Symboldetails angezeigt.
* **App-Features**: Sie können Ihrer App die folgenden Features hinzufügen:
  * Persönliche App
  * Bot
  * Connector
  * Szene
  * Gruppen- und Kanal-App
  * Messaging-Erweiterung
  * Besprechungserweiterung
  * Aktivitätsfeedbenachrichtigung
* **Berechtigungen**: In diesem Abschnitt können Sie Geräteberechtigungen, Teamberechtigungen, Chat- oder Besprechungsberechtigungen und Benutzerberechtigungen für Ihre App erteilen.
* **Einmaliges Anmelden**: Sie können Ihre App so konfigurieren, dass Benutzer mit einmaligem Anmelden (Single Sign-On, SSO) authentifiziert werden.
* **Sprachen**: Sie können die Sprache Ihrer App einrichten oder ändern.
* **Domäne**: Sie können die Domänen hinzufügen, um Ihre Apps im Teams-Client zu laden (z. B.: *.example.com).

## <a name="see-also"></a>Siehe auch

* [Entwicklerportal für Teams](../concepts/build-and-test/teams-developer-portal.md)
* [Verwalten Ihrer Apps im Entwicklerportal](../concepts/build-and-test/manage-your-apps-in-developer-portal.md)
