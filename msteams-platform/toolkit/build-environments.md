---
title: Vorbereiten des Erstellens von Apps mit dem Teams-Toolkit
author: surbhigupta
description: In diesem Artikel erfahren Sie, wie Sie die Umgebung des Teams-Toolkits erstellen und die App im Entwicklerportal verwalten.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 7f092d18075030777f0978f6e963c8513256a0f5
ms.sourcegitcommit: 637b8f93b103297b1ff9f1af181680fca6f4499d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2022
ms.locfileid: "68499181"
---
# <a name="prepare-to-build-apps-using-teams-toolkit"></a>Vorbereiten des Erstellens von Apps mithilfe des Teams-Toolkits

Das Teams-Toolkit unterstützt Umgebungen zum Erstellen von Apps. Das Teams-Toolkit hilft auch, Azure Functions Funktionen sowie Clouddienste in die von Ihnen erstellte Teams-App zu integrieren.

:::image type="content" source="../assets/images/buildapps-TTK.png" alt-text="Vorbereiten des Erstellens von Apps mithilfe des Teams-Toolkits":::

## <a name="build-environments"></a>Erstellen von Umgebungen

Das Teams-Toolkit in Microsoft Visual Studio Code bietet eine Reihe von Umgebungen zum Erstellen Ihrer Teams-App. Sie können jede der folgenden Umgebungen auswählen, die für Ihre App am besten geeignet sind:

* JavaScript oder TypeScript
* SharePoint-Framework (SPFx)

### <a name="create-your-teams-app-using-javascript-or-typescript"></a>Erstellen Ihrer Teams-App mit JavaScript oder TypeScript

Die mit JavaScript erstellten Apps haben die folgenden Vorteile:

* Die App verfügt über eine eigene Benutzeroberfläche und UX-Funktionen, die reichhaltig und benutzerfreundlich sind.
* Bietet schnelle Upgrades auf vorhandene Apps.
* Verteilt Apps auf mehreren Plattformen, z. B. Android und iOS.
* Kompatibel zum Erstellen einer App mit vorhandenen APIs.

Das Teams-Toolkit in Visual Studio Code unterstützt das Erstellen der folgenden Apps mit JavaScript oder TypeScript:

* Registerkarten-App: Ihre Registerkarten-App kann webbasierte Inhalte enthalten, Sie können über eine benutzerdefinierte Registerkarte für Ihre Webinhalte in Teams verfügen oder Ihren Webinhalten Teams-spezifische Funktionen hinzufügen.
* Bot-App: Bots können Chat-Bots oder Unterhaltungsbots sein, mit denen Sie einfache und sich wiederholende Aufgaben wie Kundendienst oder Supportmitarbeiter ausführen können.
* Benachrichtigungs-Bot: Sie können Nachrichten im Teams-Kanal oder gruppen- oder persönlichen Chat über Benachrichtigungs-Bots mit HTTP-Anforderung senden.
* Befehlsbot: Sie können sich wiederholende Aufgaben mithilfe des Befehls-Bots automatisieren. Befehlsbots helfen Ihnen bei der Beantwortung einfacher Abfragen oder Befehle, die in Chats gesendet werden.
* Nachrichtenerweiterungen: Sie können mit Ihrem Webdienst über Schaltflächen und Formulare interagieren. Von der Nachrichtenerweiterung bereitgestellte Funktion.

### <a name="create-your-teams-app-using-spfx"></a>Erstellen Ihrer Teams-App mit SPFx

Mit dem Teams-Toolkit in Visual Studio Code können Sie Registerkarten-Apps mit SPFx erstellen. Diese Apps haben die folgenden Vorteile:

* Bietet Ihnen eine einfache Integration von Daten in SharePoint in Ihre Teams.
* Sie können Ihre SPFx-Lösung in Ihre Geschäfts-APIs integrieren, die mit Microsoft Azure Active Directory (Azure AD) gesichert sind.
* Bietet Ihnen Zugriffe auf verschiedene Open Source-Tools.
* Erstellt für Ihre leistungsstarken Anwendungen, die eine hervorragende UX bieten können.
* Lässt sich problemlos in andere Microsoft (Office) 365-Workloads integrieren.
* Bietet Flexibilität beim Hosten von Anwendungen, wo immer dies erforderlich ist.

## <a name="support-for-azure-functions"></a>Unterstützung für Azure Functions

Sie können das Teams-Toolkit verwenden, um [Azure Functions](/azure/azure-functions/functions-overview) Funktionen in das Erstellen von Apps zu integrieren. Sie können sich auf die wichtigsten Codeelemente konzentrieren und Azure Functions den Rest erledigen.
Azure Functions ermöglichen Ihnen folgende Implementierung:

1. Systemlogik in Ihre leicht verfügbaren Codeblöcke. Diese Blöcke werden als Funktionen bezeichnet.
1. Mit zunehmenden Anforderungen erfüllt Azure Functions die Anforderung mit so vielen Anforderungen wie nötig.

Die Azure-Funktion lässt sich in eine Reihe von [Clouddiensten](add-resource.md#types-of-cloud-resources) integrieren und bietet funktionsreiche Implementierungen. Im Folgenden sind nur einige häufige Szenarien für Azure Functions aufgeführt:

* Beim Erstellen einer Web-API
* Verarbeitung von Datenbankänderungen
* Verarbeiten von IoT-Datenströmen
* Verwalten von Nachrichtenwarteschlangen

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Toolkit-Erweiterung für Visual Studio](visual-studio-overview.md)
* [Verwalten Ihrer Teams-Apps mithilfe des Entwicklerportals](../concepts/build-and-test/teams-developer-portal.md)
* [Erstellen einer neuen Teams-App mit Teams Toolkit](create-new-project.md)
