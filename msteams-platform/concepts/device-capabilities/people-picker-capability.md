---
title: Integration der Personenauswahl
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK zum Integrieren des Personenauswahl-Steuerelements
keywords: Personenauswahl-Steuerelement
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: 7a7a229bdeab7d83f71f8dbe3b24da8b44b3db32
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518142"
---
# <a name="integrate-people-picker"></a>Integration der Personenauswahl  

Die Personenauswahl ist ein Steuerelement zum Suchen und Auswählen von Personen. Dies ist eine systemeigene Funktion, die in Teams Plattform verfügbar ist. Sie können Teams systemeigene Personenauswahl-Eingabesteuerung in Ihre Web-Apps integrieren. Sie können zwischen einzelner oder mehrfacher Auswahl und Konfigurationen auswählen, z. B. das Einschränken der Suche in einem Chat, in Kanälen oder in der gesamten Organisation.

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das eine API zum Integrieren der Personenauswahl in Ihre Web-App bereitstellt`selectPeople`. 

## <a name="advantages-of-integrating-the-native-people-picker"></a>Vorteile der Integration der systemeigenen Personenauswahl 

* Das Steuerelement "Personenauswahl" funktioniert auf allen Teams Oberflächen, z. B. in einem Aufgabenmodul, einem Chat, einem Kanal, einer Besprechungsregisterkarte und einer persönlichen App.
* Mit diesem Steuerelement können Sie innerhalb eines Chats, Kanals oder der gesamten Organisation nach Benutzern suchen und diese auswählen.
* Die Personenauswahl hilft bei Szenarien mit Aufgabenzuweisung, Tagging und Benachrichtigung eines Benutzers. 
* Sie können dieses leicht verfügbare Steuerelement in Ihrer Web-App verwenden. Es spart den Aufwand und die Zeit, um ein solches Steuerelement selbst zu erstellen.

Sie müssen die API aufrufen, um das `selectPeople` Personenauswahl-Steuerelement in Ihre Teams-App zu integrieren. Um eine effektive Integration zu ermöglichen, müssen Sie über Kenntnisse des [Codeausschnitts](#code-snippet) für den Aufruf der API verfügen. Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Web-App zu behandeln.

> [!NOTE] 
> Derzeit ist Microsoft Teams Unterstützung für die Personenauswahl nur für mobile Clients verfügbar.

## <a name="selectpeople-api"></a>`selectPeople` API 

`selectPeople`Mit der API können Sie Ihren Web-Apps Teams nativen `People Picker input control` Hinzufügen hinzufügen.  
Die API-Beschreibung lautet wie folgt:

| API      | Beschreibung  |
| --- | --- |
|**selectPeople**|Startet eine Personenauswahl und ermöglicht es dem Benutzer, eine oder mehrere Personen in der Liste zu suchen und auszuwählen.<br/><br/>Diese API gibt die ID, den Namen und die E-Mail-Adresse ausgewählter Benutzer an die aufrufende Web-App zurück.<br/><br/>Bei einer persönlichen App durchsucht das Steuerelement die gesamte Organisation. Wenn die App einem Chat oder Kanal hinzugefügt wird, wird der Suchkontext je nach Szenario konfiguriert. Die Suche ist innerhalb der Mitglieder dieses Chats, Kanals oder in der gesamten Organisation eingeschränkt.|

Die `selectPeople` API enthält die folgenden Eingabekonfigurationen:

|Konfigurationsparameter|Typ|Beschreibung| Standardwert|
|-----|------|--------------|------|
|`title`| String| Es handelt sich um einen optionalen Parameter. Er legt den Titel für das Steuerelement "Personenauswahl" fest. | Auswählen von Personen|
|`setSelected`|Zeichenfolge| Es handelt sich um einen optionalen Parameter. Sie müssen Microsoft Azure Active Directory (Azure AD)-IDs der Personen übergeben, die vorab ausgewählt werden sollen. Dieser Parameter wählt Personen beim Starten des Personenauswahl-Steuerelements vorab aus. Bei einer einzelnen Auswahl wird nur der erste gültige Benutzer vorbefüllt, wobei der Rest ignoriert wird. |Null| 
|`openOrgWideSearchInChatOrChannel`|Boolesch | Es handelt sich um einen optionalen Parameter. Wenn sie auf "true" festgelegt ist, wird die Personenauswahl im organisationsweiten Bereich gestartet, auch wenn die App zu einem Chat oder Kanal hinzugefügt wird. |Falsch|
|`singleSelect`|Boolescher Wert|Es handelt sich um einen optionalen Parameter. Wenn sie auf "true" festgelegt ist, wird die Personenauswahl gestartet, wodurch die Auswahl auf nur einen Benutzer beschränkt wird. |Falsch|

Die folgende Abbildung zeigt die Erfahrung der Personenauswahl in einer Beispiel-Web-App:

![Web-App-Erfahrung der Personenauswahl](../../assets/images/tabs/people-picker-control-capability.png)

### <a name="code-snippet"></a>Codeausschnitt

**Aufrufen `selectPeople` API** zum Auswählen von Personen aus einer Liste:

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

## <a name="see-also"></a>Weitere Artikel

* [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
* [Integrieren von QR-Code oder Strichcodescanner-Funktion in Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](location-capability.md)
