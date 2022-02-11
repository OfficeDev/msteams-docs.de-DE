---
title: Registerkarten für Microsoft Teams
author: surbhigupta
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Teams-Plattform
ms.localizationpriority: high
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: c9d4e7a97cc9272faab32408683f6d8d43338a0d
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518345"
---
# <a name="build-tabs-for-microsoft-teams"></a>Registerkarten für Microsoft Teams erstellen

Registerkarten sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind. Es handelt sich um einfache HTML-<iframe\>-Tags, die auf im App-Manifest deklarierte Domänen verweisen und als Teil eines Kanals innerhalb eines Teams, Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzugefügt werden können. Sie können benutzerdefinierte Registerkarten in Ihre App einschließen, um Ihre eigenen Webinhalte in Teams einzubetten oder Ihren Webinhalten Teams-spezifische Funktionen hinzuzufügen. Weitere Informationen finden Sie unter [JavaScript-Client-SDK für Teams](/javascript/api/overview/msteams-client).

> [!IMPORTANT]
> Derzeit sind benutzerdefinierte Registerkarten in Government Community Cloud (GCC), GCC-High und Department of Defense (DOD) verfügbar.

Die folgende Abbildung zeigt persönliche Registerkarten:

![Persönliche Registerkarten](../assets/images/tabs/personaltab.png)

Die folgende Abbildung zeigt die Contoso-Kanalregisterkarten:

![Kanal- oder Gruppenregisterkarten](../assets/images/tabs/tabs.png)

Es gibt einige Voraussetzungen, die Sie erfüllen müssen, bevor Sie mit Registerkarten arbeiten.

Es gibt zwei Arten von Registerkarten in Teams: persönliche und Kanal oder Gruppe. [Persönliche Registerkarten](~/tabs/how-to/create-personal-tab.md) sind zusammen mit auf eine Person bezogene Bots Bestandteil persönlicher Apps und sind auf einen einzelnen Benutzer beschränkt. Sie können für den einfachen Zugriff an die linke Navigationsleiste angeheftet werden. [Kanal-- oder Gruppenregisterkarten](~/tabs/how-to/create-channel-group-tab.md) übermitteln Inhalte an Kanäle und Gruppenchats und sind eine hervorragende Möglichkeit zum Erstellen von Bereichen für die Zusammenarbeit rund um dedizierte webbasierte Inhalte.

Sie können als Teil einer persönlichen Registerkarte, einer Kanal- oder Gruppenregisterkarte oder eines Aufgabenmoduls [eine Inhaltsseite erstellen](~/tabs/how-to/create-tab-pages/content-page.md). Sie können [eine Konfigurationsseite erstellen](~/tabs/how-to/create-tab-pages/configuration-page.md), mit der Benutzer die Microsoft Teams-App konfigurieren und diese zum Konfigurieren einer Kanal- oder Gruppenchatregisterkarte, einer Messaging-Erweiterung oder eines Office 365-Connectors verwenden können. Sie können Benutzern erlauben, Ihre Registerkarte nach der Installation neu zu konfigurieren und für Ihre Anwendung [eine Seite zum Entfernen von Registerkarten zu erstellen](~/tabs/how-to/create-tab-pages/removal-page.md). Wenn Sie eine Teams-App erstellen, die eine Registerkarte enthält, müssen Sie testen, wie Ihre [Registerkarte auf den Android- und iOS Teams-Clients funktioniert](~/tabs/design/tabs-mobile.md). Ihre Registerkarte muss durch grundlegende Informationen, Gebietsschema- und Designinformationen sowie `entityId` oder `subEntityId` [Kontext erhalten](~/tabs/how-to/access-teams-context.md), der identifiziert, was sich in der Registerkarte befindet.

Sie können Registerkarten mit adaptiven Karten erstellen und alle Teams-App-Funktionen zentralisieren, indem Sie die Notwendigkeit für ein anderes Back-End für Ihre Bots und Registerkarten eliminieren. [Bühnenansicht](~/tabs/tabs-link-unfurling.md) ist eine neue Benutzeroberflächenkomponente, die es Ihnen ermöglicht, den in Teams im Vollbildmodus geöffneten und als Registerkarte angehefteten Inhalt zu rendern. Der bestehende Dienst zum [Aufklappen von Verknüpfungen](~/tabs/tabs-link-unfurling.md) wird aktualisiert, sodass URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte umgewandelt werden können. Sie können [Unterhaltungsregisterkarten erstellen](~/tabs/how-to/conversational-tabs.md) indem Sie Unterentitäten von Unterhaltungen verwenden, mit denen Benutzer Unterhaltungen über Unterentitäten auf Ihrer Registerkarte führen können, z. B. über bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu diskutieren. Sie können Änderungen an [Registerkartenrändern](~/resources/removing-tab-margins.md) vornehmen, um die Erfahrung des Entwicklers beim Erstellen von Apps zu verbessern. Sie können die Registerkarte ziehen und an der gewünschten Position platzieren, um die Registerkartenpositionen in Ihren persönlichen Apps und in Kanal- oder Gruppenchats auszutauschen. 

> [!NOTE]
> **Beiträge** und **Dateien** können nicht von ihren Positionen verschoben werden.

## <a name="tab-features"></a>Registerkartenfeatures

Die Registerkartenfeatures sind wie folgt:

