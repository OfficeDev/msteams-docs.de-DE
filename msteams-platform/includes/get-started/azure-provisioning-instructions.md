## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten.  Zunächst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet). Anschließend wird der Code Ihrer App in die erstellten Cloudressourcen kopiert. In diesem Lernprogramm stellen Sie die Registerkarten-App bereit.

> <details>
> <summary>Was ist der Unterschied zwischen Bereitstellung und Bereitstellung?</summary>
>
> Der **Bereitstellungsschritt** erstellt Ressourcen in Azure und Microsoft 365 für Ihre App, aber kein Code (HTML, CSS, JavaScript usw.) wird in die Ressourcen kopiert. Der Schritt **"Bereitstellen** " kopiert den Code für Ihre App in die Ressourcen, die Sie während des Bereitstellungsschritts erstellt haben. Es ist üblich, mehrmals bereitzustellen, ohne neue Ressourcen bereitzustellen. Da der Bereitstellungsschritt einige Zeit in Anspruch nehmen kann, ist er vom Bereitstellungsschritt getrennt.
</details>

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

Wählen Sie das Symbol Teams Toolkits :::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: in der Visual Studio Code-Randleiste aus.

1. Wählen Sie **"Bereitstellung in der Cloud" aus**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle" border="false":::

1. Wählen Sie ein Abonnement aus, das für die Azure-Ressourcen verwendet werden soll.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/select-resource.png" alt-text="Screenshot der Ressourcen für die Bereitstellung" border="false":::

   > [!NOTE]
   > Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.

    In einem Dialogfeld werden Sie gewarnt, dass beim Ausführen von Ressourcen in Azure Möglicherweise Kosten anfallen.

1. Wählen Sie **"Bereitstellen" aus**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provision-warning.png" alt-text="Screenshot des Bereitstellungsdialogfelds." border="false":::

   Der Bereitstellungsprozess erstellt Ressourcen in der Azure-Cloud. Es kann einige Zeit dauern. Sie können den Fortschritt überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten sehen Sie den folgenden Hinweis:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-success.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;." border="false":::

    Wenn Sie möchten, können Sie die bereitgestellten Ressourcen anzeigen. Für dieses Lernprogramm müssen Sie keine Ressourcen anzeigen.

    Die bereitgestellte Ressource wird im Abschnitt **"Umgebung"** angezeigt.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provisioned-resources-env.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;." border="false":::

1. Wählen Sie " **In der Cloud bereitstellen** " im **Bereitstellungsbereich** aus, nachdem die Bereitstellung abgeschlossen ist.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="Screenshot der Stelle, auf die sie klicken können, um sie in der Cloud bereitzustellen." border="false":::

   Wie bei der Bereitstellung dauert die Bereitstellung einige Zeit. Sie können den Prozess überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten wird ein Abschlusshinweis angezeigt.

Jetzt können Sie den gleichen Prozess verwenden, um Ihre Bot- und Nachrichtenerweiterungs-Apps in Azure bereitzustellen.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

In Ihrem Terminalfenster:

1. Ausführen `teamsfx provision`.

   ``` bash
   teamsfx provision
   ```

   Wenn Sie dazu aufgefordert werden, wählen Sie ein Azure-Abonnement aus, um Azure-Ressourcen zu verwenden.

   > [!NOTE]
   > Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.

1. Ausführen `teamsfx deploy`.

   ``` bash
   teamsfx deploy
   ```

---

## <a name="run-the-deployed-app"></a>Ausführen der bereitgestellten App

Sobald die Bereitstellungs- und Bereitstellungsschritte abgeschlossen sind:

1. Öffnen Sie den Debugbereich (**STRG+UMSCHALT+D** / **⌘⇧-D** oder **Ansicht > Ausführen**) aus Visual Studio Code.
1. Wählen Sie **"Remote starten (Edge)"** in der Startkonfigurations-Dropdownliste aus.
1. Wählen Sie die Schaltfläche "Wiedergeben" aus, um Ihre App über Azure zu starten.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="Screenshot der Remotestart-App." border="false":::

1. Wählen Sie **Hinzufügen**.
   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/remote-app-client.png" alt-text="Screenshot der installierten App." border="false":::

   Ihre App wird auf der Azure-Website geladen.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/azure-deployed-app.png" alt-text="Screenshot der installierten App." border="false":::

    Herzlichen Glückwunsch! Ihre Registerkarten-App wird jetzt remote über Azure ausgeführt!
