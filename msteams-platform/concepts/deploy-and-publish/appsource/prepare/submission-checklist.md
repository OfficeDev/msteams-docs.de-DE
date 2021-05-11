---
title: Vorbereiten der Übermittlung an den Store
description: Beschreibt die letzten Schritte vor dem Übermitteln Microsoft Teams App, die im Store aufgeführt werden soll.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: f73e36ca0587768421daf60229d0a241cae171e1
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230939"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Vorbereiten der Microsoft Teams Speicherübermittlung

Sie haben Ihre App entworfen, erstellt und Microsoft Teams getestet. Jetzt können Sie sie auflisten, damit Die Benutzer Ihre App entdecken und mit der Verwendung beginnen können.

Bevor Sie Ihre App an [Partner Center übermitteln,](/office/dev/store/use-partner-center-to-submit-to-appsource)stellen Sie sicher, dass Sie folgendes getan haben.

## <a name="validate-your-app-package"></a>Überprüfen Des App-Pakets

Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um zu vermeiden, dass während des Übermittlungsprozesses Probleme auftreten.

Das Microsoft Teams-App-Validierungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie sie an Partner Center übermitteln. Das Tool überprüft die Konfigurationen Ihrer App automatisch mit den gleichen Testfällen, die während der Speicherüberprüfung verwendet werden.

