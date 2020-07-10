---
wts:
    title: '01 � Erstellen eines virtuellen Computers im Portal'
    module: 'Modul 02 � Core Azure Services'
---
# 01 � Erstellen eines virtuellen Computers im Portal

In dieser schrittweisen Anleitung erstellen wir einen virtuellen Computer im Azure-Portal, stellen eine Verbindung zum virtuellen Computer her, installieren die Webserverrolle und testen dann. 

**Hinweis**: Nehmen Sie sich bei dieser exemplarischen Vorgehensweise die Zeit, auf die Informationssymbole zu klicken und diese zu lesen. 

# Aufgabe�1: Den virtuellen Computer erstellen

In dieser Aufgabe erstellen wir einen virtuellen Windows Server 2019 Datacenter-Computer. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Virtuelle Computer**, und w�hlen Sie diese Option aus. Klicken Sie dann auf **+ Hinzuf�gen**.

3. Auf der Registerkarte **Grundlagen** geben Sie die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellungen | Werte |
    |  -- | -- |
    | Abonnement | **W�hlen Sie Ihr Abonnement**|
    | Ressourcengruppe | **myRGVM** (Neu erstellen) |
    | Name des virtuellen Computers | **myVM** |
    | Ort | **(US) East US**|
    | Bild | **Windows Server 2019 Datacenter**|
    | Gr��e | Standard D2s v3|
    | Benutzername des Administratorkontos | **azureuser** |
    | Kennwort f�r das Administratorkonto | **Pa$$w0rd1234**|
    | Regeln f�r eingehende Ports � Ports ausw�hlen zulassen | **RDP (3389)** und **HTTP (80)**|
    | | |

4. Wechseln Sie zur Registerkarte �Verwaltung�, und w�hlen Sie im Abschnitt **�berwachung** die folgende Einstellung aus:

    | Einstellungen | Werte |
    | -- | -- |
    | Startdiagnose | **Aus**|
    | | |

5. �bernehmen Sie die verbleibenden Standardeinstellungen, und klicken Sie dann auf die Schaltfl�che **�berpr�fen + Erstellen** am unteren Rand der Seite.

6. Sobald die Validierung bestanden ist, klicken Sie auf die Schaltfl�che **Erstellen**. Die Bereitstellung des virtuellen Computers kann zwischen f�nf und sieben Minuten dauern.

7. Sie erhalten Updates auf der Bereitstellungsseite und �ber den Bereich **Benachrichtigungen** (das Glockensymbol im obersten Men�).

# Aufgabe�2: Eine Verbindung zum virtuellen Computer herstellen

In dieser Aufgabe stellen wir �ber RDP eine Verbindung zu unserem neuen virtuellen Computer her. 

1. Suchen Sie nach **myVM**, und w�hlen Sie Ihren neuen virtuellen Computer aus.

    **Hinweis**: Sie k�nnen auch den Link **Zu Ressource wechseln** auf der Bereitstellungsseite oder den Link zu der Ressource im Bereich **Benachrichtigung** verwenden.

2. Klicken Sie auf dem Blatt **�berblick** des virtuellen Computers auf die Schaltfl�che **Verbinden**.

    ![Screenshot der Eigenschaften des virtuellen Computers mit hervorgehobener Schaltfl�che �Verbinden�.](../images/0101.png)

    **Hinweis**: In den folgenden Anweisungen erfahren Sie, wie Sie von einem Windows-Computer aus eine Verbindung zu Ihrem virtuellen Computer herstellen. Auf einem Mac ben�tigen Sie einen RDP-Client wie diesen Remotedesktopclient aus dem Mac App Store. Auf einem Linux-Computer k�nnen Sie einen Open Source-RDP-Client verwenden.

2. Auf der Seite **Verbindung zum virtuellen Computer herstellen** behalten Sie die Standardoptionen f�r die Verbindung mit der �ffentlichen IP-Adresse �ber Port 3389 bei und klicken auf **RDP-Datei herunterladen**.

3. **�ffnen** Sie die heruntergeladene RDP-Datei, und klicken Sie auf **Verbinden**, wenn Sie dazu aufgefordert werden. 

    ![Screenshot der Eigenschaften des virtuellen Computers mit hervorgehobener Schaltfl�che �Verbinden�. ](../images/0102.png)

