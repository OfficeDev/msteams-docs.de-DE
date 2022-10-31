---
title: Verwalten von Teams-App-Berechtigungen
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Teams-Apps basierend auf dem Feature an verschiedenen Orten verwaltet werden.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 2bc501444e52f31061312c325ddf7dd80370240a
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791846"
---
# <a name="permissions-in-teams-app"></a>Berechtigungen in der Teams-App

Die Berechtigung für die Teams-App wird je nach App-Feature an zwei Stellen verwaltet:

* [Ressourcenspezifische Zustimmung (RSC)](#resource-specific-consent)
* [Azure Active Directory (Azure AD)](#azure-active-directory)

:::image type="content" source="../../assets/images/teams-app-permissions.png" alt-text="Der Screenshot beschreibt die verschiedenen Teams-App-Berechtigungen.":::

## <a name="resource-specific-consent"></a>Ressourcenspezifische Zustimmung

RSC ist eine Integration von Microsoft Teams und Microsoft Graph-API, die es Ihrer App ermöglicht, API-Endpunkte zum Verwalten bestimmter Ressourcen innerhalb einer Organisation zu verwenden, entweder Teams oder Chats. Weitere Informationen finden Sie unter [Aktivieren der ressourcenspezifischen Zustimmung in Teams](../rsc/resource-specific-consent.md).

RSC-Berechtigungen sind nur für Teams-Apps verfügbar, die auf dem Teams-Client installiert sind und derzeit nicht Teil des Azure AD-Portals sind und in der TEAMS-App-Manifestdatei (JSON) deklariert werden.

## <a name="azure-active-directory"></a>Azure Active Directory

Azure AD ist ein cloudbasierter Identitäts- und Zugriffsverwaltungsdienst. Dieser Dienst hilft Ihren Mitarbeitern beim Zugriff auf externe Ressourcen wie Microsoft 365, die Azure-Portal und Tausende anderer SaaS-Anwendungen. Weitere Informationen finden Sie unter [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis).

### <a name="microsoft-graph-api-permission"></a>Microsoft Graph-API-Berechtigung

Graph-API Berechtigungen werden in Azure AD verwaltet. Damit Ihre App auf Daten in Microsoft Graph zugreifen kann, muss der Benutzer oder Administrator ihr die korrekten Berechtigungen über einen Einwilligungsvorgang erteilen. Weitere Informationen finden Sie unter [Microsoft Graph-Berechtigungen](/graph/permissions-reference).

## <a name="capability-wise-management"></a>Funktionsbezogene Verwaltung

### <a name="bot-and-messaging-extension"></a>Bot- und Messaging-Erweiterung

Die Bot- oder Messagingerweiterungs-ID wird basierend auf der folgenden Registrierungsplattform generiert. Diese ID ist erforderlich, um einer Teams-App einen Bot oder eine Messaging-Erweiterung hinzuzufügen.

* Azure AD-Portal
* Entwickler- oder Bot Framework-Portal

#### <a name="azure-ad-portal"></a>Azure AD-Portal

Wenn ein Bot oder eine Messagingerweiterung im Azure AD-Portal registriert ist, ist ihr eine Azure AD-App-ID zugeordnet, die im **Azure AD-Portal** > **App-Registrierungen** zu finden ist. Endpunkte und andere Botkonfigurationen werden im Azure-Portal verwaltet.

#### <a name="developer-or-bot-framework-portal"></a>Entwickler- oder Bot Framework-Portal

Wenn ein Bot oder eine Messagingerweiterung im Entwickler- oder Bot Framework-Portal registriert ist, verfügt er nicht über eine Azure AD-App-ID. Die Bot- oder Messagingerweiterungs-ID finden Sie jedoch im Bot Framework-Portal. Endpunkte und andere Botkonfigurationen werden im Bot Framework-Portal verwaltet.

Andere Teams-spezifische Konfigurationen für den Bot können im Abschnitt Entwicklerportal für die App verwaltet werden.

### <a name="connectors"></a>Connectors

Connectors verfügen über eine Connector-ID und werden über das Connector Developer Dashboard registriert und verwaltet. Diese ID ist erforderlich, um einen Connector für die Teams-App einzuführen. Andere Teams-spezifische Konfigurationen für Connectors können im Abschnitt entwicklerportal für die App verwaltet werden.
