---
title: Testen des App-Verhaltens in unterschiedlichen Umgebungen
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie das App-Verhalten in verschiedenen Umgebungen testen.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: 187219fec76830119e795d1dd60a36b2374c65ac
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617219"
---
# <a name="test-app-behavior-in-different-environment"></a>Testen des App-Verhaltens in unterschiedlichen Umgebungen

Sie können Ihre Teams-App nach der Integration in Microsoft Teams testen. Um Ihre Teams-App zu testen, müssen Sie mindestens einen Arbeitsbereich in Ihrer Umgebung erstellen. Sie können das Teams-Toolkit zum Testen Ihrer Teams-App verwenden:

* **Lokal in Teams gehostet**: Das Teams-Toolkit hostet Ihre Teams-App lokal, indem sie zum Testen in der lokalen Umgebung in Teams quergeladen wird.

* **In Teams gehostete Cloud**: Zum Remote-Testen Ihrer Teams-App müssen Sie sie mithilfe der Bereitstellung und Bereitstellung auf Microsoft Azure Active Directory (Azure AD) in der Cloud hosten. Dazu gehört das Hochladen Ihrer Lösung in Azure AD und das anschließende Hochladen in Teams.

> [!NOTE]
> Für das Debuggen und Testen im Produktionsmaßstab empfehlen wir, dass Sie Ihre eigenen Unternehmensrichtlinien befolgen, um sicherzustellen, dass Sie Tests, Staging und Bereitstellung über Ihre eigenen Prozesse unterstützen können.

## <a name="locally-hosted-environment"></a>Lokal gehostete Umgebung

Teams ist ein cloudbasiertes Produkt, das erfordert, dass alle Dienste, auf die es zugreift, öffentlich über HTTPS-Endpunkte verfügbar sind. Beim lokalen Hosting geht es um das Querladen in Teams zum Testen in der lokalen Umgebung.

> [!NOTE]
> Sie können zwar jedes beliebige Tool Ihrer Wahl zum Testen verwenden, es wird jedoch empfohlen, [ngrok](https://ngrok.com/download) zu verwenden.

## <a name="cloud-hosted-environment"></a>In der Cloud gehostete Umgebung

Um Ihren Entwicklungs- und Produktionscode und die zugehörigen HTTPS-Endpunkte zu hosten, müssen Sie Ihre Teams-App remote mithilfe der Bereitstellung und Bereitstellung in Azure AD testen. Sie müssen sicherstellen, dass auf alle Domänen über Ihre Teams-App zugegriffen werden kann, die [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) im Objekt in der `manifest.jason` Datei aufgeführt ist.

> [!NOTE]
> Um eine sichere Umgebung zu gewährleisten, müssen Sie die genauen Domänen und Unterdomänen, auf die Sie verweisen, explizit angeben, und diese Domänen müssen unter Ihrer Kontrolle stehen. Beispielsweise wird `*.azurewebsites.net` nicht empfohlen, aber `contoso.azurewebsites.net` wird empfohlen.

## <a name="see-also"></a>Siehe auch

* [Lokales Debuggen Ihrer Microsoft Teams-App](debug-local.md)
* [Debuggen von Hintergrundprozessen](debug-background-process.md)
* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen in die Cloud](deploy.md)
* [Vorschau und Anpassen des Teams-App-Manifests](TeamsFx-preview-and-customize-app-manifest.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
