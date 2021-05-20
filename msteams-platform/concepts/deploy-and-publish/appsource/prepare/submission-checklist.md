---
title: Vorbereiten der Übermittlung an den Store
description: Beschreibt die letzten Schritte vor dem Senden Ihrer Microsoft Teams-App, die im Store aufgeführt werden soll.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 975d3ef8fc8bdc8d6d7c336cf3a61a3a42ef5315
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566033"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a>Vorbereiten Der Microsoft Teams-Shop-Übermittlung

Sie haben Ihre Microsoft Teams-App entworfen, erstellt und getestet. Jetzt können Sie es auflisten, damit die Leute Ihre App entdecken und verwenden können.

Bevor Sie Ihre App an [das Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource)übermitteln, stellen Sie sicher, dass Sie Folgendes getan haben.

## <a name="validate-your-app-package"></a>Überprüfen Ihres App-Pakets

Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um Probleme während des Übermittlungsprozesses zu vermeiden.

Das Microsoft Teams App-Validierungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie an das Partner Center senden. Das Tool überprüft automatisch die Konfigurationen Ihrer App mit den gleichen Testfällen, die während der Speicherüberprüfung verwendet werden.

1. Wechseln Sie zum [Microsoft Teams-App-Validierungstool](https://dev.teams.microsoft.com/appvalidation.html). (Hinweis: Das Tool ist auch in [App Studio](../../../build-and-test/app-studio-overview.md)verfügbar.)
1. Hochladen Ihr App-Paket, um die automatisierten Tests auszuführen.
1. Wechseln Sie zur **vorläufigen Checkliste,** und überprüfen Sie die schwer zu automatisierenden Testfälle.
1. [Beheben Sie Probleme mit Ihren Konfigurationen](~/resources/schema/manifest-schema.md) oder Ihrer App im Allgemeinen, wenn die automatisierten Tests Ihnen Fehler beschwichtigen oder Sie nicht alle Kriterien in der Checkliste erfüllt haben.

## <a name="compile-testing-instructions"></a>Erstellen von Testanweisungen

Geben Sie Anweisungen und Ressourcen an, mit denen die Prüfer Ihre App testen können, einschließlich Testkonten, Anmeldeinformationen und Lizenzschlüssel. Sie können Anweisungen im Partner Center hinzufügen oder an einen öffentlich zugänglichen Speicherort auf SharePoint hochladen.

### <a name="feature-list"></a>Feature-Liste

Geben Sie Details zu den Funktionen Ihrer App in Teams und Schritte zum Testen der einzelnen Apps an.

### <a name="accounts"></a>Konten

Sie müssen Testkonten bereitstellen, wenn Ihre App eine Lizenz oder ein Backend-Safelisting erfordert. Alle von Ihnen zur Verfügung stellenkonten müssen vorab ausgefüllte Daten enthalten, um das Testen zu erleichtern.

Abhängig von den Funktionen Ihrer App müssen Sie möglicherweise alle folgenden Optionen bereitstellen:

* Admin-Konto (erforderlich)
* Nicht-Admin-Konto (erforderlich)
* Ein Konto, das nicht vorkonfiguriert ist, um die Anmeldeerfahrung für die erste Ausführung ordnungsgemäß zu testen (erforderlich)
* Ein Konto mit Zugriff auf Premium- oder Upgrade-Funktionen (falls zutreffend)
* Zwei Konten im selben Mandanten, um die Zusammenarbeit für Apps zu testen, die in freigegebenen Kontexten funktionieren (falls zutreffend)

### <a name="tenant-configurations"></a>Mandantenkonfigurationen

Wenn Sie einen Teams Mandanten für die Verwendung Ihrer App konfigurieren müssen, fügen Sie diese Anweisungen sowie Administrator- und Nicht-Admin-Konten zur Validierung hinzu.

### <a name="video-optional"></a>Video (optional)

Stellen Sie eine Aufzeichnung Ihrer App bereit, damit Microsoft die Funktionalität vollständig verstehen kann.

## <a name="create-your-store-listing-details"></a>Erstellen Sie Ihre Shop-Eintragsdetails

Die Informationen, die Sie an [das Partner Center](https://partner.microsoft.com) übermitteln,&#8212;einschließlich Ihres Namens, Ihrer Beschreibungen, Symbole und Bilder&#8212;wird zum Teams-Store und Microsoft AppSource-Eintrag für Ihre App.

Ein Store-Eintrag kann der erste Eindruck Ihrer App sein. Erhöhen Sie die Installationen mit einem Eintrag, der die Vorteile, Funktionen und Marken Ihrer App effektiv vermittelt.

### <a name="specify-a-short-name"></a>Angeben eines kurzen Namens

Der Name Ihrer App (insbesondere der [*kurzbeinige Name)*](~/resources/schema/manifest-schema.md#name)spielt eine entscheidende Rolle, wie Benutzer sie im Store entdecken.

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Beispiel-Screenshot zeigt, wo der Kurzname einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihr Kurzname den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)entspricht.

### <a name="write-descriptions"></a>Schreiben von Beschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben.

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Zusammenfassung Ihrer App, die originell, ansprechend und an Ihre Zielgruppe gerichtet sein sollte. Halten Sie die Kurzbeschreibung auf einen Satz.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Beispiel-Screenshot zeigt, wo die Kurzbeschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre Kurzbeschreibung den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)entspricht.

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine Erzählung bereitstellen, die die Hauptfunktionen Ihrer App, die probleme, die sie löst, und ihre Zielgruppe hervorhebt. Während diese Beschreibung bis zu 4.000 Zeichen lang sein kann, lesen die meisten Benutzer nur zwischen 300-500 Wörtern.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Beispiel-Screenshot zeigt, wo die lange Beschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Stellen Sie sicher, dass Ihre lange Beschreibung den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)entspricht.

