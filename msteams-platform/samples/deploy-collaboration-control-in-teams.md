---
title: Bereitstellen einer App mit Steuerelementen für die Zusammenarbeit in Microsoft Teams
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Ihre App mit der Zusammenarbeitssteuerung in Microsoft Teams bereitstellen und anderen Personen die Verwendung Ihrer App ermöglichen.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 816dd8052cdfb13ab83bfc34ae2a99a16f9f9569
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373038"
---
# <a name="deploy-collaboration-controls-to-microsoft-teams"></a>Bereitstellen von Steuerelementen für die Zusammenarbeit in Microsoft Teams

Steuerelemente für die Zusammenarbeit funktionieren derzeit am besten in Microsoft Teams. Sie können eine neue App erstellen, die sowohl als persönliche App als auch als Registerkarten-App in die Teams-App eingebettet werden kann.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

## <a name="configure-the-app-for-teams"></a>Konfigurieren der App für Teams

Die App, die Sie beim [Erstellen einer modellgesteuerten Anwendung](~/samples/app-with-collaboration-controls.md#create-a-model-driven-application) erstellt haben, verfügt nur über einen einzigen linken Bereich, und es gibt keine komplexen Befehle. Bevor Sie Ihre App zu Teams hinzufügen, können Sie also den linken Bereich ausblenden und eine verständlichere Kopfzeilenansicht erstellen.

> [!NOTE]
> Aktivieren Sie die folgenden Schritte nicht, wenn Sie den linken Bereich und die Kopfzeile mit hoher Dichte für Ihre Benutzer anzeigen möchten.

Dazu verwenden wir **neue Power Apps-App-Einstellungen** .

1. Wechseln Sie im linken Bereich zu **"Lösungen** ".

1. Wechseln Sie zum Ende der Lösungsliste, und wählen Sie **"Standardlösung**" aus.

1. Suchen Sie nach **der Einstellungsdefinition**, und wählen Sie sie aus.

     :::image type="content" source="../assets/images/collaboration-control/settings-defnition.png" alt-text="Screenshot der Such- und Einstellungsdefinition in Power-Apps.":::

1. Suchen Sie **die Navigationsleiste aus der** Liste der Einstellungsdefinitionen, und wählen Sie sie aus. Dadurch wird der linke Bereich in Ihrer Anwendung ausgeblendet.

     :::image type="content" source="../assets/images/collaboration-control/hide-the-nav-bar.png" alt-text="Der Screenshot zeigt, wie Sie die Navigationsleiste ausblenden auswählen.":::

1. Unten rechts in der Anwendung im Bearbeitungsbereich befindet sich ein Abschnitt mit dem Titel **"App-Werte festlegen"**. Wenn Sie Ihre App mit dem modernen App-Designer erstellt haben, wird Ihre App in der Liste angezeigt. Wählen Sie unter Ihrer App den **Wert "Neue App** " aus.

1. Ändern Sie den Wert von **"Nein"** in **"Ja".**

     :::image type="content" source="../assets/images/collaboration-control/value-to-yes.png" alt-text="Screenshot zeigt die Dropdownliste an, um den Änderungswert in &quot;Ja&quot; auszuwählen.":::

1. Wählen Sie **"Speichern" aus.**

1. Suchen Sie in der Liste der Einstellungsdefinitionen die **App-Kopfzeile mit hoher Dichte** , und wählen Sie sie aus, und wiederholen Sie den Vorgang.

     :::image type="content" source="../assets/images/collaboration-control/density-page-header.png" alt-text="Screenshot zeigt, wie Sie den Seitenkopf der App mit hoher Dichte auswählen.":::

1. Wählen Sie **"Zurück zu Lösungen**" aus.

     :::image type="content" source="../assets/images/collaboration-control/default-solution.png" alt-text="Der Screenshot zeigt die Standardlösung.":::

1. Wählen Sie **"Alle Anpassungen veröffentlichen** " aus, um alle abgeschlossenen Arbeiten zu veröffentlichen.

     :::image type="content" source="../assets/images/collaboration-control/publish-cusomization.png" alt-text="Veröffentlichen Sie alle Anpassungen.":::

## <a name="add-the-app-to-microsoft-teams-app-catalog"></a>Hinzufügen der App zum Microsoft Teams-App-Katalog

Wenn die Einstellungen definiert sind, können Sie die App jetzt zu Microsoft Teams hinzufügen. Navigieren Sie zunächst im Power Apps Maker-Portal zur Seite " **Apps** ", suchen Sie die von Ihnen erstellte App, und wählen Sie "Ellipse" **aus**.

Um die App zu Teams hinzuzufügen, wählen Sie **"Zu Teams hinzufügen" aus**.

:::image type="content" source="../assets/images/collaboration-control/add-to-teams.png" alt-text="Zu Teams hinzufügen.":::

Wenn Sie **"Zu Teams hinzufügen" auswählen,** wird ein Dialogfeld geöffnet, in dem Sie die Details überprüfen und " **App herunterladen"** auswählen können, in dem das Microsoft Teams-App-Manifest auf Ihrem Gerät gespeichert wird.

:::image type="content" source="../assets/images/collaboration-control/colab-manager-inspection.png" alt-text="Der Screenshot ist ein Beispiel für die Überprüfung des Zusammenarbeits-Managers.":::

Informationen zum Hochladen Ihrer App in Teams finden Sie [unter "Hochladen Ihrer App in Team"](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="enable-others-to-use-your-application"></a>Anderen personen die Verwendung Ihrer Anwendung ermöglichen

Es sind Folgendes erforderlich, damit Benutzer die bereitgestellten Collaboration Manager Anwendungen ausführen können, die mithilfe der Steuerelemente für die Zusammenarbeit erstellt wurden:

* Erstellen eines Teams für die Zusammenarbeit
* Hinzufügen von Mitgliedern zum Team
* Erstellen einer Sicherheitsrolle
* Zuweisen von Sicherheitsrollen zu Teammitgliedern

### <a name="create-a-collaboration-team"></a>Erstellen eines Teams für die Zusammenarbeit

1. Melden Sie sich beim [Power Platform Admin Center an](https://admin.powerplatform.microsoft.com/environments).

     1. Wählen Sie die Umgebung aus, in der die App bereitgestellt wird.
     1. Wählen Sie **"Benutzereinstellungen"** >  + **aus**.
     1. Wählen Sie **"Teams" aus**.

1. Wählen Sie oben auf der Seite die Schaltfläche **+Team erstellen** aus.

1. Fügen Sie alle erforderlichen Felder hinzu:
     1. **Teamname:** Stellen Sie sicher, dass der Name innerhalb der Geschäftseinheit eindeutig ist.
     1. **Beschreibung:** Geben Sie eine Beschreibung des Teams ein.
     1. **Geschäftsbereich:** Wählen Sie eine Geschäftseinheit aus der Dropdownliste aus.
     1. **Administrator:** Suchen Sie nach dem Benutzer in Ihrer Organisation, den Sie als Administrator zuweisen möchten, indem Sie Zeichen eingeben.
     1. **Teamtyp:** Wählen Sie den Teamtyp aus. Bei den folgenden Schritten wird davon ausgegangen, dass Sie "Besitzer" aus der Dropdownliste ausgewählt haben. Die anderen Teamtypen (Microsoft 365-Team und Microsoft Azure Active Directory-Team) füllen Teammitglieder automatisch aus Azure Active Directory aus.

         :::image type="content" source="../assets/images/collaboration-control/new-team.png" alt-text="Screenshot zum Auswählen eines neuen Teamtyps.":::

     1. Stellen Sie sicher, dass Sie den Teamnamen notieren. Sie benötigen dies später, um dieses Team als Besitzer eines Datensatzes zuzuweisen.

     1. Wählen Sie **"Weiter" aus.**

### <a name="add-members-to-the-team"></a>Hinzufügen von Mitgliedern zum Team

> [!NOTE]
> Das Hinzufügen von Mitgliedern zum Team ist nicht erforderlich, wenn Ihr Teamtyp Azure Active Directory oder Microsoft 365 ist.

1. Wählen Sie ein Team und dann **"Teammitglieder verwalten**" aus.

1. Um neue Teammitglieder hinzuzufügen, wählen Sie **+Teammitglieder hinzufügen** und benutzer aus Ihrer Organisation aus, die hinzugefügt werden sollen.

     :::image type="content" source="../assets/images/collaboration-control/add-team-members.png" alt-text="Der Screenshot beschreibt, wie Teammitglieder hinzugefügt werden.":::

1. Um ein Teammitglied zu löschen, wählen Sie den Benutzer und dann " **Entfernen"** aus.

### <a name="create-a-security-role"></a>Erstellen einer Sicherheitsrolle

1. Wählen Sie **"Benutzereinstellungen"** >  +  in der Umgebung aus, in der die App bereitgestellt wird.

1. Wählen Sie **"Sicherheitsrollen" aus**.

     :::image type="content" source="../assets/images/collaboration-control/users-permission.png" alt-text="Screenshot zum Hinzufügen neuer Teammitglieder für Benutzerberechtigungen.":::

1. Wählen Sie oben links auf der Seite die **Option "Neue Rolle** " aus, wodurch nun eine neue Seite geöffnet wird.

1. Geben Sie auf der **Registerkarte "Details"** einen Namen für Ihre Sicherheitsrolle an.

1. Wechseln Sie zur Registerkarte **"Benutzerdefinierte Entitäten** ".

     1. Erteilen Sie Organisationsberechtigungen (vollständiger grüner Kreis) für jede der Entitäten für die Zusammenarbeit, **die Zuordnung zur Zusammenarbeit**, **die Metadaten** für die Zusammenarbeit und **das Stammverzeichnis für die Zusammenarbeit**.

         :::image type="content" source="../assets/images/collaboration-control/collab-map.png" alt-text="Screenshot zeigt, wie Sie eine Sicherheitsrolle auf der Karte für die Zusammenarbeit erstellen.":::

1. Wählen Sie **"Speichern"** und **"Schließen" aus**.

### <a name="assign-security-roles"></a>Zuweisen von Sicherheitsrollen

1. Wählen Sie **"Benutzereinstellungen"** >  +  in der Umgebung aus, in der die App bereitgestellt wird.

1. Wählen Sie **"Teams**" und dann das Team aus, das Sie in [einem Team für die Zusammenarbeit](#create-a-collaboration-team) erstellt haben.

1. Wählen Sie in der Kopfzeile " **Sicherheitsrollen verwalten** " aus.

     :::image type="content" source="../assets/images/collaboration-control/edit-team.png" alt-text="Der Screenshot zeigt die Zuordnung zur Zusammenarbeit, Die Metadaten für die Zusammenarbeit und den Stamm der Zusammenarbeit an. für &quot;Team bearbeiten&quot;.":::

1. Wählen Sie die Rollen aus, die [in einer Sicherheitsrolle erstellt wurden](#create-a-security-role).

1. Wählen Sie **Speichern** aus.

Weitere Informationen zu Rollenberechtigungen finden Sie unter [Konfigurieren der Benutzersicherheit in einer Umgebung](/power-platform/admin/database-security).
