---
wts:
    title: '11 � Erstellen eines virtuellen Computers mithilfe der CLI'
    module: 'Modul 02 � Core Azure Services'
---
# 11 � Erstellen eines virtuellen Computers mithilfe der CLI

In dieser exemplarischen Vorgehensweise konfigurieren wir die Cloud Shell, erstellen mithilfe von Azure CLI eine Ressourcengruppe und einen virtuellen Computer und �berpr�fen die Empfehlungen von Azure Advisor. 

# Aufgabe�1: Die Cloud Shell konfigurieren

In dieser Aufgabe konfigurieren wir Cloud Shell. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. �ffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

    ![Screenshot des Azure Cloud Shell-Symbols im Azure-Portal.](../images/1002.png)

3. Wenn Sie die Cloud Shell bereits verwendet haben, fahren Sie mit der n�chsten Aufgabe fort. 

4. Wenn Sie aufgefordert werden, entweder **Bash** oder **PowerShell** auszuw�hlen, w�hlen Sie **Bash** aus. 

5. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Speicher erstellen**, und warten Sie, bis die Azure Cloud Shell initialisiert ist. 

# Aufgabe�2: Ressourcengruppe und virtuellen Computer erstellen

In dieser Aufgabe verwenden wir Azure CLI, um eine Ressourcengruppe und einen virtuellen Computer zu erstellen.  

1. Stellen Sie sicher, dass **Bash** im Dropdownmen� oben links im Cloud Shell-Bereich ausgew�hlt ist (w�hlen Sie andernfalls diese Option aus).

    ![Screenshot der Azure-Portal Azure Cloud-Shell mit hervorgehobenem Bash-Dropdown.](../images/1002a.png)

2. Erstellen Sie in der Bash-Sitzung im Cloud Shell-Bereich eine neue Ressourcengruppe. 

    ```cli
    az group create --name myRGCLI --location EastUS
    ```

3. �berpr�fen Sie, ob die Ressourcengruppe erstellt wurde.

    ```cli
    az group list --output table
    ```

4. Erstellen Sie einen neuen virtuellen Computer. Stellen Sie sicher, dass auf jede Zeile mit Ausnahme der letzten Zeile ein umgekehrter Schr�gstrich (`\`) folgt. Wenn Sie den gesamten Befehl in derselben Zeile eingeben, verwenden Sie keine umgekehrten Schr�gstriche. 

    ```cli
    az vm create \
    --name myVMCLI \
    --resource-group myRGCLI \
    --image UbuntuLTS \
    --location EastUS \
    --admin-username azureuser \
    --admin-password Pa$$w0rd1234
    ```

    >**Hinweis**: Wenn Sie die Befehlszeile auf einem Windows-Computer verwenden, ersetzen Sie den umgekehrten Schr�gstrich (`\`) durch das Caretzeichen (`^`).
    
    **Hinweis**: Die Ausf�hrung des Befehls dauert 2 bis 3 Minuten. Der Befehl erstellt einen virtuellen Computer und verschiedene damit verbundene Ressourcen wie Speicher-, Netzwerk- und Sicherheitsressourcen. Fahren Sie mit dem n�chsten Schritt erst dann fort, wenn die Bereitstellung des virtuellen Computers abgeschlossen ist. 

5. Wenn der Befehl ausgef�hrt wurde, schlie�en Sie im Browserfenster den Cloud Shell-Bereich.

6. Suchen Sie im Azure-Portal nach **Virtuelle Computer**, und �berpr�fen Sie, ob **myVMCLI** ausgef�hrt wird.

    ![Screenshot der Seite �Virtuelle Computer�, wobei myVMPS ausgef�hrt wird.](../images/1101.png)


# Aufgabe�3: Befehle in der Cloud Shell ausf�hren

In dieser Aufgabe �ben wir das Ausf�hren von CLI-Befehlen �ber Cloud Shell. 

1. �ffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

2. Stellen Sie sicher, dass **Bash** im Dropdown-Men� oben links des Cloud Shell-Bereichs ausgew�hlt ist.

3. Rufen Sie Informationen zu dem von Ihnen bereitgestellten virtuellen Computer ab, einschlie�lich Name, Ressourcengruppe, Ort und Status. Beachten Sie, dass PowerState **ausgef�hrt wird**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

4. Halten Sie den virtuellen Computer an. Beachten Sie die Meldung, dass die Abrechnung weiterl�uft, bis die Zuordnung des virtuellen Computers aufgehoben wird. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

5. �berpr�fen Sie den Status Ihres virtuellen Computers. PowerState sollte jetzt den Wert **angehalten** haben.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

# Aufgabe�4: Azure Advisor-Empfehlungen �berpr�fen

In dieser Aufgabe �berpr�fen wir die Empfehlungen von Azure Advisor.

   **Hinweis:** Wenn Sie das vorherige Lab (Erstellen eines virtuellen Computers mithilfe von PowerShell) abgeschlossen haben, haben Sie diese Aufgabe bereits ausgef�hrt. 

1. Suchen Sie auf Blatt **Alle Dienste** nach **Advisor**, und w�hlen Sie diese Option aus. 

2. W�hlen Sie im Blatt **Advisor** den Eintrag **�berblick** aus. Beachten Sie, dass Empfehlungen nach Hochverf�gbarkeit, Sicherheit, Leistung und Kosten gruppiert sind. 

    ![Screenshot der Seite �Advisor-�bersicht�. ](../images/1103.png)

3. W�hlen Sie **Alle Empfehlungen** aus und nehmen Sie sich die Zeit, um die einzelnen Empfehlungen und vorgeschlagenen Ma�nahmen anzuzeigen. 

    **Hinweis:** Die Empfehlungen sind je nach Ihren Ressourcen unterschiedlich. 

    ![Screenshot der Advisor-Seite �Alle Empfehlungen�. ](../images/1104.png)

4. Beachten Sie, dass Sie die Empfehlungen als CSV- oder PDF-Datei herunterladen k�nnen. 

5. Beachten Sie, dass Sie Warnungen erstellen k�nnen. 

6. Wenn Sie Zeit haben, experimentieren Sie weiter mit Azure CLI. 

Herzlichen Gl�ckwunsch! Sie haben Cloud Shell konfiguriert, einen virtuellen Computer mit Azure CLI erstellt, Azure CLI-Befehle ge�bt und Advisor-Empfehlungen angesehen.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
