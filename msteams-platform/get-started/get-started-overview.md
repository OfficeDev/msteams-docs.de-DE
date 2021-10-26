---
title: Get started - Overview
description: Overview to Get started for Microsoft Teams Developer Documentation
ms.localizationpriority: medium
ms.topic: reference
keywords: Microsoft Teams developer samples
---
# Get started

Welcome to Get started for building and deploying customized apps for Microsoft Teams!

Walk through the steps to build a basic, real-world Teams app. The Get started also introduces you to common tools, fundamental concepts, and more advanced features.

Here's an idea of what you'll learn:

- Get up and running quickly with the Microsoft Teams Toolkit (a Visual Studio Code extension).
- Get experience with the Toolkit and SDKs.
- Configure and build different types of Teams apps.

Let's take a quick glance at the build environment options you can choose from, and the road-map to building and deploying a Teams app.

:::image type="content" source="../assets/images/get-started/gs-overview-build-options.png" alt-text="Illustration showing basic steps to build and deploy a Teams app.":::

## App capabilities and development tools

Depending on the capabilities you want for your app, choose an appropriate development tool set.

| App capabilities | User interactions | Recommended tools | SDKs | Technology stacks / Languages |
|--------|-------------|--------|--------|--------|
| Tabs | A full-screen embedded web experience. | VS Code with Teams Toolkit extension, or [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) if you prefer using CLI | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) for core libs & [Teams client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) for UI functionalities | Web technology in general, HTML, CSS, and JavaScript (incl. React) |
| Bots | A chat bot that converses with members. | VS Code with Teams Toolkit extension, or [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) & [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C#, etc. |
| Messaging extensions | Shortcuts for inserting external content into a conversation or taking action on messages. | VS Code with Teams Toolkit extension, or [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) & [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C#, etc. |

*You aren't limited to using these particular stacks!*

If you are already familiar with Yeoman workflow, you may prefer using [YoTeams Yeoman Generator](https://github.com/pnp/generator-teams/blob/master/docs/docs/tutorials/build-your-first-microsoft-teams-app.md) to build your apps.

> [!NOTE]
> If you have been using App Studio, we recommend that you'd try the Developer Portal to configure, distribute, and manage your Teams apps.

This tutorial will walk you through the process with recommended tools, as well as a few other options.

## Build your first Teams app

Now, let's build your first Teams app. But first, pick your language (or framework) and prepare your development environment.

> [!div class="nextstepaction"]
> [Build a Teams app with JavaScript using React](../sbs-gs-javascript.yml)

> [!div class="nextstepaction"]
> [Build a Teams app with Blazor](../sbs-gs-blazor.yml)

> [!div class="nextstepaction"]
> [Build a Teams app with SPFx](../sbs-gs-spfx.yml)

> [!div class="nextstepaction"]
> [Build a Teams app with C# or .NET](../sbs-gs-csharp.yml)

> [!div class="nextstepaction"]
> [Build a Teams app with Node.js](../sbs-gs-nodejs.yml)

