---
wts:
    title: '06 � Implementieren eines Azure IoT Hubs'
    module: 'Modul 02 � Core Azure Services'
---
# 06 � Implementieren eines Azure IoT Hub

In dieser exemplarischen Vorgehensweise konfigurieren wir einen neuen Azure IoT Hub im Azure-Portal und authentifizieren dann eine Verbindung zu einem IoT-Ger�t mit Hilfe des Raspberry Pi-Ger�tesimulators. Sensordaten und Nachrichten werden vom Raspberry Pi-Simulator an Ihren Azure IoT Hub �bergeben, und Sie sehen Metriken f�r die Meldungsaktivit�t im Azure-Portal.

# Aufgabe�1: Erstellen eines IoT-Hubs 

In dieser Aufgabe erstellen wir einen IoT-Hub. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **IoT Hub** und w�hlen Sie diese Option aus; anschlie�end klicken Sie auf **+ Hinzuf�gen**.

3. Auf der Registerkarte **Grundlagen** des Blattes **IoT-Hub** f�llen Sie die Felder mit den folgenden Details aus (ersetzen Sie **xxxx** im Namen des Speicherkontos mit Buchstaben und Ziffern, so dass der Name global eindeutig ist):

    | Einstellungen | Wert |
    |--|--|
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe |  **myRGIoT** (Neu erstellen)|
    | Region | **USA, Osten** |
    | IoT Hub-Name | **my-hub-groupxxxx** |
    | | |	

4. Wechseln Sie zur Registerkarte **Gr��e und Skalierung**, und verwenden Sie die Dropdownliste, um die **Preis- und Skalierungsebene** festzulegen auf **S1: Standard-Tarif**. 

5. Klicken Sie auf die Schaltfl�che **�berpr�fen + Erstellen**.

6. Klicken Sie auf die Schaltfl�che **Erstellen**, um mit der Erstellung Ihrer neuen Azure IoT Hub-Instanz zu beginnen.

7. Warten Sie, bis die Azure IoT Hub-Instanz bereitgestellt ist. 

# Aufgabe�2: IoT-Ger�t hinzuf�gen

In dieser Aufgabe f�gen wir dem IoT-Hub ein IoT-Ger�t hinzu. 

1. Wenn die Bereitstellung abgeschlossen ist, klicken Sie im Blatt �Bereitstellung� auf **Zur Ressource wechseln**. Alternativ suchen Sie auf dem Blatt **Alle Dienste** nach **IoT Hub**, w�hlen diese Option aus und suchen Ihre neue IoT Hub-Instanz

	![Screenshot der Benachrichtigungen �Die Bereitstellung wird ausgef�hrt� und �Bereitstellung erfolgreich� im Azure-Portal.](../images/0601.png)

2. Scrollen Sie zum Hinzuf�gen eines neuen IoT-Ger�ts nach unten zum Abschnitt **Explorer**, und klicken Sie auf **IoT-Ger�te**. Klicken Sie dann auf **+ Neu**.

	![Screenshot des Bereichs �IoT-Ger�te�, der auf dem IoT Hub-Navigationsblatt im Azure-Portal hervorgehoben ist. Die Schaltfl�che �Neu� ist hervorgehoben, um zu veranschaulichen, wie dem IoT-Hub eine neue IoT-Ger�teidentit�t hinzugef�gt wird.](../images/0602.png)

3. Geben Sie einen Namen f�r Ihr neues IoT-Ger�t ein ( **myRaspberryPi**), und klicken Sie auf die Schaltfl�che **Speichern**. Dadurch wird eine neue IoT-Ger�teidentit�t in Ihrem Azure IoT Hub erstellt.

4. Wenn Sie Ihr neues Ger�t nicht sehen, **Aktualisieren** Sie die Seite �IoT-Ger�te�. 

5. W�hlen Sie **myRaspberryPi** aus, und kopieren Sie den Wert von **Prim�re Verbindungszeichenfolge**. Mit diesem Schl�ssel werden Sie in der n�chsten Aufgabe eine Verbindung zum Raspberry Pi-Simulator authentifizieren.

	![Screenshot der Seite �Prim�re Verbindungszeichenfolge� mit hervorgehobenem Kopiersymbol.](../images/0603.png)

# Aufgabe�3: Ger�t mit dem Raspberry Pi-Simulator testen

In dieser Aufgabe testen wir unser Ger�t mit dem Raspberry Pi-Simulator. 

1. �ffnen Sie im Webbrowser eine neue Registerkarte, und wechseln Sie zum [Online-Raspberry Pi-Simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/#Getstarted). 

2. Lesen Sie mehr �ber den Raspberry Pi-Simulator. Wenn ein �bersichts-Popup angezeigt wird, w�hlen Sie �**X**�, um das Fenster zu schlie�en.

3. Suchen Sie im Codebereich auf der rechten Seite die Zeile mit der Zeichenfolge �const connectionString =�. Ersetzen Sie dies durch die Verbindungszeichenfolge, die Sie aus dem Azure-Portal kopiert haben. Beachten Sie, dass die Verbindungszeichenfolge die Eintr�ge DeviceId (**myRaspberryPi**) und SharedAccessKey enth�lt.

	![Screenshot des Codierungsbereichs im Raspberry Pi-Simulator.](../images/0604.png)

4. Klicken Sie auf **Ausf�hren** (unterhalb des Codebereichs), um die Anwendung auszuf�hren. Die Konsolenausgabe sollte die Sensordaten und Nachrichten anzeigen, die vom Raspberry Pi-Simulator an Ihren Azure IoT Hub gesendet werden. Daten und Nachrichten werden jedes Mal gesendet, wenn die Raspberry Pi-Simulator-LED blinkt. 

	![Screenshot der Raspberry Pi.Simulator-Konsole.  Die Konsolenausgabe zeigt Sensordaten und Nachrichten an, die vom Raspberry Pi-Simulator an Azure IoT Hub gesendet wurden.](../images/0605.png)

5. Klicken Sie auf **Beenden**, um das Senden von Daten zu beenden.

6. Kehren Sie zum Azure-Portal und zu Ihrem IoT-Hub zur�ck.

7. Wechseln Sie zum IoT Hub-Blatt **�berblick** und scrollen Sie nach unten zur Information **IoT Hub-Nutzung**.

	![Screenshot der Metriken im IoT-Hub-Nutzungsbereich des Azure-Portals.](../images/0606.png)


Herzlichen Gl�ckwunsch! Sie haben Azure IoT Hub so eingerichtet, dass Sensordaten von einem IoT-Ger�t erfasst werden.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
