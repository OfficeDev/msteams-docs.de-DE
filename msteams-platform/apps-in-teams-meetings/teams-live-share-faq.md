---
title: Live Share – FAQ
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über häufig gestellte Fragen zu Live Share.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 7cea66e58461814e3b2cd3be85e979b7a5b75c4b
ms.sourcegitcommit: 0fa0bc081da05b2a241fd8054488d9fd0104e17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68552511"
---
---

# <a name="live-share-sdk-faq"></a>Live Share SDK – FAQ

Erhalten Sie Antworten auf häufig gestellte Fragen, wenn Sie Live Share verwenden.<br>

<br>

<details>

<summary><b>Kann ich meinen eigenen Azure Fluid Relay-Dienst verwenden?</b></summary>

Ja! Beim Initialisieren der Live-Freigabe können Sie Eigenes `AzureConnectionConfig`definieren. Live Share ordnet Containern zu, die Sie mit Besprechungen erstellen, aber Sie müssen die Schnittstelle zum Signieren von `ITokenProvider` Token für Ihre Container implementieren. Sie können z. B. eine bereitgestellte `AzureFunctionTokenProvider`Funktion verwenden, die eine Azure-Cloudfunktion verwendet, um ein Zugriffstoken von einem Server anzufordern.

Obwohl es für die meisten von Ihnen von Vorteil ist, unseren kostenlos gehosteten Dienst zu verwenden, kann es immer noch Vorkommen geben, in denen es von Vorteil ist, Ihren eigenen Azure Fluid Relay-Dienst für Ihre Live Share-App zu verwenden. Erwägen Sie die Verwendung einer benutzerdefinierten AFR-Dienstverbindung, wenn Sie:

* Speicherung von Daten in Fluid-Containern über die Lebensdauer einer Besprechung hinaus erforderlich.
* Übertragen vertraulicher Daten über den Dienst, der eine benutzerdefinierte Sicherheitsrichtlinie erfordert.
* Entwickeln Sie Features beispielsweise `SharedMap`über Fluid Framework für Ihre Anwendung außerhalb von Teams.

Weitere [Informationen finden Sie](./teams-live-share-how-to/how-to-custom-azure-fluid-relay.md) in der [Azure Fluid Relay-Dokumentation](/azure/azure-fluid-relay/).

<br>

</details>

<details>

<summary><b>Wie lange sind Daten, die im gehosteten Dienst von Live Share gespeichert sind, zugänglich?</b></summary>

Alle Daten, die mittels Fluid-Container gesendet oder gespeichert wurden, die von dem von Live Share gehosteten Azure Fluid Relay-Dienst erstellt wurden, sind für 24 Stunden zugänglich. Wenn Sie Daten länger als 24 Stunden speichern möchten, können Sie unseren gehosteten Azure Fluid Relay-Dienst durch Ihren eigenen ersetzen. Alternativ können Sie Ihren eigenen Speicheranbieter parallel zum gehosteten Dienst von Live Share verwenden.

<br>

</details>

<details>

<summary><b>Welche Besprechungstypen werden von Live Share unterstützt?</b></summary>

Geplante Besprechungen, Einzelanrufe, Gruppenanrufe und Besprechungen werden jetzt unterstützt. Kanalbesprechungen werden noch nicht unterstützt.

<br>

</details>

<details>

<summary><b>Funktioniert das Medienpaket von Live Share mit DRM-Inhalten?</b></summary>

