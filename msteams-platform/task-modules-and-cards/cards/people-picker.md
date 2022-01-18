---
title: Personenauswahl in adaptiven Karten
description: Beschreibt die Verwendung des Personenauswahl-Steuerelements in adaptiven Karten
localization_priority: Normal
keywords: Personenauswahl für adaptive Karten
ms.topic: reference
author: Rajeshwari-v
ms.author: surbhigupta
ms.openlocfilehash: d0183ea8f00c14e93586c0c12e02b837a41572c9
ms.sourcegitcommit: 98cde8ff08552da4ce36fb0463982366bed979e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2022
ms.locfileid: "62062546"
---
# <a name="people-picker-in-adaptive-cards"></a>Personenauswahl in adaptiven Karten

>[!NOTE]
> Derzeit ist die Personenauswahl in adaptiven Karten in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) nur für mobilgeräte und allgemein verfügbar (GA) für Desktops verfügbar.

Die Personenauswahl hilft Benutzern, Benutzer auf einer adaptiven Karte zu suchen und auszuwählen. Sie können die Personenauswahl als Eingabesteuerelement zur adaptiven Karte hinzufügen, die in Chats, Kanälen, Aufgabenmodulen und Registerkarten funktioniert. Die Personenauswahl unterstützt die folgenden Features:        

* Durchsucht einzelne oder mehrere Benutzer.
* Wählt einzelne oder mehrere Benutzer aus. 
* Weist einzelnen oder mehreren Benutzern neu zu. 
* Füllt den Namen der ausgewählten Benutzer vorab auf.

## <a name="popular-scenarios"></a>Beliebte Szenarien 

Die folgende Tabelle enthält häufig verwendete Szenarien für die Personenauswahl in adaptiven Karten und die entsprechenden Aktionen:

|Szenarien|Aktionen|
|----------|-------------------------|
|Genehmigungsbasierte Szenarien| Um die Genehmigung basierend auf der Anforderung anzufordern, zuzuweisen und dem gewünschten Benutzer neu zuzuweisen.|
|Verwaltung von Sicherheitsvorfällen| Zum Nachverfolgen von Vorfällen und benachrichtigen, zuweisen und dem vorgesehenen Benutzer zur sofortigen Aktion erneut zuweisen.| 
|Projektmanagement| So weisen Sie bestimmten Benutzern Tickets oder Fehler zu.|
|Benutzersuche| So suchen Sie in der gesamten Organisation nach Benutzern.|

# <a name="desktop"></a>[Desktop](#tab/desktop)

Der Web- und Desktopclient unterstützt personenauswahl in adaptiver Karte. Bei der Suche im Web umfasst die Personenauswahl eine Inline-Eingabeoberfläche.

### <a name="reassignment-scenario-example"></a>Beispiel für ein Neuzuweisungsszenario

Benutzer A (Robert) erhält ein Ticket für eine Aufgabe in einem Kanal und erkennt einen falschen Zugewiesenen. Benutzer A weist die Aufgabe, die die Informationen zurück an den Bot sendet, neu zu. 

**So weisen Sie eine Aufgabe neu zu**

1. Wählen Sie **"Neu zuweisen"** aus, wo das Personenauswahlfeld mit dem Namen vorgefüllt wird, um die Aufgabe dem gewünschten Benutzer neu zuzuweisen.
1. Entfernen Sie den falschen Benutzernamen. 
1. Wählen Sie die gewünschten Benutzer gemäß Bildszenario, Benutzer B (Dropdown) und Benutzer C (Robin) für die Aufgabe aus. 
1. Wählen Sie **Zuweisen** aus. Nach der Zuweisung werden die Informationen an den Bot gesendet. 
   Der Bot aktualisiert die adaptive Karte und benachrichtigt die beabsichtigten Benutzer. 
 
Die folgende Abbildung zeigt das Neuzuweisungsszenario:    

![Personenauswahl auf desktop](../../assets/images/cards/desktoppp.gif)

# <a name="mobile"></a>[Mobil](#tab/mobile)

> [!NOTE]
> Derzeit ist dieses Feature nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) verfügbar.

Mobile Android- und iOS-Clients unterstützen personenauswahl in adaptiven Karten. Sie können die Personenauswahl in mobilen Umgebungen verwenden, um den Benutzer zu suchen und auszuwählen, um die Benutzererfahrung zu verbessern. Die Suchumgebung ähnelt jeder anderen Benutzerauswahlerfahrung auf mobilen Geräten.

### <a name="reassignment-scenario-example"></a>Beispiel für ein Neuzuweisungsszenario

