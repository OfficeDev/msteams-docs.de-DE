---
title: Live Share – FAQ
description: In diesem Modul erfahren Sie mehr über häufig gestellte Fragen zu Live Share.
ms.topic: overview
ms.localizationpriority: high
ms.author: v-ypalikila
ms.openlocfilehash: 0c51d88ba08dea50e23b0b8eb451f84557f1f867
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189297"
---
---

# <a name="live-share-sdk-faq"></a>Live Share SDK – FAQ

Erhalten Sie Antworten auf häufig gestellte Fragen, wenn Sie Live Share verwenden.<br>

<br>

<details>

<summary><b>Kann ich meinen eigenen Azure Fluid Relay-Dienst verwenden?</b></summary>

Ja. Beim Erstellen der `TeamsFluidClient` Klasse können Sie eigene `AzureConnectionConfig`definieren. Live Share ordnet Container, die Sie erstellen, Besprechungen zu, aber Sie müssen Ihr eigenes Azure `ITokenProvider` erstellen, um Token für Ihre Container und regionale Anforderungen zu signieren. Weitere Informationen finden Sie in der Azure [Fluid Relay-Dokumentation](/azure/azure-fluid-relay/).

<br>

</details>

<details>

<summary><b>Wie lange sind Daten, die im gehosteten Dienst von Live Share gespeichert sind, zugänglich?</b></summary>

Alle Daten, die mittels Fluid-Container gesendet oder gespeichert wurden, die von dem von Live Share gehosteten Azure Fluid Relay-Dienst erstellt wurden, sind für 24 Stunden zugänglich. Wenn Sie Daten länger als 24 Stunden speichern möchten, können Sie unseren gehosteten Azure Fluid Relay-Dienst durch Ihren eigenen ersetzen. Alternativ können Sie Ihren eigenen Speicheranbieter parallel zum gehosteten Dienst von Live Share verwenden.

<br>

</details>

<details>

<summary><b>Welche Besprechungstypen werden von Live Share unterstützt?</b></summary>

Derzeit werden nur geplante Besprechungen unterstützt, und alle Teilnehmer müssen sich im Besprechungskalender befinden. Besprechungstypen wie 1:1-Anrufe, Gruppenanrufe und Besprechungen werden nicht unterstützt.

<br>

</details>

<details>

<summary><b>Funktioniert das Medienpaket von Live Share mit DRM-Inhalten?</b></summary>

Nein. Teams unterstützt derzeit keine verschlüsselten Medien für Registerkartenanwendungen.

<br>

</details>

<details>
<summary><b>Wie viele Personen können an einer Live Share-Sitzung teilnehmen?</b></summary>

Derzeit unterstützt Live Share maximal 100 Teilnehmer pro Sitzung.

<br>

</details>

## <a name="have-more-questions-or-feedback"></a>Haben Sie weitere Fragen oder Feedback?

Melden Sie Probleme, und senden Sie Featureanforderungen an das SDK-Repository für [Live Share SDK](https://github.com/microsoft/live-share-sdk). Verwenden Sie das `live-share` und `microsoft-teams`-Tag, um Fragen zum SDK bei [Stack Overflow](https://stackoverflow.com/questions/tagged/live-share+microsoft-teams) zu posten.

## <a name="see-also"></a>Siehe auch

- [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
- [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
- [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
- [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