Nein. Teams unterstützt derzeit keine verschlüsselten Medien für Registerkartenanwendungen auf dem Desktop. Chrome-, Edge- und mobile Clients werden unterstützt. Weitere Informationen finden Sie [hier](https://github.com/microsoft/live-share-sdk/issues/14).

<br>

</details>

<details>
<summary><b>Wie viele Personen können an einer Live Share-Sitzung teilnehmen?</b></summary>

Derzeit unterstützt Live Share maximal 100 Teilnehmer pro Sitzung. Wenn Sie daran interessiert sind, können Sie [hier eine Diskussion beginnen](https://github.com/microsoft/live-share-sdk/discussions).

<br>

</details>

<details>
<summary><b>Kann ich die Datenstrukturen von Live Share außerhalb von Teams verwenden?</b></summary>

Derzeit ist für Live-Freigabepakete das Teams Client SDK erforderlich, damit es ordnungsgemäß funktioniert. Features in `@microsoft/live-share` oder `@microsoft/live-share-media` funktionieren nicht außerhalb von Microsoft Teams. Wenn Sie daran interessiert sind, können Sie [hier eine Diskussion beginnen](https://github.com/microsoft/live-share-sdk/discussions).

<br>

</details>

<details>
<summary><b>Kann ich mehrere Fluid-Container verwenden?</b></summary>

Derzeit unterstützt Live Share nur einen Container mit unserem bereitgestellten Azure Fluid Relay-Dienst. Es ist jedoch möglich, sowohl einen Live Share-Container als auch einen Container zu verwenden, der von Ihrer eigenen Azure Fluid Relay-Instanz erstellt wurde.

<br>

</details>

<details>
<summary><b>Kann ich mein Fluid-Containerschema nach dem Erstellen des Containers ändern?</b></summary>

Derzeit unterstützt Live Share das Hinzufügen neuer Elemente `initialObjects` zu Fluid `ContainerSchema` nach dem Erstellen oder Verknüpfen eines Containers nicht. Da Live Share-Sitzungen kurzlebig sind, ist dies am häufigsten ein Problem während der Entwicklung, nachdem Sie Ihrer App neue Features hinzugefügt haben.

> [!NOTE]
> Wenn Sie die `dynamicObjectTypes` Eigenschaft in der `ContainerSchema`verwenden, können Sie jederzeit neue Typen hinzufügen. Wenn Sie später Typen aus dem Schema entfernen, schlagen vorhandene DDS-Instanzen dieser Typen ordnungsgemäß fehl.

Um Fehler zu beheben, die sich aus Änderungen am `initialObjects` lokalen Testen in Ihrem Browser ergeben, entfernen Sie die Container-ID mit Hash von Ihrer URL, und laden Sie die Seite neu. Wenn Sie in einer Teams-Besprechung testen, starten Sie eine neue Besprechung, und versuchen Sie es erneut.

Wenn Sie planen, Ihre App mit neuen `SharedObject` oder `LiveObject` häufigen Instanzen zu aktualisieren, sollten Sie überlegen, wie Sie neue Schemaänderungen in der Produktion bereitstellen. Obwohl das tatsächliche Risiko relativ gering und kurz anhaltend ist, kann es zu dem Zeitpunkt, zu dem Sie die Änderung bereitstellen, aktive Sitzungen geben. Vorhandene Benutzer in der Sitzung sollten nicht beeinträchtigt werden, aber Benutzer, die dieser Sitzung beitreten, nachdem Sie eine grundlegende Änderung bereitgestellt haben, können Probleme beim Herstellen der Verbindung mit der Sitzung haben. Um dies zu entschärfen, können Sie einige der folgenden Lösungen in Betracht ziehen:

* Stellen Sie Schemaänderungen für Ihre Webanwendung außerhalb der normalen Geschäftszeiten bereit.
* Verwenden Sie `dynamicObjectTypes` dies für alle Änderungen, die an Ihrem Schema vorgenommen wurden, anstatt sie zu ändern `initialObjects`.

> [!NOTE]
> Live Share unterstützt derzeit weder die Versionsverwaltung Ihrer `ContainerSchema`App noch apIs, die für Migrationen vorgesehen sind.

<br>

</details>

<details>
<summary><b>Gibt es Einschränkungen für die Anzahl der Änderungsereignisse, die ich über Live Share ausgeben kann?</b></summary>

Während sich die Livefreigabe in der Vorschau befindet, wird kein Grenzwert für Ereignisse erzwungen, die über Live Share ausgegeben werden. Um eine optimale Leistung zu erzielen, müssen Sie Änderungen, die durch `SharedObject` instanzen ausgegeben werden, `LiveObject` auf eine Nachricht pro 50 Millisekunden oder mehr entprellen. Dies ist besonders wichtig, wenn Änderungen basierend auf Maus- oder Touchkoordinaten gesendet werden, z. B. beim Synchronisieren von Cursorpositionen, Beim Freihandzeichnen und Ziehen von Objekten um eine Seite.

<br>

</details>

## <a name="have-more-questions-or-feedback"></a>Haben Sie weitere Fragen oder Feedback?

Melden Sie Probleme, und senden Sie Featureanforderungen an das SDK-Repository für [Live Share SDK](https://github.com/microsoft/live-share-sdk). Verwenden Sie das `live-share` und `microsoft-teams`-Tag, um Fragen zum SDK bei [Stack Overflow](https://stackoverflow.com/questions/tagged/live-share+microsoft-teams) zu posten.

## <a name="see-also"></a>Siehe auch

* [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
* [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
