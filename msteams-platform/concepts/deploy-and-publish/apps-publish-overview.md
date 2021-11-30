---
title: Übersicht – Verteilen Ihrer App
description: Beschreibt die Optionen für die Veröffentlichung Ihrer Microsoft Teams-App, das Hochladen Ihrer App und GCC.
ms.topic: conceptual
author: v-rpatkur
ms.author: surbhigupta
ms.localizationpriority: none
keywords: Bereitstellen von Veröffentlichungs-App-Upload gcc
ms.openlocfilehash: 567abdb058f3618236840c993a0ab1a4d638c016
ms.sourcegitcommit: 660273bc6833ab84ba7550e6b374ea6e3780459d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61233498"
---
# <a name="distribute-your-microsoft-teams-app"></a>Verteilen Ihrer Microsoft Teams-App

Sie können Ihre Microsoft Teams-App für eine Einzelperson, ein Team, eine Organisation oder jede Person bereitstellen, die sie verwenden möchte. Die Verteilung hängt von mehreren Faktoren ab, einschließlich der Anforderungen der Benutzer, geschäftlichen, technischen Anforderungen und Ihrer Ziele für die App.

## <a name="configure-default-install-options"></a>Konfigurieren der Standardinstallationsoptionen

Sie konfigurieren Standardinstallationsoptionen. Wenn die primäre Funktion Ihrer App beispielsweise ein Bot ist, können Sie den Bot auch als Standardfunktion festlegen, wenn ein Benutzer Ihre App in einem Team installiert.

## <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Um Ihre Microsoft Teams App zu verteilen, benötigen Sie ein gültiges App-Paket.  Ein App-Paket ist eine ZIP-Datei, die ein **App-Manifest** und **App-Symbole** enthält.

## <a name="upload-your-app-in-teams"></a>Hochladen Ihrer App in Teams

Querladen einer App für den persönlichen Gebrauch, Zusammenarbeit mit Ihrem Team oder Testen und Debuggen. Für diese Art der Verteilung ist kein formaler Überprüfungsprozess erforderlich.

> [!IMPORTANT]
> Sideloading-Apps sind derzeit in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und DoD (Department of Defense).

Weitere Informationen finden Sie unter [Hochladen Ihrer App in Teams.](apps-upload.md)

## <a name="publish-your-app-to-your-org"></a>Veröffentlichen Ihrer App in Ihrer Organisation

Stellen Sie Ihre App für Personen in Ihrer Organisation zur Verfügung. Diese Art der Verteilung erfordert die Genehmigung Ihres Teams Administrators.

Weitere Informationen finden Sie unter [Verwalten Ihrer Apps im Teams Admin Center.](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2FMicrosoftTeams%2Fbreadcrumb%2Ftoc.json)

### <a name="government-community-cloud-gcc-organizations"></a>Government Community Cloud (GCC) Organisationen

In GCC Teams Umgebungen sind kompatible Microsoft-Apps standardmäßig aktiviert. Stellen Sie vor der Veröffentlichung einer App jedoch sicher, dass alle Endpunkte der App den Anforderungen Ihrer GCC Organisation entsprechen.

> [!IMPORTANT]
>Wenn Ihre App einen Bot oder eine Messaging-Erweiterung enthält, müssen Sie die Option **Microsoft Teams für Behörden** auswählen, wenn Sie einen Kanal zwischen Ihrem Bot und Teams in Azure einrichten. Weitere Informationen finden Sie unter [Verbinden eines Bots mit Kanälen.](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0&preserve-view=true)

## <a name="publish-your-app-to-the-teams-store"></a>Veröffentlichen Ihrer App im Teams Store

Stellen Sie Ihre App für alle Benutzer zur Verfügung. Diese Art der Verteilung erfordert eine Genehmigung von Microsoft.

Weitere Informationen finden Sie unter [Veröffentlichen im Teams Store.](~/concepts/deploy-and-publish/appsource/publish.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurieren der Standardinstallationsoptionen der App](~/concepts/deploy-and-publish/add-default-install-scope.md)

## <a name="see-also"></a>Siehe auch

[Microsoft 365-App-Compliance Program](/microsoft-365-app-certification/overview)
