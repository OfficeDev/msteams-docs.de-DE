---
title: Konfigurieren von OAuth 2.0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter mit Einem Fokus auf Azure AD konfiguriert werden
ms.topic: how-to
keywords: Teams authentication AAD oauth identity provider
ms.openlocfilehash: b5ffd6c4c1edd2c4315ea1e31474a626de53aba1
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014467"
---
# <a name="configure-identity-providers"></a><span data-ttu-id="cb26d-104">Identitätsanbieter konfigurieren</span><span class="sxs-lookup"><span data-stu-id="cb26d-104">Configure identity providers</span></span>

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a><span data-ttu-id="cb26d-105">Konfigurieren einer Anwendung für die Verwendung von Azure Active Directory als Identitätsanbieter</span><span class="sxs-lookup"><span data-stu-id="cb26d-105">Configuring an application to use Azure Active Directory as an identity provider</span></span>

<span data-ttu-id="cb26d-106">Identitätsanbieter, die OAuth 2.0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen. Anwendungen müssen im Voraus registriert werden.</span><span class="sxs-lookup"><span data-stu-id="cb26d-106">Identity providers supporting OAuth 2.0 will not authenticate requests from unknown applications; applications must be registered ahead of time.</span></span> <span data-ttu-id="cb26d-107">Führen Sie die folgenden Schritte aus, um dies mit Azure AD zu tun:</span><span class="sxs-lookup"><span data-stu-id="cb26d-107">To do this with Azure AD, follow these steps:</span></span>

1. <span data-ttu-id="cb26d-108">Öffnen Sie [das Anwendungsregistrierungsportal.](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)</span><span class="sxs-lookup"><span data-stu-id="cb26d-108">Open the [Application Registration Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span></span>

2. <span data-ttu-id="cb26d-109">Wählen Sie Ihre App aus, um ihre Eigenschaften anzeigen zu können, oder klicken Sie auf die Schaltfläche "Neue Registrierung".</span><span class="sxs-lookup"><span data-stu-id="cb26d-109">Select your app to view its properties, or click the "New Registration" button.</span></span> <span data-ttu-id="cb26d-110">Suchen Sie den **Abschnitt "Umleitungs-URI"** für die App.</span><span class="sxs-lookup"><span data-stu-id="cb26d-110">Find the **Redirect URI** section for the app.</span></span>

3. <span data-ttu-id="cb26d-111">Stellen Sie im Dropdownmenü sicher, dass **"Web"** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="cb26d-111">In the dropdown menu, make sure **Web** is selected.</span></span> <span data-ttu-id="cb26d-112">Aktualisieren Sie die URL auf Ihren Authentifizierungsendpunkt.</span><span class="sxs-lookup"><span data-stu-id="cb26d-112">Update the URL to your authentication endpoint.</span></span> <span data-ttu-id="cb26d-113">Für die TypeScript/Node.js- und C#-Beispiel-Apps auf GitHub sind die Umleitungs-URLs ähnlich wie die folgenden:</span><span class="sxs-lookup"><span data-stu-id="cb26d-113">For the TypeScript/Node.js and C# sample apps on GitHub, the redirect URLs will be similar to this:</span></span>

    <span data-ttu-id="cb26d-114">Umleitungs-URLs: `https://<hostname>/bot-auth/simple-start`</span><span class="sxs-lookup"><span data-stu-id="cb26d-114">Redirect URLs: `https://<hostname>/bot-auth/simple-start`</span></span>

<span data-ttu-id="cb26d-115">Ersetzen `<hostname>` Sie dies durch den tatsächlichen Host.</span><span class="sxs-lookup"><span data-stu-id="cb26d-115">Replace `<hostname>` with your actual host.</span></span> <span data-ttu-id="cb26d-116">Dies kann eine dedizierte Hostingwebsite wie Azure, Glitch oder ein ngrok-Tunnel zu localhost auf Ihrem Entwicklungscomputer sein, z. B. `abcd1234.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="cb26d-116">This might be a dedicated hosting site such as Azure, Glitch, or an ngrok tunnel to localhost on your development machine such as `abcd1234.ngrok.io`.</span></span> <span data-ttu-id="cb26d-117">Sie verfügen möglicherweise noch nicht über diese Informationen, wenn Sie Ihre App (oder die oben erwähnte Beispiel-App) noch nicht abgeschlossen oder gehostet haben. Sie können jedoch jederzeit zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="cb26d-117">You may not have this information yet if you have not completed or hosted your app (or the sample app mentioned above), but you can always return to this page when that information is known.</span></span>

## <a name="other-authentication-providers"></a><span data-ttu-id="cb26d-118">Andere Authentifizierungsanbieter</span><span class="sxs-lookup"><span data-stu-id="cb26d-118">Other authentication providers</span></span>

* <span data-ttu-id="cb26d-119">**LinkedIn** Befolgen Sie die Anweisungen unter ["Konfigurieren der LinkedIn-Anwendung".](https://developer.linkedin.com/docs/oauth2)</span><span class="sxs-lookup"><span data-stu-id="cb26d-119">**LinkedIn** Follow the instructions in [Configuring your LinkedIn application](https://developer.linkedin.com/docs/oauth2)</span></span>

* <span data-ttu-id="cb26d-120">**Google** Abrufen von OAuth 2.0-Clientanmeldeinformationen aus der [Google -API-Konsole](https://console.developers.google.com/)</span><span class="sxs-lookup"><span data-stu-id="cb26d-120">**Google** Obtain OAuth 2.0 client credentials from the [Google API Console](https://console.developers.google.com/)</span></span>
