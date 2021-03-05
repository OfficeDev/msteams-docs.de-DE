---
title: Lernprogramm – Aktualisieren von Teams mithilfe des Microsoft Teams Yeoman-Generators
description: Erfahren Sie, wie Sie den Microsoft Teams Yeoman-Generator zum Upgraden von Teams verwenden.
ms.topic: tutorial
ms.openlocfilehash: 0c52dd15703000a1c0f99ddd28401dd686e1b1bb
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449610"
---
# <a name="upgrade-teams-using-microsoft-teams-yeoman-generator"></a>Aktualisieren von Teams mithilfe des Microsoft Teams Yeoman-Generators
Dieses Lernprogramm hilft Ihnen, Ihre aktuelle Microsoft Teams-App-Version mithilfe des Microsoft Teams Yeoman-Generators auf die neueste Version zu aktualisieren.

## <a name="get-current-version-of-teams"></a>Aktuelle Version von Teams erhalten
```PowerShell
 yo teams --version
```

## <a name="update-teams"></a>Aktualisieren von Teams
Der yo-Befehl listet verschiedene Optionen auf, die vom Erstellen eines Projekts bis zum Aktualisieren des Generators reichen. Verwenden Sie den folgenden Befehl, um den Aktualisierungsgenerator auszuwählen:
```PowerShell
 yo
```

Verwenden Sie die Pfeiltasten, um **Update Generators zu wählen.**
![Bild von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

In der Liste werden alle verfügbaren Generatoren angezeigt. Verwenden Sie zum Auswählen oder Aufheben der Auswahl der Teams-Version aus den verfügbaren Optionen die **Leerraumleiste,** und wählen Sie einen bestimmten Generator aus.
![Abbildung von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)

Es dauert einige Sekunden bis Minuten, bis die Installation von Teams abgeschlossen ist.

Verwenden Sie nach Abschluss der Installation den folgenden Befehl, um die installierte Version zu überprüfen:

```PowerShell
yo teams --version
```

![Abbildung von FindVersionAfterInstallation](~/assets/images/Update-Teams/FindVersionAfterInstallation.png)

Congrat! Sie haben Microsoft Teams aktualisiert.

