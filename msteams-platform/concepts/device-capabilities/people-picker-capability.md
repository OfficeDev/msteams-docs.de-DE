---
title: Integrieren der Funktion "Personenauswahl"
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK zum Integrieren der Personenauswahlfunktion
keywords: Personenauswahl-Steuerelement
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 8399eeb1a088e4b60c466d51c223b9405ebf1711
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211636"
---
# <a name="integrate-people-picker-capability"></a><span data-ttu-id="4be28-104">Integrieren der Funktion "Personenauswahl"</span><span class="sxs-lookup"><span data-stu-id="4be28-104">Integrate People Picker capability</span></span> 

<span data-ttu-id="4be28-105">Die Personenauswahl ist ein Steuerelement zum Suchen und Auswählen von Personen.</span><span class="sxs-lookup"><span data-stu-id="4be28-105">People Picker is a control to search and select people.</span></span> <span data-ttu-id="4be28-106">Dies ist eine systemeigene Funktion, die in Teams Plattform verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="4be28-106">This is a native capability available in Teams platform.</span></span> <span data-ttu-id="4be28-107">Sie können Teams systemeigene Personenauswahl-Eingabesteuerelement in Ihre Web-Apps integrieren.</span><span class="sxs-lookup"><span data-stu-id="4be28-107">You can integrate Teams native People Picker input control with your web apps.</span></span> <span data-ttu-id="4be28-108">Sie können zwischen einzelner oder mehrfacher Auswahl und Konfigurationen auswählen, z. B. das Einschränken der Suche in einem Chat, in Kanälen oder in der gesamten Organisation.</span><span class="sxs-lookup"><span data-stu-id="4be28-108">You can select between single or multi selection, and configurations, such as limiting search within a chat, channels, or across the entire organization.</span></span>

<span data-ttu-id="4be28-109">Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das `selectPeople` eine API zum Integrieren der Personenauswahlfunktion in Ihre Web-App bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="4be28-109">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides `selectPeople` API to integrate the People Picker capability within your web app.</span></span> 

## <a name="advantages-of-integrating-people-picker-capability"></a><span data-ttu-id="4be28-110">Vorteile der Integration der Personenauswahlfunktion</span><span class="sxs-lookup"><span data-stu-id="4be28-110">Advantages of integrating People Picker capability</span></span>

* <span data-ttu-id="4be28-111">Das Steuerelement "Personenauswahl" funktioniert auf allen Teams Oberflächen, z. B. in einem Aufgabenmodul, einem Chat, einem Kanal, einer Besprechungsregisterkarte und einer persönlichen App.</span><span class="sxs-lookup"><span data-stu-id="4be28-111">The People Picker control works in all of Teams surfaces, such as task module, a chat, channel, meeting tab, and personal app.</span></span>
* <span data-ttu-id="4be28-112">Mit diesem Steuerelement können Sie innerhalb eines Chats, Kanals oder der gesamten Organisation nach Benutzern suchen und diese auswählen.</span><span class="sxs-lookup"><span data-stu-id="4be28-112">This control allows you to search for and select users within a chat, channel, or the entire organization.</span></span>
*  <span data-ttu-id="4be28-113">Die Funktion "Personenauswahl" hilft bei Szenarien mit Aufgabenzuweisung, Tagging und Benachrichtigung eines Benutzers.</span><span class="sxs-lookup"><span data-stu-id="4be28-113">The People Picker capability helps with scenarios involving task assignment, tagging, notifying a user.</span></span> 
* <span data-ttu-id="4be28-114">Sie können dieses leicht verfügbare Steuerelement in Ihrer Web-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="4be28-114">You can use this readily available control in your web app.</span></span> <span data-ttu-id="4be28-115">Es spart den Aufwand und die Zeit, um ein solches Steuerelement selbst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4be28-115">It saves the effort and time significantly to build such a control on your own.</span></span>

