---
title: App-Konfiguration im Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams
keywords: Erste Schritte für Entwicklerportal-Teams
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: ce290bd7daa46467be279aae7c608321e75e2d57
ms.sourcegitcommit: 25539046d408c4270b988fd826d7cf1275f4b9dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2021
ms.locfileid: "52763135"
---
# <a name="app-configuration"></a>App-Konfiguration

Der wichtigste Teil eines Microsoft Teams App-Pakets ist die manifest.json-Datei. Diese Datei muss dem [Teams App-Schema](~/resources/schema/manifest-schema.md)entsprechen. Die manifest.json-Datei enthält Metadaten, mit denen Teams Ihre App den Benutzern korrekt präsentieren können.

Im Abschnitt **"Konfigurieren"** des Entwicklerportals können Sie die folgenden Aktionen ausführen:

* Erstellen Sie einfach ein App-Paket.
* Beschreiben Sie die App.
* Hochladen Ihrer Symbole.
* Erstellen Sie eine .zip-Datei für eine einfache Verteilung.

> [!NOTE]
> Das Entwicklerportal erstellt keinen funktionalen Code für Ihre App oder hosten Ihre App. Ihre App muss bereits unter der im Manifest angegebenen URL gehostet und ausgeführt werden, damit der App-Upload-Vorgang zu einer funktionierenden App führt.

:::image type="content" source="~/assets/images/tdp/tdp_configure_1.png" alt-text="Screenshot der Seite &quot;Konfigurieren&quot; des Teams Entwicklerportals.":::

## <a name="basic-information-and-branding"></a>Grundlegende Informationen und Branding

Die Abschnitte **"Grundlegende Informationen"** und **"Branding"** definieren die allgemeine Beschreibung der App, die Sie erstellen. Dies umfasst den Namen, die Beschreibung und das visuelle Branding der App. Die Informationen in diesem Abschnitt werden im Dialog Teams Store-Eintrags und der App-Installation Ihrer App verwendet.

## <a name="capabilities"></a>Funktionen

Im Abschnitt **"Funktionen"** der Konfiguration sind die Funktionen der App aufgeführt.

> [!NOTE]
> Die App-Anpassungsfunktion ist derzeit nur in der Entwicklervorschau verfügbar.
> 
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen können. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)

Nachfolgend sind die Funktionen dargestellt:

:::image type="content" source="~/assets/images/tdp/tdp_capabilities.png" alt-text="Screenshot der Seite &quot;Konfigurieren&quot; des Teams Entwicklerportals.":::

* **Persönliche App** 

  In diesem Abschnitt können Sie eine Gruppe von Registerkarten definieren, die standardmäßig in der persönlichen App-Oberfläche angezeigt werden, d. h. die Erfahrung, die ein Benutzer mit Ihrer App außerhalb des Kontexts eines Teams oder Kanals hat. Geben Sie in diesem Abschnitt die folgenden Details an:

  * Der Registerkartenname.
  * Ein eindeutiger Bezeichner.
  * Die URL, die auf die Benutzeroberfläche verweist, die in Teams angezeigt werden soll.
  * Die URL, die verwendet werden soll, wenn ein Benutzer die Registerkarte in einem Browser anzeigen möchte. Dies ist eine optionale Information.
  * Alle zusätzlichen Domänen, von denen die Registerkarte erwartet, dass sie geladen wird oder mit denen eine Verknüpfung hergestellt wird.

* **Gruppen- und Kanal-App**

  Eine Teams Registerkarte wird Teil eines Kanals und bietet schnellen Zugriff auf Teaminformationen und Ressourcen. Beispielsweise enthält die Registerkarte Planner für einen Kanal einen einzelnen Plan, die Registerkarte Power BI einem bestimmten Bericht zugeordnet ist. Benutzer können einen Drilldown zum relevanten Kontext durchführen, sollten jedoch nicht in der Lage sein, außerhalb der Registerkarte zu navigieren. Auf der Registerkarte Power BI wird beispielsweise nicht die Navigation zu anderen Power BI-Berichten aktiviert, sondern die Schaltfläche **Zur Website wechseln**, mit welcher der Bericht auf der Power BI-Hauptwebsite gestartet wird.

    > [!NOTE]
    > Für Teamregisterkarten müssen Sie eine Konfigurations-URL angeben, um Optionen anzuzeigen und Informationen zu sammeln, die Ihnen helfen, den Inhalt und die Benutzeroberfläche Ihrer Registerkarte anzupassen. Diese iframed HTML-Seite wird angezeigt, wenn ein Benutzer die Registerkarte zum ersten Mal zu einem Kanal hinzufügt.
    > Sie müssen auch alle zusätzlichen Domänen angeben, von denen die Registerkarte erwartet, dass sie geladen werden oder mit denen sie verlinkt wird.

* **Bot**

  In diesem Abschnitt können Sie Ihrer App einen [Unterhaltungs-Bot](~/bots/what-are-bots.md) hinzufügen. Wenn Sie bereits einen Bot bei Bot Framework registriert haben, können Sie diesen Bot hinzufügen, indem Sie auf **Einrichten** klicken, den Bot-Namen und die Bot Framework-ID angeben und die Bereiche definieren, in denen der Bot arbeiten soll.

  Wenn Sie den Bot noch nicht beim Bot Framework registriert haben, klicken Sie auf **"Registrieren",** um einen neuen zu erstellen. Nachdem Sie Ihren Bot registriert haben, kehren Sie zu diesem Abschnitt des Manifest-Editors zurück, um den Namen und die Bot Framework-ID einzugeben.

  Nachdem Sie die Informationen Ihres Bots bereitgestellt haben, können Sie jetzt optional eine Liste der Befehle definieren, die Ihr Bot Benutzern vorschlagen kann. Fügen Sie den Befehlsnamen, eine Befehlsbeschreibung mit Angaben zu dessen Syntax und Argumenten sowie die Bereiche hinzu, für die dieser Befehl gelten soll.

  Beachten Sie, dass Befehle, die für den nicht unterstützten Bereich angegeben wurden, ignoriert werden, wenn Sie Ihren Bot so definiert haben, dass er nur einen Bereich unterstützt. Sie können die vom Bot unterstützten Bereiche jederzeit bearbeiten.