### <a name="adhere-to-icon-design-guidelines"></a>Einhaltung der Richtlinien für das Icon-Design

Symbole sind eines der Wichtigsten Elemente, die Benutzer beim Durchsuchen des Shops sehen. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig Teams Anforderungen einhalten.

Weitere Informationen finden Sie unter [Anleitung zum Erstellen Teams App-Symbole](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="capture-screenshots"></a>Screenshots erfassen

Screenshots bieten eine prominente visuelle Vorschau Ihrer App, um Ihren App-Namen, Ihr Symbol und Ihre Beschreibungen zu ergänzen.

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Beispiel-Screenshots, bei denen App-Screenshots in einem Store-Eintrag angezeigt werden.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

Erinnern Sie sich an die folgenden Screenshots:

* Sie können bis zu fünf Screenshots pro Liste haben.
* Zu den unterstützten Dateitypen gehören PNG, JPEG und GIF.
* Die Abmessungen sollten 1366x768 Pixel betragen.
* Maximale Größe von 1.024 KB.

Bewährte Methoden finden Sie in den folgenden Ressourcen:

* [Teams-Shop-Validierungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [Erstellen effektiver Bilder für Microsoft App Stores](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a>Erstellen eines Videos

Ein Video in Ihrem Eintrag kann die effektivste Möglichkeit sein, zu kommunizieren, warum Benutzer Ihre App verwenden sollten. Die folgenden Fragen sollten Sie in einem Video beantworten:

* Wer ist Ihre App?
* Welche Probleme kann Ihre App lösen?
* Wie funktioniert Ihre App?
* Welche weiteren Vorteile haben Sie bei der Nutzung Ihrer App?

#### <a name="best-practices-for-videos"></a>Bewährte Methoden für Videos

* Halten Sie Ihr Video zwischen 30-90 Sekunden.
* Ziel für Qualität. In einem Eintrag sehen Benutzer Ihr Video vor Screenshots.

### <a name="select-a-category-for-your-app"></a>Auswählen einer Kategorie für Ihre App

Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren. In der folgenden Tabelle werden Teams Shopkategorien den im [Partner Center](https://aka.ms/PartnerCenterHomePage)aufgeführten Kategorien zugeordnet.

| Teams Kategorien       | Partner Center-Kategorien  |
|:---------------------|:---------------|
| Analytics und BI | Analytics, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Schulung und Weiterbildung | Schulung und Weiterbildung |
| Personalwesen | Personal wesenund Personal und Recruiting |
| Produktivität | Content Management, Dateien und Dokumente, Produktivität, Schulung und Tutorials und Dienstprogramme |
| Projektmanagement | Kommunikation, Project Management, Workflow und Business Management |
| Vertrieb und Support | Kunden- und Kontaktmanagement, Kundensupport, Finanzmanagement, Vertrieb und Marketing |
| Sozial und Spaß | Bild- und Videogalerien, Lebensstil, Nachrichten und Wetter, Soziales, Reisen und Navigation |

### <a name="localize-your-store-listing"></a>Lokalisieren Sie Ihren Shop-Eintrag

Partner Center unterstützt [lokalisierte Shop-Einträge](/office/dev/store/prepare-localized-solutions). Weitere Informationen finden Sie unter [Lokalisierung Ihrer Teams App-Liste](../../../../concepts/build-and-test/apps-localization.md).

## <a name="complete-publisher-verification"></a>Vollständige Publisher-Überprüfung

[Publisher Überprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams im Store aufgeführten Apps erforderlich. Weitere Informationen finden Sie unter [Häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [wie Sie Ihre App als verifizierten Herausgeber markieren](/azure/active-directory/develop/mark-app-as-publisher-verified)und die [Herausgeberüberprüfung beheben](/azure/active-directory/develop/troubleshoot-publisher-verification).

## <a name="complete-publisher-attestation"></a>Vollständige Publisher-Bescheinigung

[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) ist auch für Teams apps erforderlich, die im Store aufgelistet sind. Der Prozess umfasst die Durchführung einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliance-Praktiken Ihrer App, die potenziellen Kunden helfen kann, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine neue App einreichen, können Sie Publisher Attestation erst dann offiziell abschließen, wenn Ihre App im Teams Store aufgeführt ist. Wenn Sie eine aufgelistete App aktualisieren, schließen Sie Publisher Bescheinigung ab, bevor Sie die neueste Version der App zur Validierung einreichen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Übermitteln Ihrer App](/office/dev/store/add-in-submission-guide)