<span data-ttu-id="4be28-116">Sie müssen die API aufrufen, um das `selectPeople` Steuerelement "Personenauswahl" in Ihre Teams-App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="4be28-116">You must call the `selectPeople` API to integrate People Picker control in your Teams app.</span></span> <span data-ttu-id="4be28-117">Um eine effektive Integration zu ermöglichen, müssen Sie über Kenntnisse des [Codeausschnitts](#code-snippet) für den Aufruf der API verfügen.</span><span class="sxs-lookup"><span data-stu-id="4be28-117">For effective integration, you must have an understanding of [code snippet](#code-snippet) for calling the API.</span></span> <span data-ttu-id="4be28-118">Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Web-App zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="4be28-118">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your web app.</span></span>

> [!NOTE] 
> <span data-ttu-id="4be28-119">Derzeit ist Microsoft Teams Unterstützung für die Personenauswahlfunktion nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4be28-119">Currently, Microsoft Teams support for People Picker capability is available for mobile clients only.</span></span>

## <a name="selectpeople-api"></a><span data-ttu-id="4be28-120">`selectPeople` Api</span><span class="sxs-lookup"><span data-stu-id="4be28-120">`selectPeople` API</span></span> 

<span data-ttu-id="4be28-121">`selectPeople`Mit der API können Sie Ihren Web-Apps Teams systemeigene `People Picker input control` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4be28-121">`selectPeople` API enables you to add Teams native `People Picker input control` to your web apps.</span></span>  
<span data-ttu-id="4be28-122">Die API-Beschreibung lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4be28-122">The API description is as follows:</span></span>

| <span data-ttu-id="4be28-123">API</span><span class="sxs-lookup"><span data-stu-id="4be28-123">API</span></span>      | <span data-ttu-id="4be28-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4be28-124">Description</span></span>  |
| --- | --- |
|<span data-ttu-id="4be28-125">**selectPeople**</span><span class="sxs-lookup"><span data-stu-id="4be28-125">**selectPeople**</span></span>|<span data-ttu-id="4be28-126">Startet eine Personenauswahl und ermöglicht es dem Benutzer, eine oder mehrere Personen in der Liste zu suchen und auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="4be28-126">Launches a People Picker and allows the user to search and select one or more people from the list.</span></span><br/><br/><span data-ttu-id="4be28-127">Diese API gibt die ID, den Namen und die E-Mail-Adresse ausgewählter Benutzer an die aufrufende Web-App zurück.</span><span class="sxs-lookup"><span data-stu-id="4be28-127">This API returns the ID, name and email address of selected users to the calling web app.</span></span><br/><br/><span data-ttu-id="4be28-128">Bei einer persönlichen App durchsucht das Steuerelement die gesamte Organisation.</span><span class="sxs-lookup"><span data-stu-id="4be28-128">In case of a personal app, the control searches across the organization.</span></span> <span data-ttu-id="4be28-129">Wenn die App einem Chat oder Kanal hinzugefügt wird, wird der Suchkontext je nach Szenario konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4be28-129">If the app is added to a chat or channel, then the search context is configured depending on the scenario.</span></span> <span data-ttu-id="4be28-130">Die Suche ist innerhalb der Mitglieder dieses Chats, Kanals oder in der gesamten Organisation eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="4be28-130">The search is restricted within the members of that chat, channel, or made available across the organization.</span></span>|

<span data-ttu-id="4be28-131">Die `selectPeople` API enthält die folgenden Eingabekonfigurationen:</span><span class="sxs-lookup"><span data-stu-id="4be28-131">The `selectPeople` API comes along with following input configurations:</span></span>

|<span data-ttu-id="4be28-132">Konfigurationsparameter</span><span class="sxs-lookup"><span data-stu-id="4be28-132">Configuration parameter</span></span>|<span data-ttu-id="4be28-133">Typ</span><span class="sxs-lookup"><span data-stu-id="4be28-133">Type</span></span>|<span data-ttu-id="4be28-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4be28-134">Description</span></span>| <span data-ttu-id="4be28-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="4be28-135">Default value</span></span>|
|-----|------|--------------|------|
|`title`| <span data-ttu-id="4be28-136">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="4be28-136">String</span></span>| <span data-ttu-id="4be28-137">Es handelt sich um einen optionalen Parameter.</span><span class="sxs-lookup"><span data-stu-id="4be28-137">It is an optional parameter.</span></span> <span data-ttu-id="4be28-138">Es legt den Titel für das Steuerelement "Personenauswahl" fest.</span><span class="sxs-lookup"><span data-stu-id="4be28-138">It sets title for the People Picker control.</span></span> | <span data-ttu-id="4be28-139">Auswählen von Personen</span><span class="sxs-lookup"><span data-stu-id="4be28-139">Select people</span></span>|
|`setSelected`|<span data-ttu-id="4be28-140">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="4be28-140">String</span></span>| <span data-ttu-id="4be28-141">Es handelt sich um einen optionalen Parameter.</span><span class="sxs-lookup"><span data-stu-id="4be28-141">It is an optional parameter.</span></span> <span data-ttu-id="4be28-142">Sie müssen AAD-IDs der Personen übergeben, die vorab ausgewählt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4be28-142">You must pass AAD IDs of the people to be preselected.</span></span> <span data-ttu-id="4be28-143">Dieser Parameter wählt Personen beim Starten des Personenauswahl-Steuerelements vorab aus.</span><span class="sxs-lookup"><span data-stu-id="4be28-143">This parameter preselects people while launching the People Picker control.</span></span> <span data-ttu-id="4be28-144">Bei einer einzelnen Auswahl wird nur der erste gültige Benutzer vorbefüllt, wobei der Rest ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="4be28-144">In case of single selection, only the first valid user is prepopulated ignoring the rest.</span></span> |<span data-ttu-id="4be28-145">Null</span><span class="sxs-lookup"><span data-stu-id="4be28-145">Null</span></span>| 
|`openOrgWideSearchInChatOrChannel`|<span data-ttu-id="4be28-146">Boolesch</span><span class="sxs-lookup"><span data-stu-id="4be28-146">Boolean</span></span> | <span data-ttu-id="4be28-147">Es handelt sich um einen optionalen Parameter.</span><span class="sxs-lookup"><span data-stu-id="4be28-147">It is an optional parameter.</span></span> <span data-ttu-id="4be28-148">Wenn sie auf "true" festgelegt ist, wird die Personenauswahl im organisationsweiten Bereich gestartet, auch wenn die App zu einem Chat oder Kanal hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="4be28-148">When it is set to true, it launches the People Picker in organization wide scope even if the app is added to a chat or channel.</span></span> |<span data-ttu-id="4be28-149">Falsch</span><span class="sxs-lookup"><span data-stu-id="4be28-149">False</span></span>|
|`singleSelect`|<span data-ttu-id="4be28-150">Boolesch</span><span class="sxs-lookup"><span data-stu-id="4be28-150">Boolean</span></span>|<span data-ttu-id="4be28-151">Es handelt sich um einen optionalen Parameter.</span><span class="sxs-lookup"><span data-stu-id="4be28-151">It is an optional parameter.</span></span> <span data-ttu-id="4be28-152">Wenn sie auf "true" festgelegt ist, wird die Personenauswahl gestartet, wodurch die Auswahl auf nur einen Benutzer beschränkt wird.</span><span class="sxs-lookup"><span data-stu-id="4be28-152">When it is set to true, it launches the People Picker restricting the selection to one user only.</span></span> |<span data-ttu-id="4be28-153">Falsch</span><span class="sxs-lookup"><span data-stu-id="4be28-153">False</span></span>|

<span data-ttu-id="4be28-154">Die folgende Abbildung zeigt die Funktion "Personenauswahl" in einer Beispiel-Web-App:</span><span class="sxs-lookup"><span data-stu-id="4be28-154">The following image depicts the experience of People Picker capability in a sample web app:</span></span>

![Web-App-Erfahrung der Personenauswahlfunktion](../../assets/images/tabs/people-picker-control-capability.png)

### <a name="code-snippet"></a><span data-ttu-id="4be28-156">Codeausschnitt</span><span class="sxs-lookup"><span data-stu-id="4be28-156">Code snippet</span></span>

<span data-ttu-id="4be28-157">**Anrufe `selectPeople` API** zum Auswählen von Personen aus einer Liste:</span><span class="sxs-lookup"><span data-stu-id="4be28-157">**Calling `selectPeople` API** to select people from a list:</span></span>

```javascript
 microsoftTeams.people.selectPeople((error: microsoftTeams.SdkError, people: microsoftTeams.people.PeoplePickerResult[]) => 
 {
    if (error) 
    {
        if (error.message) 
           {
             alert(" ErrorCode: " + error.errorCode + error.message);
           }
            else 
            {
              alert(" ErrorCode: " + error.errorCode);
            }
      }
    if (people)
     {
            output(" People length: " + people.length + " " + JSON.stringify(people));
      }
  });
```

## <a name="error-handling"></a><span data-ttu-id="4be28-158">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="4be28-158">Error handling</span></span>

<span data-ttu-id="4be28-159">Sie müssen sicherstellen, dass die Fehler in Ihrer Web-App ordnungsgemäß behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="4be28-159">You must ensure to handle the errors appropriately in your web app.</span></span> <span data-ttu-id="4be28-160">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="4be28-160">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="4be28-161">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="4be28-161">Error code</span></span> |  <span data-ttu-id="4be28-162">Fehlername</span><span class="sxs-lookup"><span data-stu-id="4be28-162">Error name</span></span>     | <span data-ttu-id="4be28-163">Bedingung</span><span class="sxs-lookup"><span data-stu-id="4be28-163">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="4be28-164">**100**</span><span class="sxs-lookup"><span data-stu-id="4be28-164">**100**</span></span> | <span data-ttu-id="4be28-165">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="4be28-165">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="4be28-166">Die API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4be28-166">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="4be28-167">**500**</span><span class="sxs-lookup"><span data-stu-id="4be28-167">**500**</span></span> | <span data-ttu-id="4be28-168">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="4be28-168">INTERNAL_ERROR</span></span> | <span data-ttu-id="4be28-169">Beim Starten der Personenauswahl ist ein interner Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="4be28-169">Internal error is encountered while launching People Picker.</span></span>|
| <span data-ttu-id="4be28-170">**4000**</span><span class="sxs-lookup"><span data-stu-id="4be28-170">**4000**</span></span> | <span data-ttu-id="4be28-171">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="4be28-171">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="4be28-172">Die API wird mit falschen oder nicht ausreichenden obligatorischen Argumenten aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="4be28-172">API is invoked with wrong or insufficient mandatory arguments.</span></span>|
| <span data-ttu-id="4be28-173">**8000**</span><span class="sxs-lookup"><span data-stu-id="4be28-173">**8000**</span></span> | <span data-ttu-id="4be28-174">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="4be28-174">USER_ABORT</span></span> |<span data-ttu-id="4be28-175">Der Benutzer hat den Vorgang abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="4be28-175">User cancelled the operation.</span></span>|
| <span data-ttu-id="4be28-176">**9000**</span><span class="sxs-lookup"><span data-stu-id="4be28-176">**9000**</span></span> | <span data-ttu-id="4be28-177">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="4be28-177">OLD_PLATFORM</span></span> | <span data-ttu-id="4be28-178">Der Benutzer befindet sich auf einem alten Plattformbuild, in dem die Implementierung der API nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="4be28-178">User is on old platform build where implementation of the API is not present.</span></span>  <span data-ttu-id="4be28-179">Das Upgrade des Builds behebt das Problem.</span><span class="sxs-lookup"><span data-stu-id="4be28-179">Upgrading the build resolves the issue.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4be28-180">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4be28-180">See also</span></span>

* [<span data-ttu-id="4be28-181">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="4be28-181">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)
* [<span data-ttu-id="4be28-182">Integrieren von QR-Code oder Strichcodescanner-Funktion in Teams</span><span class="sxs-lookup"><span data-stu-id="4be28-182">Integrate QR code or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
* [<span data-ttu-id="4be28-183">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="4be28-183">Integrate location capabilities in Teams</span></span>](location-capability.md)
