---
title: Vorbereiten der Übermittlung an den Store
description: Beschreibt die letzten Schritte, bevor Sie Ihre Microsoft Teams-App übermitteln, die im Store aufgeführt werden soll. Erfahren Sie, wie Sie Ihr App-Paket überprüfen, Testanweisungen kompilieren und Details zum Store-Eintrag erstellen.
ms.topic: how-to
ms.localizationpriority: medium
author: heath-hamilton
ms.author: surbhigupta
keywords: Verteilen von Validierungsrichtlinien für App-Pakete im Übermittlungsspeicher lokalisieren
ms.openlocfilehash: da0daf5daf927dcaf4346171fe78c3db6e874259
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398946"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Vorbereiten der Übermittlung an den Microsoft Teams Store

Sie haben Ihre Microsoft Teams-App entworfen, erstellt und getestet. Jetzt können Sie sie auflisten, damit Benutzer Ihre App entdecken und verwenden können.

Bevor Sie Ihre App an [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource) übermitteln, stellen Sie sicher, dass Sie Folgendes getan haben.

## <a name="validate-your-app-package"></a>Überprüfen des App-Pakets

Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um Probleme während des Übermittlungsprozesses zu vermeiden.

> [!NOTE]
> App Studio wird in Kürze eingestellt. Konfigurieren, Verteilen und Verwalten Ihrer Teams-Apps mit dem neuen [Entwicklerportal](https://dev.teams.microsoft.com/)

Das Microsoft Teams App-Überprüfungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie an Partner Center übermitteln. Das Tool überprüft die Konfigurationen Ihrer App automatisch anhand der gleichen Testfälle, die während der Store-Überprüfung verwendet werden.

1. Wechseln Sie zum [Microsoft Teams App-Überprüfungstool](https://dev.teams.microsoft.com/appvalidation.html). (Hinweis: Das Tool ist auch in [App Studio](../../../build-and-test/app-studio-overview.md) verfügbar.)
1. Hochladen Ihr App-Paket, um die automatisierten Tests auszuführen.
1. Wechseln Sie zur **vorläufigen Checkliste** , und überprüfen Sie die Testfälle, die schwierig zu automatisieren sind.
1. [Beheben von Problemen mit Ihren Konfigurationen](~/resources/schema/manifest-schema.md) oder Ihrer App im Allgemeinen. Diese Probleme treten auf, wenn die automatisierten Tests Ihnen Fehler liefern oder sie nicht alle Kriterien in der Prüfliste erfüllt haben.

## <a name="compile-testing-instructions"></a>Kompilieren von Testanweisungen

Stellen Sie Anweisungen und Ressourcen bereit, um die Prüfer beim Testen Ihrer App zu unterstützen, einschließlich:

* Testkonten
* Anmeldeinformationen
* Lizenzschlüssel

Sie können Anweisungen im Partner Center hinzufügen oder an einen öffentlich verfügbaren Speicherort auf SharePoint hochladen.

### <a name="feature-list"></a>Featureliste

Geben Sie Details zu den Funktionen Ihrer App in Teams und Schritten zum Testen der einzelnen Funktionen an.

### <a name="accounts"></a>Konten

Stellen Sie Testkonten bereit, wenn Ihre App eine Lizenz oder einen sicheren Back-End-Eintrag erfordert. Alle von Ihnen bereitgestellten Konten müssen vorab ausgefüllte Daten enthalten, um beim Testen zu helfen.

Abhängig von den Features Ihrer App müssen Sie möglicherweise alle folgenden Konten bereitstellen:

* Administratorkonto (erforderlich)
* Nicht-Administratorkonto (erforderlich)
* Ein Konto, das nicht vorkonfiguriert ist, um die Anmeldung bei der ersten Ausführung ordnungsgemäß zu testen (erforderlich)
* Ein Konto mit Zugriff auf Premium- oder aktualisierte Features (falls zutreffend)
* Zwei Konten im selben Mandanten zum Testen der Zusammenarbeitserfahrung für Apps, die in freigegebenen Kontexten funktionieren (falls zutreffend)

### <a name="tenant-configurations"></a>Mandantenkonfigurationen

Wenn Sie einen Teams Mandanten für die Verwendung Ihrer App konfigurieren müssen, fügen Sie diese Anweisungen sowie Administrator- und Nicht-Administratorkonten zur Überprüfung ein.

### <a name="video-optional"></a>Video (optional)

Stellen Sie eine Aufzeichnung Ihrer App bereit, damit Microsoft die Funktionalität vollständig verstehen kann.

## <a name="create-your-store-listing-details"></a>Erstellen der Details ihres Store-Eintrags

Die Informationen, die Sie an [Partner Center](https://partner.microsoft.com) übermitteln&#8212;einschließlich Name, Beschreibungen, Symbolen und Bildern&#8212;werden zum Teams Store- und Microsoft AppSource-Eintrag für Ihre App.

Ein Store-Eintrag kann der erste Eindruck einer Person von Ihrer App sein. Erhöhen Sie Installationen mit einem Eintrag, der die Vorteile, Funktionen und Marken Ihrer App effektiv vermittelt.

### <a name="specify-a-short-name"></a>Angeben eines Kurznamens

Der Name Ihrer App (insbesondere der [*Kurzname*](~/resources/schema/manifest-schema.md#name)) spielt eine wichtige Rolle, wenn es darum geht, wie Benutzer sie im Store entdecken.

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo der Kurzname einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihr Kurzname den Richtlinien für die [Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#app-name) entspricht.

### <a name="write-descriptions"></a>Beschreibungen schreiben

Sie müssen eine kurze und lange Beschreibung Ihrer App haben.

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Zusammenfassung Ihrer App, die originell, ansprechend und an Ihre Zielgruppe gerichtet sein sollte. Halten Sie die kurze Beschreibung in einem Satz.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo die kurze Beschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre kurze Beschreibung den Richtlinien für die [Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#short-description) entspricht.

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine Darstellung liefern, die Ihre Apps hervorhebt:

* Hauptfeatures
* Die gelösten Probleme
* Zielgruppe

Obwohl diese Beschreibung bis zu 4 000 Zeichen lang sein kann, werden die meisten Benutzer nur zwischen 300 und 500 Wörter lesen.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo die lange Beschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre lange Beschreibung den Richtlinien für die [Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#long-description) entspricht.

### <a name="adhere-to-icon-design-guidelines"></a>Befolgen von Richtlinien für das Design von Symbolen

Symbole sind eines der Hauptelemente, die Benutzern beim Durchsuchen des Stores angezeigt werden. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig Teams Anforderungen erfüllen.

Weitere Informationen finden Sie unter [Anleitungen zum Erstellen von Teams App-Symbolen](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="capture-screenshots"></a>Screenshots erfassen

Screenshots bieten eine auffällige visuelle Vorschau Ihrer App, um Ihren App-Namen, das Symbol und die Beschreibungen zu ergänzen.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Im Beispiel-Screenshot wird hervorgehoben, wo App-Screenshots in einem Store-Eintrag angezeigt werden.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Denken Sie an die folgenden bewährten Methoden für Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag erstellen.
* Zu den unterstützten Dateitypen gehören .png-, JPEG- und GIF-Bildformate.
* Die Abmessungen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1 024 KB.

Bewährte Methoden finden Sie in den folgenden Ressourcen:

* [Teams Store Validierungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#screenshots)
* [Erstellen effektiver Bilder für Microsoft-App-Stores](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Erstellen eines Videos

Ein Video in Ihrem Eintrag kann die effektivste Methode sein, um zu vermitteln, warum Benutzer Ihre App verwenden sollten. Behandeln Sie die folgenden Fragen in einem Video:

* Wer ist Ihre App dafür?
* Welche Probleme kann Ihre App lösen?
* Wie funktioniert Ihre App?
* Welche weiteren Vorteile haben Sie durch die Verwendung Ihrer App?

Sie können eine URL für Ihr YouTube- oder YouTube-Video hinzufügen.

#### <a name="best-practices-for-videos"></a>Bewährte Methoden für Videos

* Behalten Sie Ihr Video zwischen 60 und 90 Sekunden bei.
* Zielen Sie auf Qualität ab. In einem Eintrag sehen Benutzer Ihr Video vor Screenshots.
* Kommunizieren Sie den Wert des Produkts in narrativer Form.
* Demonstrieren, wie das Produkt funktioniert.

### <a name="select-a-category-for-your-app"></a>Auswählen einer Kategorie für Ihre App

Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren. In der folgenden Tabelle werden Teams Store Kategorien den im [Partner Center](https://aka.ms/PartnerCenterHomePage) aufgeführten Kategorien zugeordnet.

| Teams Kategorien       | Partner Center-Kategorien  |
|:---------------------|:---------------|
| Analyse und BI | Analyse, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Bildung | Bildung |
| Personalwesen | Personal und Personalwesen |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Hilfsprogramme |
| Projektmanagement | Kommunikations-, Project-, Workflow- und Unternehmensverwaltung |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzmanagement sowie Vertrieb und Marketing |
| Soziales und Spaß | Bild- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

### <a name="localize-your-store-listing"></a>Lokalisieren Des Store-Eintrags

Partner Center unterstützt [lokalisierte Store-Einträge](/office/dev/store/prepare-localized-solutions). Weitere Informationen finden Sie unter ["Lokalisieren ihres Teams App-Eintrags](../../../../concepts/build-and-test/apps-localization.md)".

## <a name="complete-publisher-verification"></a>Abschließen Publisher Überprüfung

[Publisher Überprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams im Store aufgeführten Apps erforderlich. Weitere Informationen finden Sie unter [Häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [wie Sie Ihre App als vom Publisher bestätigt markieren](/azure/active-directory/develop/mark-app-as-publisher-verified)und [Fehlerbehebung bei der Publisher-Verifizierung](/azure/active-directory/develop/troubleshoot-publisher-verification).

## <a name="complete-publisher-attestation"></a>Vollständige Publisher Nachweis

[Publisher Nachweis](/microsoft-365-app-certification/docs/attestation) ist auch für Teams im Store aufgeführten Apps erforderlich. Der Prozess umfasst die Durchführung einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliancepraktiken Ihrer App. Der Prozess kann potenziellen Kunden helfen, fundierte Entscheidungen zur Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine neue App übermitteln, können Sie Publisher Nachweis erst offiziell abschließen, wenn Ihre App im Teams Store aufgeführt ist. Wenn Sie eine aufgeführte App aktualisieren, führen Sie Publisher Nachweis aus, bevor Sie die neueste Version der App zur Überprüfung übermitteln.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Übermitteln Ihrer App](/office/dev/store/add-in-submission-guide)

## <a name="see-also"></a>Siehe auch

[Beheben von Problemen, wenn die Übermittlung Microsoft Teams Store fehlschlägt](~/concepts/deploy-and-publish/appsource/resolve-submission-issues.md)