* **Connector**

  In diesem Abschnitt können Sie Ihrer App einen Connector hinzufügen. Wenn Sie bereits einen Office 365 Connector registriert haben, wählen Sie **"Einrichten"** aus, und geben Sie den Namen und die ID des Connectors ein. Wenn Sie einen neuen Konnektor möchten, klicken Sie auf **Registrieren**, um zum Connector Developer Dashboard in Ihrem Browser zu gelangen.

  > [!NOTE]
  > Die App-Anpassung ermöglicht Es Administratoren, das Aussehen und Verhalten der Apps zu ändern, die über Bots, Messaging-Erweiterungen, Registerkarten und Connectors geladen werden. Wenn der Teams-Administrator beispielsweise den Namen einer App von auf an anpasst, `Contoso` wird die App den Benutzern mit dem neuen Namen `Contoso Agent` `Contoso Agent` angezeigt. Beim Hinzufügen eines Connectors zu einem Chat wird in der Liste jedoch weiterhin der Name der App `Contoso` angezeigt.

* **Messaging-Erweiterungen**

  [Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) bieten Benutzern eine leistungsstarke Möglichkeit, mit Ihrer App in Microsoft Teams zu agieren. Benutzer können Informationen von Ihrem Dienst abfragen und diese Informationen in Form von Karten direkt im Kanal oder in der Chat-Unterhaltung veröffentlichen.

  Messaging-Erweiterungen werden von Bot Framework-Bots unterstützt, sodass für den Betrieb ein konfigurierter Bot erforderlich ist. Wenn über Sie den Namen und die Bot Framework-ID des Bots verfügen, für den Sie die Messaging-Erweiterung aktivieren möchten, geben Sie ihn ein. Andernfalls klicken Sie auf *Registrieren*, um den Namen zu erstellen, und geben Sie anschließend die Informationen ein. Wählen Sie aus, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann.

  Nachdem Sie den zugrunde liegenden Bot konfiguriert haben, definieren Sie die Befehle und Parameter, die die Messaging-Erweiterung akzeptieren kann.

  Jeder Befehl erfordert einen Titel und eine ID. Der Befehl kann optional eine Beschreibung für den Benutzer enthalten. Jeder Befehl kann bis zu fünf Parameter unterstützen, für die jeweils Folgendes erforderlich ist:

  * Der Name des Parameters, wie er im Teams-Client angezeigt wird und in der Benutzeranforderung enthalten ist.
  * Ein benutzerfreundlicher Titel.
  * Eine optionale Beschreibung.

  > [!NOTE]
  > Informationen zum Erstellen von Messaging-Erweiterungen mit App Studio finden Sie unter ["Erstellen einer Messaging-Erweiterung mit App Studio".](~/resources/create-messaging-extension-using-appstudio.md)

* **Besprechungserweiterung**

  TODO: Rajesh R.

* **Szene**

  Szenen im Zusammen-Modus ist ein Artefakt, das vom Szenenentwickler mithilfe des Microsoft Scene-Studio erstellt wurde und Personen zusammen mit ihrem Videostream in einer vom Szenenersteller konzipierten kreativen Umgebung zusammenführt. In einer eingestellten Szeneneinstellung haben die Teilnehmer Arbeitsplätze mit Videostreams festgelegt, die auf diesen Arbeitsplätzen gerendert werden. Weitere Informationen finden Sie unter [Teams Together Mode](~/apps-in-teams-meetings/teams-together-mode.md).

## <a name="permissions"></a>Berechtigungen

Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort erweitern.

## <a name="languages"></a>Sprachen

Richten Sie die sprachen ein, die Ihre App unterstützt, oder ändern Sie sie.

## <a name="single-sign-on"></a>Einmaliges Anmelden

Konfigurieren Sie Ihre App so, dass Benutzer mit einmaligem Anmelden (Single Sign-On, SSO) authentifiziert werden.

## <a name="domains"></a>Domänen

Eine Liste der gültigen Domänen für Websites, die von der App im Teams-Client geladen werden sollen. Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. . Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendeten navigieren muss, muss diese Domäne hier angegeben werden.

Es ist nicht erforderlich, die Domänen der Identitätsanbieter, die Sie in Ihrer App unterstützen möchten, einzuschließen. Um sich beispielsweise mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten. Sie dürfen jedoch keine accounts.google.com in `validDomains[]` einschließen.

Teams Apps, die ihre eigenen SharePoint-URLs benötigen, um ordnungsgemäß zu funktionieren, enthalten "{teamsitedomain}" in ihrer gültigen Domänenliste.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter. Ist z. `yourapp.onmicrosoft.com` B. gültig, ist jedoch `*.onmicrosoft.com` ungültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="advanced"></a>Fortgeschritten
Todo von Karthig

### <a name="app-content"></a>App-Inhalt
Todo von Karthig

### <a name="first-party-settings"></a>Einstellungen für Erstanbieter
Todo von Karthig

## <a name="see-also"></a>Siehe auch

* [Übersicht über Teams Entwicklerportal](~/concepts/build-and-test/teams-developer-portal.md)
* [Verteilen Teams Entwicklerportals](~/concepts/tdp-distribute.md)
* [Tools im Teams Entwicklerportal](~/concepts/tdp-tools.md)