---
title: Übersicht – Verteilen Ihrer App
description: Beschreibt die Optionen zum Veröffentlichen Ihrer Microsoft Teams-App, zum Hochladen ihrer App und zum GCC.
ms.topic: conceptual
author: v-rpatkur
ms.author: surbhigupta
ms.localizationpriority: none
keywords: Bereitstellen des Uploads der Veröffentlichungs-App gcc
ms.openlocfilehash: f691edee8f4e3aab34aa616f9bbf0ed451874070
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073069"
---
# <a name="distribute-your-microsoft-teams-app"></a>Verteilen Ihrer Microsoft Teams-App

Sie können Ihre Microsoft Teams-App für eine Person, ein Team, eine Organisation oder jede Person bereitstellen, die sie verwenden möchte. Wie Sie verteilen, hängt von mehreren Faktoren ab, einschließlich der Anforderungen der Benutzer, geschäftlicher, technischer Anforderungen und Ihrer Ziele für die App.

## <a name="configure-default-install-options"></a>Konfigurieren der Standardinstallationsoptionen

Sie konfigurieren die Standardinstallationsoptionen. Wenn die primäre Funktion Ihrer App beispielsweise ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.

## <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Um Ihre Microsoft Teams App verteilen zu können, benötigen Sie ein gültiges App-Paket.  Ein App-Paket ist eine ZIP-Datei, die ein **App-Manifest** und **App-Symbole** enthält.

## <a name="upload-your-app-in-teams"></a>Hochladen Ihrer App in Teams

Querladen einer App für den persönlichen Gebrauch, Zusammenarbeit mit Ihrem Team oder Testen und Debuggen. Für diese Art der Verteilung ist kein formaler Überprüfungsprozess erforderlich.

> [!IMPORTANT]
> Derzeit sind Querladen-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und Department of Defense (DOD).

Weitere Informationen finden Sie [unter Hochladen Ihrer App in Teams](apps-upload.md).

## <a name="publish-your-app-to-your-org"></a>Veröffentlichen der App in Ihrer Organisation

Stellen Sie Ihre App für Personen in Ihrer Organisation zur Verfügung. Für diese Art der Verteilung ist die Genehmigung Ihres Teams Administrators erforderlich.

Weitere Informationen finden Sie [unter Verwalten Ihrer Apps im Teams Admin Center](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2FMicrosoftTeams%2Fbreadcrumb%2Ftoc.json).

### <a name="government-community-cloud-gcc-organizations"></a>Government Community Cloud (GCC) Organisationen

In GCC Teams Umgebungen sind kompatible Microsoft-Apps standardmäßig aktiviert. Stellen Sie vor der Veröffentlichung einer App jedoch sicher, dass alle Endpunkte der App den Anforderungen Ihrer GCC Organisation entsprechen. Weitere Informationen finden Sie [unter Government Community Cloud](../app-fundamentals-overview.md#government-community-cloud).

> [!IMPORTANT]
>Wenn Ihre App eine Bot- oder Messaging-Erweiterung enthält, müssen Sie beim Einrichten eines Kanals zwischen Ihrem Bot und Teams in Azure die Option **Microsoft Teams für Behörden** auswählen. Weitere Informationen finden Sie unter [Verbinden eines Bots mit Kanälen](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0&preserve-view=true).

## <a name="publish-your-app-to-the-teams-store"></a>Veröffentlichen Ihrer App im Teams Store

Stellen Sie Ihre App für jeden zur Verfügung. Für diese Art der Verteilung ist eine Genehmigung durch Microsoft erforderlich.

Weitere Informationen finden Sie unter [Veröffentlichen im Teams Store](~/concepts/deploy-and-publish/appsource/publish.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurieren der Standardinstallationsoptionen der App](~/concepts/deploy-and-publish/add-default-install-scope.md)

## <a name="see-also"></a>Siehe auch

[Microsoft 365-App-Compliance Program](/microsoft-365-app-certification/overview)
