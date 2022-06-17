---
title: Vorbereiten der Übermittlung an den Store
description: Lernen Sie die letzten Schritte kennen, bevor Sie Ihre Microsoft Teams-App übermitteln, die im Store aufgeführt werden soll. Erfahren Sie, wie Sie Ihr App-Paket überprüfen und vieles mehr.
ms.topic: how-to
ms.localizationpriority: high
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: c71579900f910d2677ab0d48bab5a37853dfb69c
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123167"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Vorbereiten der Übermittlung an den Microsoft Teams Store

Sie haben Ihre Microsoft Teams-App entworfen, erstellt und getestet. Jetzt können Sie sie auflisten, damit Benutzer Ihre App entdecken und verwenden können.

Sehen Sie sich das folgende Video an, um mehr über die Veröffentlichung Ihrer Anwendung im Microsoft Teams App Store zu erfahren:
<br>

> [!VIDEO <https://www.microsoft.com/videoplayer/embed/RE4WG3l>]
<br>

Bevor Sie Ihre App beim[Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource)einreichen, sollten Sie Folgendes tun.

## <a name="validate-your-app-package"></a>Überprüfen Ihres App-Pakets

Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um Probleme während des Übermittlungsprozesses zu vermeiden.

> [!WARNING]
> Wenn Sie App Studio verwendet haben, empfehlen wir Ihnen, das[Developer Portal](https://dev.teams.microsoft.com/)auszuprobieren, um Ihre Teams-Anwendungen zu konfigurieren, zu verteilen und zu verwalten. App Studio wird zum 30. Juni 2022 eingestellt.

Das Microsoft Teams App-Überprüfungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie sie an Partner Center übermitteln. Das Tool überprüft die Konfigurationen Ihrer App automatisch anhand der gleichen Testfälle, die während der Store-Überprüfung verwendet werden.

1. Wechseln Sie zum [Microsoft Teams App-Überprüfungstool](https://dev.teams.microsoft.com/appvalidation.html). (Hinweis: Das Tool ist auch in [App Studio](../../../build-and-test/app-studio-overview.md) verfügbar.)
1. Laden Sie Ihr App-Paket hoch, um die automatisierten Tests auszuführen.
1. Wechseln Sie zur **vorläufigen Checkliste**, und überprüfen Sie die Testfälle, die schwierig zu automatisieren sind.
1. [Beheben Sie Fehler mit Ihren Konfigurationen ](~/resources/schema/manifest-schema.md) oder Ihrer App ganz allgemein. Diese Probleme treten auf, wenn die automatisierten Tests Ihnen Fehler liefern, oder wenn Sie nicht alle Kriterien in der Prüfliste erfüllt haben.

## <a name="compile-testing-instructions"></a>Kompilieren von Testanweisungen

Stellen Sie Anweisungen und Ressourcen bereit, um die Prüfer beim Testen Ihrer App zu unterstützen, einschließlich:

* Testkonten
* Anmeldeinformationen
* Lizenzschlüssel

Sie können Anweisungen im Partner Center hinzufügen oder an einen öffentlich verfügbaren Speicherort auf SharePoint hochladen.

### <a name="feature-list"></a>Featureliste

Geben Sie Details zu den Funktionen Ihrer App in Teams und Schritten zum Testen der einzelnen Funktionen an.

### <a name="accounts"></a>Konten

Stellen Sie Testkonten bereit, wenn Ihre App eine Lizenz oder eine sichere Back-End-Auflistung erfordert. Alle von Ihnen bereitgestellten Konten müssen vorab ausgefüllte Daten enthalten, um beim Testen zu helfen.

Abhängig von den Features Ihrer App müssen Sie möglicherweise alle folgenden Konten bereitstellen:

* Administratorkonto (erforderlich)
* Nicht-Administratorkonto (erforderlich)
* Ein Konto, das nicht vorkonfiguriert ist, um die Anmeldung bei der ersten Ausführung ordnungsgemäß zu testen (erforderlich)
* Ein Konto mit Zugriff auf Premium- oder aktualisierte Features (falls zutreffend)
* Zwei Konten im selben Mandanten zum Testen der Zusammenarbeitserfahrung für Apps, die in freigegebenen Kontexten funktionieren (falls zutreffend)

### <a name="tenant-configurations"></a>Mandantenkonfigurationen

Wenn Sie einen Teams-Mandanten für die Verwendung Ihrer App konfigurieren müssen, schließen Sie diese Anweisungen sowie Administrator- und Nicht-Administratorkonten für die Überprüfung ein.

### <a name="video-optional"></a>Video (optional)

Stellen Sie eine Aufzeichnung Ihrer App bereit, damit Microsoft die Funktionalität vollständig verstehen kann.

## <a name="create-your-store-listing-details"></a>Erstellen der Details ihres Store-Eintrags

Die Informationen, die Sie an [Partner Center](https://partner.microsoft.com) übermitteln&#8212;einschließlich Name, Beschreibungen, Symbolen und Bildern&#8212;werden zum Teams Store- und Microsoft AppSource-Eintrag für Ihre App.

Ein Store-Eintrag kann der erste Eindruck einer Person von Ihrer App sein. Erhöhen Sie Installationen mit einem Eintrag, der die Vorteile, Funktionen und Marken Ihrer App effektiv vermittelt.

### <a name="specify-a-short-name"></a>Geben Sie einen kurzen Namen ein.

Der Name Ihrer App (insbesondere der *[Kurzname](~/resources/schema/manifest-schema.md#name)*) spielt eine wichtige Rolle, wenn es darum geht, wie Benutzer sie im Store entdecken.

:::row:::

:::column span="3":::
:::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Der Beispiel-Screenshot zeigt, wo der Kurzname einer App in einem Store-Eintrag angezeigt wird.":::
:::column-end:::
:::column span="1":::
:::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihr Kurzname den Richtlinien für die [Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#app-name) entspricht.

### <a name="write-descriptions"></a>Verfassen attraktiver Beschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben.

#### <a name="short-description"></a>Kurzbeschreibung

Eine präzise Zusammenfassung Ihrer App, die originell, ansprechend und auf Ihre Zielgruppe ausgerichtet sein sollte. Beschränken Sie die kurze Beschreibung auf einen Satz.

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

Symbole sind eines der Hauptelemente, die Benutzer beim Durchsuchen des Teams-Speichers sehen. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig die folgenden Anforderungen erfüllen.

Weitere Informationen finden Sie unter [Anleitungen zum Erstellen von Teams App-Symbolen](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="capture-screenshots"></a>Bildschirmfotos aufnehmen

Screenshots bieten eine auffällige visuelle Vorschau Ihrer App, um Ihren App-Namen, das Symbol und die Beschreibungen zu ergänzen.

:::row:::

:::column span="3":::
:::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Im Beispiel-Screenshot wird hervorgehoben, wo App-Screenshots in einem Store-Eintrag angezeigt werden.":::
:::column-end:::
:::column span="1":::
:::column-end:::

:::row-end:::

Beachten Sie die folgenden bewährten Methoden für Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag erstellen.
* Unterstützte Dateitypen sind .png-, .jpeg- und .gif-Bildformate.
* Die Abmessungen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1 024 KB.

Bewährte Methoden finden Sie in den folgenden Ressourcen:

* [Validierungsrichtlinien für den Microsoft Teams Store](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#screenshots)
* [Erstellen effektiver Bilder für Microsoft-App-Stores](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Erstellen eines Videos

Ein Video in Ihrem Listing kann die effektivste Methode sein, um zu kommunizieren, warum Personen Ihre App verwenden sollten. Beantworten Sie die folgenden Fragen in einem Video:

* Für wen ist Ihre App geeignet?
* Welche Probleme kann Ihre App lösen?
* Wie funktioniert Ihre App?
* Welche weiteren Vorteile haben Sie durch die Verwendung Ihrer App?

Sie können eine URL für Ihr YouTube- oder Vimeo-Video hinzufügen.

#### <a name="best-practices-for-videos"></a>Bewährte Methoden für Videos

* Halten Sie Ihr Video zwischen 60 und 90 Sekunden.
* Achten Sie auf Qualität. In einem Listing sehen Benutzer Ihr Video vor Screenshots.
* Kommunizieren Sie den Wert des Produkts in erzählerischer Form.
* Veranschaulichen, wie das Produkt funktioniert.

### <a name="select-a-category-for-your-app"></a>Wählen Sie eine Kategorie für Ihre App aus.

Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren. In der folgenden Tabelle werden Teams Store Kategorien den im [Partner Center](https://aka.ms/PartnerCenterHomePage) aufgeführten Kategorien zugeordnet.

| Teams Kategorien       | Partner Center Kategorien  |
|:---------------------|:---------------|
| Analysen und BI | Analyse, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Bildung | Bildung |
| Personalwesen | Personalwesen und Rekrutierung |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Hilfsprogramme |
| Projektmanagement | Kommunikations-, Project-, Workflow- und Unternehmensverwaltung |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzmanagement sowie Vertrieb und Marketing |
| Soziale Netzwerke und Unterhaltung | Bild- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

### <a name="localize-your-store-listing"></a>Lokalisieren Ihres Store-Eintrags

Partner Center unterstützt [lokalisierte Store-Einträge](/office/dev/store/prepare-localized-solutions). Weitere Informationen finden Sie unter [wie Sie Ihre Teams-App-Auflistung](../../../../concepts/build-and-test/apps-localization.md) lokalisieren.

## <a name="complete-publisher-verification"></a>Abschließen der Herausgeberüberprüfung

[Herausgeberüberprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams-Apps erforderlich, die im Store aufgeführt sind. Weitere Informationen finden Sie unter [Häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [wie Sie Ihre App als vom Publisher bestätigt markieren](/azure/active-directory/develop/mark-app-as-publisher-verified)und [Fehlerbehebung bei der Publisher-Verifizierung](/azure/active-directory/develop/troubleshoot-publisher-verification).

## <a name="complete-publisher-attestation"></a>Abschließen des Herausgebernachweises

[Herausgebernachweis](/microsoft-365-app-certification/docs/attestation) ist auch für Teams-Apps erforderlich, die im Store aufgeführt sind. Der Prozess umfasst die Durchführung einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliancepraktiken Ihrer App. Der Prozess kann potenziellen Kunden helfen, fundierte Entscheidungen zur Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine neue App übermitteln, können Sie den Herausgebernachweis erst offiziell abschließen, wenn Ihre App im Teams Store aufgeführt ist. Wenn Sie eine aufgelistete App aktualisieren, schließen Sie den Herausgebernachweis ab, bevor Sie die neueste Version der App zur Überprüfung übermitteln.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Übermitteln Ihrer App](/office/dev/store/add-in-submission-guide)

## <a name="see-also"></a>Siehe auch

[Beheben von Problemen, wenn ihre Microsoft Teams Store-Übermittlung fehlschlägt](~/concepts/deploy-and-publish/appsource/resolve-submission-issues.md)
