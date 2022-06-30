---
title: Erstellen eines geheimen Clientschlüssels
description: Beschreibt das Erstellen eines geheimen Clientschlüssels.
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Microsoft Azure Active Directory (Azure AD) Graph-API
ms.openlocfilehash: 77d1c4e43c9bdfb9d2cb9e3e97ee3a26b8b0fa01
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558849"
---
# <a name="create-client-secret"></a>Erstellen eines geheimen Clientschlüssels

Ein geheimer Clientschlüssel ist eine Zeichenfolge, mit der die Anwendung ihre Identität beim Anfordern eines Tokens nachweist.

1. Wählen Sie **"Zertifikate & geheime Schlüssel** **verwalten** > " aus.

2. Wählen Sie **+Neuer geheimer Clientschlüssel aus**.

    :::image type="content" source="../../../assets/images/adaptive-cards/client-secret.png" alt-text="Seite &quot;Geheimer Clientschlüssel&quot;":::

   Die Seite **"Geheimen Clientschlüssel hinzufügen** " wird angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-secret.png" alt-text="Seite &quot;Geheimen Clientschlüssel hinzufügen&quot;":::

3. Geben Sie die Beschreibung ein.
4. Wählen Sie die Gültigkeitsdauer für den geheimen Schlüssel aus.
5. Klicken Sie auf **Hinzufügen**.

   Im Browser wird eine Meldung angezeigt, die besagt, dass der geheime Clientschlüssel aktualisiert wurde, und der geheime Clientschlüssel wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-secret-added.png" alt-text="Geheimer Clientschlüssel hinzugefügt":::

6. Wählen Sie die Schaltfläche "Kopieren" neben dem **Wert** des geheimen Clientschlüssels aus.
7. Speichern Sie den Wert, den Sie zur späteren Verwendung kopiert haben.

   > [!NOTE]
   > Stellen Sie sicher, dass Sie den Wert des geheimen Clientschlüssels direkt nach dem Erstellen kopieren. Der Wert ist nur zu dem Zeitpunkt sichtbar, zu dem der geheime Clientschlüssel erstellt wird, und kann danach nicht mehr angezeigt werden.
