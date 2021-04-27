---
title: Azure-Bot-Kanalregistrierung
description: Beschreibt Azure-Botkanäle für die Registrierung
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta12
ms.openlocfilehash: 3cbbd204daf98f1c3528dcb6efcfde299a402912
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020949"
---
1. Wählen Sie [im Azure-Portal](https://ms.portal.azure.com/#home)unter Azure Services die Option **Ressource erstellen aus.**
1. Geben Sie im Suchfeld "Bot" ein. Wählen Sie in der Dropdownliste Bot **Channels Registration aus.**
1. Wählen Sie die **Schaltfläche Erstellen** aus.
1. Geben Sie **im Blatt Bot Channel Registration** die angeforderten Informationen zu Ihrem Bot an.
1. Lassen Sie **das Feld** Messaging-Endpunkt vorerst leer, geben Sie nach der Bereitstellung des Bots die erforderliche URL ein. Die folgende Abbildung zeigt ein Beispiel für die Registrierungseinstellungen:

    ![Registrierung von Bot-App-Kanälen](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Klicken **Sie auf Microsoft App-ID und -Kennwort,** und erstellen Sie dann **Neu**.

    ![Erstellen der Microsoft App-ID ](../../assets/images/authentication/CreateMicrosoftAppID.png) ![ Erstellen einer neuen Microsoft App-ID](../../assets/images/authentication/CreateNewMicrosoftAppID.png)    

1. Klicken **Sie im Link App-Registrierungsportal auf App-ID** erstellen.

   ![App-Registrierungen](../../assets/images/authentication/AppRegistration.png)
   
1. Klicken Sie im angezeigten **App-Registrierungsfenster** **oben** links auf die Registerkarte Neue Registrierung.
1. Geben Sie den Namen der Botanwendung ein, die Sie registrieren, wir haben *BotTeamsAuth* verwendet (Sie müssen Ihren eigenen eindeutigen Namen auswählen).
1. Wählen Sie für die unterstützten **Kontotypen** Konten in einem beliebigen Organisationsverzeichnis *(Beliebiges Azure AD-Verzeichnis - Multitenant) und persönlichen Microsoft-Konten (z. B. Skype, Xbox) aus.*
1. Klicken Sie auf **die Schaltfläche Registrieren.** Nach Abschluss zeigt Azure die Seite *Übersicht* für die Anwendung an.
1. Kopieren und speichern Sie in einer Datei den **Application (client)-ID-Wert.**
1. Klicken Sie im linken Bereich auf **Zertifikat und geheime Schlüssel.**
    1. Klicken *Sie unter Geheime* Clientgeheimnisse auf **Neuer Geheimer Clientgeheimnis.**
    1. Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen Personen zu identifizieren, die Sie möglicherweise für diese App erstellen müssen.
    1. Set *Expires* to your selection.
    1. Klicken Sie auf **Hinzufügen**.
    1. Kopieren Sie den geheimen Clientgeheimnis, und speichern Sie ihn in einer Datei.
1. Wechseln Sie zurück zum **Fenster Bot Channel Registration,** und kopieren Sie die *App-ID* und den geheimen *Client* in die Felder **Microsoft App-ID** **und** Kennwort.
1. Klicken Sie auf **OK**.
1. Klicken Sie schließlich auf **Erstellen**.

Nachdem Azure die Registrierungsressource erstellt hat, wird sie in die Ressourcengruppenliste aufgenommen.  

![Registrierungsgruppe für Bot-App-Kanäle](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

Nachdem Die Registrierung Ihrer Botkanäle erstellt wurde, müssen Sie den Teams-Kanal aktivieren.

1. Wählen Sie [im Azure-Portal](https://ms.portal.azure.com/#home)unter Azure Services die gerade erstellte **Botkanalregistrierung** aus.
1. Klicken Sie im linken Bereich auf **Kanäle**.
1. Klicken Sie auf das Microsoft Teams-Symbol, und wählen Sie **dann Speichern aus.**
