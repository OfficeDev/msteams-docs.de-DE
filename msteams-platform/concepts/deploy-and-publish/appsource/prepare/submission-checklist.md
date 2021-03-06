---
title: Vorbereiten der Übermittlung an den Store
description: Beschreibt die letzten Schritte, bevor Sie Ihre Microsoft Teams-App übermitteln, die im Store aufgeführt werden soll.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: c0f9c3328018884290c86a49b8026ce81022cd83
ms.sourcegitcommit: 25539046d408c4270b988fd826d7cf1275f4b9dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2021
ms.locfileid: "52763108"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Vorbereiten der Übermittlung Microsoft Teams Store

Sie haben Ihre Microsoft Teams-App entworfen, erstellt und getestet. Jetzt können Sie sie auflisten, damit Benutzer Ihre App entdecken und verwenden können.

Bevor Sie Ihre App an [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource)übermitteln, stellen Sie sicher, dass Sie Folgendes getan haben.

## <a name="validate-your-app-package"></a>Überprüfen des App-Pakets

Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um Probleme während des Übermittlungsprozesses zu vermeiden.

Das Microsoft Teams App-Überprüfungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie an Partner Center übermitteln. Das Tool überprüft die Konfigurationen Ihrer App automatisch anhand der gleichen Testfälle, die während der Store-Überprüfung verwendet werden.

