---
title: Entwicklerplattform für Microsoft Teams
author: clearab
description: Übersichtsseite mit Beschreibungen der Microsoft Teams-Entwicklerplattform und erste Schritte beim Erstellen von Apps für Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 5225669ccc8c76bb532d045df6b65105c893e734
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455485"
---
# <a name="what-are-microsoft-teams-apps"></a>Was sind Microsoft Teams-Apps?

Microsoft Teams ist ein Arbeitsbereich für die Zusammenarbeit in Office 365, der in apps und Dienste integriert wird, die für die Zusammenarbeit verwendet werden. Die Microsoft Teams-Entwicklerplattform erleichtert Entwicklern das Integrieren ihrer eigenen apps und Dienste, um die Produktivität zu verbessern, Entscheidungen schneller zu treffen, den Fokus zu erhöhen (durch Reduzieren des Kontextwechsels) und die Zusammenarbeit in vorhandenen Inhalten und Workflows zu erstellen. Auf der Microsoft Teams-Plattform erstellte apps sind Brücken zwischen dem Teams-Client und Ihren Diensten und Workflows; direkte Integration in den Kontext ihrer Plattform für die Zusammenarbeit.

## <a name="what-can-teams-apps-do"></a>Was können Teams-apps tun?

Auf der Microsoft Teams-Plattform integrierte apps konzentrieren sich hauptsächlich auf die Steigerung der Zusammenarbeit und die Verbesserung der Produktivität. Ihre APP kann etwas einfaches sein, wie das Veröffentlichen von Benachrichtigungen von anderen Systemen oder komplexe Anwendungen mit mehreren Facetten. Denken Sie daran, dass Teams eine Plattform für soziale Zusammenarbeit ist; die besten Apps konzentrieren sich auf die Unterstützung von Personen, die sich selbst Ausdrücken und besser zusammenarbeiten.

* **Zusammenarbeiten an Elementen in externen Systemen.** Eines der Hauptszenarien für eine benutzerdefinierte Microsoft Teams-App besteht darin, Informationen oder Elemente von einer anderen Stelle aus in Microsoft Teams zu integrieren und eine Unterhaltung darüber zu führen. Sie können Informationen in Microsoft Teams übertragen, Ihren Benutzern die Suche und das Abrufen bei Bedarf oder das Bereitstellen in einer eingebetteten Webansicht ermöglichen.

* **Workflows aus Unterhaltungen auslösen.** Häufig führen Unterhaltungen dazu, dass Sie einen Workflow starten oder einige Aktionen abschließen müssen. Notieren Sie sich dies, überprüfen Sie meine Pull-Anforderung, konvertieren Sie diese in einen Vertriebsleiter usw. Ihre Teams-App kann den Zugriff auf diesen Workflow direkt innerhalb von Teams platzieren.

* **Benachrichtigen Sie Ihr Team über wichtige Ereignisse.** SICK von e-Mail-Benachrichtigungen? Senden Sie stattdessen Benachrichtigungen an Microsoft Teams! Senden Sie Benachrichtigungen direkt an Benutzer, an einen Kanal, an den Aktivitäts Feed oder an alle Personen, die diese abonnieren.

* **Funktionen von anderen Websites/Diensten einbetten.** Manchmal müssen Sie Ihre APP einfacher entdecken lassen. Betten Sie Ihre vorhandene Einzelseiten-App ein, oder erstellen Sie ein neues Layout für Microsoft Teams.

## <a name="how-do-teams-apps-work"></a>Wie funktionieren Teams-apps?

Das erste, was Sie über benutzerdefinierte Apps für Microsoft Teams wissen sollten (abgesehen davon, wie erstaunlich Sie sein können), ist, dass Teams kein Hostingdienst sind. Ihr App-Paket enthält Metadaten zu Ihrer APP (Name, Symbole usw.) und Zeiger auf die Webdienste, die Sie hosten, mit denen Ihre APP versorgt wird. Microsoft Teams stellt den Verteilungsmechanismus, UI/UX-Konstrukte zur Nutzung und APIs bereit, mit denen Sie die Informationen und Aktionen erweitern können, die für Ihre APP zur Verfügung stehen.

Eine Teams-App besteht aus drei Hauptteilen:

* **Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"),** auf dem Benutzer mit Ihrer APP interagieren können.
* **Ihr Teams-App-Paket** , das die von Ihren Benutzern installierte App erstellt und die Metadaten und Verweise Ihrer APP auf ihre Dienste enthält.
* **Ihr Dienst, Workflow oder Ihre Website** , die die erforderliche Logik, Datenspeicherung und API-Aufrufe ausführen, um Ihre APP zu vertreiben.

Beachten Sie, dass alle Funktionen, die Sie in einer Microsoft Teams-app verfügbar machen, öffentlich über das Internet verfügbar sind, es sei denn, Sie führen zusätzliche Schritte aus, um Sie zu sichern. Wenn Sie Zugriff auf vertrauliche oder geschützte Informationen gewähren möchten, müssen Sie sicherstellen, dass ihre Dienste mindestens den Endpunkt authentifizieren, der eine Verbindung zu Ihrer APP herstellt oder [Ihre Benutzer authentifiziert](concepts/authentication/authentication.md).

## <a name="how-can-you-share-your-teams-app"></a>Wie können Sie Ihre Teams-App freigeben?

Wenn Sie bereit sind, Ihre Microsoft Teams-apps freizugeben, haben Sie je nach Zielgruppe drei Optionen.

* **[Direktes Hochladen Ihrer APP](concepts/deploy-and-publish/apps-upload.md)** Wenn Ihre APP nur für Ihr Team oder einige wenige Personen in Ihrer Organisation freigegeben werden muss, können Sie Ihr App-Paket freigeben und direkt hochladen.
* **[Veröffentlichen im Organisations-App-Katalog](concepts/deploy-and-publish/apps-upload.md)** Sie können Ihre APP für Ihre gesamte Organisation über den App-Katalog freigeben.
* **[Veröffentlichen im öffentlichen App Store](concepts/deploy-and-publish/apps-upload.md)** Wenn Ihre APP für alle Benutzer geeignet ist, können Sie Sie in unserem öffentlichen App-Store veröffentlichen. Je nach Ihren Zielen sind Sie möglicherweise für Marketing-und Vertriebsunterstützung berechtigt.

## <a name="get-started"></a>Erste Schritte

* [Erstellen einer bot-und Tab-app in C #](tutorials/get-started-dotnet-app-studio.md)
* [Erstellen einer bot-und Tab-app in JavaScript/Node. js](tutorials/get-started-nodejs-app-studio.md)

## <a name="learn-more"></a>Weitere Informationen

* [Erweiterbarkeitspunkte im Teams-Client](concepts/extensibility-points.md)
* [Erstellen von Apps für Microsoft Teams](concepts/building-an-app.md)
