---
title: Personenauswahl in Adaptiven Karten
description: Beschreibt die Verwendung des Personenauswahl-Steuerelements in adaptiven Karten
localization_priority: Normal
keywords: Personenauswahl für adaptive Karten
ms.topic: reference
author: Rajeshwari-v
ms.author: surbhigupta
ms.openlocfilehash: 8a78be74d8142600ccc08093744491a19900e60b
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073426"
---
# <a name="people-picker-in-adaptive-cards"></a>Personenauswahl in Adaptiven Karten

>[!NOTE]
> Derzeit ist die Personenauswahl in adaptiven Karten in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) nur für mobilgeräte und allgemein verfügbar (GA) für Desktop verfügbar.

Die Personenauswahl hilft Benutzern beim Suchen und Auswählen von Benutzern in der adaptiven Karte. Sie können die Personenauswahl als Eingabesteuerelement zur adaptiven Karte hinzufügen, die in Chats, Kanälen, Aufgabenmodulen und Registerkarten funktioniert. Die Personenauswahl unterstützt die folgenden Features:

* Durchsucht einzelne oder mehrere Benutzer.
* Wählt einzelne oder mehrere Benutzer aus.
* Wird einzelnen oder mehreren Benutzern neu zugewiesen.
* Der Name der ausgewählten Benutzer wird vorab ausgefüllt.

## <a name="popular-scenarios"></a>Beliebte Szenarien

Die folgende Tabelle enthält beliebte Szenarien für die Personenauswahl in adaptiven Karten und die entsprechenden Aktionen:

|Szenarien|Aktionen|
|----------|-------------------------|
|Genehmigungsbasierte Szenarien| Zum Anfordern, Zuweisen und erneuten Zuweisen der Genehmigung an den vorgesehenen Benutzer basierend auf der Anforderung.|
|Verwaltung von Sicherheitsvorfällen| Zum Nachverfolgen von Vorfällen und Benachrichtigung, Zuweisen und erneuter Zuweisung an den vorgesehenen Benutzer zur sofortigen Aktion.|
|Projektmanagement| So weisen Sie bestimmten Benutzern Tickets oder Fehler zu.|
|Benutzersuche| So suchen Sie nach Benutzern in der gesamten Organisation.|

# <a name="desktop"></a>[Desktop](#tab/desktop)

Der Web- und Desktopclient unterstützt die Personenauswahl in adaptiver Karte. Bei der Suche im Web umfasst die Personenauswahl eine Inlineeingabe.

### <a name="reassignment-scenario-example"></a>Beispiel für ein Szenario für die neu zugewiesene Zuweisung

Benutzer A (Robert) erhält ein Ticket für eine Aufgabe in einem Kanal und erkennt einen falschen Zugewiesenen. Benutzer A zuweisen die Aufgabe, die die Informationen zurück an den Bot sendet.

So weisen Sie eine Aufgabe erneut zu:

1. Wählen Sie **"Neu zuweisen** " aus, wo das Personenauswahlfeld mit dem Namen vorbefüllt ist, um die Aufgabe dem beabsichtigten Benutzer neu zuzuweisen.
1. Entfernen Sie den namen des falschen Benutzers.
1. Wählen Sie die vorgesehenen Benutzer gemäß dem Bildszenario, Benutzer B (Mona) und Benutzer C (Robin) für die Aufgabe aus.
1. Wählen Sie **Zuweisen** aus. Nach dem Zuweisen werden die Informationen an den Bot gesendet.
   Der Bot aktualisiert die adaptive Karte und benachrichtigt die beabsichtigten Benutzer.

Die folgende Abbildung zeigt das Szenario für die Neuzuweisung:

![Personenauswahl auf dem Desktop](../../assets/images/cards/desktoppp.gif)

# <a name="mobile"></a>[Mobil](#tab/mobile)

> [!NOTE]
> Derzeit ist dieses Feature nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md#public-developer-preview-for-microsoft-teams) verfügbar.

