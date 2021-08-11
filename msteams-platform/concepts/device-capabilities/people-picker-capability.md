---
title: Integration der Personenauswahlfunktion
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK zum Integrieren der Personenauswahlfunktion
keywords: Personenauswahl-Steuerelement
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 1d8840853c6fce808b1ec5f13ad95c099698de3ebb37f3613a14c64b4a11d3f8
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57702784"
---
# <a name="integrate-people-picker-capability"></a>Integration der Personenauswahlfunktion 

Die Personenauswahl ist ein Steuerelement zum Suchen und Auswählen von Personen. Dies ist eine systemeigene Funktion, die in Teams Plattform verfügbar ist. Sie können Teams systemeigene Personenauswahl-Eingabesteuerung in Ihre Web-Apps integrieren. Sie können zwischen einzelner oder mehrfacher Auswahl und Konfigurationen auswählen, z. B. das Einschränken der Suche in einem Chat, in Kanälen oder in der gesamten Organisation.

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das `selectPeople` eine API zum Integrieren der Personenauswahlfunktion in Ihre Web-App bereitstellt. 

## <a name="advantages-of-integrating-people-picker-capability"></a>Vorteile der Integration der Personenauswahlfunktion

* Das Steuerelement "Personenauswahl" funktioniert auf allen Teams Oberflächen, z. B. in einem Aufgabenmodul, einem Chat, einem Kanal, einer Besprechungsregisterkarte und einer persönlichen App.
* Mit diesem Steuerelement können Sie innerhalb eines Chats, Kanals oder der gesamten Organisation nach Benutzern suchen und diese auswählen.
*  Die Funktion "Personenauswahl" hilft bei Szenarien mit Aufgabenzuweisung, Tagging und Benachrichtigung eines Benutzers. 
* Sie können dieses leicht verfügbare Steuerelement in Ihrer Web-App verwenden. Es spart den Aufwand und die Zeit, um ein solches Steuerelement selbst zu erstellen.

Sie müssen die `selectPeople` API aufrufen, um das Personenauswahl-Steuerelement in Ihre Teams-App zu integrieren. Um eine effektive Integration zu ermöglichen, müssen Sie über Kenntnisse des [Codeausschnitts](#code-snippet) für den Aufruf der API verfügen. Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Web-App zu behandeln.

> [!NOTE] 
> Derzeit ist Microsoft Teams Unterstützung für die Personenauswahlfunktion nur für mobile Clients verfügbar.

## <a name="selectpeople-api"></a>`selectPeople` Api 

`selectPeople`Mit der API können Sie Ihren Web-Apps Teams nativen Hinzufügen `People Picker input control` hinzufügen.  
Die API-Beschreibung lautet wie folgt:

| API      | Beschreibung  |
| --- | --- |
|**selectPeople**|Startet eine Personenauswahl und ermöglicht es dem Benutzer, eine oder mehrere Personen in der Liste zu suchen und auszuwählen.<br/><br/>Diese API gibt die ID, den Namen und die E-Mail-Adresse ausgewählter Benutzer an die aufrufende Web-App zurück.<br/><br/>Bei einer persönlichen App durchsucht das Steuerelement die gesamte Organisation. Wenn die App einem Chat oder Kanal hinzugefügt wird, wird der Suchkontext je nach Szenario konfiguriert. Die Suche ist innerhalb der Mitglieder dieses Chats, Kanals oder in der gesamten Organisation eingeschränkt.|

Die `selectPeople` API enthält die folgenden Eingabekonfigurationen:

|Konfigurationsparameter|Typ|Beschreibung| Standardwert|
|-----|------|--------------|------|
|`title`| Zeichenfolge| Es handelt sich um einen optionalen Parameter. Er legt den Titel für das Steuerelement "Personenauswahl" fest. | Auswählen von Personen|
|`setSelected`|Zeichenfolge| Es handelt sich um einen optionalen Parameter. Sie müssen AAD-IDs der Personen übergeben, die vorab ausgewählt werden sollen. Dieser Parameter wählt Personen beim Starten des Personenauswahl-Steuerelements vorab aus. Bei einer einzelnen Auswahl wird nur der erste gültige Benutzer vorbefüllt, wobei der Rest ignoriert wird. |Null| 
|`openOrgWideSearchInChatOrChannel`|Boolesch | Es handelt sich um einen optionalen Parameter. Wenn sie auf "true" festgelegt ist, wird die Personenauswahl im organisationsweiten Bereich gestartet, auch wenn die App zu einem Chat oder Kanal hinzugefügt wird. |Falsch|
|`singleSelect`|Boolesch|Es handelt sich um einen optionalen Parameter. Wenn sie auf "true" festgelegt ist, wird die Personenauswahl gestartet, wodurch die Auswahl auf nur einen Benutzer beschränkt wird. |Falsch|

Die folgende Abbildung zeigt die Funktion "Personenauswahl" in einer Beispiel-Web-App:

![Web-App-Erfahrung der Personenauswahlfunktion](../../assets/images/tabs/people-picker-control-capability.png)

### <a name="code-snippet"></a>Codeausschnitt

**Anrufe `selectPeople` API** zum Auswählen von Personen aus einer Liste:

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

Sie müssen sicherstellen, dass die Fehler in Ihrer Web-App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden: 

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Beim Starten der Personenauswahl ist ein interner Fehler aufgetreten.|
| **4000** | INVALID_ARGUMENTS | Die API wird mit falschen oder nicht ausreichenden obligatorischen Argumenten aufgerufen.|
| **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000** | OLD_PLATFORM | Der Benutzer befindet sich auf einem alten Plattformbuild, in dem die Implementierung der API nicht vorhanden ist.  Das Upgrade des Builds behebt das Problem.|

## <a name="see-also"></a>Weitere Informationen

* [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
* [Integrieren von QR-Code oder Strichcodescanner-Funktion in Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](location-capability.md)
