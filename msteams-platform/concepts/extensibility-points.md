---
title: Erweiterbare Punkte im Microsoft Teams-Client
author: clearab
description: Informieren Sie sich über die Erweiterungspunkte, die für Ihre APP im Microsoft Teams-Client verfügbar sind.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 0624aefa7873678b1d69c1d5796340cdac69c381
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867132"
---
# <a name="extensible-points-in-the-teams-client"></a>Erweiterbare Punkte im Microsoft Teams-Client

Eine auf der Microsoft Teams-Plattform erstellte App erweitert den Microsoft Teams-Client (Web, Mobil und Desktop) durch Webdienste, die Sie hosten. Die Teams-Plattform bietet eine umfassende und flexible Palette an Erweiterungspunkten, Benutzeroberflächen-Konstrukten und APIs, die Sie für das Erstellen Ihrer App nutzen können. Bei Ihrer App kann es sich um etwas derart einfaches wie das Einbetten Ihrer vorhandenen Website in eine Registerkarte für Ihr Team handeln oder um eine vielseitige App mit vollem Funktionsumfang, die Ihre Benutzer über die gesamte Bandbreite des Teams-Clients einbindet. Sie können zwischen der Integration einer vorhandenen App oder dem Erstellen einer neuen, vollständig auf Teams ausgerichteten Benutzeroberfläche wählen.

Es gibt mehrere Orte, an denen der Microsoft Teams-Client erweitert werden kann, damit Benutzer mit Ihrer App interagieren können. Je nach Szenario möchten Sie möglicherweise den Fokus auf einen einzelnen Erweiterungspunkt (beispielsweise einen persönlichen Unterhaltungs-Bot) legen oder mehrere Erweiterungspunkte kombinieren.

## <a name="teams-channels-and-group-chats"></a>Teams, Kanäle und Gruppenchats

Mit Teams, Kanälen und Gruppenchats können mehrere Personen zusammenarbeiten. Apps in diesem Kontext stehen allen Mitgliedern der Gruppe oder Unterhaltung zur Verfügung, die sich in der Regel auf die Aktivierung zusätzlicher kollaborativer Workflows oder das Entsperren neuer sozialer Interaktionen konzentrieren. Ihrer App wird der Zugriff auf APIs erlaubt, die es Ihnen ermöglichen, Informationen zu den Teilnehmern einer Unterhaltung, zu den Kanälen eines Teams sowie Metadaten zu einem Team oder einer Unterhaltung abzurufen.

Sie können erweitert werden mit:

* [**Konversations Bots**](~/bots/what-are-bots.md) interagieren mit Mitgliedern der Unterhaltung durch Chat und reagieren auf Ereignisse (wie ein Hinzuzufügender neuer Member oder ein Kanal, der umbenannt wird). Alle in diesem Kontext mit einem Bot geführten Unterhaltungen sind für alle Mitglieder eines Kanals oder einer Gruppe sichtbar, weshalb Sie sicherstellen müssen, dass die Unterhaltung für jeden relevant ist.

* [**Konfigurierbare Registerkarten**](~/tabs/what-are-tabs.md) mit einer eingebetteten voll Bildumgebung, die für den Kanal oder den Gruppenchat konfiguriert ist, in dem die Datei installiert ist. Alle Mitglieder interagieren über dieselbe freigegebenen Web-App, weshalb eine zustandslose Einzelseiten-App-Oberfläche üblich ist.

