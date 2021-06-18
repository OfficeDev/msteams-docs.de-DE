## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten.  Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie das Teams-Toolkit in der Seitenleiste aus, indem Sie das Symbol "Teams" auswählen.
1. Wählen Sie **"Bereitstellung in der Cloud" aus.**

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

1. Wählen Sie bei Bedarf ein Abonnement aus, das für die Azure-Ressourcen verwendet werden soll.

   > [!NOTE]
   > Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.

1. In einem Dialogfeld werden Sie gewarnt, dass Kosten auftreten können, wenn Ressourcen in Azure ausgeführt werden.  Drücken **Sie "Bereitstellen".**

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-warning.png" alt-text="Screenshot des Bereitstellungsdialogfelds.":::

   Der Bereitstellungsprozess erstellt Ressourcen in der Azure-Cloud. Dies dauert einige Zeit. Sie können den Fortschritt überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten sehen Sie den folgenden Hinweis:

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. Wählen Sie nach Abschluss der Bereitstellung die Option **"In der Cloud bereitstellen"** aus.  Wie bei der Bereitstellung dauert dieser Vorgang einige Zeit.  Sie können den Prozess überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen. Nach ein paar Minuten wird ein Abschlusshinweis angezeigt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

In Ihrem Terminalfenster:

1. Führen Sie `teamsfx provision` aus.

   ``` bash
   teamsfx provision
   ```

   Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement anzumelden. Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.

   > [!NOTE]
   > Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.

1. Führen Sie `teamsfx deploy` aus.

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> **Was ist der Unterschied zwischen Bereitstellung und Bereitstellung?**
>
> Der **Bereitstellungsschritt** erstellt Ressourcen in Azure und M365 für Ihre App, aber kein Code (HTML, CSS, JavaScript usw.) wird in die Ressourcen kopiert. Der Schritt **"Bereitstellen"** kopiert den Code für Ihre App in die Ressourcen, die Sie während des Bereitstellungsschritts erstellt haben. Es ist üblich, mehrmals bereitzustellen, ohne neue Ressourcen bereitzustellen. Da der Bereitstellungsschritt einige Zeit in Anspruch nehmen kann, ist er vom Bereitstellungsschritt getrennt.

Sobald die Bereitstellungs- und Bereitstellungsschritte abgeschlossen sind:

1. Öffnen Sie in Visual Studio Code den Debugbereich (**STRG+UMSCHALT+D**  /  **⌘⇧-D** oder **Ansicht > Ausführen)**
1. Wählen Sie **"Remote starten (Edge)"** in der Startkonfigurations-Dropdownliste aus.
1. Drücken Sie die Play-Taste, um Ihre App zu starten – jetzt remote in Azure ausgeführt!