* Wenn eine Registerkarte zu einer App hinzugefügt wird, die auch über einen Bot verfügt, wird der Bot ebenfalls zum Team hinzugefügt.
* Kenntnis der Microsoft Azure Active Directory-ID (Azure AD) des aktuellen Benutzers.
* Gebietsschemakenntnis für den Benutzer, um die Sprache anzugeben, die `en-us` ist.
* SSO-Funktion (Single Sign-On), falls unterstützt.
* Möglichkeit zum Verwenden von Bots oder App-Benachrichtigungen zum Deep-Link zur Registerkarte oder zu einer Unterentität innerhalb des Diensts, z. B. zu einem einzelnen Arbeitselement.
* Die Möglichkeit, ein Aufgabenmodul über Links innerhalb einer Registerkarte zu öffnen.
* Wiederverwenden von SharePoint-Webparts innerhalb der Registerkarte.

## <a name="tabs-user-scenarios"></a>Benutzerszenarien für Registerkarten

**Scenario:** Fügen Sie eine vorhandene webbasierte Ressource in Teams ein. \
**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-App, die Benutzern eine informative Unternehmenswebsite anzeigt.

**Scenario:** Fügen Sie einem Teams-Bot oder einer Messaging-Erweiterung Supportseiten hinzu. \
**Beispiel:** Sie erstellen persönliche Registerkarten, die Webseiteninhalte für **Info** und **Hilfe** für Benutzer bereitstellen.

**Scenario:** Bieten Sie Zugriff auf Elemente, mit denen Ihre Benutzer regelmäßig für kooperative Dialoge und Zusammenarbeit interagieren. \
**Beispiel:** Sie erstellen eine Kanal- oder Gruppenregisterkarte mit Deep Linking zu einzelnen Elementen.

## <a name="understand-how-tabs-work"></a>Grundlegendes zur Funktionsweise von Registerkarten

Sie können eine der folgenden Methoden verwenden, um Registerkarten zu erstellen:

* [Benutzerdefinierte Registerkarte im App-Manifest deklarieren](#declare-custom-tab-in-app-manifest)
* [Eine adaptiven Karte zum Erstellen von Registerkarten verwenden](~/tabs/how-to/build-adaptive-card-tabs.md)

### <a name="declare-custom-tab-in-app-manifest"></a>Benutzerdefinierte Registerkarte im App-Manifest deklarieren

Eine benutzerdefinierte Registerkarte wird im App-Manifest Ihres App-Pakets deklariert. Für jede Webseite, die Sie als Registerkarte in Ihrer App hinzufügen möchten, definieren Sie eine URL und einen Bereich. Darüber hinaus können Sie die [JavaScript-Client-SDK von Teams](/javascript/api/overview/msteams-client) zu Ihrer Seite hinzufügen und `microsoftTeams.initialize()` nach dem Laden Ihrer Seite aufrufen. Teams zeigt Ihre Seite an und bietet Zugriff auf Teams-spezifische Informationen, z. B. dass der Teams-Client das dunkle Design ausführt.

Unabhängig davon, ob Sie Ihre Registerkarte innerhalb des Kanals, der Gruppe oder des persönlichen Bereichs verfügbar machen möchten, müssen Sie eine <iframe\>HTML-[Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) auf Ihrer Registerkarte präsentieren. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in Ihrem Teams-App-Manifest durch die `contentUrl`-Eigenschaft in der `staticTabs`-Matrix festgelegt. Der Inhalt Ihrer Registerkarte ist für alle Benutzer identisch.

Für Kanal- oder Gruppenregisterkarten können Sie auch eine zusätzliche Konfigurationsseite erstellen. Auf dieser Seite können Sie die URL der Inhaltsseite konfigurieren, in der Regel mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden. Dies liegt daran, dass Ihre Kanal- oder Gruppenregisterkarte mehreren Teams oder Gruppenchats hinzugefügt werden kann. Bei jeder nachfolgenden Installation können Ihre Benutzer die Registerkarte konfigurieren, sodass Sie die Benutzeroberfläche nach Bedarf anpassen können. Wenn Benutzer eine Registerkarte hinzufügen oder konfigurieren, wird der Registerkarte, die auf der Benutzeroberfläche (User Interface, UI) von Teams angezeigt wird, eine URL zugeordnet. Das Konfigurieren einer Registerkarte fügt dieser URL einfach zusätzliche Parameter bei. Wenn Sie beispielsweise die Registerkarte „Azure Boards“ hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte lädt. Die URL der Konfigurationsseite wird von der `configurationUrl`-Eigenschaft in der `configurableTabs`-Matrix in Ihrem App-Manifest angegeben.

Sie können mehrere Kanäle oder Gruppenregisterkarten und bis zu 16 persönliche Registerkarten pro App haben.

### <a name="tools-you-can-use-to-build-tabs"></a>Tools, die Sie zum Erstellen von Registerkarten verwenden können
* [Teams-Toolkit für Microsoft Visual Studio Code](../toolkit/visual-studio-code-overview.md)
* [Microsoft Teams-Toolkit-Erweiterung für Visual Studio](../toolkit/visual-studio-overview.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Voraussetzungen](~/tabs/how-to/tab-requirements.md)

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](../concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren eines QR- oder Barcodescanners](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integration von Standortfunktionen](../concepts/device-capabilities/location-capability.md)
* [Registerkarten auf mobilen Geräten](design/tabs-mobile.md#tabs-on-mobile)
