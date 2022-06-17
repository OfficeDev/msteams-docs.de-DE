---
title: Authentifizieren von App-Benutzern
description: In diesem Modul lernen Sie die Authentifizierung in Teams und deren Verwendung in den Apps, den webbasierten Authentifizierungsfluss und den OAuthPrompt-Fluss für Unterhaltungsbots kennen.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 0ea8813d8428036521cc4488668a30d82470a8d0
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143466"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Authentifizieren von Benutzern in Microsoft Teams

Bei der Authentifizierung geht es darum, App-Benutzer zu überprüfen und die App- und App-Benutzer vor ungerechtfertigten Zugriffen zu schützen. Sie können eine Authentifizierungsmethode verwenden, die für Ihre App geeignet ist, um App-Benutzer zu überprüfen, die die Teams-App verwenden möchten.

Wählen Sie aus, ob Sie die Authentifizierung für Ihre App auf eine der beiden folgenden Arten hinzufügen möchten:

- **Aktivieren des einmaligen Anmeldens (Single Sign-On, SSO) in einer Teams-App**: SSO innerhalb Teams ist eine Authentifizierungsmethode, die die identitätsbasierte Teams eines App-Benutzers verwendet, um ihnen Zugriff auf Ihre App zu gewähren. Ein Benutzer, der sich bei Teams angemeldet hat, muss sich in der Teams Umgebung nicht erneut bei Ihrer App anmelden. Wenn nur eine Zustimmung des App-Benutzers erforderlich ist, ruft die Teams App Zugriffsdetails für sie aus Azure Active Directory (AD) ab. Nachdem der App-Benutzer seine Zustimmung erteilt hat, kann er auch von anderen Geräten aus auf die App zugreifen, ohne erneut überprüft werden zu müssen.

- **Aktivieren Sie die Authentifizierung mithilfe des OAuth-Anbieters eines Drittanbieters**: Sie können einen OAuth-Identitätsanbieter (IdP) eines Drittanbieters verwenden, um Ihre App-Benutzer zu authentifizieren. Der App-Benutzer ist beim Identitätsanbieter registriert, der eine Vertrauensstellung mit Ihrer App hat. Wenn der Benutzer versucht, sich anzumelden, überprüft der Identitätsanbieter den App-Benutzer und gewährt dem Benutzer Zugriff auf Ihre App. Azure AD ist ein solcher OAuth-Anbieter von Drittanbietern. Sie können andere Anbieter wie Google, Facebook, GitHub oder einen anderen Anbieter verwenden.

## <a name="select-authentication-method"></a>Authentifizierungsmethode auswählen

Aktivieren Sie die Authentifizierung mit SSO oder OAuth-IdPs von Drittanbietern in Ihrer Registerkarten-App, Bot-App und Messaging-Erweiterungs-App. Wählen Sie eine der beiden Methoden zum Hinzufügen der Authentifizierung in Ihrer App aus:

:::row:::
    :::column span="1":::
        SSO
    :::column-end:::
    :::column span="1":::
        &nbsp;
    :::column-end:::
    :::column span="1":::
        OAuth
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/tab-sso-icon.png" alt-text="SSO für Registerkarten-App" link="../../tabs/how-to/authentication/tab-sso-overview.md" border="false":::
    :::column-end:::
    :::column span="1":::
        <br>

        &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **Registerkarten-App**  
        
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/tab-app-idp.png" alt-text="Authentifizierung mit OAuth-Anbieter eines Drittanbieters für Registerkarten-App." link="../../tabs/how-to/authentication/auth-tab-aad.md" border="false":::
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/bot-sso-icon.png" alt-text="SSO für Bot-App" link="../../bots/how-to/authentication/auth-aad-sso-bots.md" border="false":::
    :::column-end:::
    :::column span="1":::
        <br>

        &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **Bot-App**
        
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/bot-app-idp.png" alt-text="Authentifizierung beim OAuth-Anbieter eines Drittanbieters für Bot-App." link="../../bots/how-to/authentication/add-authentication.md" border="false":::
    :::column-end:::
:::row-end:::
:::row:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/mex-sso-icon.png" alt-text="SSO für Messaging-Erweiterungs-App" link="../../messaging-extensions/how-to/enable-SSO-auth-me.md" border="false":::
    :::column-end:::
    :::column span="1":::
        <br>

        &nbsp;&nbsp; &nbsp; **Nachrichtenerweiterungs-App**
        
    :::column-end:::
    :::column span="1":::
        :::image type="content" source="../../assets/images/authentication/mex-app-idp.png" alt-text="Authentifizierung mit oAuth-IdPs von Drittanbietern für Messaging-Erweiterungs-App." link="../../messaging-extensions/how-to/add-authentication.md" border="false":::
    :::column-end:::
:::row-end:::

> [!NOTE]
> Die Seite "Automatische Authentifizierung" wird in das Modul "Ressourcen" verschoben. Weitere Informationen finden Sie [unter Automatische Authentifizierung](../../tabs/how-to/authentication/auth-silent-aad.md).

## <a name="see-also"></a>Siehe auch

- [Aktivieren des einmaligen Anmeldens in einer Registerkarten-App](../../tabs/how-to/authentication/tab-sso-overview.md)
- [Microsoft Teams-Authentifizierungsablauf für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md)
- [Unterstützung für einmaliges Anmelden für Bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
- [Hinzufügen der Authentifizierung zu Ihrer Nachrichtenerweiterung](~/messaging-extensions/how-to/add-authentication.md)
