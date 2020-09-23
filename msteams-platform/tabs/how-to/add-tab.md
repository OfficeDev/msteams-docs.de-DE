---
title: Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte
author: laujan
description: Vorgehensweise Erstellen einer Registerkarte für Microsoft Teams mit App Studio oder manuell.
keywords: Teams-Registerkartengruppe Kanal konfigurierbar
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 78077a19c8597826ca6d10a7c1c6240fae3f3fbd
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209718"
---
# <a name="extend-your-teams-app-with-a-custom-tab"></a>Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte

Mit benutzerdefinierten Registerkarten können Sie Webinhalte bereitstellen, die Sie für Ihren Kanal, Gruppenchat und persönliche Benutzer hosten. Auf einer hohen Ebene müssen Sie die folgenden Schritte ausführen, um eine Registerkarte zu erstellen:

1. Vorbereiten Ihrer Entwicklungsumgebung.
1. Erstellen Sie Ihre Seite (n).
1. Hosten Sie Ihren app-Dienst.
1. Erstellen Sie Ihr App-Paket, und laden Sie es in Microsoft Teams hoch.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-pages"></a>Erstellen Ihrer Seite (n)

Unabhängig davon, ob Sie die Registerkarte innerhalb des persönlichen oder des Kanals/Gruppenbereichs präsentieren, besteht Sie aus einer oder mehreren HTML-Seiten, die Sie hosten. Registerkarten mit einem persönlichen Bereich bestehen aus einer einzelnen Inhaltsseite, während für Registerkarten mit einem Kanal oder Gruppenbereich eine Konfigurationsseite erforderlich ist, die die URL der Inhaltsseite basierend auf der Benutzereingabe zum Zeitpunkt der Installation festlegt.

Es gibt drei Arten von Registerkartenseiten. Ausführliche Informationen zum Erstellen dieser Website finden Sie auf der entsprechenden Dokumentationsseite.

1. [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md), die Seite, die auf einer Registerkarte angezeigt wird.
1. [Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md), die Seite, die zum Festlegen oder Aktualisieren der Inhaltsseiten-URL verwendet wird, und Sie einer Kanal-Gruppe-Registerkarte hinzufügen.
1. [Entfernungs Seite](~/tabs/how-to/create-tab-pages/removal-page.md), eine optionale Seite, die angezeigt wird, wenn ein Kanal/eine Gruppenregisterkarte entfernt wird.

### <a name="tab-requirements"></a>Registerkarten Anforderungen

Unabhängig vom Typ der Seite müssen Sie die folgenden Anforderungen erfüllen:

* Sie müssen zulassen, dass Ihre Seiten in einem IFRAME, über X-Frame-Options und/oder Inhalts-Security-Policy-HTTP-Antwortheader zugestellt werden.
  * Kopfzeile festlegen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`        
  * Für Internet Explorer 11 Kompatibilität, legen Sie `X-Content-Security-Policy` ebenfalls fest.    
  * Alternativ können Sie Header festlegen `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` . Dieser Header ist veraltet, wird von den meisten Browsern jedoch noch respektiert.
* In der Regel werden Anmeldeseiten als Schutz vor Klick-Jacking nicht in iframes gerendert. Daher muss Ihre Authentifizierungslogik eine andere Methode als Redirect verwenden (beispielsweise die Token-basierte oder die Cookie-basierte Authentifizierung verwenden).

> [!NOTE]
> In Chrome 80, das für die Veröffentlichung Anfang 2020 vorgesehen ist, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt. Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen. *Siehe* [SameSite-Cookie-Attribut (2020 Update)](../../resources/samesite-cookie-update.md).

* Browser befolgen eine Richtlinie mit demselben Ursprung, die verhindert, dass eine Webseite Anforderungen an eine andere Domäne annimmt als die, die einer Webseite zugestellt ist. Möglicherweise müssen Sie die Konfigurations-oder Inhaltsseite jedoch an eine andere Domäne oder Unterdomäne umleiten. Ihre domänenübergreifende Navigationslogik sollte es dem Microsoft Teams-Client ermöglichen, den Ursprung anhand einer statischen validDomains-Liste im App-Manifest zu überprüfen, wenn die Registerkarte geladen oder kommuniziert wird.

* Um eine nahtlose Benutzeroberfläche zu erstellen, sollten Sie Ihre Registerkarten auf der Grundlage des Designs, des Designs und der Absicht des Teams-Clients formatieren. Normalerweise funktionieren Registerkarten am besten, wenn Sie für einen bestimmten Bedarf erstellt wurden, und konzentrieren sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge der Daten, die für den Kanal Speicherort der Registerkarte relevant sind.

* Fügen Sie auf der Inhaltsseite einen Verweis auf [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client) mithilfe von Skripttags hinzu. Führen Sie nach dem Laden der Seite einen Anruf an `microsoftTeams.initialize()` . Die Seite wird nicht angezeigt, wenn dies nicht der Fall ist.

## <a name="host-your-app-service"></a>Hosten des App-Diensts

Ihre Inhalte müssen in einer öffentlich verfügbaren URL gehostet werden, die über HTTPS verfügbar ist. Für Tests können Sie einen Reverseproxy wie [ngrok](https://ngrok.com/)verwenden, um den lokalen Port für eine mit dem Internet verbundene URL verfügbar zu machen.

## <a name="create-your-app-package-with-app-studio"></a>Erstellen eines App-Pakets mit App Studio

Sie können die APP Studio-app innerhalb des Microsoft Teams-Clients verwenden, um das App-Manifest zu erstellen. Wenn das App-Studio nicht in Microsoft Teams installiert ist, wählen Sie **apps** ![ Store ](/microsoftteams/platform/assets/images/tab-images/storeApp.png) -app in der unteren linken Ecke der Teams-App aus, und suchen Sie nach App Studio. Nachdem Sie die Kachel gefunden haben, wählen Sie Sie aus, und wählen Sie im Dialogfeld Popupfenster installieren aus.

1. Öffnen Sie den Microsoft Teams-Client – mithilfe der [webbasierten Version](https://teams.microsoft.com) können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
1. Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.
1. Wählen Sie die Kachel **neue APP erstellen** aus.
1. Fügen Sie Ihre APP-Details hinzu (siehe [Manifest-Schema Definition](~/resources/schema/manifest-schema.md) für eine vollständige Beschreibung der einzelnen Felder).
1. Wählen Sie im Abschnitt Funktionen die Option **Registerkarten**aus.
    * Wählen Sie für eine persönliche Registerkarte persönliche *Registerkarte hinzufügen* aus, und wählen Sie **Hinzufügen**aus. Ihnen wird ein Popup-Dialogfenster angezeigt, in dem Sie Ihre Registerkarten Details hinzufügen können.
    * Wählen Sie für einen Kanal/eine Gruppe Registerkarte unter *Team Tab* die Registerkarte Details im Popupfenster Team Tab **Hinzufügen** aus, und füllen Sie die Felder aus. Stellen Sie sicher, dass die *Konfiguration aktualisiert werden kann? Team* -und *Gruppenchat* Felder werden überprüft, und wählen Sie **Speichern**aus.
1. Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld die Host-oder Reverse-Proxy-URL ohne das HTTPS-Präfix enthalten.
1. Auf der **Finish**  =>  Registerkarte Finish**Test und Distribute** können Sie Ihr App-Paket **herunterladen** , das Paket in einem Team **Installieren** oder sich zur Genehmigung an den App-Store von Teams **senden** . *Wenn Sie einen Reverseproxy verwenden, erhalten Sie eine Warnung im Feld **Beschreibung** auf der rechten Seite. Die Warnung kann beim Testen der Registerkarte ignoriert werden*.

## <a name="create-your-app-package-manually"></a>Manuelles Erstellen Ihres App-Pakets

Wie bei Bots und Messaging-Erweiterungen aktualisieren Sie das [App-Manifest](~/resources/schema/manifest-schema.md) Ihrer APP so, dass die Eigenschaften der Registerkarte enthalten sind. Diese Eigenschaften bestimmen die Bereiche, in denen die Registerkarte verfügbar ist, die zu verwendenden URLs und verschiedene andere Eigenschaften.

### <a name="personal-tabs"></a>Persönliche Registerkarten

Der angezeigte Inhalt für persönliche Registerkarten ist für alle Benutzer gleich und wird im Array konfiguriert `staticTabs` . Sie können bis zu sechzehn (16) persönliche Registerkarten in einer APP deklarieren.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|String|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|String|2048 Zeichen|✔|Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.|
|`websiteUrl`|String|2048 Zeichen||Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.|
|`scopes`|Array von Enumerationen|1|✔|Statische Registerkarten unterstützen nur den `personal` Bereich, was bedeutet, dass Sie nur als Teil einer persönlichen App zur Verfügung gestellt werden können.|

#### <a name="simple-personal-tab-manifest-example"></a>Beispiel für einfaches persönliches Tab-Manifest

Das folgende Beispiel zeigt nur das `staticTabs` Array aus einem App-Manifest.

```json
...
"staticTabs": [
    {
      "entityId": "idForPage",
      "name": "Display name for tab",
      "contentUrl": "https:// yourURL.com/content ",
      "websiteUrl": "https://yourURL.com/website",
      "scopes": [ "personal" ]
    }
...
```

### <a name="channelgroup-tabs"></a>Kanal/Gruppenregisterkarten

Im Array werden Kanäle/Gruppenregisterkarten hinzugefügt `configurableTabs` . Sie können im Array nur einen Kanal/eine Gruppe-Registerkarte deklarieren `configurableTabs` .

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|String|2048 Zeichen|✔|Die Seite https://URL to Configuration.|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann. Standard `true`|
|`scopes`|Array von Enumerationen|1|✔|Konfigurierbare Registerkarten unterstützen nur die `team` und `groupchat` Bereiche. |

#### <a name="simple-channelgroup-tab-manifest-example"></a>Beispiel für einfaches Channel/Group-Registerkarten Manifest

Das folgende Beispiel zeigt nur das `configurableTabs` Array aus einem App-Manifest.

```json
...
"configurableTabs": [
    {
      "configurationUrl": "https://yourURL.com/configure",
      "canUpdateConfiguration": true,
      "scopes": [ "team", "groupchat" ]
    }
...
```

Nachdem Sie Ihr `manifest.json` Bundle in einem ZIP-Ordner zusammen mit ihren beiden erforderlichen Symbolen abgeschlossen haben.

### <a name="upload-app-package-directly-to-a-team"></a>Direktes Hochladen des App-Pakets in ein Team

1. Öffnen Sie den Microsoft Teams-Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
1. Wählen Sie im *YourTeams* -Bereich auf der linken Seite das `...` Menü neben dem Team aus, das Sie zum Testen der Registerkarte verwenden, und wählen Sie **Team verwalten**aus.
1. Wählen Sie im Hauptbereich **apps** in der Registerkartenleiste aus, und wählen Sie **eine benutzerdefinierte App hochladen** , die sich in der unteren rechten Ecke der Seite befindet.
1. Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum Ordner **./Paket** , wählen Sie den ZIP-Ordner für das App-Paket aus, und wählen Sie **Öffnen**aus. Ihre Registerkarte wird in Teams hochgeladen.

### <a name="view-your-tab-in-teams"></a>Anzeigen der Registerkarte in Microsoft Teams

1. Anzeigen Ihrer persönlichen Registerkarte:
    * Wählen Sie in der navbar, die sich auf der linken Seite des Teams-Clients befindet, das `...` Menü aus, und wählen Sie Ihre APP aus der Liste aus.

1. Zeigen Sie die Registerkarte Kanal/Gruppe an:
    * Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie in der Registerkartenleiste ➕ aus, und wählen Sie im Katalog die Registerkarte aus.
    * Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass für die Registerkarte Kanal/Gruppe ein benutzerdefiniertes Konfigurationsdialogfeld vorhanden ist. Wählen Sie **Speichern** aus, und ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.

## <a name="learn-more"></a>Weitere Informationen

* [Erstellen einer Inhaltsseite für die Registerkarte](~/tabs/how-to/create-tab-pages/content-page.md)
* [Erstellen einer Konfigurationsseite für die Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [Aktualisieren oder Entfernen einer Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md)