1. Wechseln Sie zum [Microsoft Teams App-Überprüfungstool.](https://dev.teams.microsoft.com/appvalidation.html) (Hinweis: Das Tool ist auch in [App Studio](../../../build-and-test/app-studio-overview.md)verfügbar.)
1. Hochladen Ihr App-Paket, um die automatisierten Tests auszuführen.
1. Wechseln Sie zur **vorläufigen Checkliste,** und überprüfen Sie die Testfälle, die schwierig zu automatisieren sind.
1. [Behebung von Problemen mit Ihren Konfigurationen](~/resources/schema/manifest-schema.md) oder Apps im Allgemeinen, wenn die automatisierten Tests Ihnen Fehler liefern oder sie nicht alle Kriterien in der Prüfliste erfüllt haben.

## <a name="compile-testing-instructions"></a>Kompilieren von Testanweisungen

Stellen Sie Anweisungen und Ressourcen bereit, die den Prüfern beim Testen Ihrer App helfen, einschließlich Testkonten, Anmeldeinformationen und Lizenzschlüsseln. Sie können Anweisungen im Partner Center hinzufügen oder an einen öffentlich verfügbaren Speicherort auf SharePoint hochladen.

### <a name="feature-list"></a>Featureliste

Geben Sie Details zu den Funktionen Ihrer App in Teams und den Schritten zum Testen der einzelnen Apps an.

### <a name="accounts"></a>Konten

Sie müssen Testkonten bereitstellen, wenn Ihre App eine Lizenz oder back-End-Safelisting erfordert. Alle von Ihnen bereitgestellten Konten müssen vorab ausgefüllte Daten enthalten, um das Testen zu vereinfachen.

Abhängig von den Features Ihrer App müssen Sie möglicherweise folgendes bereitstellen:

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

Der Name Ihrer App (insbesondere der [*Kurzname)*](~/resources/schema/manifest-schema.md#name)spielt eine wichtige Rolle, wenn es darum geht, wie Benutzer sie im Store entdecken.

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo der Kurzname einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihr Kurzname den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#app-name)entspricht.

### <a name="write-descriptions"></a>Beschreibungen schreiben

Sie benötigen eine kurze und lange Beschreibung Ihrer App.

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Zusammenfassung Ihrer App, die originell, ansprechend und an Ihre Zielgruppe gerichtet sein sollte. Behalten Sie die kurze Beschreibung auf einen Satz bei.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo die kurze Beschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre kurze Beschreibung den Richtlinien für die [Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#short-description)entspricht.

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine Darstellung liefern, die die wichtigsten Features Ihrer App, die von ihr gelösten Probleme und ihre Zielgruppe hervorhebt. Obwohl diese Beschreibung bis zu 4.000 Zeichen umfassen kann, lesen die meisten Benutzer nur zwischen 300 und 500 Wörter.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo die lange Beschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre lange Beschreibung den Richtlinien für die [Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#long-description)entspricht.

### <a name="adhere-to-icon-design-guidelines"></a>Befolgen von Richtlinien für das Design von Symbolen

Symbole sind eines der Hauptelemente, die Benutzern beim Durchsuchen des Stores angezeigt werden. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig Teams Anforderungen erfüllen.

Weitere Informationen finden Sie unter [Anleitungen zum Erstellen von Teams App-Symbolen.](~/concepts/build-and-test/apps-package.md#app-icons)

### <a name="capture-screenshots"></a>Screenshots erfassen

Screenshots bieten eine ansprechende visuelle Vorschau Ihrer App, um den App-Namen, das Symbol und die Beschreibungen zu ergänzen.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Der Beispiel-Screenshot zeigt, wo App-Screenshots in einem Store-Eintrag angezeigt werden.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Denken Sie an Folgendes zu Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag haben.
* Unterstützte Dateitypen sind PNG, JPEG und GIF.
* Die Abmessungen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1.024 KB.

Bewährte Methoden finden Sie in den folgenden Ressourcen:

* [Teams Richtlinien für die Speicherüberprüfung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#screenshots)
* [Erstellen effektiver Bilder für Microsoft-App-Stores](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Erstellen eines Videos

Ein Video in Ihrem Eintrag kann die effektivste Möglichkeit sein, zu kommunizieren, warum Benutzer Ihre App verwenden sollten. Sie sollten die folgenden Fragen in einem Video beantworten:

* Wer ist Ihre App dafür?
* Welche Probleme kann Ihre App lösen?
* Wie funktioniert Ihre App?
* Welche weiteren Vorteile haben Sie durch die Verwendung Ihrer App?

#### <a name="best-practices-for-videos"></a>Bewährte Methoden für Videos

* Behalten Sie Ihr Video zwischen 30 und 90 Sekunden bei.
* Zielen Sie auf Qualität ab. In einem Eintrag sehen Benutzer Ihr Video vor Screenshots.

### <a name="select-a-category-for-your-app"></a>Auswählen einer Kategorie für Ihre App

Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren. In der folgenden Tabelle werden Teams Store-Kategorien den kategorien zugeordnet, die im [Partner Center](https://aka.ms/PartnerCenterHomePage)aufgeführt sind.

| Teams Kategorien       | Partner Center-Kategorien  |
|:---------------------|:---------------|
| Analyse und BI | Analyse, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Education | Education |
| Personalwesen | Personal und Personalwesen |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Hilfsprogramme |
| Projektmanagement | Kommunikations-, Project-, Workflow- und Unternehmensverwaltung |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzmanagement, Vertrieb und Marketing |
| Soziales und Spaß | Bild- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

### <a name="localize-your-store-listing"></a>Lokalisieren Des Store-Eintrags

Partner Center unterstützt [lokalisierte Store-Einträge.](/office/dev/store/prepare-localized-solutions) Weitere Informationen finden Sie unter [Lokalisieren ihres Teams App-Eintrags.](../../../../concepts/build-and-test/apps-localization.md)

## <a name="complete-publisher-verification"></a>Abschließen Publisher Überprüfung

[Publisher Überprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams im Store aufgeführten Apps erforderlich. Weitere Informationen finden Sie unter [häufig gestellte Fragen,](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions) [wie Sie Ihre App als herausgebergeprüft kennzeichnen](/azure/active-directory/develop/mark-app-as-publisher-verified)und problembehandlung bei der [Herausgeberüberprüfung](/azure/active-directory/develop/troubleshoot-publisher-verification)durchführen.

## <a name="complete-publisher-attestation"></a>Vollständiger Publisher Nachweis

[Publisher Nachweis](/microsoft-365-app-certification/docs/attestation) ist auch für Teams im Store aufgeführten Apps erforderlich. Der Prozess umfasst die Durchführung einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliance-Praktiken Ihrer App, die potenziellen Kunden helfen können, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine neue App übermitteln, können Sie Publisher Nachweis erst offiziell abschließen, wenn Ihre App im Teams Store aufgeführt ist. Wenn Sie eine aufgeführte App aktualisieren, führen Sie Publisher Nachweis aus, bevor Sie die neueste Version der App zur Überprüfung übermitteln.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Übermitteln Ihrer App](/office/dev/store/add-in-submission-guide)
