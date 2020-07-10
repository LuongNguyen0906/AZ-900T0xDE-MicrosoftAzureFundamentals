---
wts:
    title: '05 � Erstellen einer SQL-Datenbank'
    module: 'Modul 02 � Core Azure Services'
---

# 05 � Erstellen einer SQL-Datenbank

In dieser exemplarischen Vorgehensweise erstellen wir eine SQL-Datenbank in Azure und fragen dann die Daten in dieser Datenbank ab.

# Aufgabe�1: Erstellen der Datenbank

In dieser Aufgabe werden wir eine SQL-Datenbank auf der Grundlage der AdventureWorksLT-Beispieldatenbank erstellen. 

1. Melden Sie sich beim Azure-Portal an unter [**https://portal.azure.com**](https://portal.azure.com).

2. Suchen Sie im Blatt **Alle Dienste** nach **SQL-Datenbanken** und w�hlen Sie es aus. Klicken Sie dann auf **+ Hinzuf�gen**. 

3. Geben Sie auf der Registerkarte **Grundlagen** diese Informationen ein.  

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGDb** (Neu erstellen) |
    | Datenbankname| **db1** | 
    | | |

3. Klicken Sie neben der Dropdownliste **Server** auf **Neu erstellen**, und geben Sie diese Informationen ein (ersetzen Sie **xxxx** im Servernamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Klicken Sie auf **OK**, wenn Sie fertig sind.

    | Einstellung | Wert | 
    | --- | --- |
    | Servername | **sqlserverxxxx** (muss eindeutig sein) | 
    | Serveradministratoranmeldung | **sqluser** |
    | Kennwort | **Pa$$w0rd1234** |
    | Ort | **(USA) USA, Osten** |
    | Azure-Diensten Zugriff auf den Server erlauben| ***Aktivieren Sie das Kontrollk�stchen*** |
    | | |

   ![Screenshot des Bereichs �Server� und des Bereichs �Neuer Server�, wobei die Felder entsprechend der Tabelle ausgef�llt und die Schaltfl�chen ��berpr�fen + Erstellen� und �OK�" hervorgehoben sind.](../images/0501.png)

4. Wechseln Sie auf die Registerkarte **Netzwerk**, und konfigurieren Sie die folgenden Einstellungen (lassen Sie andere mit ihren Standardeinstellungen). 

    | Einstellung | Wert | 
    | --- | --- |
    | Konnektivit�tsmethode | **�ffentlicher Endpunkt** |    
    | Erm�glichen Sie Azure-Diensten und -Ressourcen den Zugriff auf diesen Server | **Ja** |
    | Aktuelle Client-IP-Adresse hinzuf�gen | **Nein** |
    | | |
    
   ![Screenshot der Registerkarte �Netzwerk� des Blattes �SQL-Datenbank erstellen� mit den in der Tabelle gew�hlten Einstellungen und hervorgehobener Schaltfl�che ��berpr�fen + Erstellen�.](../images/0501b.png)

5. Wechseln Sie in die Registerkarte **Zus�tzliche Einstellungen**. Wir werden die AdventureWorksLT-Beispieldatenbank verwenden.

    | Einstellung | Wert | 
    | --- | --- |
    | Vorhandene Daten verwenden | **Stichprobe** |
    | Sortierung | ***Standard verwenden*** |
    | Advanced Data Security aktivieren | **Nicht jetzt** |
    | | |

    ![Screenshot der Registerkarte �Zus�tzliche Einstellungen� des Blatts �SQL-Datenbank erstellen�, wobei die Einstellungen gem�� der Tabelle ausgew�hlt und die Schaltfl�che ��berpr�fen + erstellen� hervorgehoben ist.](../images/0501c.png)

6. Klicken Sie auf **�berpr�fen + Erstellen** und dann auf **Erstellen**, um die Ressourcengruppe, den Server und die Datenbank bereitzustellen. Die Bereitstellung kann etwa 2 bis 5 Minuten dauern.

7. �berwachen Sie Ihre Bereitstellung. 

# Aufgabe�2: Datenbank testen.

In dieser Aufgabe konfigurieren wir den SQL Server und f�hren eine SQL-Abfrage aus. 

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **SQL-Datenbanken**, und w�hlen Sie diese Option aus. Vergewissern Sie sich, dass Ihre neue Datenbank erstellt wurde. M�glicherweise m�ssen Sie die Seite **Aktualisieren**.

    ![Screenshot der gerade bereitgestellten SQL-Datenbank und des SQL-Servers.](../images/0502.png)

2. Klicken Sie auf den Eintrag **db1**, der die von Ihnen erstellte SQL-Datenbank darstellt, und klicken Sie dann auf **Abfrage-Editor (Vorschau)**.

3. Melden Sie sich als **sqluser** mit dem Kennwort **Pa$$$w0rd1234** an.

4. Sie werden sich nicht anmelden k�nnen. Lesen Sie den Fehler genau durch und notieren Sie sich die IP-Adresse, die durch die Firewall erlaubt werden muss. 

    ![Screenshot der Anmeldeseite des Abfrage-Editors mit IP-Adressfehler.](../images/0503.png)

5. Klicken Sie im Blatt **db1** auf **�berblick**. 

    ![Screenshot der Seite �SQL-Server�.](../images/0504.png)

6. Klicken Sie im SQL-Server-Blatt **�berblick** auf **Server-Firewall einstellen**.

7. Klicken Sie auf **Client-IP hinzuf�gen** (obere Men�leiste), um die IP-Adresse hinzuzuf�gen, auf die in der Fehlermeldung verwiesen wird. Achten Sie darauf, Ihre �nderungen zu **Speichern**. 

    ![Screenshot der Einstellungsseite der SQL-Server-Firewall mit hervorgehobener neuer IP-Regel.](../images/0506.png)

8. Kehren Sie zu Ihrer SQL-Datenbank und der Anmeldeseite von **Abfrage-Editor (Vorschau)** zur�ck. Versuchen Sie, sich wieder als **sqluser** mit dem Kennwort **Pa$$$w0rd1234** anzumelden. Diesmal sollten Sie Erfolg haben. Beachten Sie, dass es einige Minuten dauern kann, bis die neue Firewall-Regel bereitgestellt wird. 

9. Sobald Sie sich erfolgreich angemeldet haben, wird das Abfragefenster angezeigt. Geben Sie die folgende Abfrage in den Editor-Bereich ein.

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Screenshot des Query-Editors mit dem Abfragebereich und den Befehlen, die erfolgreich ausgef�hrt wurden.](../images/0507.png)

10. Klicken Sie auf **Ausf�hren**, und �berpr�fen Sie dann die Abfrageergebnisse im Bereich **Ergebnisse**. Die Abfrage sollte erfolgreich ausgef�hrt werden.

    ![Screenshot des Datenbank-Abfrage-Editor-Bereichs, in dem der SQL-Code erfolgreich ausgef�hrt wurde und die Ausgabe im Ergebnisbereich sichtbar ist.](../images/0508.png)

Herzlichen Gl�ckwunsch! Sie haben eine SQL-Datenbank in Azure erstellt und die Daten in dieser Datenbank erfolgreich abgefragt.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
