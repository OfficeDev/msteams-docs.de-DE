---
title: Erweiterbare Punkte im Microsoft Teams-Client
author: clearab
description: Informieren Sie sich über die Erweiterungspunkte, die für Ihre APP im Microsoft Teams-Client verfügbar sind.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 1db9b6828ef8a4e186160351b90c01f253df552d
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034029"
---
# <a name="extensible-points-in-the-teams-client"></a>Erweiterbare Punkte im Microsoft Teams-Client

Eine auf der Microsoft Teams-Plattform aufgebaute App erweitert den Microsoft Teams-Client (Internet, Mobil und Desktop) mit Webdiensten, die Sie hosten. Die Teams-Plattform bietet eine umfassende und flexible Reihe von Erweiterbarkeitspunkten, Benutzeroberflächen-Konstrukten und APIs, die Sie beim Erstellen Ihrer APP nutzen können. Ihre APP kann so einfach sein wie das Einbetten Ihrer vorhandenen Website in eine Registerkarte für Ihr Team oder eine voll ausgestattete, vielseitige APP, die Ihre Benutzer über die gesamte Breite des Teams-Clients hinweg einbinden lässt. Sie können beschließen, eine vorhandene APP zu integrieren oder eine neue Erfahrung zu erstellen, die vollständig für Microsoft Teams entwickelt wurde.

Es gibt mehrere Orte, an denen der Microsoft Teams-Client erweitert werden kann, damit Benutzer mit Ihrer APP interagieren können. Je nach Szenario können Sie sich auf einen einzelnen Erweiterungspunkt (wie einen persönlichen Unterhaltungs-bot) konzentrieren oder mehrere Erweiterungspunkte kombinieren.

## <a name="teams-channels-and-group-chats"></a>Teams, Kanäle und Gruppenchats

Mit Teams, Kanälen und Gruppenchats können mehrere Personen zusammenarbeiten. Apps in diesem Kontext stehen allen Mitgliedern der Gruppe oder Unterhaltung zur Verfügung, die sich in der Regel auf die Aktivierung zusätzlicher kollaborativer Workflows oder das Entsperren neuer sozialer Interaktionen konzentrieren. Ihre APP hat Zugriff auf APIs, mit denen Sie Informationen über die Mitglieder in der Unterhaltung, die Kanäle in einem Team und Metadaten über das Team oder die Unterhaltung abrufen kann.

Sie können erweitert werden mit:

* [**Konversations Bots**](~/bots/what-are-bots.md) interagieren mit Mitgliedern der Unterhaltung durch Chat und reagieren auf Ereignisse (wie ein Hinzuzufügender neuer Member oder ein Kanal, der umbenannt wird). Alle Unterhaltungen mit einem bot in diesem Kontext sind für alle Mitglieder des Kanals oder der Gruppe sichtbar, daher müssen Sie sicherstellen, dass die Unterhaltung für jeden relevant ist.

* [**Konfigurierbare Registerkarten**](~/tabs/what-are-tabs.md) mit einer eingebetteten voll Bildumgebung, die für den Kanal oder den Gruppenchat konfiguriert ist, in dem die Datei installiert ist. Alle Mitglieder interagieren mit der gleichen freigegebenen Webanwendung, sodass eine Status lose Einzelseiten-App-Erfahrung typisch ist.

