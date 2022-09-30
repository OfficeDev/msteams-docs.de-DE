---
title: Konfigurieren von Aufgaben für externe Clients in der Steuerelement-App für die Zusammenarbeit
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Aufgaben für externe Clients in der Steuerelement-App für die Zusammenarbeit in Microsoft Teams konfigurieren.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 7d458cc97429772695958606835edd4ef953b5db
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243164"
---
# <a name="configure-tasks-for-external-clients"></a>Konfigurieren von Aufgaben für externe Clients

Externe Aufgaben, die Benutzern zugewiesen werden können, die nicht Teil Ihrer Organisation sind oder keinen Zugriff auf Ihre Anwendung haben, z. B. das Zuweisen einer Aufgabe zu einem Kunden.

Um dies zu aktivieren, benötigen Sie einen zusätzlichen Schritt zum Übergeben einer XML-Zeichenfolge an jede Instanz des Tasks-PCF-Steuerelements, das der Unterrasterkomponente im gewünschten MDA-Formular zugeordnet ist. XML-Zeichenfolge ist eine parametrisierte Abfrage, mit der das Steuerelement die erforderlichen Daten aus einer Tabelle extrahieren kann, die Kundeninformationen enthält.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

Führen Sie die folgenden Schritte aus, um externe Aufgaben zu erstellen:

1. Erstellen Sie eine neue benutzerdefinierte Entität, z. B. "Kunde", oder verwenden Sie eine vorhandene Kundenentität wie "Kontakte".

1. Erstellen Sie neue Felder, die die folgenden Informationen enthalten:
    1. Name
    1. E-Mails
    1. Übergeordnetes Element (Nachschlagen in der übergeordneten Tabelle, z. B. Inspektionen)
    > [!NOTE]
    > Die oben erstellte Kundenentität ist, aus der das Aufgabensteuerelement die Kundeninformationen beim Zuweisen einer externen Aufgabe abruft. Das Feld "Übergeordnetes Element" stellt sicher, dass die Kundenentität mit einem Prüfdatensatz verknüpft ist.

1. Generieren Sie eine FETCH-XML-Datei, damit das PCF-Steuerelement die richtigen Kundeninformationen abrufen kann.

    **Konfigurieren des XML-Schemas**

    Nachfolgend sehen Sie die Schemadefinition für die Aufgabenkonfiguration Fetch XML. Jeder Fetch-XML-Code muss so konzipiert sein, dass er die folgenden Anforderungen erfüllt:

    * Das Abfrageergebnis muss die folgenden Eigenschaften für jedes Benutzerobjekt zurückgeben:
      * ID
      * Displayname
      * E-Mail verwenden, bei Bedarf Alias verwenden.
    * Die Abfrage muss den **parameter @top** enthalten, damit der Aufrufer die Anzahl der Ergebnisse einschränken kann.
    * Die Abfrage muss **@rootEntityId** Parameter haben, um ergebnisse bei Bedarf nur nach verwandten Datensätzen zu filtern.
    * Die Abfrage muss **über @useName** Parameter verfügen, um die Ergebnisfilterung nach Namen zuzulassen.
    * Die Abfrage muss **über @useIdentifier** Parameter verfügen, damit nur ausgewählte Benutzer abgerufen werden können.

    **Xml-Konfigurationsschema und Beispiel**

    Die Konfiguration des XML-Schemas ruft Daten aus der Kundentabelle ab. Sie können den `<fetch/>` Knoten anpassen, um Ihre eigene Abfrage anzugeben, um Benutzer aus jeder anderen benutzerdefinierten Tabelle anzuzeigen.

    > [!NOTE]
    > Die oben aufgeführten Entitäts- und Attributnamen- und -reihenfolgesattribute im XML-Code haben **PublisherPrefix_TableColumn** Format.

    ```xml
    
    <custom-tasks> 
    <custom-task id="external" name="External" for="guest"> 
    <fetch top="@top"> 
    <entity name="[Name of table, e.g. Crb2891_customer]"> 
    <attribute name="[Name of ID column, e.g. Crb2891_customerid]" alias="id" /> 
    <attribute name="[Name of primary name column, e.g. Crb2891_name]" alias="displayname" /> 
    <attribute name="[Name of email column, e.g. Crb2891_email]" alias="email" /> 
    <order attribute ="[Name of primary name column, e.g. Crb2891_name]" descending="false" /> 
    <filter type="and"> 
    <condition attribute="[Name of parent lookup column, e.g. Crb2891_parent]" operator="eq" value="@rootEntityId" /> 
    <condition attribute="[Name of primary name column, e.g. Crb2891_name]" operator="like" value="@userName" /> 
    <condition attribute="[Name of email column, e.g. Crb2891_email]" operator="like" value="@userIdentifier" /> 
    </filter> 
    </link-entity> 
    </entity> 
    </fetch> 
    </custom-task> 
    </custom-tasks> 
    
    ```

1. Binden Sie die Aufgabensteuerelemente an das Subgrid im klassischen Formular-Designer. Wählen Sie **"Speichern"** und dann **"Zu klassisch wechseln**" aus.

1. Navigieren Sie im klassischen Formular-Designer, bis Sie die Registerkarte " **Aufgaben** " gefunden haben. Doppelklicken Sie auf das Untergrid, um das Eigenschaftendialogfeld zu öffnen.

    :::image type="content" source="~/assets/images/collaboration-control/subgrid-property.png" alt-text="Screenshot des Dialogfelds &quot;Aufgabeneigenschaft&quot;.":::

1. Legen Sie im Eigenschaftendialogfeld die Eigenschaften wie in der folgenden Abbildung dargestellt fest:

    :::image type="content" source="~/assets/images/collaboration-control/tasks-property.png" alt-text="Sceenshot zeigt an, dass die Eigenschaften in den Einstellungen der Tasks-Eigenschaft festgelegt werden.":::

1. Wechseln Sie zur Registerkarte "Steuerelemente", und wählen Sie :::image type="icon" source="~/assets/images/collaboration-control/edit-icon.png" alt-text="&quot;Screenshot&quot; aus, um zu erfahren, wie Sie die Aufgaben bearbeiten."::: für die Eigenschaft "Benutzerdefinierte Aufgaben", um den oben generierten FETCH-XML-Code hinzuzufügen.

1. Einfügen des FETCH-XML-Codes

    :::image type="content" source="~/assets/images/collaboration-control/set-fetchproperties.png" alt-text="Der Screenshot zeigt, wie Fetch XML eingefügt wird.":::

    :::image type="content" source="~/assets/images/collaboration-control/custom-tasksproperty.png" alt-text="Der Screenshot zeigt, wie Benutzerdefinierte Eigenschafteneinstellungen konfiguriert werden.":::

1. Wählen Sie " **OK** " unter "Benutzerdefinierte Aufgaben konfigurieren" und "Eigenschaften festlegen" aus.

1. Speichern und veröffentlichen.
