---
wts:
    title: '16 � Verwalten von Ressourcensperren'
    module: 'Modul 03 � Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 16 � Verwalten von Ressourcensperren

In dieser exemplarischen Vorgehensweise erstellen wir eine Ressourcengruppe, f�gen der Ressourcengruppe eine Sperre hinzu und testen das L�schen, testen das L�schen einer Ressource in der Ressourcengruppe und entfernen die Ressourcensperre. 

# Aufgabe�1: Erstellen einer Ressourcengruppe

In dieser Aufgabe erstellen wir f�r diese �bung eine Ressourcengruppe. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie im Blatt **Alle Dienstleistungen** nach **Ressourcengruppen** und w�hlen Sie es aus. W�hlen Sie dann **+ Hinzuf�gen** aus.

3. Erstellen Sie eine neue Ressourcengruppe. Wenn Sie fertig sind, klicken Sie auf **�berpr�fen + Erstellen** und dann auf **Erstellen**. 

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **Verwenden Sie Ihr Abonnement** |
    | Name | **myRGLocks** |
    | Region | **(USA) USA, Osten** |
    | | |

# Aufgabe�2:  Sperre zur Ressourcengruppe hinzuf�gen und das L�schen testen

In dieser Aufgabe f�gen wir der Ressourcengruppe eine Ressourcensperre hinzu und testen das L�schen der Ressourcengruppe. 

1. Navigieren Sie im Azure-Portal zu der neu erstellten Ressourcengruppe **myRGLocks**.

2. Sie k�nnen eine Sperre auf ein Abonnement, eine Ressourcengruppe oder eine einzelne Ressource anwenden, um ein versehentliches L�schen oder �ndern kritischer Ressourcen zu verhindern. 

3. Klicken Sie im Abschnitt **Einstellungen** auf **Sperren** und dann auf **+ Hinzuf�gen**. 

    ![Screenshot der Ressourcengruppe �myRGLocks� mit dem angezeigten Bereich �Sperren�.](../images/1601.png)

4. Konfigurieren Sie die neue Sperre. Klicken Sie anschlie�end auf **OK**. 

    | Einstellung | Wert |
    | -- | -- |
    | Sperrenname | **RGLock** |
    | Sperrtyp | **L�schen** |
    | | |

5. Klicken Sie auf **�bersicht** und dann auf **Ressourcengruppe l�schen**. Geben Sie den Namen der Ressourcengruppe ein, und klicken Sie anschlie�end auf **OK**. Sie erhalten eine Fehlermeldung, dass die Ressourcengruppe gesperrt ist und nicht gel�scht werden kann.

    ![Screenshot der fehlgeschlagenen L�schsperren.](../images/1602.png)

# Aufgabe�3: Testl�schung eines Mitglieds der Ressourcengruppe

In dieser Aufgabe testen wir, ob die Ressourcensperre ein Speicherkonto in der Ressourcengruppe sch�tzt. 

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Speicherkonten**, und w�hlen Sie diese Option aus. Klicken Sie dann auf **+ Hinzuf�gen**. 

2. Geben Sie auf dem Blatt **Speicherkonto erstellen** auf der Registerkarte **Grundlagen** die folgenden Informationen ein (ersetzen Sie **xxxx** im Speicherkontonamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGLocks** |
    | Name des Speicherkontos | **storageaccountxxxx** |
    | Ort | **(USA) USA, Osten**  |
    | Leistung | **Standard** |
    | Kontotyp | **StorageV2 (universell v2)** |
    | Replikation | **Lokal redundanter Speicher (LRS)** |
    | Zugriffsebene (Standard) | **Hei�e Ebene** |
    | | |

3. Klicken Sie auf **�berpr�fen + Erstellen** um die Einstellungen Ihres Speicherkontos zu �berpr�fen und Azure die �berpr�fung der Konfiguration zu erm�glichen. 

4. Klicken Sie nach der Validierung auf **Erstellen**. Warten Sie auf die Benachrichtigung, dass das Konto erfolgreich erstellt wurde. 

5.  Warten Sie auf die Benachrichtigung, dass das Speicherkonto erfolgreich erstellt wurde. 

6. Greifen Sie auf Ihr neues Speicherkonto zu, und klicken Sie im Bereich **�bersicht** auf **L�schen**. Sie erhalten eine Fehlermeldung, dass die Ressource oder die �bergeordnete Ressource �ber eine L�schsperre verf�gt. 

    ![Screenshot der Meldung bez�glich eines Fehlers beim L�schen des Speicherkontos.](../images/1603.png)

    **Hinweis**: Obwohl wir keine Sperre speziell f�r das Speicherkonto erstellt haben, haben wir eine Sperre auf der Ressourcengruppenebene erstellt, die das Speicherkonto enth�lt. Als solches verhindert die *�bergeordnete* Ebenensperre, dass wir die Ressource l�schen, und das Speicherkonto �bernimmt die Sperre vom �bergeordneten Element.

# Aufgabe�4:  Ressourcensperre entfernen

In dieser Aufgabe entfernen wir die Ressourcensperre und testen. 

1. Wechseln Sie wieder zum Ressourcengruppen-Blatt **myRGLocks**, und klicken Sie im Abschnitt **Einstellungen** auf **Sperren**.
    
2. Klicken Sie den Link **L�schen** rechts neben dem Eintrag **RGLock**.

    ![Screenshot der Sperre mit hervorgehobenem Link zum L�schen.](../images/1604.png)

3. Kehren Sie in das Blatt �Speicherkonto� zur�ck und best�tigen Sie, dass Sie die Ressource jetzt l�schen k�nnen.

Herzlichen Gl�ckwunsch! Sie haben eine Ressourcengruppe erstellt, der Ressourcengruppe eine Sperre hinzugef�gt und das L�schen getestet, das L�schen einer Ressource in der Ressourcengruppe getestet und die Ressourcensperre entfernt. 

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.