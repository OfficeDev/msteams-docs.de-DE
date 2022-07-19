---
title: Häufig gestellte Fragen zu Moodle
description: In diesem Artikel erhalten Sie Antworten auf einige häufig gestellte Fragen zum Verwenden von Moodle LMS.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: Surbhigupta
ms.openlocfilehash: 02c6a5086bd2132b43f3e36b85bb63c67c7b0d26
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66842010"
---
# <a name="moodle-faq"></a>Häufig gestellte Fragen zu Moodle

Erhalten Sie Antworten auf einige Ihrer Abfragen, wenn Sie Moodle LMS verwenden.<br>

<br>

<details>

<summary><b>Was soll ich tun, wenn mindestens ein Kursteam nach der Synchronisierung nicht erstellt wurde?</b></summary>

Jeder Moodle-Kurs muss über mindestens eine Lehrkraft und einen Kursteilnehmer verfügen, der mit einem Microsoft 365 AAD UPN-Konto übereinstimmt. Das Team kann nicht erstellt werden, wenn die Synchronisierung keine Übereinstimmung findet.

Jede Teamkursinstanz muss über einen Besitzer verfügen, und durch die Synchronisierung wird die Lehrkraft als Besitzer festgelegt, wobei davon ausgegangen wird, dass die Lehrkraft über eine Teams-Lizenz verfügt.

<br>

</details>

<details>

<summary><b>Was sollten wir tun, um die Moodle-Anmeldeseite zu entfernen, wenn wir in Teams arbeiten? Können wir einmaliges Anmelden (Single Sign-On, SSO) erzwingen?</b></summary>

Die Benutzer verfügen über mehrere Anmeldeoptionen auf der Moodle-Anmeldeseite.

