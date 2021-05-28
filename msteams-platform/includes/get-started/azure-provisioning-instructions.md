## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten.  Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie Teams Toolkit aus der Seitenleiste aus, indem Sie das Symbol Teams auswählen.
1. Wählen **Sie Bereitstellung in der Cloud aus.**

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

1. Wählen Sie bei Bedarf ein Abonnement aus, das für die Azure-Ressourcen verwendet werden soll.

   > [!NOTE]
   > Es gibt immer einige Azure-Ressourcen, die für das Hosten Ihrer App verwendet werden.

1. In einem Dialogfeld werden Sie gewarnt, dass beim Ausführen von Ressourcen in Azure Kosten entstehen können.  Drücken Sie **die Bereitstellung**.

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-warning.png" alt-text="Screenshot des Bereitstellungsdialogfelds.":::

   Der Bereitstellungsprozess erstellt Ressourcen in der Azure-Cloud.  Dies dauert einige Zeit.  Sie können den Fortschritt überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen.  Nach ein paar Minuten sehen Sie den folgenden Hinweis:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. Nachdem die Bereitstellung abgeschlossen ist, wählen **Sie Bereitstellen in der Cloud aus.**  Wie bei der Bereitstellung dauert dieser Prozess einige Zeit.  Sie können den Prozess überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten wird eine Abschlussbenachrichtigung zu sehen sein.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Im Terminalfenster:

1. Führen Sie `teamsfx provision` aus.

   ``` bash
   teamsfx provision
   ```

   Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement zu melden.  Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.

   > [!NOTE]
   > Es gibt immer einige Azure-Ressourcen, die für das Hosten Ihrer App verwendet werden.

1. Führen Sie `teamsfx deploy` aus.

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> **Was ist der Unterschied zwischen Bereitstellung und Bereitstellen?**
>
> Der **Schritt Bereitstellung** erstellt Ressourcen in Azure und M365 für Ihre App, aber kein Code (HTML, CSS, JavaScript usw.) wird in die Ressourcen kopiert.  Der **Schritt Bereitstellen** kopiert den Code für Ihre App in die Ressourcen, die Sie während des Bereitstellungsschritts erstellt haben.  Es ist üblich, dass sie mehrmals bereitgestellt werden, ohne neue Ressourcen bereitstellen zu müssen. Da der Bereitstellungsschritt einige Zeit in Sich nehmen kann, ist er vom Bereitstellungsschritt getrennt.

Sobald die Bereitstellungs- und Bereitstellungsschritte abgeschlossen sind:

1. Öffnen Visual Studio Code sie den Debugbereich (**STRG+Umschalt+D**  /  **bzw. ⇧-D** oder Ansicht **> Ausführen**)
1. Wählen Sie in der Dropdownliste Startkonfiguration die Option **Remote starten (Edge)** aus.
1. Drücken Sie die Schaltfläche Wiedergabe, um Ihre App zu starten – wird jetzt remote von Azure ausgeführt!
