---
title: App-Konfiguration im Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams
keywords: Erste Schritte für Entwicklerportalteams
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: ce290bd7daa46467be279aae7c608321e75e2d57
ms.sourcegitcommit: d972953994e405c6afc42e4d4a76b48c6d4cfb5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52635113"
---
# <a name="app-configuration"></a>App-Konfiguration

Der wichtigste Teil eines Microsoft Teams-App-Pakets ist die manifest.jsDatei. Diese Datei muss dem Teams [-App-Schema entsprechen.](~/resources/schema/manifest-schema.md) Die manifest.json-Datei enthält Metadaten, mit denen Teams Benutzer Ihre App korrekt präsentieren können.

Sie können die folgenden Aktionen im **Abschnitt Konfigurieren** des Entwicklerportals ausführen:

* Erstellen Sie einfach ein App-Paket.
* Beschreiben Sie die App.
* Hochladen Ihre Symbole.
* Erstellen Sie .zip Datei für eine einfache Verteilung.

> [!NOTE]
> Das Entwicklerportal erzeugt keinen funktionstüchtigen Code für Ihre App oder hosten Sie Ihre App. Ihre App muss bereits unter der im Manifest angegebenen URL gehostet und ausgeführt werden, damit der App-Upload-Vorgang zu einer funktionierenden App führt.

:::image type="content" source="~/assets/images/tdp/tdp_configure_1.png" alt-text="Screenshot mit der Seite Konfigurieren des Teams Entwicklerportals.":::

## <a name="basic-information-and-branding"></a>Grundlegende Informationen und Branding

Die **Abschnitte Grundlegende Informationen** und **Branding** definieren die allgemeine Beschreibung der App, die Sie erstellen. Dies umfasst den Namen, die Beschreibung und das visuelle Branding der App. Die Informationen in diesem Abschnitt werden im Teams-Store-Eintrag und im Dialog zur App-Installation verwendet.

## <a name="capabilities"></a>Funktionen

Im **Abschnitt** Funktionen von Configuration sind die Funktionen der App aufgeführt.

> [!NOTE]
> Die App-Anpassungsfunktion ist derzeit nur in der Entwicklervorschau verfügbar.
> 
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)

Im Folgenden finden Sie die folgenden Funktionen:

:::image type="content" source="~/assets/images/tdp/tdp_capabilities.png" alt-text="Screenshot mit der Seite Konfigurieren des Teams Entwicklerportals.":::

* **Persönliche App** 

  In diesem Abschnitt können Sie eine Reihe von Registerkarten definieren, die standardmäßig in der persönlichen App-Benutzeroberfläche angezeigt werden, d. h. die Erfahrung, die ein Benutzer mit Ihrer App außerhalb des Kontexts eines Teams oder Kanals hat. Geben Sie in diesem Abschnitt die folgenden Details an:

  * Der Registerkartenname.
  * Ein eindeutiger Bezeichner.
  * Die URL, die auf die benutzeroberfläche verweist, die in der Teams.
  * Die URL, die verwendet werden soll, wenn ein Benutzer die Registerkarte in einem Browser anzeigen will. Dies ist eine optionale Information.
  * Alle zusätzlichen Domänen, von denen die Registerkarte erwartet, dass sie geladen werden oder mit denen sie eine Verknüpfung dazu hat.

* **Gruppen- und Kanal-App**

  Eine Teams wird Teil eines Kanals und bietet schnellen Zugriff auf Teaminformationen und Ressourcen. Beispielsweise enthält die Registerkarte Planner für einen Kanal einen einzelnen Plan, die Registerkarte Power BI einem bestimmten Bericht. Benutzer können einen Drilldown zum relevanten Kontext durchführen, sollten jedoch nicht in der Lage sein, außerhalb der Registerkarte zu navigieren. Auf der Registerkarte Power BI wird beispielsweise nicht die Navigation zu anderen Power BI-Berichten aktiviert, sondern die Schaltfläche **Zur Website wechseln**, mit welcher der Bericht auf der Power BI-Hauptwebsite gestartet wird.

    > [!NOTE]
    > Für Teamregisterkarten müssen Sie eine Konfigurations-URL angeben, um Optionen anzuzeigen und Informationen zu sammeln, die Ihnen helfen, den Inhalt und die Benutzererfahrung Ihrer Registerkarte anzupassen. Diese iframed-HTML-Seite wird angezeigt, wenn ein Benutzer die Registerkarte zum ersten Mal zu einem Kanal hinzufügt.
    > Sie müssen auch alle zusätzlichen Domänen angeben, von denen die Registerkarte erwartet, dass sie geladen werden oder mit denen sie verlinkt wird.

* **Bot**

  In diesem Abschnitt können Sie Ihrer App einen [Unterhaltungs-Bot](~/bots/what-are-bots.md) hinzufügen. Wenn Sie bereits einen Bot bei Bot Framework registriert haben, können Sie diesen Bot hinzufügen, indem Sie auf **Einrichten** klicken, den Bot-Namen und die Bot Framework-ID angeben und die Bereiche definieren, in denen der Bot arbeiten soll.

  Wenn Sie den Bot noch nicht beim Bot Framework registriert haben, klicken Sie **auf Registrieren,** um einen neuen zu erstellen. Nachdem Sie den Bot registriert haben, gehen Sie zurück zu diesem Abschnitt des Manifest-Editors, um seinen Namen und die Bot Framework-ID ein eingeben.

  Nachdem Sie die Informationen Ihres Bots bereitgestellt haben, können Sie nun optional eine Liste von Befehlen definieren, die Ihr Bot Benutzern vorschlagen kann. Fügen Sie den Befehlsnamen, eine Befehlsbeschreibung mit Angaben zu dessen Syntax und Argumenten sowie die Bereiche hinzu, für die dieser Befehl gelten soll.

  Beachten Sie, dass Befehle, die für den nicht unterstützten Bereich angegeben wurden, ignoriert werden, wenn Sie Ihren Bot so definiert haben, dass er nur einen Bereich unterstützt. Sie können die vom Bot unterstützten Bereiche jederzeit bearbeiten.

