---
title: Konfigurieren von OAuth 2,0-Identitätsanbietern
description: Beschreibt, wie Identitätsanbieter mit einem Fokus auf Azure AD konfiguriert werden.
keywords: Teams-Authentifizierung Aad OAuth Identity Provider
ms.openlocfilehash: 799b0c20cda64456a4610acbdbedf758989bee55
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674463"
---
# <a name="configuring-identity-providers"></a><span data-ttu-id="5623e-104">Konfigurieren von Identitätsanbietern</span><span class="sxs-lookup"><span data-stu-id="5623e-104">Configuring identity providers</span></span>

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a><span data-ttu-id="5623e-105">Konfigurieren einer Anwendung für die Verwendung von Azure Active Directory als Identitätsanbieter</span><span class="sxs-lookup"><span data-stu-id="5623e-105">Configuring an application to use Azure Active Directory as an identity provider</span></span>

<span data-ttu-id="5623e-106">Identitätsanbieter, die OAuth 2,0 unterstützen, authentifizieren keine Anforderungen von unbekannten Anwendungen; Anwendungen müssen frühzeitig registriert werden.</span><span class="sxs-lookup"><span data-stu-id="5623e-106">Identity providers supporting OAuth 2.0 will not authenticate requests from unknown applications; applications must be registered ahead of time.</span></span> <span data-ttu-id="5623e-107">Führen Sie dazu die folgenden Schritte aus Azure AD aus:</span><span class="sxs-lookup"><span data-stu-id="5623e-107">To do this with Azure AD, follow these steps:</span></span>

1. <span data-ttu-id="5623e-108">Öffnen Sie das [Anwendungs Registrierungs Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span><span class="sxs-lookup"><span data-stu-id="5623e-108">Open the [Application Registration Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span></span>

2. <span data-ttu-id="5623e-109">Wählen Sie Ihre APP aus, um die Eigenschaften anzuzeigen, oder klicken Sie auf die Schaltfläche "neue Registrierung".</span><span class="sxs-lookup"><span data-stu-id="5623e-109">Select your app to view its properties, or click the "New Registration" button.</span></span> <span data-ttu-id="5623e-110">Suchen Sie den Abschnitt **Umleitungs-URI** für die app.</span><span class="sxs-lookup"><span data-stu-id="5623e-110">Find the **Redirect URI** section for the app.</span></span>

3. <span data-ttu-id="5623e-111">Stellen Sie sicher, dass im Dropdownmenü die Option **Internet** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="5623e-111">In the dropdown menu, make sure **Web** is selected.</span></span> <span data-ttu-id="5623e-112">Aktualisieren Sie die URL auf Ihren Authentifizierungs Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="5623e-112">Update the URL to your authentication endpoint.</span></span> <span data-ttu-id="5623e-113">Die Umleitungs-URLs sind für die Beispielanwendungen "Code/Node. js" und "C#" auf GitHub ähnlich:</span><span class="sxs-lookup"><span data-stu-id="5623e-113">For the TypeScript/Node.js and C# sample apps on GitHub, the redirect URLs will be similar to this:</span></span>

    <span data-ttu-id="5623e-114">Umleitungs-URLs:`https://<hostname>/bot-auth/simple-start`</span><span class="sxs-lookup"><span data-stu-id="5623e-114">Redirect URLs: `https://<hostname>/bot-auth/simple-start`</span></span>

<span data-ttu-id="5623e-115">Ersetzen `<hostname>` Sie durch ihren tatsächlichen Host.</span><span class="sxs-lookup"><span data-stu-id="5623e-115">Replace `<hostname>` with your actual host.</span></span> <span data-ttu-id="5623e-116">Dies kann eine dedizierte Hostwebsite wie Azure, glitch oder ein ngrok-Tunnel sein, der auf dem Entwicklungscomputer wie `abcd1234.ngrok.io`.</span><span class="sxs-lookup"><span data-stu-id="5623e-116">This might be a dedicated hosting site such as Azure, Glitch, or an ngrok tunnel to localhost on your development machine such as `abcd1234.ngrok.io`.</span></span> <span data-ttu-id="5623e-117">Sie verfügen möglicherweise noch nicht über diese Informationen, wenn Sie Ihre APP (oder die oben erwähnte Beispiel-APP) nicht abgeschlossen oder gehostet haben, aber Sie können jederzeit zu dieser Seite zurückkehren, wenn diese Informationen bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="5623e-117">You may not have this information yet if you have not completed or hosted your app (or the sample app mentioned above), but you can always return to this page when that information is known.</span></span>

## <a name="other-authentication-providers"></a><span data-ttu-id="5623e-118">Andere Authentifizierungsanbieter</span><span class="sxs-lookup"><span data-stu-id="5623e-118">Other authentication providers</span></span>

* <span data-ttu-id="5623e-119">**LinkedIn** Befolgen Sie die Anweisungen unter [Konfigurieren ihrer LinkedIn-Anwendung](https://developer.linkedin.com/docs/oauth2) .</span><span class="sxs-lookup"><span data-stu-id="5623e-119">**LinkedIn** Follow the instructions in [Configuring your LinkedIn application](https://developer.linkedin.com/docs/oauth2)</span></span>

* <span data-ttu-id="5623e-120">**Google** - Abrufen von OAuth 2,0-Clientanmeldeinformationen über die [Google-API-Konsole](https://console.developers.google.com/)</span><span class="sxs-lookup"><span data-stu-id="5623e-120">**Google** Obtain OAuth 2.0 client credentials from the [Google API Console](https://console.developers.google.com/)</span></span>