* Um sich ausschließlich mit Microsoft 365 Anmeldeinformationen anzumelden, aktivieren Sie die Konfigurationseinstellungen **Umleitung erzwingen** für das **auth_oidc-Plug-In**. Wenn der Dienst aktiviert ist, wird dem Benutzer die Microsoft-Anmeldeseite angezeigt.
* Informationen zum manuellen Anmelden beim Moodle-Portal finden Sie unter [Moodle](https://moodle.org/login/index.php).

<br>

</details>

<details>

<summary><b>Wie kann ich angeben, welche Benutzer synchronisiert werden sollen? Ich möchte nicht, dass alle Azure AD Benutzer mit der Moodle-Website synchronisiert werden. </b></summary>

Verwenden Sie die Option **Einschränkung der Benutzererstellung**, um die Benutzer anzugeben, indem Sie die Konfigurationsoptionen des **local_o365** -Plug-Ins synchronisieren. Das Dropdownmenü links neben dem **Filter** bietet Optionen wie Land, Firmenname und Sprache an.

> [!TIP]
> Erstellen Sie eine dynamische Microsoft 365 Gruppe, um die **Filter**-Option mit mehreren Profileigenschaften zu aktivieren.

Die folgende Abbildung zeigt Optionen für Einschränkungen bei der Benutzererstellung:

:::image type="content" source="../assets/images/MoodleInstructions/faq-2.png" alt-text="sync":::

:::image type="content" source="../assets/images/MoodleInstructions/faq-3.png" alt-text="Azure AD":::

<br>

</details>

<details>

<summary><b>Wir möchten, dass unsere Lehrpersonal Kurse mit Teams synchronisieren kann? Sind Moodle-Administratoren die einzigen, die die Synchronisierung von Kursen steuern können?</b></summary>

Standardmäßig können nur Moodle-Administratoren die Synchronisierung konfigurieren. Der Teambesitzer kann steuern, ob ein Kurs mit Teams synchronisiert wird, und ob **"Konfigurieren der Kurssynchronisierung im Kurs zulassen"** aktiviert ist. In diesem Fall ist der Teambesitzer das Lehrpersonal. Der Block zeigt die Konfigurationsoption für Personen mit den entsprechenden Besitzerberechtigungen an.

<!-- For more information, see Microsoft 365 block within the Moodle course interface. -->

Die folgende Abbildung zeigt die Option **Konfigurieren der Kurssynchronisierung im Kurs zulassen**:

:::image type="content" source="../assets/images/MoodleInstructions/faq-4.png" alt-text="Admin":::

Die folgende Abbildung zeigt die Synchronisierung von Kursen:

:::image type="content" source="../assets/images/MoodleInstructions/faq-5.png" alt-text="Synchronisierung":::

<br>

</details>

<details>

<summary><b>Wir haben die Dokumentation befolgt, aber die Benutzerkonten können AAD und Moodle nicht synchronisieren. Was sollten wir tun?</b></summary>

Das Problem kann behoben werden, bevor Benutzer die **Löschtokenbereinigung** als letzten Problembehandlungsschritt ausführen.

Die folgende Tabelle enthält die Aktionen und Abhängigkeiten, die ausgeführt und überprüft werden sollen:

| Abhängigkeit  | Aktion | Referenz|
|-------|------------|----------|
| Stabile Version| Stellen Sie sicher, dass die Version von Moodle als **stabil** aufgeführt ist.| Weitere Informationen finden Sie unter [Version-Unterstützung](https://docs.moodle.org/dev/Releases#Version_support).|
|Berechtigungen| Stellen Sie sicher, dass die Azure-Anwendung über die erforderlichen Berechtigungen zum Ausführen der Synchronisierung verfügt.| Weitere Informationen finden Sie unter [Microsoft-Berechtigungen](https://docs.moodle.org/311/en/Microsoft_365#Permissions).|
| Vollständige Synchronisierung| Vergewissern Sie sich, dass **Erfüllen einer vollständigen Synchronisierung bei jeder Ausführung** aktiviert ist, und überprüfen Sie die **Taskprotokolle** für **Synchronisierung von Benutzern mit Azure AD**.| Weitere Informationen finden Sie unter [Aktivieren der vollständigen Synchronisierung](https://docs.moodle.org/311/en/local_o365)</br>Weitere Informationen finden Sie unter [Überprüfen von Aufgabenprotokollen](https://docs.moodle.org/311/en/local_o365#Sync_users_with_Azure_AD). |
|Tokenaktualisierung|Bereinigen Sie das **Deltatoken für die Benutzersynchronisierung** im local_o365-Plug-In.| Weitere Informationen finden Sie unter [Tokenaktualisierung](https://docs.moodle.org/38/en/Office365).|
<!-- |Tokenaktualisierung|Bereinigen des **Deltatokens für die Benutzersynchronisierung** im local_o365-Plug-In| {moodle_url}\local_o365\acp.php?Mode=maintenance_cleandeltatoken| -->
<br>

</details>

<details>

<summary><b>Ein oder mehrere Benutzer können sich nicht mit ihren Microsoft 365 Anmeldeinformationen anmelden, obwohl sich die meisten Benutzer ohne Problem anmelden können. Was ist die Ursache für diese Inkonsistenz?</b></summary>

Die Ursache für Inkonsistenzen bei Benutzern, die sich nicht mit ihren Microsoft 365 Anmeldeinformationen anmelden können, kann mit dem Benutzerzuordnungsvorgang während der Synchronisierung zusammenhängen. Führen Sie die folgenden Schritte aus, um das Problem zu beheben:

* Überprüfen Sie, ob der Moodle-Benutzerauthentifizierungstyp **OpenID** ist.
* Überprüfen Sie, ob der Moodle-**Benutzername** mit dem AAD-Benutzernamen übereinstimmt.
* Bereinigen Sie die **Token-Problem** und versuchen Sie es noch mal.
* Überprüfen Sie, ob die Benutzer **Berechtigungen** haben, um auf die Azure-Anwendung zuzugreifen.

<br>

</details>

<details>

<summary><b>Alle Benutzer können sich nicht mit ihren Microsoft 365 Anmeldeinformationen anmelden. Was können wir tun, um dieses Problem zu beheben?</b></summary>

Benutzer, die sich zu Beginn nicht anmelden konnten, müssen das Problem melden und verifizieren, dass der **geheime Clientschlüssel** der Anwendung nicht abgelaufen ist.

Die folgende Abbildung zeigt die Fehlermeldung, die beim Anmelden des Benutzers mithilfe seiner Microsoft 365 Anmeldeinformationen empfangen wurde:

:::image type="content" source="../assets/images/MoodleInstructions/faq-6.png" alt-text="Problem melden":::

Die folgende Abbildung zeigt den Fehler im Azure-Portal:

:::image type="content" source="../assets/images/MoodleInstructions/faq-7.png" alt-text="Azure-Portal":::

Wenn der **Geheime Clientschlüssel** abgelaufen ist, muss der Benutzer einen neuen **Geheimen Clientschlüssel** generieren und die auf der Seite gefundene Konfiguration aktualisieren. Benutzer können sich erneut anmelden, nachdem der **Geheime Clientschlüssel** aktualisiert wurde. Die erneute Bereitstellung kann bis zu 24 Stunden dauern.

<br>

</details>

<details>

<summary><b>Ändern der Teams-Instanz, die mit einem Kurs verknüpft ist?</b></summary>

Administratoren können die einem Kurs zugeordnete Teams-Instanz über die Seite **Teams-Verbindungen verwalten** ändern. Wählen Sie **Verbinden** neben dem Kurs aus, der geändert werden soll, und wählen Sie die Teams-Instanz aus. Wenn Sie die Kurszurücksetzung verwenden, um ein Team zu archivieren, können Sie es mit dem vorherigen Team verknüpfen.

Die folgende Abbildung zeigt die Teams-Instanz:

:::image type="content" source="../assets/images/MoodleInstructions/faq-8.png" alt-text="Teams-Instanz":::

<br>

</details>

<details>

<summary><b>Warum wird die Atto Teams-Besprechungsintegration nicht im Atto-Editor angezeigt?</b></summary>

Der Benutzer kann mit einem Atto Teams-Besprechungsproblem konfrontiert werden, wenn der Symbolverweis in der **Symbolleistenkonfiguration** fehlt, die das Teams-Symbol im Atto-Editor anzeigt. Der Benutzer muss das Teams-Besprechungssymbol rechts neben dem Linksymbol hinzufügen, indem er die folgenden Schritte ausführt:

* Installieren Sie das Plug-In.
* Aktualisieren Sie **Symbolleistenkonfiguration** mit **Teams-Besprechungen**.

Die folgenden Abbildungen zeigen das Symbol "Symbolleiste" nach der Anpassung der Symbolleistenkonfiguration:

:::image type="content" source="../assets/images/MoodleInstructions/faq-9.png" alt-text="Symbolleiste":::

:::image type="content" source="../assets/images/MoodleInstructions/faq-10.png" alt-text="Links-Symbol":::

Weitere Informationen zum Bearbeiten der Atto-Symbolleiste finden Sie unter:

* [Atto Editor-ModdleDocs](https://docs.moodle.org/311/en/Atto_editor)
* [Atto-Editor-Symbolzuordnung](https://docs.moodle.org/311/en/Atto_editor#:~:text=in%20the%20editor.-,Atto%20editor%20toolbar,-Atto%20Row%201)
<br>

</details>

<details>

<summary><b>Werden die über die Microsoft-Integration geplanten Besprechungen in Outlook oder in Teams-Kalendern angezeigt? Wie lautet die Standardzeitachse für die Besprechungen, die angezeigt werden sollen?</b></summary>

Die über die App geplanten Besprechungen werden nicht im Outlook- oder Teams-Kalender des Planers angezeigt, da sie Kanalbesprechungen ähneln. Alle Mitglieder im Kurskanal können direkt über den eingebetteten Kanallink an der Besprechung teilnehmen. Weitere Informationen finden Sie unter [Kanalbesprechungen](https://www.knowledgewave.com/blog/benefits-of-channel-meetings-in-microsoft-teams).

Sie können jedoch auf die Einladung zugreifen und den Feldern **Erforderlich** oder **Optional** der Besprechungseinladung manuell Teilnehmernamen hinzufügen, um die Remotebesprechung in ihren Kalendern anzuzeigen. Die Standardzeitachsen basieren auf dem Datum, an dem der Benutzer angibt, wann die Besprechung erstellt wird. Weitere Informationen finden Sie unter [Grenzwerte und Spezifikationen für Teams](/microsoftteams/limits-specifications-teams).

<br>

</details>

<details>

<summary><b>Gibt es eine Supportwebsite, auf der wir weitere Hilfe zu Produkten und anderen Problemen erhalten können?</b></summary>

Support und Hilfe zu Produkt- und Dienstproblemen oder Hilfe zur Entwicklercommunity finden Sie unter [Support und Feedback](/microsoftteams/platform/feedback).
