---
title: Teams-App-Manifest im Teams-Toolkit für Visual Studio
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie teams-App-Manifest in der verschiedenen Umgebung für Visual Studio bearbeiten, in der Vorschau anzeigen und anpassen.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
ms.openlocfilehash: c391df383c97638d3c8ff5944afab75db2400580
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027456"
---
# <a name="edit-teams-app-manifest-using-visual-studio"></a>Bearbeiten des Teams-App-Manifests mit Visual Studio

Das Teams-Toolkit in Visual Studio lädt manifest mit Konfigurationen aus `state.{env}.json` und `config.{env}.json` während der Bereitstellung und Vorbereitung von `manifest.template.json` App-Abhängigkeiten. Sie können die Microsoft Teams-App auch im [Entwicklerportal](https://dev.teams.microsoft.com/apps) mit dem Manifest erstellen.

Nach dem Gerüst wird in der Manifestvorlagendatei unter `templates/appPackage` dem Ordner `manifest.template.json` zwischen der lokalen und der Remoteumgebung freigegeben.

Wählen Sie in der Manifestvorlage **"Project** > **Teams Toolkit** > **Open Manifest File**" aus.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png" alt-text="Manifestdatei öffnen":::

### <a name="customize-app-manifest-in-teams-toolkit"></a>Anpassen des App-Manifests im Teams-Toolkit

Es gibt zwei Arten von Platzhaltern in `manifest.template.json`:

- `{{state.xx}}` ist ein vordefinierter Platzhalter, dessen Wert vom Teams Toolkit aufgelöst wird, definiert in `state.{env}.json`. Es wird empfohlen, die Werte in `state.{env}.json`nicht zu ändern.
- `{{config.manifest.xx}}` benutzerdefinierter Platzhalter ist, dessen Wert aus `config.{env}.json`aufgelöst wird.

Sie können einen benutzerdefinierten Parameter wie folgt hinzufügen:

- Hinzufügen eines Platzhalters mit `manifest.template.json` Muster: `{{config.manifest.xx}}`.
- Hinzufügen eines Config-Werts in `config.{env}.json`.

    ```
        {
            "manifest": {
            "KEY": "VALUE"
            }
    }
    ```

### <a name="preview-app-manifest-in-teams-toolkit"></a>Vorschau-App-Manifest im Teams-Toolkit

Sie können eine Vorschau von Werten im App-Manifest auf zwei Arten anzeigen:

- Wenn Sie mit der Maus auf den Platzhalter in `manifest.template.json`zeigen, werden die Werte für **die Entwicklungs** - und **lokale** Umgebung angezeigt.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png" alt-text="Mit der Maus auf den Platzhalter zeigen":::

- Sie können auch neben jedem Platzhalter in `manifest.template.json`auf den Schlüssel zeigen, wobei dieselben Werte für **entwickler****- und lokale** Umgebungen zu sehen sind.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png" alt-text="Mit der Maus auf die Taste neben dem Platzhalter zeigen":::

   > [!NOTE]
   > Wenn die Umgebung nicht bereitgestellt wurde oder die Abhängigkeiten der Teams-App nicht vorbereitet wurden, weist dies darauf hin, dass die Werte für platzhalter nicht generiert wurden. Bitte folgen Sie den Anweisungen im Hovern, um entsprechende Werte zu generieren.

### <a name="preview-manifest-file"></a>Vorschaumanifestdatei

Sie können eine Vorschau der Manifestdatei anzeigen, indem Sie die folgenden Schritte ausführen:

- Wählen Sie das **Menü "Project** > **Teams-Toolkit** " aus, und lösen **Sie "Teams-App-Abhängigkeiten** vorbereiten" oder " **Bereitstellung in der Cloud** " aus, die eine Konfiguration für die lokale oder Remote-Teams-App generiert.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png" alt-text="Vorschaumanifestdatei":::

- Um eine Vorschau des Manifests mit echtem Inhalt anzuzeigen, generiert das Teams-Toolkit die Vorschaumanifestdateien, klicken Sie mit der rechten Maustaste auf **"manifest.template.json** " im Ordner **"appPackage** ". Wählen Sie **"Vorschaumanifestdatei** > **für lokal** " oder **"Für Azure**" aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png" alt-text="Vorschaukontextmenü":::

Es gibt zwei weitere Möglichkeiten, eine Vorschau der Manifestdatei anzuzeigen:

- Wählen Sie "**Zip-App-Paket**" des **Project** > **Teams-Toolkits** >  und dann **"Für lokal**" oder **"Für Azure**" aus.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png" alt-text="ZIP-App-Paket":::

- Sie können auch die gleiche Liste der Menüs anzeigen, die sich unter Project > Teams Toolkit befinden, wenn Sie mit der rechten Maustaste auf Ihren Projektnamen klicken und dann unter **Projektmappen-Explorer** **das Teams-Toolkit** auswählen.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png" alt-text="Liste der Teams-Toolkit-Menüs aus dem Projektmappen-Explorer":::

    > [!NOTE]
    >In diesem Szenario lautet der Projektname **"MyTeamsApp1**".

### <a name="sync-local-changes-to-developer-portal"></a>Lokale Änderungen mit dem Entwicklerportal synchronisieren

Ihre lokalen Änderungen können mit dem Entwicklerportal synchronisiert werden, nachdem Sie die Manifestdatei in der Vorschau angezeigt haben. Wählen Sie **das Updatemanifest des Project** > **Teams-Toolkits** > **im Teams-Entwicklerportal** oder das Kontextmenü aus Projektmappen-Explorer aus.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png" alt-text="Updatemanifest im Teams-Entwicklerportal":::

> [!NOTE]
> Die Änderungen werden auf das Teams Developer Portal aktualisiert. Wenn Sie einige manuelle Updates im Entwicklerportal haben, können diese überschrieben werden. Im Dialogfeld **"Warnung** " können Sie " **Überschreiben und aktualisieren"** oder **"Abbrechen"** auswählen.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png" alt-text="Warnung aktualisieren":::

## <a name="see-also"></a>Siehe auch

- [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
- [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
