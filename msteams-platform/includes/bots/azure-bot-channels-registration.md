1. Wählen Sie im [Azure-Portal](https://ms.portal.azure.com/#home)unter Azure Services die Option **Ressource erstellen**aus.
1. Geben Sie in das Suchfeld "bot" ein. Wählen Sie in der Dropdownliste die Option **bot Channels Registration**aus.
1. Klicken Sie auf die Schaltfläche **Erstellen** .
1. Geben Sie im Blade für die **bot-Kanal Registrierung** die angeforderten Informationen zu Ihrem bot an.
1. Lassen Sie das Feld **Messaging-Endpunkt** jetzt leer, geben Sie nach der Bereitstellung des bot die erforderliche URL ein. Die folgende Abbildung zeigt ein Beispiel für die Registrierungseinstellungen:

    ![Registrierung von bot-App-Kanälen](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Klicken Sie auf **Microsoft App-ID und Kennwort** , und erstellen Sie dann **neue**.
1. Klicken Sie **im Link zum App-Registrierungs Portal auf APP-ID erstellen** .
1. Klicken Sie im Fenster angezeigte **App-Registrierung** oben links auf die Registerkarte **neue Registrierung** .
1. Geben Sie den Namen der bot-Anwendung ein, die Sie registrieren, wir haben *BotTeamsAuth* verwendet (Sie müssen ihren eigenen eindeutigen Namen auswählen).
1. Wählen Sie für die **unterstützten Kontotypen** *Konten in einem beliebigen Organisations Verzeichnis (Azure AD Verzeichnis – Multimandanten) und persönliche Microsoft-Konten (beispielsweise Skype, Xbox)* aus.
1. Klicken Sie auf die Schaltfläche **registrieren** . Sobald abgeschlossen, zeigt Azure die Übersichts *Seite für die Anwendung* an.
1. Kopieren und speichern Sie den Wert der **Anwendungs-ID (Client)** in einer Datei.
1. Klicken Sie im linken Bereich auf **Zertifikat und Geheimnisse**.
    1. Klicken Sie unter *Client Geheimnisse*auf **neuer geheimer Client Schlüssel**.
    1. Fügen Sie eine Beschreibung hinzu, um dieses Geheimnis von anderen Personen zu identifizieren, die Sie für diese APP möglicherweise erstellen müssen.
    1. Festlegen *läuft* auf Ihre Auswahl ab.
    1. Klicken Sie auf **Hinzufügen**.
    1. Kopieren Sie den geheimen Client Schlüssel, und speichern Sie ihn in einer Datei.
1. Wechseln Sie zurück zum **Fenster bot-Kanal Registrierung** , und kopieren Sie die *App-ID* und den *geheimen Client Schlüssel* in die Felder **Microsoft App-ID** und **Kennwort** .
1. Klicken Sie auf **OK**.
1. Klicken Sie schließlich auf **Erstellen**.
