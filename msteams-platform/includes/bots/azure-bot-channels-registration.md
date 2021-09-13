---
title: Azure Bot-Kanalregistrierung
description: beschreibt Azure-Botkanäle für die Registrierung
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta12
ms.openlocfilehash: 96d7ed857074547d0c3da5b412b8065d063f3a3100da6a7431fd65879bfa91ff
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57703787"
---
1. Wählen Sie im [Azure-Portal](https://ms.portal.azure.com/#home)unter Azure-Dienste die Option **"Ressource erstellen"** aus.
1. Geben Sie im Suchfeld "Bot" ein. Wählen Sie in der Dropdownliste die **Bot-Kanalregistrierung** aus.
1. Wählen Sie die Schaltfläche **"Erstellen"** aus.
1. Geben Sie im Blatt **"Bot Channel Registration"** die angeforderten Informationen zu Ihrem Bot an.
1. Lassen Sie das Feld für den **Messaging-Endpunkt** vorerst leer. Nach der Bereitstellung des Bots geben Sie die erforderliche URL ein. Die folgende Abbildung zeigt ein Beispiel für die Registrierungseinstellungen:

    ![Registrierung von Bot-App-Kanälen](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Klicken Sie auf **Microsoft App-ID und Kennwort,** und erstellen Sie dann **"Neu".**

    ![Erstellen einer Microsoft App-ID ](../../assets/images/authentication/CreateMicrosoftAppID.png) ![ Zum Erstellen einer neuen Microsoft App-ID](../../assets/images/authentication/CreateNewMicrosoftAppID.png)    

1. Klicken Sie im Link **"App-Registrierungsportal" auf "App-ID erstellen".**

   ![App-Registrierungen](../../assets/images/authentication/AppRegistration.png)
   
1. Klicken Sie im angezeigten **App-Registrierungsfenster** oben links auf die Registerkarte **"Neue Registrierung".**
1. Geben Sie den Namen der Bot-Anwendung ein, die Sie registrieren, wir haben *BotTeamsAuth* verwendet (Sie müssen Ihren eigenen eindeutigen Namen auswählen).
1. Wählen Sie für die **unterstützten Kontotypen** *Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD-Verzeichnis – Mehrinstanzenfähig) und persönliche Microsoft-Konten (z. B. Skype, Xbox) aus.*
1. Klicken Sie auf die Schaltfläche **"Registrieren".** Nach Abschluss zeigt Azure die *Übersichtsseite* für die Anwendung an.
1. Kopieren und speichern Sie den Wert der **Anwendungs-ID (Client)** in eine Datei.
1. Klicken Sie im linken Bereich auf **"Zertifikat und geheime Schlüssel".**
    1. Klicken Sie unter *"Geheime Clientschlüssel"* auf **"Neuer geheimer Clientschlüssel".**
    1. Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen Benutzern zu identifizieren, die Sie möglicherweise für diese App erstellen müssen.
    1. Legen Sie *"Läuft ab"* auf Ihre Auswahl fest.
    1. Klicken Sie auf **Hinzufügen**.
    1. Kopieren Sie den geheimen Clientschlüssel, und speichern Sie ihn in einer Datei.
1. Wechseln Sie zurück zum Fenster **"Bot Channel-Registrierung",** und kopieren Sie die *App-ID* und den *geheimen Clientschlüssel* in den Feldern **"Microsoft-App-ID"** bzw. **"Kennwort".**
1. Klicken Sie auf **OK**.
1. Klicken Sie abschließend auf **"Erstellen".**

Nachdem Azure die Registrierungsressource erstellt hat, wird sie in die Ressourcengruppenliste aufgenommen.  

![Registrierungsgruppe für Bot-App-Kanäle](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

Nachdem Ihre Bot-Kanalregistrierung erstellt wurde, müssen Sie den Teams Kanal aktivieren.

1. Wählen Sie im [Azure-Portal](https://ms.portal.azure.com/#home)unter Azure-Dienste die **Bot-Kanalregistrierung** aus, die Sie soeben erstellt haben.
1. Klicken Sie im linken Bereich auf **"Kanäle".**
1. Klicken Sie auf das Symbol Microsoft Teams und dann auf **"Speichern".**