Benutzer A (Robert) erhält ein Ticket für eine Aufgabe in einem Kanal und erkennt einen falschen Zugewiesenen. Benutzer A weist die Aufgabe, die die Informationen zurück an den Bot sendet, neu zu. 

**So weisen Sie eine Aufgabe neu zu**

1. Wählen Sie **"Neu zuweisen"** aus, wo das Personenauswahlfeld mit dem Namen vorgefüllt wird, um die Aufgabe dem gewünschten Benutzer neu zuzuweisen.
1. Entfernen Sie den falschen Benutzernamen.
1. Wählen Sie die gewünschten Benutzer gemäß Bildszenario, Benutzer B (Dropdown) und Benutzer C (Robin) für die Aufgabe aus.
1. Wählen Sie **Fertig** aus.
1. Wählen Sie **Zuweisen** aus. Nach der Zuweisung werden die Informationen an den Bot gesendet. 
   Der Bot aktualisiert die adaptive Karte und benachrichtigt die beabsichtigten Benutzer. 

Die folgende Abbildung zeigt das Neuzuweisungsszenario: 

![Personenauswahl auf Mobilgeräten](../../assets/images/cards/mobilepp.gif)

---

## <a name="implement-people-picker"></a>Implementieren der Personenauswahl

Die Personenauswahl wird als Erweiterung des [Input.ChoiceSet-Steuerelements](https://adaptivecards.io/explorer/Input.ChoiceSet.html) implementiert. Das Eingabesteuerelement enthält die folgenden Auswahlen:   

* Dropdown, z. B. eine erweiterte Auswahl.
* Optionsfeld, z. B. eine einzelne Auswahl.
* Kontrollkästchen, z. B. Mehrfachauswahl.  

> [!NOTE]
> Das `Input.ChoiceSet` Steuerelement basiert auf den Eigenschaften und den `style` `isMultiSelect` Eigenschaften.  

### <a name="update-schema"></a>Schema aktualisieren

Die folgenden Eigenschaften sind Ergänzungen zum `Input.ChoiceSet` Schema, um die Personenauswahl auf der Karte zu aktivieren:  

#### <a name="inputchoiceset-control"></a>Input.ChoiceSet-Steuerelement

|Eigenschaft |Typ |Erforderlich |Beschreibung |
|----|----|----|----|
|**choices.data** |**Data.Query** |Nein |Ermöglicht die dynamische automatische Fertigstellung für verschiedene Benutzertypen, indem Ergebnisse aus dem angegebenen Dataset abgerufen werden. |

#### <a name="dataquery"></a>Data.Query

|Eigenschaft |Typ |Erforderlich |Beschreibung|
|--|--|--|--|
|**Dataset** |String |Ja |Der Datentyp, der dynamisch abgerufen werden muss.|   

#### <a name="dataset"></a>Dataset
Die folgende Tabelle enthält vordefinierte Werte als **Dataset** für die Personenauswahl:   

|Dataset|Suchbereich
|--|--|
|**graph.microsoft.com/users** |Durchsuchen Sie alle Mitglieder in der gesamten Organisation.|
|**graph.microsoft.com/users?scope=currentContext** |Suchen Sie innerhalb der Mitglieder der aktuellen Unterhaltung, z. B. Chat oder Kanal, in dem die bestimmte Karte gesendet wird.|        

### <a name="example"></a>Beispiel
Das Codebeispiel für das Erstellen der Personenauswahl mit der Organisationssuche lautet wie folgt:

```json 
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "People Picker with Org search enabled"
        },
        {
            "type": "Input.ChoiceSet",
            "choices": [],
            "choices.data": {
                "type": "Data.Query",
                "dataset": "graph.microsoft.com/users"
            },
            "id": "people-picker",
            "isMultiSelect": true
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Submit"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```  

Die folgende Abbildung veranschaulicht die Personenauswahl in adaptiven Karten mit der Organisationssuche:

![Personenauswahl-Organisationssuche](../../assets/images/cards/peoplepicker-org-search.png)

Um die Suche in einer Liste von Unterhaltungsmitgliedern zu aktivieren, verwenden Sie das entsprechende Dataset, das in der [Datasettabelle](#dataset) definiert ist. `isMultiSelect` wird verwendet, um die Auswahl mehrerer Benutzer im Steuerelement zu aktivieren. Sie ist standardmäßig auf "false" festgelegt, und mit dieser Einstellung können Sie nur einen einzelnen Benutzer auswählen.

### <a name="data-submission"></a>Datenübermittlung

Sie können ausgewählte Daten verwenden `Action.Submit` oder an Ihren Bot `Action.Execute` übermitteln. Die `invoke` auf Ihrem Bot empfangene Nutzlast ist eine Liste der AAD-IDs oder der in der statischen Liste bereitgestellten IDs.
Wenn in der Personenauswahl ein Benutzer im Steuerelement ausgewählt wird, `AAD ID` ist der Benutzer der zurückgegebene Wert. Dies `AAD ID` ist eine Zeichenfolge und identifiziert einen Benutzer im Verzeichnis eindeutig.

Das Format des an den Bot übermittelten Werts hängt vom Wert der `isMultiSelect` Eigenschaft ab:

|Wert von `isMultiSelect`|Format|
|--|--|
|false _(einzelne Auswahl)_|<selected_AAD_ID>|
|true _(Mehrfachauswahl)_|<selected_AAD_ID_1>,<selected_AAD_ID_2>,<selected_AAD_ID_3>|  

Mit der wählt die `AAD ID` Personenauswahl den entsprechenden Benutzer vorab aus. 

## <a name="preselection-of-user"></a>Vorauswahl des Benutzers

Die Personenauswahl unterstützt die Vorabauswahl des Benutzers im Steuerelement beim Erstellen und Senden einer adaptiven Karte. `Input.ChoiceSet` unterstützt die `value` Eigenschaft, die für die Vorabauswahl eines Benutzers verwendet wird. Das Format dieser `value` Eigenschaft entspricht dem format des übermittelten Werts in der [Datenübermittlung.](#data-submission)  
Die folgende Liste enthält die Informationen für die Vorabauswahl von Benutzern:

* Geben Sie für einen einzelnen Benutzer im Steuerelement `AAD ID` den Benutzer als `value` . 
* Geben Sie für mehrere Benutzer, z. B. `isMultiSelect` `true` eine durch Trennzeichen getrennte Zeichenfolge von s `AAD ID` an.  

Im folgenden Beispiel wird die Vorauswahl eines einzelnen Benutzers beschrieben:

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "People Picker with Org search enabled"
        },
        {
            "type": "Input.ChoiceSet",
            "choices": [],
            "choices.data": {
                "type": "Data.Query",
                "dataset": "graph.microsoft.com/users"
            },
            "id": "people-picker",
            "value": "<AAD ID 1>"
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Submit"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```  

Im folgenden Beispiel wird die Vorauswahl mehrerer Benutzer beschrieben:

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "People Picker with Org search enabled"
        },
        {
            "type": "Input.ChoiceSet",
            "choices": [],
            "choices.data": {
                "type": "Data.Query",
                "dataset": "graph.microsoft.com/users"
            },
            "id": "people-picker",
            "isMultiSelect": true,
            "value": "<AAD ID 1>,<AAD ID 2>,<AAD ID 3>"
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Submit"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```
 
## <a name="static-choices"></a>Statische Auswahlmöglichkeiten

Die statische Auswahl unterstützt Szenarien, in denen benutzerdefinierte Profile in die vordefinierten Datasets eingefügt werden müssen. `Input.ChoiceSet` unterstützt die statische Angabe `choices` in der JSON. Die statische Auswahl wird verwendet, um die Auswahlmöglichkeiten zu erstellen, aus denen der Benutzer auswählen kann.

> [!NOTE]
> Statisch `choices` werden mit dynamischen Datasets verwendet. 

Die Auswahl besteht aus `title` und `value` . Wenn diese Auswahl zusammen mit der Personenauswahl verwendet wird, werden diese Optionen in Benutzerprofile übersetzt, `title` die den Namen und den `value` Bezeichner aufweisen. Diese benutzerdefinierten Profile sind auch Teil der Suchergebnisse, wenn die Suchabfrage mit der angegebenen `title` übereinstimmt.    
Im folgenden Beispiel werden statische Auswahlmöglichkeiten beschrieben: 

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "People Picker with Org search enabled"
        },
        {
            "type": "Input.ChoiceSet",
            "choices": [
                {
                    "title": "Custom Profile 1",
                    "value": "Profile1"
                },
                {
                    "title": "Custom Profile 2",
                    "value": "Profile2"
                }
            ],
            "choices.data": {
                "type": "Data.Query",
                "dataset": "graph.microsoft.com/users"
            },
            "id": "people-picker",
            "isMultiSelect": true
        }
    ],
    "actions": [
        {
            "type": "Action.Submit",
            "title": "Submit"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

Die folgende Abbildung zeigt die Personenauswahl in adaptiven Karten mit statischen Auswahlmöglichkeiten in der Organisationssuche:

![Statische Auswahl der Personenauswahl](../../assets/images/cards/peoplepicker-static-choice.png)


Sie können die Personenauswahl für eine effiziente Aufgabenverwaltung in verschiedenen Szenarien implementieren.  

## <a name="see-also"></a>Siehe auch

[Kartenreferenz](cards-reference.md)

