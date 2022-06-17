---
title: Übersicht – Verteilen Ihrer App
description: In diesem Artikel lernen Sie die Optionen zum Veröffentlichen Ihrer Microsoft Teams-App, Hochladen und Bereitstellen Ihrer App und GCC kennen.
ms.topic: conceptual
author: v-rpatkur
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: 72f902b340653cd6d57eccaf7bbd21e7ad608ebc
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123531"
---
# <a name="distribute-your-microsoft-teams-app"></a>Verteilen Ihrer Microsoft Teams-App

Sie können Ihre Microsoft Teams-App für eine Person, ein Team, eine Organisation oder jede Person bereitstellen, die sie verwenden möchte. Wie Sie verteilen, hängt von mehreren Faktoren ab, darunter die Bedürfnisse der Benutzer, geschäftliche, technische Anforderungen und Ihre Ziele für die App.

## <a name="configure-default-install-options"></a>Konfigurieren der Standardinstallationsoptionen

Sie konfigurieren Standardinstallationsoptionen. Wenn die primäre Funktion Ihrer App beispielsweise ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.

## <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Um Ihre Microsoft Teams-App zu verteilen, müssen Sie über ein gültiges App-Paket verfügen.  Ein App-Paket ist eine ZIP-Datei, die ein **App-Manifest** und **App-Symbole** enthält.

## <a name="upload-your-app-in-teams"></a>Hochladen Ihrer App in Teams

Querladen einer App für den persönlichen Gebrauch, in Zusammenarbeit mit Ihrem Team oder beim Testen und Debuggen. Diese Art der Verteilung erfordert keinen formellen Überprüfungsprozess.

> [!IMPORTANT]
> Derzeit sind Querladen-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und Department of Defense (DOD).

Weitere Informationen finden Sie unter [Hochladen Ihrer App in Teams](apps-upload.md).

## <a name="publish-your-app-to-your-org"></a>Veröffentlichen der App in Ihrer Organisation

Machen Sie Ihre App für Personen in Ihrer Organisation verfügbar. Diese Art der Verteilung erfordert die Genehmigung Ihres Teams-Administrators.

Weitere Informationen finden Sie unter [Verwalten Ihrer Apps im Teams Admin Center](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2FMicrosoftTeams%2Fbreadcrumb%2Ftoc.json).

### <a name="government-community-cloud-gcc-organizations"></a>Government Community Cloud (GCC)-Organisationen

In GCC Teams-Umgebungen sind konforme Microsoft-Apps standardmäßig aktiviert. Stellen Sie jedoch vor dem Veröffentlichen einer App sicher, dass alle Endpunkte der App den Anforderungen Ihrer GCC-Organisation entsprechen. Weitere Informationen finden Sie unter [Government Community Cloud](../app-fundamentals-overview.md#government-community-cloud).

> [!IMPORTANT]
>Wenn Ihre App einen Bot oder eine Nachrichtenerweiterung enthält, müssen Sie beim Einrichten eines Kanals zwischen Ihrem Bot und Teams in Azure die Option **Microsoft Teams for Government** auswählen. Weitere Informationen finden Sie unter [Verbinden eines Bots mit Kanälen](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0&preserve-view=true).

## <a name="publish-your-app-to-the-teams-store"></a>Veröffentlichen Sie Ihre App im Teams Store

Machen Sie Ihre App für alle verfügbar. Diese Art der Verteilung erfordert die Genehmigung von Microsoft.

Weitere Informationen finden Sie unter [Veröffentlichen im Teams Store](~/concepts/deploy-and-publish/appsource/publish.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurieren der Standardinstallationsoptionen der App](~/concepts/deploy-and-publish/add-default-install-scope.md)

## <a name="see-also"></a>Siehe auch

[Microsoft 365-App-Compliance Program](/microsoft-365-app-certification/overview)
