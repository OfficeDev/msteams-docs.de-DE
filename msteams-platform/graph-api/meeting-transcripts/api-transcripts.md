---
title: Abrufen von Transkripten mithilfe von Graph-APIs
description: Beschreibt die APIs zum Abrufen von Besprechungstranskripten.
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: 2142bc1346a032f27d8612f6081156d2c4927e8f
ms.sourcegitcommit: 372aade09e62ac7e5936215173a6632fbb042c9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2022
ms.locfileid: "68699178"
---
# <a name="use-graph-apis-to-fetch-transcript"></a>Abrufen von Transkripten mithilfe von Graph-APIs

Verwenden Sie Graph-REST-APIs, um Transkripte für eine bestimmte Besprechung abzurufen. Ihre App ruft die Transkripte basierend auf der Benutzer-ID des Besprechungsorganisators und der Besprechungs-ID ab.

Die folgenden APIs werden zum Abrufen von Transkripten verwendet:

- [callTranscripts auflisten](#list-calltranscripts)
- [callTranscript abrufen](#get-calltranscript)
- [Abrufen von callTranscript-Inhalten](#get-calltranscript-content)

### <a name="list-calltranscripts"></a>CallTranscripts auflisten

Diese API wird verwendet, um eine Liste aller `callTranscript`Objekte basierend auf der Benutzer-ID und Besprechungs-ID abzurufen. Sie gibt die Metadaten der Transkripts der Besprechung zurück, die die Transkript-ID und das Erstellungsdatum und die Erstellungszeit dieses Transkripts enthalten.

**HTTP-Anforderung**

```http
GET /me/onlineMeetings('{meetingId}')/transcripts
GET /users('{userId}')/onlineMeetings('{meetingId}')/transcripts
```

**Optionale Abfrageparameter**

Die Methode unterstützt die `$skipToken` und `$top` [OData-Abfrageparameter](/graph/query-parameters), um die Antwort anzupassen.

**Unterstützte Abfragemuster**

| Muster                | Unterstützt | Syntax                                 | Anmerkungen |
| ---------------------- | ------- | -------------------------------------- | ----- |
| Serverseitige Paginierung |     ✓     | `@odata.nextLink`                      | Rufen Sie ein Fortsetzungstoken in der Antwort ab, wenn sich eine Ergebnismenge über mehrere Seiten erstreckt. |
| Seitenlimit             |     ✓     | `/transcripts?$top=20` | Transkripte mit Seitengröße 20 abrufen. Der Standardseitengrenzwert ist 10. Das maximale Seitenlimit beträgt 100. |

**Anforderungsheader**

| Kopfzeile       | Wert |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

**Anforderungstext**

Geben Sie keinen Anforderungstext für diese Methode an.

**Antwort**

Wenn die Methode erfolgreich ist, werden ein `200 OK` Antwortcode und eine Auflistung von `callTranscript` Objekten im Antworttext zurückgegeben.

<br>
<details>
<summary><b>Beispiel: Liste von callTranscript</b></summary>
<br>
<b>Anforderung</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts
```

<br>
<b>Antwort</b>
<br>

> [!NOTE]
> Das hier gezeigte Antwortobjekt wird möglicherweise zur besseren Lesbarkeit verkürzt.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts",
    "@odata.count": 3,
    "@odata.nextLink": "https://graph.microsoft.com/beta/users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts?$skiptoken=MSMjMCMjMjAyMS0wOS0xNlQxMzo1OToyNy4xMjEwMzgzWg%3d%3d",
    "value": [
        {
            "id": "MSMjMCMjZDAwYWU3NjUtNmM2Yi00NjQxLTgwMWQtMTkzMmFmMjEzNzdh",
            "createdDateTime": "2021-09-17T06:09:24.8968037Z"
        },
        {
            "id": "MSMjMCMjMzAxNjNhYTctNWRmZi00MjM3LTg5MGQtNWJhYWZjZTZhNWYw",
            "createdDateTime": "2021-09-16T18:58:58.6760692Z"
        },
        {
            "id": "MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4",
            "createdDateTime": "2021-09-16T18:56:00.9038309Z"
        }        
    ]
}
```

</details>

### <a name="get-calltranscript"></a>CallTranscript abrufen

Ihre Anwendung durchsucht die Liste der Transkript-IDs, die sie als Antwort von der `List callTranscripts`-API erhält, um die gewünschte Transkript-ID zu ermitteln. Diese API wird verwendet, um einzelne Transkriptmetadaten auf der Grundlage der Benutzer-ID, der Besprechungs-ID und der Transkript-ID zu erhalten.

**HTTP-Anforderung**

```http
GET me/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')
GET users('{userId}')/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')
```

**Anforderungsheader**

| Kopfzeile       | Wert |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

**Anforderungstext**

Geben Sie keinen Anforderungstext für diese Methode an.

**Antwort**

Wenn die Methode erfolgreich ist, werden ein `200 OK` Antwortcode und ein `callTranscript` Objekt im Antworttext zurückgegeben.

<br>
<details>
<summary><b>Beispiel: Abrufen eines callTranscript</b></summary>
<br>
<b>Anforderung</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4
```

<br>
<b>Antwort</b>
<br>

> [!NOTE]
> Das hier gezeigte Antwortobjekt wird möglicherweise zur besseren Lesbarkeit verkürzt.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('ba321e0d-79ee-478d-8e28-85a19507f456')/onlineMeetings('MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ')/transcripts/$entity",
    "id": "MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4",
    "createdDateTime": "2021-09-17T06:09:24.8968037Z"
}
```

</details>

### <a name="get-calltranscript-content"></a>Abrufen von callTranscript-Inhalten

Diese API wird verwendet, um das Transkript der ausgewählten Transkript-ID abzurufen, die in der Antwort der `Get callTranscript` API erhalten wurde. Sie gibt den Inhalt des Transkripts zurück.

**HTTP-Anforderung**

```http
GET me/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')/content
GET users('{userId}')/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')/content
```

**Optionale Abfrageparameter**

Diese Methode unterstützt den `$format` [OData-Abfrageparameter](/graph/query-parameters), der die Anpassung von Antworten ermöglicht.

Die unterstützten Formattypen sind`text/vtt`für das VTT- ODER`application/vnd.openxmlformats-officedocument.wordprocessingml.document`für das DOCX-Format.

**Anforderungsheader**

| Kopfzeile       | Wert |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |
| Annehmen  | text/vtt ODER application/vnd.openxmlformats-officedocument.wordprocessingml.document. Optional.  |

**Anforderungstext**

Geben Sie keinen Anforderungstext für diese Methode an.

**Antwort**

Bei erfolgreicher Ausführung gibt diese Methode einen `200 OK` Antwortcode zurück und enthält Bytes für das callTranscript-Objekt im Antworttext. Der `content-type` Header gibt den Typ des Transkriptinhalts an.

**Beispiele**
<br>
<details>
<summary><b>Beispiel: Abrufen eines callTranscript-Inhalts</b></summary>
<br>
<b>Anforderung</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
```

<br>
<b>Antwort</b>
<br>

Die Antwort enthält Bytes für das Transkript im Text. Der `content-type` Header gibt den Typ des Transkriptinhalts an.

> [!NOTE]
> Das hier gezeigte Antwortobjekt wird möglicherweise zur besseren Lesbarkeit verkürzt.

```http
HTTP/1.1 200 OK
Content-type: text/vtt

WEBVTT
    
0:0:0.0 --> 0:0:5.320
<v User Name>This is a transcript test.</v>
```

</details>
<br>
<details>
<summary><b> Beispiel: Abrufen eines callTranscript-Inhalts unter Angabe des Abfrageparameters $format</b></summary>
<br>
<b>Anforderung</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content?$format=text/vtt
 ```

<br>
<b>Antwort</b>
<br>

Die Antwort enthält Bytes für das Transkript im Text. Der `content-type` Header gibt den Typ des Transkriptinhalts an.

> [!NOTE]
> Das hier gezeigte Antwortobjekt wird möglicherweise zur besseren Lesbarkeit verkürzt.

```http
HTTP/1.1 200 OK
Content-type: text/vtt
    
WEBVTT
    
0:0:0.0 --> 0:0:5.320
<v User Name>This is a transcript test.</v>
```

</details>
<br>
<details>
<summary><b>Beispiel: Abrufen eines callTranscript-Inhalts, der den Accept-Header angibt</b></summary>
<br>
<b>Anforderung</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content
Accept: application/vnd.openxmlformats-officedocument.wordprocessingml.document
```

<br>
<b>Antwort</b>
<br>

Die Antwort enthält Bytes für das Transkript im Text. Der `content-Type` Header gibt den Typ des Transkriptinhalts an.

> [!NOTE]
> Das hier gezeigte Antwortobjekt wird möglicherweise zur besseren Lesbarkeit verkürzt.

```http
HTTP/1.1 200 OK
Content-type: application/vnd.openxmlformats-officedocument.wordprocessingml.document
    
0:0:0.0 --> 0:0:5.320
User Name
This is a transcript test.
```

</details>
<br>
<details>
<summary><b> Beispiel: Abrufen eines callTranscript-Inhalts mit $format mit Vorrang vor dem Accept-Header</b></summary>
<br>
<b>Anforderung</b>
<br>

```http
GET https://graph.microsoft.com/beta/users/ba321e0d-79ee-478d-8e28-85a19507f456/onlineMeetings/MSo1N2Y5ZGFjYy03MWJmLTQ3NDMtYjQxMy01M2EdFGkdRWHJlQ/transcripts/MSMjMCMjNzU3ODc2ZDYtOTcwMi00MDhkLWFkNDItOTE2ZDNmZjkwZGY4/content?$format=text/vtt
Accept: application/vnd.openxmlformats-officedocument.wordprocessingml.document
```

<br>
<b>Antwort</b>
<br>

Die Antwort enthält Bytes für das Transkript im Text. Der `content-Type` Header gibt den Typ des Transkriptinhalts an.

> [!NOTE]
> Das hier gezeigte Antwortobjekt wird möglicherweise zur besseren Lesbarkeit verkürzt.

```http
HTTP/1.1 200 OK
Content-type: text/vtt
    
WEBVTT
   
0:0:0.0 --> 0:0:5.320
<v User Name>This is a transcript test.</v>
```

</details>

