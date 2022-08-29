---
title: Abrufen von Besprechungs-ID und Organisator-ID zum Abrufen von Besprechungstranskripten
description: Beschreibt den Prozess zum Abrufen von Besprechungs-ID und Organisator-ID zum Abrufen von Besprechungstranskripten
ms.localizationpriority: high
ms.topic: concept
ms.openlocfilehash: 316eabb77eb440a171ca6f357e1db8a2f3b18b6b
ms.sourcegitcommit: d5628e0d50c3f471abd91c3a3c2f99783b087502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2022
ms.locfileid: "67434985"
---
# <a name="obtain-meeting-id-and-organizer-id"></a>Abrufen von Besprechungs-ID und Organisator-ID

Ihre App kann Transkriptionen einer Besprechung mithilfe der Besprechungs-ID und der Benutzer-ID des Besprechungsorganisators abrufen, die auch als Organisator-ID bezeichnet wird. Die Graph-REST-APIs rufen Transkriptionen basierend auf der Besprechungs-ID und Organisator-ID ab, die als Parameter in der API übergeben werden.

> [!NOTE]
> Die Besprechungs-ID für geplante Besprechungen kann in einigen Tagen ablaufen, wenn sie nicht verwendet wird. Sie kann mithilfe der Besprechungs-URL wiederbelebt werden, um an der Besprechung teilzunehmen. Weitere Informationen zur Ablaufzeitachse für Besprechungen für verschiedene Besprechungstypen finden Sie unter [Besprechungsablauf](/microsoftteams/limits-specifications-teams#meeting-expiration).

Um die Besprechungs-ID und Organisator-ID zum Abrufen des Transkripts abzurufen, wählen Sie eine der beiden Folgenden aus:

- [Abonnieren von Änderungsbenachrichtigungen](#subscribe-to-change-notifications)
- [Verwenden von Bot Framework](#use-bot-framework-to-get-meeting-id-and-organizer-id)

### <a name="subscribe-to-change-notifications"></a>Abonnieren von Änderungsbenachrichtigungen

Sie können Ihre App abonnieren, um Änderungsbenachrichtigungen für geplante Besprechungsereignisse zu erhalten. Wenn Ihre App über die abonnierten Besprechungsereignisse benachrichtigt wird, kann sie Transkriptionen abrufen, wenn sie über erforderliche Azure AD-Berechtigungen autorisiert ist.

Ihre App erhält eine Benachrichtigung über den Typ der Besprechungsereignisse, für die sie abonniert ist:

- [Benachrichtigung auf Benutzerebene](#obtain-meeting-details-using-user-level-notification)
- [Benachrichtigung auf Mandantenebene](#obtain-meeting-details-using-tenant-level-notification)

Wenn Ihre App über ein abonniertes Besprechungsereignis benachrichtigt wird, kann sie die Besprechungs-ID und Organisator-ID aus der Benachrichtigungsnachricht abrufen. Basierend auf den abgerufenen Besprechungsdetails kann Ihre App die Besprechungstranskripte abrufen, nachdem die Besprechung beendet wurde.

#### <a name="obtain-meeting-details-using-user-level-notification"></a>Abrufen von Besprechungsdetails mithilfe von Benachrichtigungen auf Benutzerebene

Wählen Sie aus, dass Sie Ihre App für Benachrichtigungen auf Benutzerebene abonnieren möchten, um Transkriptionen des Besprechungsereignisses eines bestimmten Benutzers zu erhalten. Wenn eine Besprechung für diesen Benutzer geplant ist, wird Ihre App benachrichtigt. Ihre App kann auch Besprechungsbenachrichtigungen mithilfe von Kalenderereignissen empfangen.

Informationen zum Abonnieren Ihrer App zu Kalenderereignissen finden Sie unter [Änderungsbenachrichtigungen für Outlook-Ressourcen in Microsoft Graph](/graph/outlook-change-notifications-overview).

Verwenden Sie das folgende Beispiel, um Benachrichtigungen auf Benutzerebene zu abonnieren:

```http
    
POST https://graph.microsoft.com/v1.0/subscriptions/
{
    "changeType": "created,updated,deleted",
    "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
    "resource": "users('1273a016-201d-4f95-8083-1b7f99b3edeb')/events",
    "expirationDateTime": "2022-05-05T14:58:56.7951795+00:00",
    "clientState": "ClientSecret",
    "includeResourceData": false
}
```

Wenn Ihre App über ein abonniertes Besprechungsereignis benachrichtigt wird, sucht sie in der Benachrichtigung nach der Kalenderereignis-ID. Verwenden Sie die Ereignis-ID, um `JoinWebUrl` eine bestimmte Chat-ID abzurufen und ihre Nachrichten zu abonnieren. Nachdem Ihre App die Chatnachrichten abonniert hat, führen Sie die für [Benachrichtigungen auf Mandantenebene angegebenen](#obtain-meeting-details-using-tenant-level-notification) Schritte aus, um Besprechungs-ID und Organisator-ID abzurufen.

So erhalten Sie Besprechungs-ID und Organisator-ID aus Benachrichtigungen auf Benutzerebene:

1. **Ereignis-ID** abrufen: Ihre App ruft die `eventId` Eigenschaft aus der Benachrichtigungsnutzlast ab.

    <details>
    <summary><b>Beispiel</b>: Benachrichtigungsnutzlast</summary>

    ```json
    {
        "subscriptionId": "ef30cdc6-b5ae-4702-b924-f458fd9e5fc3",
        "changeType": "created",
        "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
        "clientState": "ClientSecret",
        "subscriptionExpirationDateTime": "2022-05-05T07:54:53.1886542-07:00",
        "resource": "Users/1273a016-201d-4f95-8083-1b7f99b3edeb/Events/AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=",
        "resourceData": {}
    }
    ```

    In diesem Beispiel ist das `eventID` enthaltene `resource` *Element AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=*.
    </details>

2. **Abrufen der Besprechungs-URL**: Verwenden Sie die Ereignis-ID, um die Besprechungs-URL abzurufen `joinUrl`.

    Weitere Informationen finden Sie unter [Get event](/graph/api/event-get).

    Verwenden Sie das folgende Beispiel, um die Besprechungs-URL anzufordern:

    ```http
    GET https://graph.microsoft.com/v1.0/users/1273a016-201d-4f95-8083-1b7f99b3edeb/events/AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=
    ```

    Die Antwortnutzlast enthält `joinURL`.

    <details>
    <summary><b>Beispiel</b>: Antwortnutzlast zum Abrufen der Besprechungs-URL</summary>

    ```json
    {
        "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('1273a016-201d-4f95-8083-1b7f99b3edeb')/events/$entity",
        "@odata.etag": "W/\"xRVh47aDEU6na1ckNYfMiwABb2Twsg==\"",
        "id": "AAMkADY0NjM1MjRhLTNiNjAtNDBiOC1hYTQxLThkMjAxN2QzMjZhYQBGAAAAAAC03Gz8aL_JQp2Kxvw5a29SBwDFFWHjtoMRTqdrVyQ1h8yLAAAAAAENAADFFWHjtoMRTqdrVyQ1h8yLAAFwC7nAAAA=",    
        "start": {
            "dateTime": "2022-05-06T15:00:00.0000000",
            "timeZone": "UTC"
        },
        "end": {
            "dateTime": "2022-05-06T15:30:00.0000000",
            "timeZone": "UTC"
        },
            
        "onlineMeeting": {
            "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MjExYzJiMTItZDY1MS00ZGZkLWE5YzQtZTBmNWI1MDg2M2Uw%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%221273a016-201d-4f95-8083-1b7f99b3edeb%22%7d",
            "conferenceId": "438824583",
            "tollNumber": "+1 213-279-1007"
        }    
    }
    ```

    </details>

    Die Besprechungs-URL ist in `joinUrl` enthalten.

3. **Abrufen der Chatthread-ID**: Verwenden Sie die abgerufene `joinUrl` Besprechungs-URL, um die Chatthread-ID abzurufen. Geben Sie diese Besprechungs-URL als Wert für den `joinWebUrl` Parameter an, während Sie die zugehörige Besprechung abrufen.

    Verwenden Sie das folgende Beispiel, um die Thread-ID anzufordern:

    ``` http
    GET https://graph.microsoft.com/v1.0/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings?$filter=JoinWebUrl%20eq%20'https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d'
    ```

    Die Antwortnutzlast enthält das `threadID` Element in der `chatInfo` Eigenschaft.
    <br>
    <details>
    <summary><b>Beispiel</b>: Antwortnutzlast mit Thread-ID</summary>

    ```json
    {
        "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings",
        "value": [
            {
                "id": "MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19NVE01T1RZM01HVXRObVk0TWkwMFlqZzRMVGsyTURVdFkySXlaR1JsTm1VMVpqQTJAdGhyZWFkLnYy",
                "creationDateTime": "2022-04-26T07:41:17.3736455Z",
                "startDateTime": "2022-04-26T10:30:00Z",
                "endDateTime": "2022-04-26T11:00:00Z",
                "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "chatInfo": {
                    "threadId": "19:meeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2@thread.v2",
                    "messageId": "0",
                    "replyChainMessageId": null
                }
            }
        ]
    }
    ```

    </details>

    Die Chat-ID ist in `threadId` enthalten.

4. **Chatnachrichten abonnieren**: Verwenden Sie die Chat-ID, um Ihre App zu abonnieren, um Chatnachrichten für diese bestimmte Besprechung zu empfangen. Weitere Informationen finden Sie unter [Abonnieren von Nachrichten in einem Chat](/graph/teams-changenotifications-chatmessage#subscribe-to-messages-in-a-chat).

    Wenn Sie möchten, dass Ihre App Nachrichten mit bestimmtem Text abonniert, lesen Sie ["Abonnieren von Nachrichten in einem Chat, die bestimmten Text enthalten"](/graph/teams-changenotifications-chatmessage#example-2-subscribe-to-messages-in-a-chat-that-contain-certain-text).

5. Führen Sie die Schritte für [Benachrichtigungen auf Mandantenebene](#obtain-meeting-details-using-tenant-level-notification) aus, um Besprechungs-ID und Organisator-ID abzurufen.

#### <a name="obtain-meeting-details-using-tenant-level-notification"></a>Abrufen von Besprechungsdetails mithilfe von Benachrichtigungen auf Mandantenebene

Benachrichtigungen auf Mandantenebene sind nützlich, wenn Ihre App berechtigt ist, auf alle Besprechungstranskripte im gesamten Mandanten zuzugreifen. Abonnieren Sie Ihre App, um über Ereignisse benachrichtigt zu werden, wenn die Transkription beginnt oder der Anruf für geplante Online-Teams-Besprechungen endet. Nachdem die Besprechung beendet wurde, kann Ihre App auf das Besprechungsprotokoll zugreifen und es abrufen.

Informationen zum Abonnieren Ihrer App für Benachrichtigungen auf Mandantenebene finden [Sie unter "Abrufen von Änderungsbenachrichtigungen"](/graph/teams-changenotifications-chatmessage#subscribe-to-messages-across-all-chats).

Wenn Ihre App über abonnierte Besprechungsereignisse benachrichtigt wird, durchsucht sie die Benachrichtigungen nach begonnenen Transkriptions- und Besprechungsendereignissen. Diese Ereignisse enthalten die Chat-ID, die zum Abrufen der Chatentität verwendet wird, und schließlich die Besprechungs-ID und die Organisator-ID.

So erhalten Sie Besprechungs-ID und Organisator-ID aus Benachrichtigungen auf Mandantenebene:

1. **Chat-ID abrufen**: Ihre App ruft die `chatId` Eigenschaft aus der Benachrichtigung ab, um nachfolgende Anrufe zu tätigen. Ihre App kann die Chat-ID aus folgenden Nutzlasten abrufen:

    - Ereignis "Transkription gestartet": `callTranscriptEventMessageDetail` Ereignistyp

        <details>
        <summary><b>Beispiel</b>: Nutzlast für das Ereignis "Transkription gestartet"</summary>

        ```json
        {
        "subscriptionId": "1217470f-564c-4fe3-b51f-ebd962cb8797",
        "changeType": "created",
        "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
        "resource": "chats('19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2')/messages('1649787549174')",
        "contentDecryptedBySimulator": {
            "@odata.context": "https://graph.microsoft.com/$metadata#chats('19%3Ameeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk%40thread.v2')/messages/$entity",
            "messageType": "systemEventMessage",
            "createdDateTime": "2022-04-12T18:19:09.174Z",
            "lastModifiedDateTime": "2022-04-12T18:19:09.174Z",
            "chatId": "19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2",
            "body": {
                "contentType": "html",
                "content": "<systemEventMessage/>"
            },
            "channelIdentity": null,
            "eventDetail": {
                "@odata.type": "#Microsoft.Teams.GraphSvc.callTranscriptEventMessageDetail",
                "callId": "16481de8-3262-419b-abc7-0139e6239515",
                "callTranscriptICalUid": "",
                "meetingOrganizer": {
                    "application": null,
                    "device": null,
                    "user": {
                    "userIdentityType": "aadUser",
                        "id": "14b779ae-cb64-47e7-a512-52fd50a4154d",
                        "displayName": null
                        }
                    }
                }
            },
            "encryptedContent": {}
        }
        ```

        </details>

    - Anruf beendetes Ereignis:  `callEndedEventMessageDetail` Ereignistyp

        <details>
        <summary><b>Beispiel</b>: Nutzlast für anrufendes Ereignis</summary>

        ```json
        {
            "subscriptionId": "1217470f-564c-4fe3-b51f-ebd962cb8797",
            "changeType": "created",
            "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
            "resource": "chats('19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2')/messages('1649787585457')",
            "resourceData": {},
            "contentDecryptedBySimulator": {
                "@odata.context": "https://graph.microsoft.com/$metadata#chats('19%3Ameeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk%40thread.v2')/messages/$entity",
                "createdDateTime": "2022-04-12T18:19:45.457Z",
                "lastModifiedDateTime": "2022-04-12T18:19:45.457Z",     
                "chatId": "19:meeting_ZjVkMjc0ZWYtNThkMy00ZGI1LWFiYjAtYjg3ZGU0ZWI3MzZk@thread.v2",
                "eventDetail": {
                    "@odata.type": "#Microsoft.Teams.GraphSvc.callEndedEventMessageDetail",
                    "callId": null,
                    "callDuration": "PT1M44S",
                    "callEventType": "meeting",
                    "callParticipants": [
                    ],
                    "initiator": {
        
                    }
                }
            },
            "encryptedContent": {
                    
            }
        }
        ```

        </details>

2. **Chatentität abrufen**: Ihre App kann die Chatentität mithilfe der in Schritt 1 abgerufenen Chat-ID abrufen. Verwenden Sie die Chatentität, um die URL für die Teilnahme am Anruf abzurufen. Das `joinWebUrl` Mitglied der `onlineMeetingInfo` Eigenschaft enthält diese URL und wird verwendet, um schließlich die Besprechungs-ID abzurufen. Die Organisator-ID ist auch Teil der Antwortnutzlast.

    Weitere Informationen zur Chatentität finden Sie unter ["Chat abrufen"](/graph/api/chat-get).

    Verwenden Sie das folgende Beispiel, um die Chatentität basierend auf der Chat-ID anzufordern:

    ``` http
    GET https://graph.microsoft.com/v1.0/chats/19:meeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2@thread.v2
    ```

    Die Antwortnutzlast enthält die folgenden Elemente:

    - **Organisator-ID**: Sie ist im `id` Element der `organizer` Eigenschaft in der Antwortnutzlast enthalten.
    - **URL für Besprechungsanrufe**: Diese URL wird zum Abrufen der Besprechungs-ID verwendet und ist in der Antwortnutzlast in einem der beiden Szenarien verfügbar:
        - Wenn es sich bei der Besprechung um eine Online-Teams-Besprechung handelt, enthält das `joinWebUrl` Mitglied der `onlineMeetingInfo` Eigenschaft diese URL.
        - Wenn die Besprechung nicht als Onlinebesprechung vom Teams-Client oder Outlook-Client erstellt wurde, enthält sie das `calendarEventId` Mitglied in der `onlineMeetingInfo` Eigenschaft. Ihre App kann die `calendarEventId` zum Abrufen `joinUrl`verwenden, die identisch ist mit `joinWebUrl`.

      Weitere Informationen zu Ereignissen finden Sie unter ["Ereignis abrufen"](/graph/api/event-get?view=graph-rest-1.0&tabs=http&preserve-view=true).

      Beispiele für Antwortnutzlastszenarien, die vom Typ der Teilnahme an der Besprechungs-URL abhängen:

        - Online-Teams-Besprechung, wo `joinWebUrl` verfügbar

            <details>
            <summary><b>Beispiel</b>: Antwortnutzlast für Onlinebesprechung</b></summary>

            ```json
            {
                "@odata.context": "https://graph.microsoft.com/beta/$metadata#chats/$entity",
                "id": "19:meeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2@thread.v2",
                "topic": "Test Meet Create Online Meeting",
                "createdDateTime": "2022-04-14T11:30:45.903Z",
                "lastUpdatedDateTime": "2022-04-26T06:27:45.265Z",
                "chatType": "meeting",
                "webUrl": "https://teams.microsoft.com/l/chat/19%3Ameeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2%40thread.v2/0?tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34",
                "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
                "viewpoint": null,
                "onlineMeetingInfo": {
                "calendarEventId": null,
                    "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NmU0NTkxYzMtM2Y2My00NzRlLWFmN2YtNTFiMGM5OWM3ZjY2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                    "organizer": {
                        "id": "14b779ae-cb64-47e7-a512-52fd50a4154d",
                        "displayName": null,
                        "userIdentityType": "aadUser"
                    }
                }
            }
            ```

            </details>

        - Besprechung, die über den Teams-Client oder Outlook-Client geplant wurde, nicht als Onlinebesprechung gekennzeichnet, wo `calendarEventId` verfügbar

            <details>
            <summary><b>Beispiel</b>: Antwortnutzlast für Besprechungen, die nicht als online gekennzeichnet sind</summary>

            ```json
            {
                "@odata.context": "https://graph.microsoft.com/beta/$metadata#chats/$entity",
                "id": "19:meeting_YzM1NGFiZWYtOGFiOS00NjM5LTg4OTktYmU0MjI4NTQyNGZm@thread.v2",
                "topic": "Non Online Meeting Teams Client",
                "createdDateTime": "2022-04-26T09:43:23.711Z",
                "lastUpdatedDateTime": "2022-04-26T09:43:46.157Z",
                "chatType": "meeting",
                "webUrl": "https://teams.microsoft.com/l/chat/19%3Ameeting_YzM1NGFiZWYtOGFiOS00NjM5LTg4OTktYmU0MjI4NTQyNGZm%40thread.v2/0?tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34",
                "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34",
                "viewpoint": null,
                "onlineMeetingInfo": {
                    "calendarEventId": "AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQBGAAAAAAD3AG5jNnlgQJvdCL_KgXJIBwBsww5BlIxtT7iFyYWrXV3AAAAAAAENAABsww5BlIxtT7iFyYWrXV3AAACSDwYeAAA=",
                    "joinWebUrl": null,
                    "organizer": {
                        "id": "14b779ae-cb64-47e7-a512-52fd50a4154d",
                        "displayName": null,
                        "userIdentityType": "aadUser"
                    }
                }
            }
            ```

            </details>

            - Verwenden Sie das folgende Beispiel, um `joinWebUrl` aus dem `calendarEventId` abzurufen:

              ``` http
                GET https://graph.microsoft.com/beta/users/14b779ae-cb64-47e7-a512-52fd50a4154d/events/AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQBGAAAAAAD3AG5jNnlgQJvdCL_KgXJIBwBsww5BlIxtT7iFyYWrXV3AAAAAAAENAABsww5BlIxtT7iFyYWrXV3AAACSDwYdAAA=
              ```

              In diesem Beispiel:

                - Die Organisator-ID lautet *14b779ae-cb64-47e7-a512-52fd50a4154d*.

              Die Antwortnutzlast dieser Anforderung enthält `joinUrl` die `onlineMeeting` Eigenschaft.

                > [!NOTE]
                > `joinUrl` ist identisch mit `joinWebUrl`.

              <br>
              <details>
              <summary><b>Beispiel</b>: Antwortnutzlast, die die URL für die Teilnahme an einer Besprechung enthält</summary>

              ```json
              {
                "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/events/$entity",
                "@odata.etag": "W/\"bMMOQZSMbU+4hcmFq11dwAAAkc3Tmw==\"",
                "id": "AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQBGAAAAAAD3AG5jNnlgQJvdCL_KgXJIBwBsww5BlIxtT7iFyYWrXV3AAAAAAAENAABsww5BlIxtT7iFyYWrXV3AAACSDwYdAAA=",    
                "start": {
                    "dateTime": "2022-04-26T10:30:00.0000000",
                    "timeZone": "UTC"
                },
                "end": {
                    "dateTime": "2022-04-26T11:00:00.0000000",
                    "timeZone": "UTC"
                },    
                "onlineMeeting": {
                    "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d"
                },
                "calendar@odata.associationLink": "https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/calendars('AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQAuAAAAAAD3AG5jNnlgQJvdCL_KgXJIAQBsww5BlIxtT7iFyYWrXV3AAAAAAAENAAA=')/$ref",
                "calendar@odata.navigationLink": "https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/calendars('AAMkAGE3NjJhOTVhLTNkZDQtNDE2OS05ZjU0LTJmOGQ0YTY2YTdiZQAuAAAAAAD3AG5jNnlgQJvdCL_KgXJIAQBsww5BlIxtT7iFyYWrXV3AAAAAAAENAAA=')"
                }
                ```

              </details>

3. **Besprechungs-ID** abrufen: Jetzt kann Ihre App die Besprechungs-ID abrufen `joinWebUrl`.

    Verwenden Sie das folgende Beispiel, um die Onlinebesprechungs-ID anzufordern:

    ``` http
    GET https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings?$filter=JoinWebUrl%20eq%20'https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d'
    ```

    Die Antwortnutzlast enthält die Besprechungs-ID im `id` Element der `value` Eigenschaft.
    <br>
    <details>
    <summary><b>Beispiel</b>: Antwortnutzlast mit Besprechungs-ID</summary>

    ```json
    {
        "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings",
        "value": [
            {
                "id": "MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19NVE01T1RZM01HVXRObVk0TWkwMFlqZzRMVGsyTURVdFkySXlaR1JsTm1VMVpqQTJAdGhyZWFkLnYy",
                "creationDateTime": "2022-04-26T07:41:17.3736455Z",
                "startDateTime": "2022-04-26T10:30:00Z",
                "endDateTime": "2022-04-26T11:00:00Z",
                "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2%40thread.v2/0?context=%7b%22Tid%22%3a%222432b57b-0abd-43db-aa7b-16eadd115d34%22%2c%22Oid%22%3a%2214b779ae-cb64-47e7-a512-52fd50a4154d%22%7d",
                "chatInfo": {
                    "threadId": "19:meeting_MTM5OTY3MGUtNmY4Mi00Yjg4LTk2MDUtY2IyZGRlNmU1ZjA2@thread.v2",
                    "messageId": "0",
                    "replyChainMessageId": null
                }
            }
        ]
    }
    ```

    </details>

4. **Transkript abrufen**: Mit der Organisator-ID und der Besprechungs-ID, die in den Schritten 2 und 3 abgerufen wurde, kann Ihre App die Transkriptionen für dieses bestimmte Besprechungsereignis abrufen.

    Zum Abrufen von Transkriptionen müssen Sie Folgendes ausführen:

    1. **Rufen Sie die Transkript-ID basierend auf der Organisator-ID und der Besprechungs-ID** ab:

       Verwenden Sie das folgende Beispiel, um die Transkript-ID anzufordern:

        ```http
        GET https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings('MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM1pqWTJAdGhyZWFkLnYy')/transcripts
        ```

        In diesem Beispiel:

        - Die Besprechungs-ID ist als Wert für `onlineMeetings` enthalten: *MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bW VldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM 1pqWTJAdGhyZWFkLnYy*.
        - Die Organisator-ID lautet *14b779ae-cb64-47e7-a512-52fd50a4154d*.

        Die Antwortnutzlast enthält die Transkript-ID für die Besprechungs-ID und die `id` Organisator-ID im Mitglied der `value` Eigenschaft.
        <br>
        <details>
        <summary><b>Beispiel</b>: Antwortnutzlast zum Abrufen der Transkript-ID</summary>

        ```json
        {
            "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings('MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM1pqWTJAdGhyZWFkLnYy')/transcripts",
            "@odata.count": 1,
            "value": [
                {
                    "id": "MSMjMCMjMDEyNjJmNjgtOTc2Zi00MzIxLTlhNDQtYThmMmY4ZjQ1ZjVh",
                    "createdDateTime": "2022-04-14T11:34:39.5662792Z"
                }
            ]
        }
        ```

        In diesem Beispiel ist die Transkript-ID *MSMjMCMjMDEyNjJmNjgtOTc2Zi00MzIxLTlhNDQtYThmMmY4ZjQ1ZjVh*.

        </details>

    1. **Zugreifen auf und Abrufen des Besprechungstranskripts basierend auf der Transkript-ID**:

        Verwenden Sie das folgende Beispiel, um die Transkriptionen für eine bestimmte Besprechung im `.vtt` Format anzufordern:

        ```http
        GET https://graph.microsoft.com/beta/users('14b779ae-cb64-47e7-a512-52fd50a4154d')/onlineMeetings('MSoxNGI3NzlhZS1jYjY0LTQ3ZTctYTUxMi01MmZkNTBhNDE1NGQqMCoqMTk6bWVldGluZ19ObVUwTlRreFl6TXRNMlkyTXkwME56UmxMV0ZtTjJZdE5URmlNR001T1dNM1pqWTJAdGhyZWFkLnYy')/transcripts('MSMjMCMjMDEyNjJmNjgtOTc2Zi00MzIxLTlhNDQtYThmMmY4ZjQ1ZjVh')/content?$format=text/vtt
        ```

        Die Antwortnutzlast enthält die Transkripte im `.vtt` Format.

### <a name="use-bot-framework-to-get-meeting-id-and-organizer-id"></a>Verwenden von Bot-Framework zum Abrufen von Besprechungs-ID und Organisator-ID

Ihre App kann das Bot-Framework verwenden, um die Besprechungs-ID und Organisator-ID abzurufen. Der Bot kann Besprechungsstart- oder -endereignisse automatisch von allen geplanten Onlinebesprechungen empfangen.

Verwenden Sie das folgende Beispiel, um die Besprechungs-ID und Organisator-ID mithilfe einer Bot-App abzurufen:

```json
GET /v1/meetings/{meetingId}
```

Die Antwortnutzlast enthält:

- Die Besprechungs-ID im `msGraphResourceId` Mitglied der `details` Eigenschaft.
- Die Organisator-ID im `id` Element der `organizer` Eigenschaft.
<br>
<details>
<summary><b>Beispiel</b>: Antwortnutzlast zum Abrufen von Besprechungsdetails</b></summary>

```json
{
  details: {
    id: "MCMxOTptZWV0aW5nX05XTTFNVEk1TnpNdE5qZ3pNeTAwWVdRNExUaG1PV1F0WlRnM01UQm1PVGczWW1VekB0aHJlYWQudjIjMA==",
    msGraphResourceId: "MSo2NzAyYWZiNi0xMDliLTRjMzItYTE0MS02ZTY1NDY5NTAyYjkqMCoqMTk6bWVldGluZ19OV00xTVRJNU56TXROamd6TXkwMFlXUTRMVGhtT1dRdFpUZzNNVEJtT1RnM1ltVXpAdGhyZWFkLnYy",
    scheduledStartTime: {
    },
    scheduledEndTime: {
    },
    joinUrl: "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NWM1MTI5NzMtNjgzMy00YWQ4LThmOWQtZTg3MTBmOTg3YmUz%40thread.v2/0?context=%7b%22Tid%22%3a%22b3cdf1c8-024a-49e2-a994-f67f830b02f3%22%2c%22Oid%22%3a%226702afb6-109b-4c32-a141-6e65469502b9%22%7d",
    title: "Testing meeting bot 1 - Hun",
    type: "Scheduled",
  },
  conversation: {
    id: "19:meeting_NWM1MTI5NzMtNjgzMy00YWQ4LThmOWQtZTg3MTBmOTg3YmUz@thread.v2",
    isGroup: true,
    conversationType: "groupChat",
  },
  organizer: {
    id: "29:1VZkVr77S3GW_RdAXKrfgFeytpqMegL3tkKvEbwrPqoCVvmqrlKtVrfKWUY7xIM-bZIx4Sq-p1MjdjSZnb5W20w",
    tenantId: "b3cdf1c8-024a-49e2-a994-f67f830b02f3",
    aadObjectId: "6702afb6-109b-4c32-a141-6e65469502b9",
  },
}
```

In diesem Beispiel:

- Die Besprechungs-ID ist als Wert für `msGraphResourceId`enthalten: *MSo2NzAyYWZiNi0xMDliLTRjMzItYTE0MS02ZTY1NDY5NTAyYjkqMCoqMTk6bWVl dGluZ19OV00xTVRJNU56TXROamd6TXlusMFlXUTRMVGht1dRdFpUZzNNVEJtT1RnM 1ltVXpAdGhyZWFkLnYy*.
- Die Organisator-ID ist als Wert für `id` `organizer`:  *29:1VZkVr77S3GW_RdAXKrfgFeytpqMegL3tkKvEbwrPqoCVvmqrlKtVrfKWUY7xIM-bZIx4Sq-p1MjdjSZnb5W20w* enthalten.

</details>

Nachdem Ihre App die Besprechungs-ID und die Organisator-ID abgerufen hat, löst sie die Graph-APIs aus, um Transkriptinhalte mithilfe dieser Besprechungsdetails abzurufen.

### <a name="code-samples"></a>Codebeispiele

Sie können das folgende Codebeispiel für eine Bot-App ausprobieren:

| **Beispielname** | **Beschreibung** | **C#** | **Node.js** |
|----------------|-----------------|--------------|--------------|--------------|
| Besprechungstranskription | Dies ist eine Beispielanwendung, die veranschaulicht, wie Transkript mithilfe von Graph-API abgerufen und im Aufgabenmodul angezeigt wird. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-transcription/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-transcription/nodejs) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Graph-APIs zum Abrufen von Transkriptionen](/graph/api/resources/calltranscript)