* [**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen externen Diensten das Bereitstellen von Nachrichten an die Unterhaltung und Ihre Benutzer zum Senden von Nachrichten an Ihren Dienst. Sie können Karten-und Karten Aktionen nutzen, um umfangreiche, Nachrichten mit Aktionen zu erstellen.

### <a name="personal-apps"></a>Persönliche apps

[Persönliche apps](~/concepts/design/personal-apps.md) sind der Teil ihrer Teams-APP, der sich auf Interaktionen mit einem einzelnen Benutzer konzentriert. Die Erfahrung ist für jeden einzelnen Benutzer eindeutig. Dieser Teil Ihrer APP kann an die linke Navigationsleiste angeheftet werden, um den Zugriff mit einem Mausklick für Ihre Benutzer zu ermöglichen.

Sie können Folgendes enthalten:

* [**Conversational Bots**](~/bots/what-are-bots.md) mit einer 1:1-Unterhaltung mit dem Benutzer. Da es sich um eine private Unterhaltung handelt, ist es in der Regel am besten, diese Interaktion in einer persönlichen APP zu haben, wenn Ihre APP eine Multi-Turn-Unterhaltung benötigt oder eine Benachrichtigung nur für einen einzelnen Benutzer bereitstellen muss.

* [**Persönliche Registerkarten**](~/tabs/what-are-tabs.md), die eine eingebettete Weboberfläche im Vollbildmodus bereitstellen.

## <a name="messages"></a>Nachrichten

Nachrichten stellen das Herzstück der Zusammenarbeit in Microsoft Teams dar. Mit einem [**Aktionsbefehl für die Messaging Erweiterung**](~/messaging-extensions/what-are-messaging-extensions.md)kann Ihre APP Benutzern das Aufrufen der API Ihrer APP aus einer Nachricht ermöglichen und den Inhalt der Nachricht zur Verarbeitung oder Aktion an Ihre APP senden. Ihre APP kann Antworten, indem Sie dem Benutzer ein Formular (ein Aufgabenmodul) zur Verfügung stellt, um weitere Informationen zu sammeln, eine Antwort auf die ursprüngliche Nachricht zu senden oder eine Nachricht direkt an den Benutzer zu senden.

## <a name="writing-messages"></a>Schreiben von Nachrichten

Ihre APP kann Benutzern helfen, effektivere Nachrichten zu erstellen, indem Sie Sie in einem externen System durchsuchen oder Aktionen ausführen können, und die Ergebnisse in ein umfangreiches, strukturiertes Format mit Aktions fähigen Schaltflächen einfügen.

Es gibt drei Möglichkeiten, wie Ihre App Benutzer bei der Erstellung besserer Nachrichten unterstützenkann:

* [**Messaging Extension – Suchbefehle**](~/messaging-extensions/what-are-messaging-extensions.md) , mit denen Sie schnell ein externes System durchsuchen, eine Vorschau der Ergebnisse dieser Suche anzeigen und dann das Ergebnis als umfangreiche Karte in den Chat einfügen.

* [**Messaging Extension-Link Entfaltung**](~/messaging-extensions/what-are-messaging-extensions.md) ermöglicht Ihrer APP, Webdomänen zu überwachen, für die Sie sich interessieren. Wenn eine URL, die diese Domäne enthält, in das Meldungsfeld verfassen eingefügt wird, wird die API ihrer app aufgerufen, sodass Sie der Nachricht eine umfangreiche Karte mit zusätzlichen Informationen zum verknüpften Element hinzufügen können.

* [**Messaging Extension-Action Commands**](~/messaging-extensions/what-are-messaging-extensions.md) präsentieren Sie Ihrem Benutzer ein modales Formular (ein Aufgabenmodul), senden Sie die Ergebnisse des Formulars an Ihre APP, und fügen Sie dann entweder direkt eine Nachricht in die Unterhaltung ein, oder erstellen Sie einen Teil einer Nachricht, die der Benutzer vor dem Senden an die Unterhaltung bearbeiten kann.

## <a name="user-interface-ui-elements"></a>Elemente der Benutzeroberfläche (UI)

Zusätzlich zu den Erweiterbarkeitspunkten bietet die Microsoft Teams-Plattform flexible Benutzeroberflächenelemente für apps, die Sie nutzen können. Diese Elemente ermöglichen es Ihnen, umfangreiche Erfahrungen zu erstellen, die sich für den Microsoft Teams-Client als systemeigen erweisen.

### <a name="cards--card-actions"></a>Karten & Karten Aktionen

[Karten](~/task-modules-and-cards/what-are-cards.md) sind von schematisierten JSON definierte Benutzeroberflächencontainer, die mehrere Eigenschaften und Anlagen enthalten können. Sie können formatierten Text, Medien, Steuerelemente (wie Dropdownfelder und Optionsfelder) und Schaltflächen enthalten, die Karten Aktionen auslösen. Karten Aktionen können Nutzlasten an die API Ihrer APP senden, einen Link öffnen, Authentifizierungs Flüsse initiieren oder Nachrichten an Unterhaltungen senden. Die Microsoft Teams-Plattform unterstützt mehrere Arten von Karten, einschließlich Adaptive Karten, Hero Cards, Thumbnail-Karten und vieles mehr. Sie können in Kartensammlungen kombiniert und in einer Liste oder einem Karussell angezeigt werden.

### <a name="task-modules"></a>Aufgaben Module

[Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md) ermöglichen Ihnen das Erstellen modaler Popups in Ihrer Teams-Anwendung. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen `<iframe>` , ein Widget wie ein YouTube-oder Microsoft-Stream-Video anzeigen oder eine Adaptive Karte anzeigen. Sie sind besonders nützlich zum initiieren und Ausführen von Aufgaben oder Anzeigen von umfangreichen Informationen wie Videos oder Power BI-Dashboards. Eine Popup Umgebung ist häufig natürlicher für Benutzer, die Aufgaben im Vergleich zu einer Registerkarte oder einer Unterhaltungs basierten bot-Erfahrung initiieren und ausführen.

### <a name="deep-links"></a>Deep links

Ihre APP kann [URL-Deep-Links](~/concepts/build-and-test/deep-links.md) erstellen, um den Benutzer über Ihre APP und den Teams-Client zu navigieren. Sie können ein Deeplink für die meisten Entitäten in Microsoft Teams erstellen, und einige (wie eine neue Besprechungsanfrage) ermöglichen das vorab Auffüllen von Informationen mithilfe von Abfragezeichenfolgen in der URL. Beispielsweise könnte Ihr Gesprächs-bot eine Nachricht an einen Kanal mit einer Deeplink an einen Aufgabenmodul senden, die dazu führt, dass eine Karte als 1:1-Nachricht an einen Benutzer gesendet wird, die wiederum ein Deeplink enthält, um eine neue Besprechung mit einem bestimmten Benutzer zu einem bestimmten Datum/einer bestimmten Uhrzeit zu erstellen. Verwenden Sie Deep Links, um über die verschiedenen Erweiterungspunkte, die für Ihre app verfügbar sind, eine Verbindung herzustellen, sodass der Benutzer jederzeit im richtigen Kontext ist.

### <a name="web-content-pages"></a>Webseiten für Webinhalte

Eine [Webinhalts Seite](~/tabs/how-to/create-tab-pages/content-page.md) ist eine von Ihnen gehostete Webseite, die in ein Tab-oder ein Aufgabenmodul eingebettet werden kann. Damit Ihre Webseite in einen Microsoft Teams-Client eingebettet werden kann, müssen Sie Folgendes tun:

* Auf einem HTTPS gehostet werden.
* In einen `<iframe>` vom Microsoft Teams-Client eingebettet werden können.
* Schließen Sie das Microsoft Teams `initialize()` -JavaScript-Client-SDK ein, und rufen Sie die SDK-Methode beim Laden der Seite auf.
