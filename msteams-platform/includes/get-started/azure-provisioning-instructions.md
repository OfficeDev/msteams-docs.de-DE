## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten.  Zunächst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet). Anschließend wird der Code Ihrer App in die erstellten Cloudressourcen kopiert. In diesem Lernprogramm stellen Sie die Registerkarten-App bereit.
<br>
<br>
<details>
<summary>Was ist der Unterschied zwischen Bereitstellung und Bereitstellung?</summary>
<br>
Der <b>Bereitstellungsschritt</b> erstellt Ressourcen in Azure und Microsoft 365 für Ihre App, aber es wird kein Code (HTML, CSS, JavaScript usw.) in die Ressourcen kopiert. Der Schritt <b>"Bereitstellen"</b> kopiert den Code für Ihre App in die Ressourcen, die Sie während des Bereitstellungsschritts erstellt haben. Es ist üblich, mehrere Male bereitzustellen, ohne neue Ressourcen bereitzustellen. Da der Bereitstellungsschritt einige Zeit dauern kann, ist er vom Bereitstellungsschritt getrennt.
</details>
<br>

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

Wählen Sie das Teams-Toolkit-Symbol :::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: in der Visual Studio Code-Randleiste aus.

1. Wählen Sie **"In der Cloud bereitstellen" aus**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot, der die Auswahl der Bereitstellung in der Cloud unter Dem Teams-Toolkit zeigt.":::

1. Wählen Sie ein Abonnement aus, das für die Azure-Ressourcen verwendet werden soll.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/select-resource.png" alt-text="Screenshot des Abonnements, das für die Azure-Ressourcen verwendet werden soll.":::

   > [!NOTE]
   > Ihre App wird mitHilfe von Azure-Ressourcen gehostet.

    In einem Dialogfeld werden Sie gewarnt, dass beim Ausführen von Ressourcen in Azure Möglicherweise Kosten anfallen.

1. Wählen Sie **"Bereitstellen" aus**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provision-warning.png" alt-text="Screenshot mit einem Dialogfeld, in dem Kosten entstehen können, wenn Ressourcen in Azure ausgeführt werden.":::

   Der Bereitstellungsprozess erstellt Ressourcen in der Azure-Cloud. Es kann einige Zeit dauern. Sie können den Fortschritt überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten wird der folgende Hinweis angezeigt:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-successmsgext.png" alt-text="Screenshot mit einer Benachrichtigung, die &quot;hellomsg&quot; anzeigt, die erfolgreich in der Cloud bereitgestellt wurde.":::

    Wenn Sie möchten, können Sie die bereitgestellten Ressourcen anzeigen. Für dieses Lernprogramm müssen Sie keine Ressourcen anzeigen.

    Die bereitgestellte Ressource wird im Abschnitt **"Umgebung"** angezeigt.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provisioned-resources-env.png" alt-text="Screenshot der Ressource, die im Abschnitt &quot;Umgebung&quot; bereitgestellt wird.":::

1. Wählen Sie " **In der Cloud bereitstellen** " aus dem **Bereitstellungsbereich** aus, nachdem die Bereitstellung abgeschlossen ist.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="Screenshot, der die Bereitstellung in der Cloud zeigt.":::

   Wie bei der Bereitstellung dauert die Bereitstellung einige Zeit. Sie können den Prozess überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten wird ein Abschlusshinweis angezeigt.

Jetzt können Sie den gleichen Prozess verwenden, um Ihre Bot- und Nachrichtenerweiterungs-Apps in Azure bereitzustellen.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Im Terminalfenster:

1. Ausführen `teamsfx provision`.

   ``` bash
   teamsfx provision
   ```

   Wenn Sie dazu aufgefordert werden, wählen Sie ein Azure-Abonnement aus, um Azure-Ressourcen zu verwenden.

   > [!NOTE]
   > Ihre App wird mitHilfe von Azure-Ressourcen gehostet.

1. Ausführen `teamsfx deploy`.

   ``` bash
   teamsfx deploy
   ```

---

## <a name="run-the-deployed-app"></a>Ausführen der bereitgestellten App

Sobald die Bereitstellungs- und Bereitstellungsschritte abgeschlossen sind:

1. Öffnen Sie den Debugbereich (**STRG+UMSCHALT+D** / **⌘⇧-D** oder **> Ausführen anzeigen**) aus Visual Studio Code.
1. Wählen Sie in der Dropdownliste "Startkonfiguration" die Option " **Remote starten(Edge)** " aus.
1. Wählen Sie das **Startdebugging (F5)** aus, um Ihre App über Azure zu starten.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="Screenshot der Remotestart-App.":::

1. Klicken Sie auf **Hinzufügen**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/add-mex-app.png" alt-text="Screenshot der installierten App.":::

   Das Toolkit zeigt eine Meldung an, die angibt, dass die App zu Teams hinzugefügt wurde.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/mex-added-msg.png" alt-text="Screenshot mit einer Meldung zum Testen der App jetzt oder später":::

    - Wenn Sie " **Herunterladen**" auswählen, können Sie die App später aus der Liste der quergeladenen Apps ausprobieren.
    - Wenn Sie **"Testen**" auswählen, lädt Teams Ihre App.

   Ihre App wird auf der Azure-Website geladen.

1. Wählen Sie **"Testen" aus**.

   Die Nachrichtenerweiterungs-App wird in einer Chat-Bot-App geladen.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/app-added-mex1.png" alt-text="Screenshot einer in Teams quergeladenen App":::
