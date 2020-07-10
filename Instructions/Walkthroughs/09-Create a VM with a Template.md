---
wts:
    title: '09 � Erstellen eines virtuellen Computers mit Hilfe einer Vorlage'
    module: 'Modul 02 � Core Azure Services'
---
# 09 � Erstellen eines virtuellen Computers mit Hilfe einer Vorlage

In dieser exemplarischen Vorgehensweise stellen wir einen virtuellen Computer mit einer Schnellstartvorlage bereit und untersuchen �berwachungsfunktionen.

# Aufgabe1: Durchsuchen Sie die Galerie und suchen Sie eine Vorlage.

In dieser Aufgabe durchsuchen wir die Azure-Schnellstartgalerie und stellen eine Vorlage bereit, mit der ein virtueller Computer erstellt wird. 

1. Greifen Sie in einem Browser auf die [Azure-Schnellstart-Vorlagengalerie](https://azure.microsoft.com/resources/templates?azure-portal=true) zu. In der Galerie finden Sie eine Reihe beliebter und k�rzlich aktualisierter Vorlagen. Diese Vorlagen automatisieren die Bereitstellung von Azure-Ressourcen, einschlie�lich der Installation g�ngiger Softwarepakete.

2. Durchsuchen Sie die vielen verschiedenen Arten von Vorlagen, die verf�gbar sind. 

    **Hinweis**: Gibt es Vorlagen, die Sie interessieren?

3. Suchen Sie die Vorlage [Einfache Windows-VM bereitstellen](https://azure.microsoft.com/resources/templates/101-vm-simple-windows?azure-portal=true), oder greifen Sie direkt auf diese zu.

    **Hinweis**: Die Schaltfl�che **Bereitstellung in Azure** erm�glicht es Ihnen, die Vorlage �ber das Azure-Portal bereitzustellen. W�hrend einer solchen Bereitstellung werden Sie nur zur Eingabe eines kleinen Satzes von Konfigurationsparametern aufgefordert. 

4. Klicken Sie auf die Schaltfl�che **In Azure bereitstellen**. Ihre Browsersitzung wird automatisch zum [Azure-Portal](http://portal.azure.com/) umgeleitet.

5. Melden Sie sich nach Aufforderung bei dem Azure-Abonnement an, das Sie in diesem Lab verwenden m�chten.

6. Klicken Sie auf **Vorlage bearbeiten**. Die Resource Manager-Vorlage verwendet das JSON-Format. �berpr�fen Sie die Variablen, und suchen Sie den Namen des virtuellen Computers. �ndern Sie den Namen zu **myVMTemplate**. **Speichern** Sie Ihre �nderungen. Sie kehren zur�ck zum Blatt **Benutzerdefinierte Bereitstellung** im Azure-Portal.

    ![Screenshot der Vorlage mit der hervorgehobenen �nderung des VM-Namens.](../images/0901.png)

7. Konfigurieren Sie auf dem Blatt **Benutzerdefinierte Bereitstellung** die f�r die Vorlage erforderlichen Parameter (ersetzen Sie ***xxxx*** im DNS-Bezeichnungsp�fix durch Buchstaben und Ziffern, sodass die Bezeichnung global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen. 

    | Einstellung| Wert|
    |----|----|
    | Abonnement | **W�hlen Sie Ihr Abonnement**|
    | Ressourcengruppe | **myRGTemplate** (Neu erstellen) |
    | Ort | **(USA) USA, Osten** |
    | Admin-Benutzername | **azureuser** |
    | Admin-Kennwort | **Pa$$w0rd1234** |
    | Pr�fix der DNS-Bezeichnung | **myvmtemplate*xxxx*** |
    | Windows-Betriebssystemversion | **2019-Datencenter** |
    | | |

8. Aktivieren Sie das Kontrollk�stchen **Ich stimme den oben genannten Bedingungen zu**, und klicken Sie dann auf **Kaufen**.

    **Hinweis**: Bei der Nutzung dieser Vorlage fallen keine Kosten an.

9. �berwachen Sie Ihre Bereitstellung. 

# Aufgabe�2: �berpr�fen und �berwachen der Bereitstellung Ihres virtuellen Computers

In dieser Aufgabe �berpr�fen wir, ob der virtuelle Computer ordnungsgem�� bereitgestellt wurde. 

1. Auf dem Blatt **Alle Dienste** suchen und w�hlen Sie **Virtuelle Computer** aus.

2. Stellen Sie sicher, dass Ihr neuer virtueller Computer erstellt wurde. 

    ![Screenshot der Seite �Virtuelle Computer�. Der neue virtuelle Computer wird angezeigt und ausgef�hrt.](../images/0902.png)

3. W�hlen Sie Ihren virtuellen Computer aus, und scrollen Sie im Bereich **�bersicht** nach unten, um die �berwachungsdaten anzuzeigen.

    **Hinweis**: Der �berwachungszeitraum kann von einer Stunde bis zu 30 Tagen angepasst werden.

4. �berpr�fen Sie verschiedene Diagramme, einschlie�lich **CPU (Durchschnitt)**, **Netzwerk (gesamt)**, und **Festplattenbytes (gesamt)**. 

    ![Screenshot der �berwachungsdiagramme zum virtuellen Computer.](../images/0903.png)

5. Klicken Sie auf ein Diagramm. Beachten Sie, dass Sie eine **Metrik hinzuf�gen** und den Diagrammtyp �ndern k�nnen. Experimentieren Sie, wenn Ihre Zeit es erlaubt. 

6. Kehren Sie zum Blatt **�bersicht** zur�ck.

7. Klicken Sie auf **Aktivit�tsprotokoll** (linker Bereich). In Aktivit�tsprotokollen werden Ereignisse wie das Erstellen oder �ndern von Ressourcen aufgezeichnet. 

8. Klicken Sie auf **Filter hinzuf�gen**, und experimentieren Sie mit der Suche nach verschiedenen Ereignistypen und Operationen. 

    ![Screenshot der Seite �Filter hinzuf�gen� mit ausgew�hltem Ereignistyp.](../images/0904.png)

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
