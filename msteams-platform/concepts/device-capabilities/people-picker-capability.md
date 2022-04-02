---
title: Integration der Personenauswahl
description: Verwenden des Microsoft Teams JavaScript-Client-SDK zum Integrieren Personenauswahl Steuerelements
keywords: Steuerelement „Personenauswahl“
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: cd7039693b146abb53e938ba020077a48c343bda
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571459"
---
# <a name="integrate-people-picker"></a>Integration der Personenauswahl

Die Personenauswahl ist ein Eingabesteuerelement in Microsoft Teams, mit dem Benutzer Personen suchen und auswählen können. Sie können die Personenauswahl in eine Web-App integrieren, sodass Endbenutzer verschiedene Funktionen ausführen können, z. B. Personen in einem Chat, Kanal oder in der gesamten Organisation innerhalb Microsoft Teams suchen und auswählen. Das Personenauswahl-Steuerelement ist für alle Microsoft Teams-Clients verfügbar, z. B. Web, Desktop und Mobil.

Sie können das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die `selectPeople`-API zum Integrieren der Personenauswahl in Ihre Web-App bereitstellt.

## <a name="advantages-of-using-people-picker"></a>Vorteile der Verwendung der Personenauswahl

* Funktioniert für alle Microsoft Teams-Funktionen, z. B. Aufgabenmodul, Chat, Kanal, Besprechungsregisterkarte und persönliche Apps.
* Ermöglicht es dem Benutzer, Personen in einem Chat, Kanal oder der gesamten Organisation innerhalb Microsoft Teams zu suchen und auszuwählen.
* Hilft in Szenarien mit Aufgabenzuweisung, Tagging und Benachrichtigung von Benutzern.
* Spart im Vergleich zum Erstellen eines ähnlichen Steuerelements viel Zeit und Mühe.

Verwenden Sie die [`selectPeople`](#selectpeople-api) API, um die Personenauswahl in Ihre Microsoft Teams-App zu integrieren. Um die API zu integrieren und aufzurufen, müssen Sie über ein gutes Verständnis des zugehörigen [Codeausschnitts](#code-snippet) verfügen. Außerdem benötigen Sie Kenntnisse über [API-Antwortfehler](#error-handling).

## <a name="selectpeople-api"></a>`selectPeople`-API

Mit der `selectPeople`-API können Sie den Web-Apps die Personenauswahl von Microsoft Teams hinzufügen. Weitere Vorteile:

* Ermöglicht es dem Benutzer, eine oder mehrere Personen in einer Liste zu suchen und auszuwählen.
* Gibt die ID, den Namen und die E-Mail-Adresse ausgewählter Benutzer an die Web-App zurück.

Bei einer persönlichen App sucht das Steuerelement in der Organisation nach Namen oder E-Mail-ID innerhalb Microsoft Teams. Wenn die App einem Chat oder Kanal hinzugefügt wird, wird der Suchkontext basierend auf dem Szenario konfiguriert. Die Suche ist auf die Mitglieder dieses Chats oder Kanals beschränkt.

Die `selectPeople`-API umfasst die folgenden Eingabekonfigurationen:

|Konfigurationsparameter|Typ|Beschreibung| Standardwert|
|-----|------|--------------|------|
|`title`|Zeichenfolge| Ein optionaler Parameter; legt den Titel für das Steuerelement "Personenauswahl" fest.|`selectPeople`|
|`setSelected`|Zeichenfolge| Ein optionaler Parameter. Sie müssen Microsoft Azure Active Directory (Azure AD)-IDs der Personen übergeben, die vorab ausgewählt werden sollen. Dieser Parameter wählt Personen beim Starten der Personenauswahl vorab aus. Bei einer einzelnen Auswahl wird nur der erste gültige Benutzer vorab geladen, während der Rest ignoriert wird.|**Null**|
|`openOrgWideSearchInChatOrChannel`|Boolescher Wert| Optionaler Parameter. Wenn er auf "true" festgelegt ist, wird die Personenauswahl mit organisationsweitem Bereich gestartet, auch wenn die App einem Chat oder Kanal hinzugefügt wird.|**False**|
|`singleSelect`|Boolean|Optionaler Parameter. Wenn er auf "true" festgelegt ist, wird die Personenauswahl gestartet und die Auswahl auf nur einen Benutzer beschränkt.|**False**|

Die folgende Abbildung zeigt die Personenauswahl auf Mobilgeräten und Desktops:

# <a name="mobile"></a>[Mobil](#tab/Samplemobileapp)

Die Personenauswahl ermöglicht dem Benutzer das Suchen und Hinzufügen von Personen mithilfe der folgenden Schritte:

1. Geben Sie den Namen der erforderlichen Person ein. Eine Liste mit Namensvorschlägen wird angezeigt.
1. Wählen Sie den Namen der erforderlichen Person aus der Liste aus. 

   :::image type="content" source="../../assets/images/tabs/people-picker-control-capability-mobile-updated.png" alt-text="Auswahl auf Mobilgerät" border="true":::

# <a name="desktop"></a>[Desktop](#tab/Sampledesktop)

Die Personenauswahl für Web oder Desktop wird in einem modalen Fenster über Ihrer Web-App gestartet, und zum Hinzufügen von Personen führen Sie die folgenden Schritte aus:

1. Geben Sie den Namen der erforderlichen Person ein. Eine Liste mit Namensvorschlägen wird angezeigt.
1. Wählen Sie den Namen der erforderlichen Person aus der Liste aus. 

   :::image type="content" source="../../assets/images/tabs/select-people-picker-byname.png" alt-text="Personenauswahl nach Name auf Desktop" border="true":::

---

## <a name="code-snippet"></a>Codeausschnitt

Der folgende Codeausschnitt zeigt die Verwendung der `selectPeople`-API für eine Liste an:

```javascript
 microsoftTeams.people.selectPeople((error: microsoftTeams.SdkError, people: microsoftTeams.people.PeoplePickerResult[]) => 
 {
    if (error) 
    {
        if (error.message) 
           {
             alert(" ErrorCode: " + error.errorCode + error.message);
           }
            else 
            {
              alert(" ErrorCode: " + error.errorCode);
            }
      }
    if (people)
     {
            output(" People length: " + people.length + " " + JSON.stringify(people));
      }
  });
```

## <a name="error-handling"></a>Fehlerbehandlung

In der folgenden Tabelle sind die Fehlercodes und deren Beschreibungen aufgeführt:

|Fehlercode |  Fehlername     | Beschreibung|
| --------- | --------------- | --------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Starten der Personenauswahl.|
| **4000** | INVALID_ARGUMENTS | Die API wird mit falschen oder nicht ausreichenden obligatorischen Argumenten aufgerufen.|
| **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000** | OLD_PLATFORM | Der Benutzer befindet sich auf einem alten Plattformbuild, in dem die Implementierung der API nicht verfügbar ist. Führen Sie ein Upgrade auf die neueste Version des Builds durch, um das Problem zu beheben.|

## <a name="see-also"></a>Weitere Informationen

* [Integrieren von Medienfunktionen in Microsoft Teams](mobile-camera-image-permissions.md)
* [Integrieren von QR-Code- oder Strichcodescanner-Funktionen in Microsoft Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Microsoft Teams](location-capability.md)