* **Connector**

  In diesem Abschnitt können Sie Ihrer App einen Connector hinzufügen. Wenn Sie bereits einen Office 365 registriert haben, wählen Sie **Einrichten** aus, und geben Sie den Namen und die ID des Connectors ein. Wenn Sie einen neuen Konnektor möchten, klicken Sie auf **Registrieren**, um zum Connector Developer Dashboard in Ihrem Browser zu gelangen.

  > [!NOTE]
  > Mithilfe der App-Anpassung können Administratoren das Aussehen und Die-Gefühl der Apps ändern, die über Bots, Messagingerweiterungen, Registerkarten und Connectors geladen werden. Wenn der Administrator Teams den Namen einer App von in anpasst, wird die App den Benutzern mit dem neuen `Contoso` `Contoso Agent` Namen `Contoso Agent` angezeigt. Beim Hinzufügen eines Connectors zu einem Chat wird in der Liste jedoch weiterhin der Name der App als `Contoso` angezeigt.

* **Messaging-Erweiterungen**

  [Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) bieten Benutzern eine leistungsstarke Möglichkeit, mit Ihrer App in Microsoft Teams zu agieren. Benutzer können Informationen von Ihrem Dienst abfragen und diese Informationen in Form von Karten direkt im Kanal oder in der Chat-Unterhaltung veröffentlichen.

  Messaging-Erweiterungen werden von Bot Framework-Bots unterstützt, sodass für den Betrieb ein konfigurierter Bot erforderlich ist. Wenn über Sie den Namen und die Bot Framework-ID des Bots verfügen, für den Sie die Messaging-Erweiterung aktivieren möchten, geben Sie ihn ein. Andernfalls klicken Sie auf *Registrieren*, um den Namen zu erstellen, und geben Sie anschließend die Informationen ein. Wählen Sie aus, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann.

  Nachdem Sie den zugrunde liegenden Bot konfiguriert haben, definieren Sie die Befehle und Parameter, die die Messagingerweiterung akzeptieren kann.

  Jeder Befehl erfordert einen Titel und eine ID. Der Befehl kann optional eine Beschreibung für den Benutzer enthalten. Jeder Befehl kann bis zu fünf Parameter unterstützen, für die jeweils Folgendes erforderlich ist:

  * Der Name des Parameters, wie er im Teams angezeigt wird und in der Benutzeranforderung enthalten ist.
  * Ein benutzerfreundlicher Titel.
  * Eine optionale Beschreibung.

  > [!NOTE]
  > Informationen zum Erstellen einer Messagingerweiterung mithilfe von App Studio finden Sie unter [Create messaging extension using app studio](~/resources/create-messaging-extension-using-appstudio.md).

* **Besprechungserweiterung**

  TODO: Rajesh R.

* **Szene**

  Szenen im gemeinsamen Modus ist ein Artefakt, das vom Szenenentwickler mithilfe des Microsoft Scene-Studio erstellt wurde, das Personen zusammen mit ihrem Videostream in einer vom Szenenersteller konzipierten kreativen Umgebung zusammen bringt. In einer konzipierten Szeneneinstellung verfügen die Teilnehmer über festgelegte Plätze mit Videostreams, die in diesen Sitzen gerendert werden. Weitere Informationen finden Sie unter [Teams Together Mode](~/apps-in-teams-meetings/teams-together-mode.md).

## <a name="permissions"></a>Berechtigungen

Sie können Ihre Teams mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort bereichern.

## <a name="languages"></a>Sprachen

Richten Sie die sprachen ein, die Ihre App unterstützt, oder ändern Sie sie.

## <a name="single-sign-on"></a>Einmaliges Anmelden

Konfigurieren Sie Ihre App für die Authentifizierung von Benutzern mit einmaligem Anmelden (Single Sign-On, SSO).

## <a name="domains"></a>Domänen

Eine Liste der gültigen Domänen für Websites, die die App im Client Teams wird. Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` . Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist nicht erforderlich, die Domänen der Identitätsanbieter, die Sie unterstützen möchten, in Ihre App zu verwenden. Um sich z. B. mithilfe einer Google-ID zu authentifizieren, müssen Sie an accounts.google.com umleiten, sie dürfen jedoch accounts.google.com in nicht `validDomains[]` enthalten.

Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter. Ist z. `yourapp.onmicrosoft.com` B. gültig, ist `*.onmicrosoft.com` jedoch ungültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="advanced"></a>Fortgeschritten
Todo von Karthig

### <a name="app-content"></a>App-Inhalt
Todo von Karthig

### <a name="first-party-settings"></a>First Party-Einstellungen
Todo von Karthig

## <a name="see-also"></a>Sehen Sie ebenfalls

* [Übersicht über Teams Developer Portal](~/concepts/build-and-test/teams-developer-portal.md)
* [Verteilen Teams Entwicklerportal](~/concepts/tdp-distribute.md)
* [Tools in Teams Developer Portal](~/concepts/tdp-tools.md)