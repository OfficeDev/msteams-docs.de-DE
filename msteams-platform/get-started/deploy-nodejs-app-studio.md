---
title: Deploy your first app using Node.js in App Studio
description: Learn how to deploy Microsoft Teams apps with Node.js in App Studio
keywords: getting started node.js app studio
ms.custom: scenarios:getting-started; languages:ASP,Node.js
ms.localizationpriority: medium
ms.topic: tutorial
ms.date: 11/09/2018
---

# Update Node.js app package in App Studio

> [!TIP]
> **Try the Developer Portal**: App Studio has evolved. Configure, distribute, and manage your Teams apps with the new [Developer Portal](https://dev.teams.microsoft.com/).

App Studio is a Teams app that you can install from the Teams store. It simplifies the creation and registration of an app.

Complete the following steps to update the app package:

1. To install App Studio in Teams, select the **Apps** icon at the bottom of the left-hand bar, and search for **App Studio**:

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Select the **App Studio** tile and choose **Install**. The App Studio is installed:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. To create the app package for your Teams app, select the **Manifest editor** tab in **App Studio**:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    The sample comes with its own manifest and is designed to build an app package when the project is built. On Node.js, this is done by typing `gulp` at the command line in the root directory of the project.

    You can build the app package on Node.js by typing `gulp` at the command line in the root directory of the project.

    ```bash
    $ gulp
    [13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
    [13:39:27] Starting 'clean'...
    [13:39:27] Starting 'generate-manifest'...
    [13:39:27] Finished 'generate-manifest' after 11 ms
    [13:39:27] Finished 'clean' after 21 ms
    [13:39:27] Starting 'default'...
    Build completed. Output in manifest folder
    [13:39:27] Finished 'default' after 62 μs
    ```

    The name of the generated app package is **helloworldapp.zip**. You can search for this file if the location is not clear in the tool you are using.

1. Now to modify this app package, select **Import an existing app** in the **Manifest editor**:

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Select the **Hello World** tile for your newly imported app:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

    The following image shows the imported app package in App Studio:

    <img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

    On the left-hand side of the Manifest editor there is a list of steps. On the right-hand side there is a list of properties that need to be filled in for each step. As you started with a sample app, much of the information is already completed. The next steps enable you to update the properties of the Hello World app.

#### App details

Select **App details** under **Details**. Select the **Generate** button to create a new App ID.

Your new App ID is similar to `2322041b-72bf-459d-b107-f4f335bc35bd`.

Go through the app details in the right-hand pane including **Developer information** and **Branding** details. These details are important if you are writing a new app for distribution.

#### Tabs

It is simple to add tabs to a Teams app. The sample app already supports several tabs, and you can enable them.

##### Team tab

Your app can only have one Team tab:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In this sample, the Team tab is where your configuration page is displayed. Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu. Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` must be replaced with the URL that you used when hosting your app.

##### Personal tabs

Your app can have up to 16 tabs, including the Team tab.

Personal tabs are different from the Team tab. **Hello Tab** is already listed in the personal tabs list with a placeholder value `com.contoso.helloworld.hellotab`. Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu. The following dialog box appears:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Update the following boxes with your app URL:

- Change the **Content URL** box to `https://yourteamsapp.ngrok.io/hello`
- Change the **Website URL** box to `https://yourteamsapp.ngrok.io/hello`

Replace `yourteamsapp.ngrok.io` by the URL that you used when hosting your app.

#### Bots

It is easy to add the bots functionality to your app. The **Hello World** sample app already has a bot as part of the sample, but you must register it with Microsoft:

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

The bot that was imported from the sample does not have an associated App ID. You must create a new bot so that App Studio can create a new App ID and register it with Microsoft.

> [!NOTE]
> The App ID created by App Studio for the bot is different from the App ID created for the app. Each bot in an app requires its own App ID.

Complete the following steps to setup your bot:

1. Select **Delete** next to the imported bot in the bot list. Now there are no bots left to show. 
1. Select **Setup** to display the **Set up a bot** dialog box.

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Add a bot name **Contoso bot** and select all three check boxes under **Scope**.
1. Choose **Save** to exit the dialog box. App Studio registers your bot with Microsoft and displays your new bot in the bot list. 
1. Now open a text file in notepad and copy and paste your new bot ID into it.
1. Click **Generate New Password**, and note the password in the same text file you noted your bot App ID.
1. Update the **Bot endpoint address** to `https://yourteamsapp.ngrok.io/api/messages`, and replace `yourteamsapp.ngrok.io` with the URL that you used when hosting your app.
1. Now save your text file as you must add the information from the file to your hosted app to allow secure communication with your bot.

#### Messaging extensions

Messaging extensions let users ask for information from your service and post that information. The information is posted in the form of cards into the channel conversation. Messaging extensions appear at the bottom of the compose box.

Complete the following steps to setup your messaging extension:

1. Select **Messaging extensions** under **Capabilities** in the left-hand pane of App Studio to configure the messaging extension:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    The sample messaging extension is listed in the **Messaging Extensions** pane.

1. Select **Delete** to remove the messaging extension, select **Set up**, and follow the same steps used for [bots](#bots). The **Messaging Extension** dialog box is displayed.
1. Select the **Use existing bot** tab and **Select from one of my existing bots**.
1. Select the bot you created from the drop-down menu. Add a **Bot name** and select **Save** to close the dialog box.
1. Under the **Command** section, select **Add**. To add a search-based command, select the **Allow users to query your service for information and insert that into a message** option.
1. In the **New command** dialog box, enter the following values:

    Under **New command**:

    - **Command ID**: Enter random text
    - **Title**: Enter random title
    - **Description**: Enter random description

    Under **Parameter**:

    - **Name**: Enter the parameter name
    - **Title**: Enter the card title
    - **Description**: Enter card description

1. After you enter the information, select **Save** to close the dialog box.

#### Register your app in Teams

After entering the details of your app, complete the following steps to register your app in Teams:

1. Use **Test and distribute** of App Studio to install your app in Teams. 
1. Update your hosted application with the App ID and password for your bot. For the sample app, use the same App ID and password for both bot and messaging extension. 
1. Select **Test and distribute**  under **Finish** in the left-hand pane of App Studio:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. To upload your app to Teams, select the **Install** button under **Test and Distribute**:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

    > [!NOTE]
    > If you are unable to sideload the app, verify whether you have [enabled custom app uploading](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option).

1. Select the **Search** box in the **Add to a team** section and select a team to add the sample app. You can set up a special team for testing.
1. Select the **Install** button at the bottom of the dialog box.

    Your app is now available in Teams. However, the bot and the messaging extension will not work until you update the hosted applications environment with the App IDs and passwords.

    <img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>

## Update the credentials for your hosted app

The sample app requires the following environment variables to be set to the values you made a note of earlier:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

The environment variables are a part of your environment. Only your app's code can access them. They aren't exposed to any third parties.

If you're running the app using ngrok, you'll need to set up local environment variables. You can use Visual Studio Code to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):

``` 
{
    "type": "node",
    "request": "launch",
    "name": "Launch - Teams Debug",
    "program": "${workspaceRoot}/src/app.js",
    "cwd": "${workspaceFolder}/src",
    "env": {
        "BASE_URI": "https://yourNgrokURL.ngrok.io",
        "MICROSOFT_APP_ID": "00000000-0000-0000-0000-000000000000",
        "MICROSOFT_APP_PASSWORD": "yourBotAppPassword",
        "NODE_DEBUG": "botbuilder",
        "SUPPRESS_NO_CONFIG_WARNING": "y",
        "NODE_CONFIG_DIR": "../config"
    }
}
```

Where:

- The authorization credentials for your bot are as follows:
  - MICROSOFT_APP_ID is ID
  - MICROSOFT_APP_PASSWORD is password
- NODE_DEBUG show you what's happening in your bot in the Visual Studio Code debug console
- NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for the root directory in the `src` folder).

> [!Note]
> If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.

<a name="ConfigureTheAppTab"></a>

## Test the app capabilities in Teams

After you install the app into Teams, you need to configure it to show content.

### Test your tab in Teams

1. Go to a channel in Teams, and select the **'+'** button to add a new tab.
1. You can then choose `Hello World` from the **Add a tab** list.
1. In the configuration dialog, select the tab you want to display in the channel. Then, select **Save**. 

You can see the `Hello World` tab loaded with the tab you chose:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### Test your bot in Teams

You can now interact with the bot in Teams. Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message. This type of message is called an **\@mention**. Whatever message you send to the bot will be sent back to you as a reply:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### Test your messaging extension

**To test your messaging extension**
1. Select the three dots below the input box in your conversation view. A menu with the **'Hello World'** app is displayed.
1. Select the menu. A set of random texts is displayed. You can select one of the random texts and that is inserted into your conversation.

    <img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Select one of the random texts. The formatted card appears ready to send with your own message included at the bottom:

    <img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />


| &nbsp; | &nbsp; |
|:--- | ---:|
|[:::image type="icon" source="../assets/images/get-started/app-roadmap/next.png":::](configure-test-nodejs-app.md) | &nbsp; |
|