* [**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen externen Diensten das Bereitstellen von Nachrichten an die Unterhaltung und Ihre Benutzer zum Senden von Nachrichten an Ihren Dienst. Sie können die durch Karten und Kartenaktionen gebotenen Möglichkeiten nutzen, um umfassende Nachrichten zu erstellen, die Aktionen erfordern.

### <a name="personal-apps"></a>Persönliche Apps

[Persönliche apps](~/concepts/design/personal-apps.md) sind der Teil ihrer Teams-APP, der sich auf Interaktionen mit einem einzelnen Benutzer konzentriert. Die Benutzererfahrung ist für jeden Benutzer einzigartig. Dieser Teil Ihrer App lässt sich an der linken Navigationsleiste anheften, sodass Ihre Benutzer mit einem einzigen Klick darauf zugreifen können.

Sie können folgende Elemente beinhalten:

* [**Conversational Bots**](~/bots/what-are-bots.md) mit einer 1:1-Unterhaltung mit dem Benutzer. Da es sich um eine private Unterhaltung handelt, ist es in der Regel am besten, diese Interaktion in einer persönlichen APP zu haben, wenn Ihre APP eine Multi-Turn-Unterhaltung benötigt oder eine Benachrichtigung nur für einen einzelnen Benutzer bereitstellen muss.

* [**Persönliche Registerkarten**](~/tabs/what-are-tabs.md) , die eine eingebettete Weboberfläche im Vollbildmodus bereitstellen.

## <a name="messages"></a>Nachrichten

Nachrichten bilden das Herzstück der Zusammenarbeit in Teams. Mit einem [**Aktionsbefehl für die Messaging Erweiterung**](~/messaging-extensions/what-are-messaging-extensions.md)kann Ihre APP Benutzern das Aufrufen der API Ihrer APP aus einer Nachricht ermöglichen und den Inhalt der Nachricht zur Verarbeitung oder Aktion an Ihre APP senden. Ihre App kann reagieren, indem Sie dem Benutzer ein Formular (ein Aufgabenmodul) präsentiert, um weitere Informationen zu sammeln, eine Antwort auf die ursprüngliche Nachricht sendet oder direkt an den Benutzer eine Nachricht sendet.

## <a name="writing-messages"></a>Schreiben von Nachrichten

Ihre APP kann Benutzern helfen, effektivere Nachrichten zu erstellen, indem Sie Sie in einem externen System durchsuchen oder Aktionen ausführen können, und die Ergebnisse in ein umfangreiches, strukturiertes Format mit Aktions fähigen Schaltflächen einfügen.

Es gibt drei Möglichkeiten, wie Ihre App Benutzer dabei unterstützen kann, bessere Nachrichten zu erstellen:

* [**Messaging Extension – Suchbefehle**](~/messaging-extensions/what-are-messaging-extensions.md) , mit denen Sie schnell ein externes System durchsuchen, eine Vorschau der Ergebnisse dieser Suche anzeigen und dann das Ergebnis als umfangreiche Karte in den Chat einfügen.

* [**Messaging Extension-Link Entfaltung**](~/messaging-extensions/what-are-messaging-extensions.md) ermöglicht Ihrer APP, Webdomänen zu überwachen, für die Sie sich interessieren. Wenn eine URL, die diese Domäne enthält, in das Feld „Nachricht verfassen“ eingefügt wird, wird die-API Ihrer App aufgerufen, sodass Sie der Nachricht eine umfangreiche Karte mit zusätzlichen Informationen zu dem verknüpften Element hinzufügen können.

* [**Messaging Extension-Action Commands**](~/messaging-extensions/what-are-messaging-extensions.md) präsentieren Sie Ihrem Benutzer ein modales Formular (ein Aufgabenmodul), senden Sie die Ergebnisse des Formulars an Ihre APP, und fügen Sie dann entweder direkt eine Nachricht in die Unterhaltung ein, oder erstellen Sie einen Teil einer Nachricht, die der Benutzer vor dem Senden an die Unterhaltung bearbeiten kann.

## <a name="user-interface-ui-elements"></a>Elemente der Benutzeroberfläche (UI)

Zusätzlich zu Erweiterungspunkten bietet die Microsoft Teams-Plattform flexible Benutzeroberflächenelemente für Apps, die Sie nutzen können. Mit diesen Elementen können Sie umfassende Benutzeroberflächen erstellen, die dem Teams-Client wie systemeigene Oberflächen erscheinen.

### <a name="cards--card-actions"></a>Karten und Kartenaktionen

[Karten](~/task-modules-and-cards/what-are-cards.md) sind von schematisierten JSON definierte Benutzeroberflächencontainer, die mehrere Eigenschaften und Anlagen enthalten können. Sie können formatierten Text, Medien, Steuerelemente (z. B. Dropdownfelder und Optionsfelder) sowie Schaltflächen, die Kartenaktionen auslösen, beinhalten. Kartenaktionen können Nutzlasten zur API Ihrer App senden, einen Link öffnen, Authentifizierungsabläufe initiieren oder Nachrichten an Unterhaltungen senden. Die Microsoft Teams-Plattform unterstützt zahlreiche unterschiedliche Kartentypen, unter anderem adaptive Karten, Hero-Karten und Miniaturbild-Karten. Diese können zu Kartensammlungen kombiniert und in Form einer Liste oder eines Karussells angezeigt werden.

### <a name="task-modules"></a>Aufgabenmodule

[Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md) ermöglichen Ihnen das Erstellen modaler Popups in Ihrer Teams-Anwendung. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, ein `<iframe>` Widget wie ein YouTube-oder Microsoft-Stream-Video anzeigen oder eine Adaptive Karte anzeigen. Sie eignen sich besonders für das Initiieren und Fertigstellen von Aufgaben oder das Anzeigen von Multimedia-Informationen wie Videos oder Power BI-Dashboards. Eine Popup-Oberfläche wirkt für Benutzer, die Aufgaben initiieren und fertigstellen, im Vergleich zu einer Registerkarte oder einer auf einer Unterhaltung basierenden Bot-Umgebung, häufig natürlicher.

### <a name="deep-links"></a>Deep-Links

Ihre APP kann [URL-Deep-Links](~/concepts/build-and-test/deep-links.md) erstellen, um den Benutzer über Ihre APP und den Teams-Client zu navigieren. Sie können für die meisten Entitäten innerhalb von Teams Deep-Links erstellen, von denen einige (ähnlich einer neuen Besprechungsanfrage) Ihnen ermöglichen, Informationen mithilfe von Abfragezeichenfolgen in der URL im Voraus auszufüllen. So könnte beispielsweise Ihr Unterhaltungs-Bot eine Nachricht an einen Kanal mit einem Deep-Link für ein Aufgabenmodul senden, was dazu führt, dass eine Karte als 1:1-Nachricht an einen Benutzer gesendet wird, die wiederum einen Deep-Link für das Erstellen einer neuen Besprechung mit einem bestimmten Benutzer zu einem bestimmten Datum/einer bestimmten Uhrzeit beinhaltet. Verwenden Sie Deep-Links, um Verbindungen mit den verschiedenen Erweiterungspunkten herzustellen, die für Ihre App verfügbar sind, damit sich Ihr Benutzer stets im richtigen Kontext befindet.

### <a name="web-content-pages"></a>Web-Inhaltsseiten

Eine [Webinhalts Seite](~/tabs/how-to/create-tab-pages/content-page.md) ist eine von Ihnen gehostete Webseite, die in ein Tab-oder ein Aufgabenmodul eingebettet werden kann. Damit Ihre Webseite in einen Microsoft Teams-Client eingebettet werden kann, müssen folgende Voraussetzungen erfüllt sein:

* Die Webseite muss in einem HTTPS-Protokoll gehostet werden.
* Der Teams-Client muss in der Lage sein, sie in einen `<iframe>` einzubetten.
* Sie muss das Microsoft Teams JavaScript-Client-SDK beinhalten und beim Laden der Seite die`initialize()`-Methode des SDK aufrufen.
