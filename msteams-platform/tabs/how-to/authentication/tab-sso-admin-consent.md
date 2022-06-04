---
title: Konfigurieren der Administratorzustimmung
description: Beschreibt das Konfigurieren der Administratorzustimmung
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Microsoft Azure Active Directory (Azure AD) Graph-API
ms.openlocfilehash: dd954ef1ede05b6025b12512dfcee03044223642
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65888310"
---
# <a name="configure-admin-consent"></a>Konfigurieren der Administratorzustimmung

Sie können den App-Bereich für eine verfügbar gemachte API definieren und bestimmen, ob Benutzer diesem Bereich in Verzeichnissen zustimmen können, in denen die Benutzerzustimmung aktiviert ist. Sie können nur Administratoren die Zustimmung für Berechtigungen mit höheren Rechten erteilen lassen.

## <a name="to-expose-an-api"></a>So machen Sie eine API verfügbar

1. Wählen Sie im linken Bereich "**API** **verwalten** > " aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-api-menu.png" alt-text="Verfügbarmachen einer API-Menüoption." border="false":::

    Die Seite **"API verfügbar machen** " wird angezeigt.

1. Wählen Sie **"Festlegen** " aus, um den App-ID-URI zu generieren.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-an-api.png" alt-text="App-ID-URI festlegen" border="false":::

    Der Abschnitt zum Festlegen des App-ID-URI wird angezeigt.

1. Geben Sie den App-ID-URI ein, und wählen Sie " **Speichern"** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/set-app-id-uri.png" alt-text="App-ID-URI" border="true":::

    Im Browser wird eine Meldung angezeigt, die besagt, dass der App-ID-URI aktualisiert wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-msg.png" alt-text="App-ID-URI-Nachricht" border="false":::

    Der App-ID-URI wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-added.png" alt-text="App-ID-URI aktualisiert" border="false":::

## <a name="to-configure-api-scope"></a>So konfigurieren Sie den API-Bereich

1. Wählen Sie in den **in diesem API-Abschnitt definierten Bereichen** den **Bereich aus, und fügen Sie einen Bereich hinzu**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-scope.png" alt-text="Bereich auswählen" border="true":::

    Die Seite **"Bereich hinzufügen** " wird angezeigt.

1. Geben Sie die App-Details für Ihren App-Bereich ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-scope.png" alt-text="Hinzufügen von Bereichsdetails" border="true":::

    1. Geben Sie den Bereichsnamen ein. Dieses Feld ist erforderlich.
    1. Wählen Sie **Administratoren und Benutzer** aus, um die Benutzer zu konfigurieren, die der Verwendung der Anmeldeinformationen des Benutzers zustimmen können. Die Standardoption ist **nur "Administratoren**".
    1. Geben Sie den **Anzeigenamen der Administratorzustimmung ein**. Dieses Feld ist erforderlich.
    1. Geben Sie die Beschreibung für die Administratorzustimmung ein. Dieses Feld ist erforderlich.
    1. Geben Sie den **Anzeigenamen der Benutzerzustimmung ein**.
    1. Geben Sie die Beschreibung für die Beschreibung der Benutzer-Zustimmung ein.
    1. Wählen Sie die Option **"Aktiviert** " für den Status aus.
    1. Klicken Sie auf **Bereich hinzufügen**.

    Im Browser wird eine Meldung angezeigt, die besagt, dass der Bereich hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added-msg.png" alt-text="Bereich hinzugefügte Nachricht" border="false":::

    Der App-ID-URI wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added.png" alt-text="Bereich hinzugefügt und angezeigt" border="false":::

## <a name="to-configure-authorized-client-application"></a>So konfigurieren Sie eine autorisierte Clientanwendung

1. Navigieren Sie durch die Seite **"API verfügbar machen** " zum Abschnitt **"Autorisierte Clientanwendung** ", und wählen Sie **"+Clientanwendung hinzufügen"** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/auth-client-apps.png" alt-text="Autorisierte Clientanwendung" border="true":::

    Die Seite **"Clientanwendung hinzufügen** " wird angezeigt.

1. Geben Sie die Details zum Hinzufügen einer Clientanwendung ein. In diesem Abschnitt fügen Sie zwei Clientanwendungen hinzu.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-app.png" alt-text="Hinzufügen einer Clientanwendung" border="true":::

    1. Geben Sie **1fec8e78-bce4-4aaf-ab1b-5451cc387264** als Client-ID für mobile Teams- oder Desktopanwendung ein.
    1. Wählen Sie die App-ID aus, die Sie für Ihre App für die **autorisierten Bereiche** erstellt haben.
    1. Wählen Sie **Anwendung hinzufügen** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass die Client-App hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Nachricht mit hinzugefügter Clientanwendung" border="false":::

    Die Client-App-IDs werden auf der Seite angezeigt.

1. Wiederholen Sie den vorherigen Schritt, um die Client-App für die Teams-Webanwendung hinzuzufügen.

    1. Geben Sie **5e3ce6c0-2b1f-4285-8d4b-75ee78787346** als Client-ID für Web-App ein.
    1. Wählen Sie die App-ID aus, die Sie für Ihre App für die **autorisierten Bereiche** erstellt haben.
    1. Wählen Sie **Anwendung hinzufügen** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass die Client-App hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Nachricht zur Hinzugefügten Clientanwendung für Web-App" border="false":::

    Die Client-App-IDs werden auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-app-added.png" alt-text="Hinzugefügte und angezeigte Client-App" border="true":::