4. W�hlen Sie im Fenster **Windows-Sicherheit** die Option **Weitere Optionen** und dann **Anderes Konto verwenden** aus. Geben Sie den Benutzernamen (.\azureuser) und das Kennwort (Pa$$w0rd1234) an. Klicken Sie auf **OK**, um die Verbindung herzustellen.

    ![Screenshot des Windows-Sicherheitsdialogfelds mit Auswahl von �Ein anderes Konto verwenden� und der Eingabe des Benutzernamens �azure user� sowie eines Kennworts.](../images/0103.png)

5. M�glicherweise erhalten Sie w�hrend des Anmeldevorgangs eine Zertifikatwarnung. Klicken Sie auf **Ja**, um die Verbindung herzustellen und eine Verbindung zu Ihrem bereitgestellten virtuellen Computer herzustellen. Sie sollten erfolgreich eine Verbindung herstellen.

    ![Screenshot des Dialogfelds �Zertifikatwarnung�, in dem der Benutzer �ber ein nicht vertrauensw�rdiges Zertifikat informiert wird, wobei die Schaltfl�che �Ja� hervorgehoben ist. ](../images/0104.png)

Herzlichen Gl�ckwunsch! Sie haben einen virtuellen Windows Server-Computer in Azure bereitgestellt und mit ihm eine Verbindung hergestellt

# Aufgabe�3: Webserverrolle installieren und testen

In dieser Aufgabe werden Sie die Webserverrolle auf dem Server installieren und sicherstellen, dass die Standard-IIS-Begr��ungsseite angezeigt werden kann.

1. �ffnen Sie eine PowerShell-Eingabeaufforderung auf dem virtuellen Computer, indem Sie auf die Schaltfl�che **Start** klicken, **PowerShell** eingeben, mit der rechten Maustaste auf **Windows PowerShell** klicken und im Kontextmen� **Als Administrator ausf�hren** ausw�hlen.

    ![Screenshot des Desktops des virtuellen Computers mit angeklickter Startschaltfl�che und Auswahl von PowerShell mit �Als Administrator ausf�hren� hervorgehoben.](../images/0105.png)

2. Installieren Sie in dem virtuellen Computer das Feature **Webserver**, indem Sie den folgenden Befehl in der PowerShell-Eingabeaufforderung ausf�hren. Sie k�nnen diesen Befehl kopieren und einf�gen.

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. Nach Abschluss wird die Eingabeaufforderung **Erfolg** mit dem Wert **Wahr** angezeigt. Sie m�ssen den virtuellen Computer nicht neu starten, um die Installation abzuschlie�en. Schlie�en Sie die RDP-Verbindung zum virtuellen Computer.

    ![Screenshot der Windows PowerShell-Eingabeaufforderung mit dem erfolgreich abgeschlossenen Befehl �Install-WindowsFeature -name Web-Server -IncludeManagementTools� und der Ausgabe, dass der Vorgang erfolgreich war.](../images/0106.png)

4. Navigieren Sie im Portal zur�ck zum Blatt **�berblick** von myVM, und verwenden Sie die Schaltfl�che **Zur Zwischenablage klicken**, um die �ffentliche IP-Adresse von myVM zu kopieren. �ffnen Sie eine neue Browserregisterkarte, f�gen Sie die �ffentliche IP-Adresse in das URL-Textfeld ein und dr�cken Sie die Taste **EINGABE**, um dorthin hin zu wechseln.

    ![Screenshot des Eigenschaftenbereichs des virtuellen Computers des Azure-Portals mit der kopierten IP-Adresse.](../images/0107.png)

5. Die Standard-Begr��ungsseite des IIS-Webservers wird ge�ffnet.

    ![Screenshot der standardm��igen Begr��ungsseite des IIS-Webservers, auf die �ber die �ffentliche IP-Adresse in einem Webbrowser zugegriffen wird.](../images/0108.png)

Herzlichen Gl�ckwunsch! Sie haben einen Webserver erstellt, auf den �ber seine �ffentliche IP-Adresse zugegriffen werden kann. Wenn Sie eine Webanwendung hosten m�ssen, k�nnen Sie Anwendungsdateien auf dem virtuellen Computer bereitstellen und sie f�r den �ffentlichen Zugriff auf dem bereitgestellten virtuellen Computer hosten.


**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu �berpr�fen, ob der L�schvorgang erfolgreich abgeschlossen wurde. 