1. Wechseln Sie zum [Microsoft Teams App-Überprüfungstool](https://dev.teams.microsoft.com/appvalidation.html). (Hinweis: Das Tool ist auch in [App Studio verfügbar.)](../../../build-and-test/app-studio-overview.md)
1. Hochladen App-Paket, um die automatisierten Tests durchzuführen.
1. Wechseln Sie zur **Vorläufigen Prüfliste,** und überprüfen Sie die Testfälle, die schwer zu automatisieren sind.
1. [Beheben Sie Probleme mit Ihren Konfigurationen](~/resources/schema/manifest-schema.md) oder Apps im Allgemeinen, wenn die automatisierten Tests Fehler verursachen oder Sie nicht alle Kriterien in der Prüfliste erfüllt haben.

## <a name="compile-testing-instructions"></a>Kompilieren von Testanweisungen

Stellen Sie Anweisungen und Ressourcen zur Verfügung, mit denen die Prüfer Ihre App testen können, einschließlich Testkonten, Anmeldeinformationen und Lizenzschlüsseln. Sie können Anweisungen im Partner Center hinzufügen oder sie an einen öffentlich verfügbaren Speicherort in SharePoint.

### <a name="feature-list"></a>Featureliste

Geben Sie Details zu den Funktionen Ihrer App in Teams und Schritte zum Testen der einzelnen Apps an.

### <a name="accounts"></a>Konten

Sie müssen Testkonten bereitstellen, wenn Ihre App eine Lizenz- oder Back-End-Safelisting erfordert. Alle konten, die Sie bereitstellen, müssen vorab ausgefüllte Daten enthalten, um tests zu erleichtern.

Je nach den Features Ihrer App müssen Sie möglicherweise folgendes bereitstellen:

* Administratorkonto (erforderlich)
* Nicht-Administrator-Konto (erforderlich)
* Ein Konto, das nicht vorkonfiguriert ist, um die Anmeldeerfahrung bei der ersten Ausführung ordnungsgemäß zu testen (erforderlich)
* Ein Konto mit Zugriff auf Premium- oder Upgradefeatures (sofern zutreffend)
* Zwei Konten im gleichen Mandanten, um die Zusammenarbeit für Apps zu testen, die in freigegebenen Kontexten funktionieren (sofern zutreffend)

### <a name="tenant-configurations"></a>Mandantenkonfigurationen

Wenn Sie einen mandanten Teams für die Verwendung Ihrer App konfigurieren müssen, fügen Sie diese Anweisungen sowie Administrator- und Nicht-Admin-Konten zur Überprüfung ein.

### <a name="video-optional"></a>Video (optional)

Stellen Sie eine Aufzeichnung Ihrer App bereit, damit Microsoft seine Funktionalität vollständig verstehen kann.

## <a name="create-your-store-listing-details"></a>Erstellen von Details zum Storeeintrag

Die informationen, die Sie an [Partner Center](https://partner.microsoft.com)&#8212;einschließlich Ihres Namens, Beschreibungen, Symbole und Bilder&#8212;wird der Teams-Store und Microsoft AppSource-Eintrag für Ihre App.

Ein Storeeintrag kann der erste Eindruck ihrer App sein. Erhöhen Sie Installationen mit einem Eintrag, der die Vorteile, Funktionalität und Marke Ihrer App effektiv vermittelt.

### <a name="specify-a-short-name"></a>Angeben eines kurzen Namens

Der Name Ihrer App (insbesondere der kurz bezeichnete [*Name)*](~/resources/schema/manifest-schema.md#name)spielt eine entscheidende Rolle bei der Benutzerentkung im Store.

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Beispiel screenshot highlights where an app's short name displays in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihr kurzer Name den Richtlinien für [die Speicherüberprüfung entspricht.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)

### <a name="write-descriptions"></a>Schreibbeschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben.

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Zusammenfassung Ihrer App, die ursprünglich, mitreißend und an Ihre Zielgruppe gerichtet sein sollte. Behalten Sie die kurz beschriebene Beschreibung auf einen Satz bei.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Beispiel screenshot highlights where an app's short description displays in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre kurze Beschreibung den Richtlinien für die [Speicherüberprüfung entspricht.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine Erzählung enthalten, die die Wichtigsten Features Ihrer App, die probleme, die sie löst, und ihre Zielgruppe hervorhebt. Während diese Beschreibung bis zu 4.000 Zeichen umfassen kann, lesen die meisten Benutzer nur zwischen 300 und 500 Wörter.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Beispiel screenshot highlights where an app's long description displays in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass ihre lange Beschreibung den Richtlinien für die [Speicherüberprüfung entspricht.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)

### <a name="adhere-to-icon-design-guidelines"></a>Einhalten von Richtlinien für das Symboldesign

Symbole sind eines der Wichtigsten Elemente, die Benutzern beim Durchsuchen des Informationsspeichers angezeigt werden. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig Teams erfüllen.

Weitere Informationen finden Sie unter [Anleitungen zum Erstellen Teams App-Symbole](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="capture-screenshots"></a>Screenshots erfassen

Screenshots bieten eine prominente visuelle Vorschau Ihrer App, um Ihren App-Namen, Ihr Symbol und Ihre Beschreibungen zu ergänzen.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Beispiel screenshot highlights where app screenshots display in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Beachten Sie Folgendes zu Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag haben.
* Unterstützte Dateitypen sind PNG, JPEG und GIF.
* Die Abmessungen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1.024 KB.

Bewährte Methoden finden Sie in den folgenden Ressourcen:

* [Teams richtlinien für die Speicherüberprüfung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [Erstellen effektiver Bilder für Microsoft-App-Stores](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Erstellen eines Videos

Ein Video in Ihrem Eintrag kann die effektivste Möglichkeit sein, um zu kommunizieren, warum Personen Ihre App verwenden sollten. Sie sollten die folgenden Fragen in einem Video beantworten:

* Wer ist Ihre App für?
* Welche Probleme kann Ihre App lösen?
* Wie funktioniert Ihre App?
* Welche weiteren Vorteile bietet ihnen die Verwendung Ihrer App?

#### <a name="best-practices-for-videos"></a>Bewährte Methoden für Videos

* Halten Sie Ihr Video zwischen 30 und 90 Sekunden.
* Zielen Sie auf Qualität ab. In einem Eintrag sehen Benutzer Ihr Video vor Screenshots.

### <a name="select-a-category-for-your-app"></a>Auswählen einer Kategorie für Ihre App

Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren. In der folgenden Tabelle werden Teams Den kategorien zugeordnet, die im [Partner Center aufgeführt sind.](https://aka.ms/PartnerCenterHomePage)

| Teams Kategorien       | Partner Center-Kategorien  |
|:---------------------|:---------------|
| Analytics und BI | Analyse, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Bildung | Bildung |
| Personalwesen | Personalwesen und Personalwerbung |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Dienstprogramme |
| Projektmanagement | Kommunikation, Project, Workflow und Unternehmensverwaltung |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzverwaltung, Vertrieb und Marketing |
| Soziales und Spaß | Bilder- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

### <a name="localize-your-store-listing"></a>Lokalisieren Des Store-Eintrags

Partner Center unterstützt [lokalisierte Store-Einträge](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions). Weitere Informationen finden Sie unter [Localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).

## <a name="complete-publisher-verification"></a>Abschließen Publisher Überprüfung

[Publisher überprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams im Store aufgeführten Apps erforderlich. Weitere Informationen finden Sie unter [häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), wie Sie Ihre [App](/azure/active-directory/develop/mark-app-as-publisher-verified)als herausgeberverifiziert markieren und die Herausgeberüberprüfung [beheben.](/azure/active-directory/develop/troubleshoot-publisher-verification)

## <a name="complete-publisher-attestation"></a>Complete Publisher Attestation

[Publisher Bescheinigung](/microsoft-365-app-certification/docs/attestation) ist auch für Teams im Store aufgeführten Apps erforderlich. Der Prozess umfasst das Abschließen einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliancepraktiken Ihrer App, die potenziellen Kunden dabei helfen können, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine neue App übermitteln, können Sie die Publisher-Bestätigung erst dann offiziell abschließen, wenn Ihre App im Teams ist. Wenn Sie eine aufgelistete App aktualisieren, füllen Sie Publisher Aus, bevor Sie die neueste Version der App zur Überprüfung übermitteln.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Übermitteln Ihrer App](https://docs.microsoft.com/office/dev/store/add-in-submission-guide)