Mobile Android- und iOS-Clients unterstützen die Personenauswahl in adaptiven Karten. Sie können die Personenauswahl auf Mobilgeräten verwenden, um Benutzer zu suchen und auszuwählen, um die Benutzerfreundlichkeit zu verbessern. Die Suchumgebung ist mit jeder anderen Benutzerauswahlerfahrung auf mobilgeräten vergleichbar.

### <a name="reassignment-scenario-example"></a>Beispiel für ein Szenario für die neu zugewiesene Zuweisung

Benutzer A (Robert) erhält ein Ticket für eine Aufgabe in einem Kanal und erkennt einen falschen Zugewiesenen. Benutzer A zuweisen die Aufgabe, die die Informationen zurück an den Bot sendet.

So weisen Sie eine Aufgabe erneut zu:

1. Wählen Sie **"Neu zuweisen** " aus, wo das Personenauswahlfeld mit dem Namen vorbefüllt ist, um die Aufgabe dem beabsichtigten Benutzer neu zuzuweisen.
1. Entfernen Sie den namen des falschen Benutzers.
1. Wählen Sie die vorgesehenen Benutzer gemäß dem Bildszenario, Benutzer B (Mona) und Benutzer C (Robin) für die Aufgabe aus.
1. Wählen Sie **Fertig** aus.
1. Wählen Sie **Zuweisen** aus. Nach dem Zuweisen werden die Informationen an den Bot gesendet.
   Der Bot aktualisiert die adaptive Karte und benachrichtigt die beabsichtigten Benutzer.

Die folgende Abbildung zeigt das Szenario für die Neuzuweisung:

![Personenauswahl auf Mobilgeräten](../../assets/images/cards/mobilepp.gif)

---

## <a name="implement-people-picker"></a>Implementieren der Personenauswahl

