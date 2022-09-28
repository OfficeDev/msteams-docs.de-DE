---
title: Verwalten Ihrer Apps mit dem Entwicklerportal
description: In diesem Artikel erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams konfigurieren, verteilen und verwalten.
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 02b9272c2c0d325501c28d150ac728230ac65255
ms.sourcegitcommit: 9ebb516ac448627e1deb42e18703791fc2ad583d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68098918"
---
# <a name="manage-your-apps-in-developer-portal"></a>Verwalten Ihrer Apps im Entwicklerportal

Nachdem Sie Ihre App erstellt oder hochgeladen haben, können Sie Ihre Apps im Entwicklerportal wie folgt verwalten:

* [Übersicht](#overview)
* [Konfigurieren](#configure)
* [Erweitert](#advanced)
* [Publish](#publish)

## <a name="overview"></a>Übersicht

Im Abschnitt **"Übersicht** " sehen Sie die folgenden Komponenten zum Verwalten Ihrer App:

* Dashboard

  * Im **Abschnitt "Dashboard** " unter " **Übersicht** " sehen Sie die folgenden Komponenten für Ihre App:
    * **Validierung des Teams-Stores**: Das App-Überprüfungstool überprüft Ihr App-Paket anhand der Testfälle, die Microsoft beim Überprüfen Ihrer App verwendet.
    * **Ankündigung**: Neueste Updates Ihrer Apps im Entwicklerportal für Teams
    * **Aktive Benutzer (Vorschau)**: Zeigt die Anzahl der aktiven Benutzer an.
    * **Grundlegende Informationen**: Zeigt die App-ID, Version, Manifestversion usw. an.

    :::image type="content" source="../../assets/images/tdp/dashboard-page.png" alt-text="Der Screenshot ist ein Beispiel, das die Übersichtsseite der App zeigt, die Sie im Entwicklerportal für Teams erstellt haben.":::

* Analyse

    Auf der **Seite "Analyse** " unter " **Übersicht** " wird die Gesamtzahl der aktiven Benutzer für Ihre App angezeigt. Weitere Informationen finden Sie unter [Analysieren der App-Nutzung](analyze-your-apps-usage-in-developer-portal.md).

## <a name="configure"></a>Konfigurieren

Um Ihre App in Teams zu installieren und zu rendern, müssen Sie eine Reihe von Konfigurationen einschließen, die Teams erkennt. Um Ihre Apps in Teams hochzuladen, benötigen Sie ein App-Manifest, das alle App-Details enthält, um Ihre App in Teams anzuzeigen. Dies kann mit Hilfe von Komponenten und Tools erreicht werden, die im Entwicklerportal verfügbar sind.

Im Abschnitt **"Konfigurieren"** sehen Sie die folgenden Komponenten zum Verwalten und Zugreifen auf Ihre App:

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
* **Einmaliges Anmelden**: Der in Azure AD registrierte Bot unterstützt single Sign-On (SSO). Wenn ein Bot im Bot Framework-Portal (oder im Entwicklerportal unter Bot-Verwaltung) registriert ist, unterstützen diese Bots SSO nicht, und Sie müssen Ihren Bot bei Azure AD registrieren, um SSO zu unterstützen. Fügen Sie für einen in Azure AD registrierten Bot den **Anwendungs-ID-URI hinzu**. Informationen zum Abrufen des Anwendungs-ID-URI aus Azure AD finden [Sie unter Verwenden der SSO-Authentifizierung für Bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).
* **Sprachen**: Sie können die Sprache Ihrer App einrichten oder ändern.
* **Domäne**: Sie können die Domänen hinzufügen, um Ihre Apps im Teams-Client zu laden (z. B.: *.example.com).

:::image type="content" source="../../assets/images/tdp/configure.png" alt-text="Der Screenshot ist ein Beispiel zum Konfigurieren von Features zum Verwalten und Zugreifen auf Ihre App im Entwicklerportal.":::

## <a name="advanced"></a>Fortgeschritten

Im Abschnitt **"Erweitert** " sehen Sie die folgenden Komponenten zum Verwalten Ihrer App im Entwicklerportal:

* **Besitzer**

    Jede App enthält eine **Seite "Besitzer"** , auf der Sie Ihre App-Registrierung für andere Personen in Ihrer Organisation freigeben können. Sie können **die Rolle "Administrator** " und " **Operative"** hinzufügen, um zu verwalten, wer die Einstellungen Ihrer App ändern kann. Die **Rolle "Operative"** verfügt über die gleichen Berechtigungen wie die **Administratorrolle** , mit Ausnahme des Löschens einer App.

    So fügen Sie einen Besitzer hinzu:

    1. Wählen Sie im Abschnitt **"Erweitert** " **die Option "Besitzer**" aus.
    1. Wählen Sie **"Besitzer hinzufügen"** aus.
    1. Geben Sie einen Namen ein, und wählen Sie eine Benutzer-ID aus der Dropdownliste aus.
    1. Wählen Sie unter **"Rolle****" die Option "Operativ**" oder **"Administrator"** aus.
    1. Klicken Sie auf **Hinzufügen**.

* **App-Inhalt**: Sie können Ihre App mit den folgenden zusätzlichen Features konfigurieren:
  
  * Ladeindikator: Zeigt einen Indikator an, um Benutzern mitzuteilen, dass Ihre gehosteten App-Inhalte (z. B. Registerkarten und Aufgabenmodule) geladen werden.
  * Vollbildmodus: Zeigt eine persönliche App ohne App-Header an. Es wird nur für die veröffentlichten Apps für Ihre Organisation unterstützt.

* **Umgebungen**

    Sie können Umgebungen und globale Variablen konfigurieren, um den Übergang Ihrer App von der lokalen Laufzeit zur Produktion zu erleichtern. Globale Variablen werden in allen Umgebungen verwendet.

    So richten Sie eine Umgebung ein:

    1. Wählen Sie im Entwicklerportal die **Apps** aus, an denen Sie gerade arbeiten.
    1. Wechseln Sie unter "**Erweitert****" zu "Umgebungen**", und wählen Sie **"+Umgebung hinzufügen"** aus.
    1. Klicken Sie auf **Hinzufügen**.

  * **Globale Variablen**

      1. Wählen Sie **"Globale Variable hinzufügen"** aus, um Konfigurationsvariablen für Ihre Umgebung zu erstellen.

      So verwenden Sie globale Variablen:

      Verwenden Sie die Variablennamen anstelle hartcodierter Werte, um Ihre App-Konfigurationen festzulegen.

      1. Geben Sie `{{` in ein beliebiges Feld im Entwicklerportal ein. Es wird eine Dropdownliste mit allen Variablen angezeigt, die Sie für die ausgewählte Umgebung zusammen mit den globalen Variablen erstellt haben.  
      1. Wählen Sie vor dem Herunterladen Ihres App-Pakets (z. B. beim Vorbereiten der Veröffentlichung im Teams-Store) die Umgebung aus, die Sie verwenden möchten. Ihre App-Konfigurationen werden automatisch basierend auf der Umgebung aktualisiert.

* **Plan und Preise**: Sie können ein SaaS-Angebot verknüpfen, das Sie im Partner Center für Ihre App erstellt haben.
* **Admin Einstellungen**:
  * App-Anpassung: Sie können Ihre App anpassen
  * App standardmäßig blockieren: Sie können Ihre App standardmäßig für Benutzer blockieren, bis ein Mandantenadministrator sie aktiviert hat.

## <a name="publish"></a>Veröffentlichen

Sie können Ihre App in Ihrer Organisation oder im Teams Store veröffentlichen.

* **Veröffentlichen Sie Ihre App in der Organisation**:

   1. Wählen Sie auf der Seite " **App-Übersicht** " unter **"Veröffentlichen**" **die Option "In Organisation veröffentlichen"** aus.
   1. Wählen Sie **"App veröffentlichen"** aus.

* **Veröffentlichen Sie Ihre App im Store**:

   1. Wählen Sie auf der Seite " **App-Übersicht** " unter **"Veröffentlichen**" **die Option "Im Store veröffentlichen" aus**.
   1. Wählen Sie **Veröffentlichen** aus.

   > [!NOTE]
   > Das App-Überprüfungstool überprüft Ihr App-Paket anhand der Testfälle, die Microsoft zum Überprüfen Ihrer App verwendet. Beheben Sie Fehler oder Warnungen, und lesen Sie die **Prüfliste für die App-Übermittlung** , bevor Sie Ihre App übermitteln.

   Sie können das App-Paket herunterladen, indem Sie auf der Seite "Im Store veröffentlichen" die Schaltfläche " **App-Paket herunterladen** " auswählen.

* **App-Paket**: Das App-Paket beschreibt, wie Ihre App konfiguriert ist, die App-Features, erforderliche Ressourcen und andere wichtige Attribute im Manifest enthält. Auf der Registerkarte "Symbol" wird das symbol angezeigt, das für Ihre App verwendet wird.

## <a name="test-your-app-directly-in-teams"></a>Testen Ihrer App direkt in Teams

Das Entwicklerportal bietet Optionen zum Testen und Debuggen Ihrer App:

* Auf der Seite **"Übersicht** " sehen Sie eine Momentaufnahme, ob Ihre App konfiguriert und anhand von Teams Store-Testfällen überprüft wurde.
* Die Schaltfläche " **Vorschau in Teams** " startet Ihre App schnell im Teams-Client zum Debuggen.

## <a name="use-tools-to-create-app-features"></a>Verwenden von Tools zum Erstellen von App-Features

Das Entwicklerportal enthält außerdem Tools, mit denen Sie wichtige Features von Teams-Apps erstellen können. Die folgenden Tools sind verfügbar:

* **Szenenstudio**: Entwerfen [benutzerdefinierter Szenen im Zusammen-Modus](~/apps-in-teams-meetings/teams-together-mode.md) für Teams-Besprechungen.
* **Editor für adaptive Karten**: Erstellen Sie adaptive Karten, und zeigen Sie eine Vorschau an, die in Ihre Apps aufgenommen werden sollen.
* **Microsoft Identity Platform-Verwaltung**: Registrieren Sie Ihre Apps bei Azure Active Directory, um Benutzern bei der Anmeldung und dem Zugriff auf APIs zu helfen.
* **Validierung der Teams Store-App**: Überprüfen Sie Ihr App-Paket anhand der Testfälle, die Microsoft zum Überprüfen Ihrer App verwendet.
* **Bot-Verwaltung**: Fügen Sie Ihrer App Unterhaltungsbots hinzu, die mit Benutzern kommunizieren, auf ihre Fragen antworten und sie proaktiv über Änderungen und andere Ereignisse informieren.

So fügen Sie einen Bot hinzu:

1. Wählen Sie im Entwicklerportal im linken Bereich " **Extras** " aus.
1. Wählen Sie die **Bot-Verwaltung** aus.
1. Wählen Sie auf der Seite "Botverwaltung" die Option **"Neuer Bot" aus**.
1. Geben Sie den Namen ein, und wählen Sie **"Hinzufügen"** aus.

   :::image type="content" source="../../assets/images/tdp/tools-in-dev-portal.png" alt-text="Der Screenshot ist ein Beispiel, das die Tools im Entwicklerportal zeigt, mit denen Sie wichtige Features erstellen können.":::

Über das Entwicklerportal können Sie zum Bot Framework-Portal wechseln und Ihren Bot so konfigurieren, dass er das Symbol und andere Eigenschaften aktualisiert.

## <a name="see-also"></a>Siehe auch

[Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
