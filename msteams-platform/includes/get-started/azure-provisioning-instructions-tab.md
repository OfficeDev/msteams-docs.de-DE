## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten. Zunächst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet). Anschließend wird der Code Ihrer App in die erstellten Cloudressourcen kopiert. In diesem Tutorial stellen Sie die Registerkarten-App bereit.
<br>
<br>
<details>
<summary>Was ist der Unterschied zwischen Bereitstellen und Bereitstellen?</summary>
<br>
Im Schritt <b>Bereitstellen</b> werden Ressourcen in Azure und Microsoft 365 für Ihre App erstellt, aber es wird kein Code (HTML, CSS, JavaScript usw.) in die Ressourcen kopiert. Der Schritt <b>Bereitstellen</b> kopiert den Code für Ihre App in die Ressourcen, die Sie während des Bereitstellungsschritts erstellt haben. Es ist üblich, mehrmals bereitzustellen, ohne neue Ressourcen bereitzustellen. Da der Bereitstellungsschritt einige Zeit in Anspruch nehmen kann, ist er vom Bereitstellungsschritt getrennt.
</details>
<br>

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

Wählen Sie das Teams-Toolkit-Symbol :::image type="icon" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: in der Visual Studio Code-Randleiste aus.

1. Wählen Sie **Bereitstellung in der Cloud** aus.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot: Bereitstellungsbefehle":::

1. Wählen Sie ein beliebiges vorhandenes Abonnement aus.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/select-subscription.png" alt-text="Screenshot: Auswahl eines vorhandenen Abonnements":::

1. Wählen Sie eine Ressourcengruppe aus, die für die Azure-Ressourcen verwendet werden soll.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/select-resource.png" alt-text="Screenshot: Ressourcen für die Bereitstellung":::

   > [!NOTE]
   > Ihre App wird mithilfe von Azure-Ressourcen gehostet.
   >
   >Weitere Informationen finden Sie unter [Erstellen einer Ressourcengruppe.](/azure/azure-resource-manager/management/manage-resource-groups-portal)

    Ein Dialogfeld warnt Sie, dass beim Ausführen von Ressourcen in Azure Möglicherweise Kosten anfallen.

1. Wählen Sie **Bereitstellen** aus.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provision-warning.png" alt-text="Screenshot: Bereitstellung des Dialogfelds":::

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-confirm1.png" alt-text="Screenshot: Auswahl des Abonnements":::

   Beim Bereitstellungsprozess werden Ressourcen in der Azure-Cloud erstellt. Es kann einige Zeit dauern. Sie können den Fortschritt überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen. Nach einigen Minuten wird der folgende Hinweis angezeigt:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-provision-successmsgext.png" alt-text="Screenshot: Erfolgreiche Bereitstellung der Ressource in der Cloud":::

    Wenn Sie möchten, können Sie die bereitgestellten Ressourcen anzeigen. Für dieses Tutorial müssen Sie keine Ressourcen anzeigen.

    Die bereitgestellte Ressource wird im Abschnitt **Umgebung** angezeigt.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/provisioned-resources-env.png" alt-text="Screenshot der bereitgestellten Ressource.":::

1. Wählen Sie nach Abschluss der Bereitstellung im Bereich **Bereitstellung** die Option **In der Cloud** bereitstellen aus.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/deploy-cloud.png" alt-text="Screenshot: Bereitstellung in der Cloud":::

   Wie bei der Bereitstellung dauert die Bereitstellung einige Zeit. Sie können den Prozess überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen. Nach einigen Minuten wird ein Abschlusshinweis angezeigt.

Jetzt können Sie den gleichen Prozess verwenden, um Ihre Bot- und Nachrichtenerweiterungs-Apps in Azure bereitzustellen.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Im Terminalfenster:

1. Führen Sie `teamsfx provision` aus.

   ``` bash
   teamsfx provision
   ```

   Wenn Sie dazu aufgefordert werden, wählen Sie ein Azure-Abonnement aus, um Azure-Ressourcen zu verwenden.

1. Führen Sie `teamsfx deploy` aus.

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> Ihre App wird mithilfe von Azure-Ressourcen gehostet.

## <a name="run-the-deployed-app"></a>Ausführen der bereitgestellten App

Nach Abschluss der Bereitstellungs- und Bereitstellungsschritte:

1. Öffnen Sie den Debugbereich (**STRG+UMSCHALT+D** / **⌘⇧-D** oder **Ansicht > Ausführen**) in Visual Studio Code.
1. Wählen Sie **remote (Edge) starten aus** der Dropdownliste Startkonfiguration aus.
1. Wählen Sie **Debuggen starten (F5)** aus, um Ihre App aus Azure zu starten.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/launch-remote.png" alt-text="Screenshot: Remotestart der App":::

1. Wählen Sie **Hinzufügen** aus, wenn Sie aufgefordert werden, die App in Teams querzuladen.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/remote-app-client.png" alt-text="Screenshot, der zeigt, dass eine App installiert wird.":::

    Herzlichen Glückwunsch, Ihre erste Registerkarten-App wird in Ihrer Azure-Umgebung ausgeführt!

   :::image type="content" source="~/assets/images/teams-toolkit-v2/deploy-azure/azure-deployed-apptab.png" alt-text="Screenshot: Meldung zum jetzt oder späteren Testen der App":::
