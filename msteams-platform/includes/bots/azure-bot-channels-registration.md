1. Wählen Sie im [Azure-Portal](https://ms.portal.azure.com/#home) unter "Azure-Dienste" **Ressource erstellen** aus.
1. Geben Sie "bot" in das Suchfeld ein. Und wählen Sie in der Dropdownliste **Registrierung von Bot-Kanälen** aus.
1. Wählen Sie die Schaltfläche **Erstellen** aus.
1. Geben Sie im Bereich **Registrierung von Bot-Kanälen** die angeforderten Informationen zu Ihrem Bot ein.
1. Lassen Sie das Feld **Messaging-Endpunkt** im Moment leer; Sie werden die erforderliche URL nach der Bereitstellung des Bots eingeben. Die folgende Abbildung zeigt ein Beispiel für die Registrierungseinstellungen:

    ![Registrierung von Bot-App-Kanälen](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Klicken Sie auf **Microsoft App-ID und Kennwort** und dann auf **Neu erstellen**.

    ![Erstellen einer Microsoft App-ID](../../assets/images/authentication/CreateMicrosoftAppID.png) ![Erstellen einer neuen Microsoft-App-ID](../../assets/images/authentication/CreateNewMicrosoftAppID.png)    

1. Klicken Sie auf **App-ID im App-Registrierungsportal erstellen**.

   ![App-Registrierungen](../../assets/images/authentication/AppRegistration.png)
   
1. Klicken Sie im angezeigten Fenster **App-Registrierung** oben links auf die Registerkarte **Neue Registrierung**.
1. Geben Sie den Namen der Bot-Anwendung ein, die Sie registrieren möchten; wir haben *BotTeamsAuth* verwendet (Sie müssen einen eigenen eindeutigen Namen eingeben).
1. Wählen Sie für **Unterstützte Kontotypen** die Option *Konten in allen Organisationsverzeichnissen (alle Azure AD-Verzeichnisse – mehrinstanzenfähig) und persönliche Microsoft-Konten (z. B. Skype, Xbox)* aus.
1. Klicken Sie auf die **Start**-Schaltfläche. Wenn der Vorgang abgeschlossen ist, wird in Azure die *Übersichtsseite* für die Anwendung angezeigt.
1. Kopieren Sie den **Application (client) ID**-Wert und speichern Sie ihn in einer Datei.
1. Klicken Sie im linken Bereich auf **Zertifikat und geheime Schlüssel**.
    1. Klicken Sie unter *Geheime Clientschlüssel* auf **Neuer geheimer Clientschlüssel**.
    1. Fügen Sie eine Beschreibung hinzu, um diesen Schlüssel von anderen zu unterscheiden, die Sie möglicherweise für diese App erstellen müssen.
    1. Legen Sie das *Ablaufdatum* auf das gewünschte Datum fest.
    1. Klicken Sie auf **Hinzufügen**.
    1. Kopieren Sie den geheimen Clientschlüssel, und speichern Sie ihn in einer Datei.
1. Wechseln Sie zurück zum Fenster **Registrierung von Bot-Kanälen**, und kopieren Sie die *App-ID* und den *geheimen Clientschlüssel* jeweils in die Felder **Microsoft App-ID** und **Kennwort**.
1. Klicken Sie auf **OK**.
1. Klicken Sie abschließend auf **Erstellen**.

Nachdem Azure die Registrierungsressource erstellt hat, wird diese in der Liste der Ressourcengruppen aufgeführt.  

![Registrierungsgruppe von Bot-App-Kanälen](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

Sobald Ihre Bot-Kanalregistrierung erstellt wurde, müssen Sie den Microsoft Teams-Kanal aktivieren.

1. Wählen Sie im [Azure-Portal](https://ms.portal.azure.com/#home) unter "Azure-Dienste" die soeben erstellte **Bot-Kanalregistrierung** aus.
1. Klicken Sie im linken Bereich auf **Kanäle**.
1. Klicken Sie auf das Microsoft Teams-Symbol, und wählen Sie dann **Speichern** aus.
