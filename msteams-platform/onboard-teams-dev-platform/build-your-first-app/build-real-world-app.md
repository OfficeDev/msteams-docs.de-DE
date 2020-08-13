---
title: Erstellen Ihrer ersten Teams-App
author: heath-hamilton
description: Lernprogramm zum Erstellen einer Microsoft Teams-app in einer realen Welt
ms.openlocfilehash: 4915dde4ef5a852f4fc5d1e4c83e3349db2eaf6b
ms.sourcegitcommit: 80bf79a952bb14cbc38c0bd1e3cf8a346158e28e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "46655674"
---
# <a name="learn-how-to-build-your-first-teams-app"></a>Erfahren Sie, wie Sie Ihre erste Teams-app erstellen

In **Erstellen Ihrer ersten App**erfahren Sie, wie Sie mithilfe von Lernprogrammen eine einfache Teams-app erstellen. Die Lektionen bauen auf einander auf und führen Sie durch jeden Schritt der Erstellung einer einfachen Real-World Teams-app. Wir stellen Ihnen allgemeine Tools, grundlegende Konzepte und nützliche Links auf dem Weg vor.

Beginnen Sie mit der Erstellung und Ausführung eines "Hello, World!" Tab-app. Anschließend erstellen Sie eine einfache Benutzeroberfläche und erfahren, wie Sie mit Microsoft Teams JavaScript SDK nützliche Kontexte erhalten.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
  >
  > - Mit dem Microsoft Teams Toolkit für Visual Studio Code können Sie **schnell mit dem Team-Toolkit in Kontakt**treten, um ein App-Projekt und ein Gerüst zu erstellen, damit Sie in wenigen Minuten eine laufende APP haben.
  > - **Definieren Sie Ihre APP mit dem Manifest**: das Manifest ist ein Blueprint, in dem Sie die Funktionen und Dienste angeben, die ihre Teams-App verwendet.
  > - **Bereich Ihrer Zielgruppe**: Sie können eine Teams-App für den persönlichen Gebrauch oder die Zusammenarbeit erstellen. In den Lernprogrammen erfahren Sie, wie Sie eine Registerkarte für einzelne Benutzer oder eine Gruppe von Personen in einem Kanal oder Chat erstellen.
  > - Verwenden von Microsoft Teams **SDK zum Abrufen von Kontexten**: Hier erfahren Sie, wie Sie das Microsoft Teams-JavaScript-SDK zum Ausführen von Designänderungen oder zum Einrichten der Konfigurationsumgebung verwenden.  
  > - **Erweitern Sie Ihre APP**: in den Lernprogrammen wird auf Verwandte Themen eingelinkt, die Sie wahrscheinlich interessieren (darunter auch Authentifizierungs-und Entwurfsrichtlinien).

## <a name="teams-app-fundamentals"></a>Grundlagen der Microsoft Teams-App

Bevor Sie mit den Lernprogrammen beginnen, sollten Sie die folgenden Informationen zum Erstellen von Apps für Microsoft Teams kennen.

### <a name="apps-can-have-multiple-capabilities"></a>Apps können mehrere Funktionen haben

Microsoft Teams-apps bestehen aus einer oder mehreren [Plattformfunktionen](../capabilities-overview.md), einschließlich [Registerkarten](../doc-links/what-are-tabs.md), [Bots](../doc-links/what-are-bots.md ), [Messaging Erweiterungen](../doc-links/what-are-messaging-extensions.md)und [webhooks und Connectors](../doc-links/what-are-webhooks-and-connectors.md). Microsoft Teams-apps weisen auch viele Benutzer [Oberflächen Konventionen und-Elemente](../doc-links/teams-ui-conventions.md)wie Karten, Aufgaben Module und Deep Linking auf, mit denen Sie die bestmögliche Benutzererfahrung erstellen können.

Für diese Lernprogramme erstellen Sie nur Registerkarten, können Ihrer APP jedoch einen bot oder eine andere Funktion hinzufügen, wie Sie möchten.

### <a name="teams-doesnt-host-your-app"></a>Ihre APP wird von Microsoft Teams nicht gehostet.  

Eine Teams-App besteht aus drei Hauptteilen:

1. Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer mit Ihrer APP interagieren.
1. Ihre APP, Ihr Dienst, Ihr Workflow oder Ihre Website, die die erforderliche Logik, Datenspeicherung und API-Aufrufe ausführt, um Ihre APP zu vertreiben.
1. Ihr App-Paket, mit dem Sie die app in Microsoft Teams installieren. Sie enthält App-Metadaten (Name, Symbole usw.) und Zeiger auf ihre Dienste.

## <a name="next-step"></a>Nächster Schritt

Das ist alles für jetzt, Let es Get Started!

> [!div class="nextstepaction"]
> [Erstellen und Ausführen ihrer ersten App](build-and-run-with-toolkit.md)