Die Personenauswahl wird als Erweiterung des [Input.ChoiceSet-Steuerelements](https://adaptivecards.io/explorer/Input.ChoiceSet.html) implementiert. Das Eingabesteuerelement enthält die folgenden Auswahlmöglichkeiten:

* Dropdown, z. B. eine erweiterte Auswahl.
* Optionsfeld, z. B. eine einzelne Auswahl.
* Kontrollkästchen, z. B. Mehrfachauswahl.  

> [!NOTE]
> Das `Input.ChoiceSet` Steuerelement basiert auf den `style` Und-Eigenschaften `isMultiSelect` .  

### <a name="update-schema"></a>Schema aktualisieren

Die folgenden Eigenschaften sind Ergänzungen zum Schema, um die `Input.ChoiceSet` Benutzerauswahl auf der Karte zu aktivieren:  

#### <a name="inputchoiceset-control"></a>Input.ChoiceSet-Steuerelement

|Eigenschaft |Typ |Erforderlich |Beschreibung |
|----|----|----|----|
|**choices.data** |**Data.Query** |Nein |Ermöglicht das dynamische Automatische Abschließen für verschiedene Benutzertypen, indem Ergebnisse aus dem angegebenen Dataset abgerufen werden. |

#### <a name="dataquery"></a>Data.Query

|Eigenschaft |Typ |Erforderlich |Beschreibung|
|--|--|--|--|
|**Dataset** |Zeichenfolge |Ja |Der Datentyp, der dynamisch abgerufen werden muss.|

#### <a name="dataset"></a>Dataset

Die folgende Tabelle enthält vordefinierte Werte als **Dataset** für die Personenauswahl:

|Dataset|Suchbereich
|--|--|
|**graph.microsoft.com/users** |Durchsuchen Sie alle Mitglieder in der gesamten Organisation.|
|**graph.microsoft.com/users?scope=currentContext** |Suchen Sie innerhalb der Mitglieder der aktuellen Unterhaltung, z. B. Chat oder Kanal, in dem die jeweilige Karte gesendet wird.|

### <a name="example"></a>Beispiel

Das Codebeispiel zum Erstellen der Personenauswahl mit der Organisationssuche lautet wie folgt:

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

:::image type="content" source="../../assets/images/Cards/peoplepicker-org-search.png" alt-text="Personenauswahl-Organisationssuche":::

Um die Suche innerhalb einer Liste von Unterhaltungsmitgliedern zu aktivieren, verwenden Sie das entsprechende Dataset, das in der [Datasettabelle](#dataset) definiert ist. `isMultiSelect` wird verwendet, um die Auswahl mehrerer Benutzer im Steuerelement zu aktivieren. Es ist standardmäßig auf "false" festgelegt, und mit dieser Einstellung können Sie nur einen einzelnen Benutzer auswählen.

### <a name="data-submission"></a>Datenübermittlung

Sie können ausgewählte Daten verwenden `Action.Submit` oder `Action.Execute` an Ihren Bot übermitteln. Die `invoke` in Ihrem Bot empfangene Nutzlast ist eine Liste der Microsoft Azure Active Directory (Azure AD)-IDs oder der in der statischen Liste bereitgestellten IDs.
Wenn in der Personenauswahl ein Benutzer im Steuerelement ausgewählt wird, ist der `Azure AD ID` Wert des Benutzers der zurückgeschickte Wert. Die `Azure AD ID` Zeichenfolge ist eine Zeichenfolge und identifiziert einen Benutzer im Verzeichnis eindeutig.

Das Format des an den Bot übermittelten Werts hängt vom Wert der `isMultiSelect` Eigenschaft ab:

|Wert von `isMultiSelect`|Format|
|--|--|
|false _(einzelne Auswahl)_|<selected_Azure_AD_ID>|
|true _(multi select)_|<selected_Azure_AD_ID_1>,<selected_Azure_AD_ID_2>,<selected_Azure_AD_ID_3>|  

Mit der `Azure AD ID`Personenauswahl wird der entsprechende Benutzer vorgewählt.

## <a name="preselection-of-user"></a>Vorauswahl des Benutzers

Die Personenauswahl unterstützt die Vorauswahl des Benutzers im Steuerelement beim Erstellen und Senden einer adaptiven Karte. `Input.ChoiceSet` unterstützt die `value` Eigenschaft, die zum Vorwählen eines Benutzers verwendet wird. Das Format dieser `value` Eigenschaft entspricht dem Format des übermittelten Werts in der [Datenübermittlung](#data-submission).  
Die folgende Liste enthält die Informationen zum Vorwählen von Benutzern:

* Geben Sie für einen einzelnen Benutzer im Steuerelement den `Azure AD ID` Des-Benutzers als an `value`.
* Geben Sie für mehrere Benutzer, z `isMultiSelect` . B. is `true`, eine durch Kommas getrennte Zeichenfolge von `Azure AD ID`s an.  

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
   "value": "<Azure AD ID 1>"
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
   "value": "<Azure AD ID 1>,<Azure AD ID 2>,<Azure AD ID 3>"
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

Die statische Auswahl unterstützt Szenarien, in denen benutzerdefinierte Profile in die vordefinierten Datasets eingefügt werden müssen. `Input.ChoiceSet` unterstützt die statische Angabe `choices` im JSON-Code. Die statische Auswahl wird verwendet, um die Auswahlmöglichkeiten zu erstellen, aus denen der Benutzer auswählen kann.

> [!NOTE]
> Statisch `choices` werden mit dynamischen Datasets verwendet.

Die Auswahl besteht aus `title` und `value`. Wenn diese Auswahl zusammen mit der Personenauswahl verwendet wird, werden diese Optionen in Benutzerprofile übersetzt, die den `title` Namen und den `value` Bezeichner aufweisen. Diese benutzerdefinierten Profile sind auch Teil der Suchergebnisse, wenn die Suchabfrage dem angegebenen `title`entspricht.
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

:::image type="content" source="../../assets/images/Cards/peoplepicker-static-choice.png" alt-text="People-Picker-Static-Choice":::

Sie können die Personenauswahl für eine effiziente Aufgabenverwaltung in verschiedenen Szenarien implementieren.  

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | C#    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Personenauswahl-Steuerelement in adaptiven Karten| In diesem Beispiel wird die Verwendung des Personenauswahl-Steuerelements in adaptiven Karten veranschaulicht.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-people-picker-adaptive-card/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-people-picker-adaptive-card/nodejs) |

## <a name="see-also"></a>Siehe auch

[Kartenreferenz](cards-reference.md)
