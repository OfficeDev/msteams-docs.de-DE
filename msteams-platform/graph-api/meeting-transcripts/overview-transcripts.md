---
title: Verwenden von Microsoft Graph zum Abrufen von Transkripten für eine Teams-Besprechung
description: Beschreibt den Prozess sowie die Szenarien und APIs zum Abrufen von Transkripten im Szenario nach der Besprechung.
ms.localizationpriority: high
ms.topic: concept
ms.openlocfilehash: 0f16fff6675f6cb0f0bd7f4dc7550885a6177174
ms.sourcegitcommit: 990a36fb774e614146444d4adaa2c9bcdb835998
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2022
ms.locfileid: "67232391"
---
# <a name="get-meeting-transcripts-using-graph-apis"></a>Abrufen von Besprechungstranskripten mithilfe von Graph-APIs

Sie können Ihre App jetzt so konfigurieren, dass Microsoft Teams-Besprechungstranskripte im Szenario nach der Besprechung abgerufen werden. Ihre App kann Microsoft Graph-REST-APIs verwenden, um auf Transkripte, die für eine zuvor geplante Teams-Besprechung generiert wurden, zuzugreifen und diese abzurufen.

Hier sind einige Anwendungsfälle für das Abrufen von Besprechungstranskripten mithilfe der Graph-API:

| Anwendungsfall | Transkript-APIs helfen in den folgenden Fällen: |
| --- | --- |
| Sie benötigen Transkripte für die Erfassung aussagekräftiger Erkenntnisse aus mehreren Besprechungen im vertikalen Vertrieb abrufen. Es ist zeitaufwändig und ineffizient, alle Besprechungen nachzuverfolgen und Besprechungsnotizen manuell abzurufen. Nachdem die Besprechung beendet ist, müssen Sie Unterhaltungen in all diesen Besprechungen untersuchen, um nützliche Informationen zu erhalten. | Bei Verwendung von Graph-APIs in Ihrer App zum Abrufen von Besprechungstranskripten werden die Transkripte aus allen für Ihren Zweck relevanten Besprechungen automatisch abgerufen. Ihre App kann Besprechungsbenachrichtigungen empfangen und das Transkript abrufen, wenn es nach dem Ende der Besprechung generiert wird. Diese Daten können dann verwendet werden, um Folgendes zu gewinnen: <br> • Aggregierte Erkenntnisse und Intelligence-Analysen <br> • Neue Leads und Highlights <br> • Besprechungsnachverfolgungen und Zusammenfassungen |
| Als HR-Initiative führen Sie eine Brainstormingsitzung durch, um die Gesundheit und Produktivität der Mitarbeiter zu verstehen und zu verbessern. Wenn Sie ständig Notizen erstellen müssen, um Zusammenfassungen nach der Besprechung bereitzustellen, kann dies den Gedankenfluss behindern, und möglicherweise erfassen Sie nicht alle wertvollen Vorschläge. Nach der Sitzung müssen Sie die Diskussion analysieren, um Datenpunkte für Planungsverbesserungen zu sammeln. | Wenn Sie Graph-APIs in Ihrer App zum Abrufen von Transkripte nach der Besprechung verwenden, können Sie und die Teilnehmer sich voll und ganz auf die Diskussion konzentrieren. Der Inhalt des Besprechungstranskripts steht zur Verfügung für: <br> • Engagement- und Stimmungsanalyse <br> • Auflisten von Aufgaben oder Problemen <br> • Besprechungsnachverfolgung und Benachrichtigungen |

> [!NOTE]
> Microsoft kann in Zukunft von Ihnen oder Ihren Kunden fordern, basierend an der Datenmenge, auf die durch die API zugegriffen wurde, zusätzliche Gebühren zu zahlen.

So rufen Sie das Transkript für eine bestimmte Besprechung ab:

- [Konfigurieren von Berechtigungen für Azure AD für den Zugriff auf Transkripte](#configure-permissions-on-azure-ad-to-access-transcript)
- [Abrufen von Besprechungs-ID und Organisator-ID](fetch-id.md)
- [Verwenden von Graph-APIs zum Abrufen von Transkripten](/graph/api/resources/calltranscript)

## <a name="configure-permissions-on-azure-ad-to-access-transcript"></a>Konfigurieren von Berechtigungen für Azure AD für den Zugriff auf Transkripte

Ihre App muss über die erforderlichen Berechtigungen zum Abrufen von Transkripten verfügen. Die App kann unter Verwendung organisationsweiter Anwendungsberechtigungen oder RSC-Anwendungsberechtigungen (Ressourcenspezifische Zustimmung) für eine bestimmte Besprechung auf Transkripte für eine Teams-Besprechung zugreifen und diese abrufen.

### <a name="use-organization-wide-application-permissions"></a>Verwenden von organisationsweiten Anwendungsberechtigungen

Sie können Ihre App für den Zugriff auf Besprechungstranskripte auf dem gesamt3en Mandanten konfigurieren. In diesem Fall muss der Besprechungsorganisator Ihre App nicht im Teams-Besprechungschat installieren. Wenn der Mandantenadministrator die organisationsweiten Anwendungsberechtigungen autorisiert, kann Ihre App Transkripte für alle Besprechungen im Mandanten lesen und darauf zugreifen.

Weitere Informationen zu den organisationsweiten Anwendungsberechtigungen, die Ihrer App erteilt werden können, finden Sie unter [Onlinebesprechungsberechtigungen](/graph/permissions-reference#online-meetings-permissions).

### <a name="use-meeting-specific-rsc-application-permissions"></a>Verwenden von besprechungsspezifischen RSC-Anwendungsberechtigungen

Wenn Ihre App nur Transkripte für die Teams-Besprechung abrufen soll, in der sie installiert ist, konfigurieren Sie die besprechungsspezifische RSC-Berechtigung für Ihre App. Autorisierte Benutzer können Ihre App im Besprechungschat installieren. Nach dem Ende der Besprechung kann Ihre App mit dem entsprechenden API-Aufruf das Transkript für diese Besprechung abrufen.

Weitere Informationen zu den besprechungsspezifischen RSC-Berechtigungen, die Ihrer App erteilt werden können, finden Sie unter [Ressourcenspezifische Zustimmung](../rsc/resource-specific-consent.md#resource-specific-permissions-for-a-chat).

Nachdem Sie die Berechtigungen konfiguriert haben, konfigurieren Sie Ihre App so, dass sie Änderungsbenachrichtigungen für alle relevanten Besprechungsereignisse empfängt. Benachrichtigungen enthalten Besprechungs-ID und Organisator-ID, die beim Zugriff auf Transkriptinhalte helfen. Ihre App kann das Transkript für eine Besprechung abrufen, wenn es nach dem Ende der Besprechung generiert wird. Der Inhalt des Transkripts ist als `.vtt`- oder `.docx`-Datei verfügbar.

Weitere Informationen dazu, wie Ihre App erkennt, wann Besprechungen enden, finden Sie unter [Abonnieren von Änderungsbenachrichtigungen](fetch-id.md#subscribe-to-change-notifications) und [Verwenden von Bot Framework zum Abrufen von Besprechungs-ID und Organisator-ID](fetch-id.md#use-bot-framework-to-get-meeting-id-and-organizer-id).

> [!NOTE]
> Der Prozess zum Aufrufen der Graph-APIs für den Zugriff auf und das Abrufen von Transkripten ist für besprechungsspezifische RSC-Anwendungsberechtigungen oder organisationsweite Anwendungsberechtigungen gleich. Diese APIs unterstützen derzeit nur geplante Besprechungen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Abrufen von Besprechungs-ID und Organisator-ID](fetch-id.md)

## <a name="see-also"></a>Siehe auch

- [API-Referenzen für Besprechungs-Apps](../../apps-in-teams-meetings/API-references.md#meeting-apps-api-references)
