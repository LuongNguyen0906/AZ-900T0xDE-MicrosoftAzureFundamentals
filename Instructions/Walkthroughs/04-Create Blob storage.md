---
wts:
    title: '04 � Blob-Speicher erstellen'
    module: 'Modul 02 � Core Azure Services'
---
# 04 � Erstellen von Blob-Speicher

In dieser exemplarischen Vorgehensweise erstellen wir ein Speicherkonto und arbeiten dann mit Blob Storage-Dateien.

# Aufgabe�1: Speicherkonto erstellen

In dieser �bung erstellen wir ein neues Speicherkonto. 

1. Melden Sie sich beim Azure-Portal an unter: <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Speicherkonten**, und w�hlen Sie diese Option aus. Klicken Sie dann auf **+ Hinzuf�gen**. 

3. Geben Sie auf dem Blatt **Speicherkonto erstellen** auf der Registerkarte **Grundlagen** die folgenden Informationen ein (ersetzen Sie **xxxx** im Speicherkontonamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGStorage** (Neu erstellen) |
    | Name des Speicherkontos | **storageaccountxxxx** |
    | Ort | **(USA) USA, Osten**  |
    | Leistung | **Standard** |
    | Kontotyp | **StorageV2 (universell v2)** |
    | Replikation | **Lokal redundanter Speicher (LRS)** |
    | Zugriffsebene (Standard) | **Hei�e Ebene** |
    | | |

5. Klicken Sie auf **�berpr�fen + Erstellen** um die Einstellungen Ihres Speicherkontos zu �berpr�fen und Azure die �berpr�fung der Konfiguration zu erm�glichen. 

6. Klicken Sie nach der Validierung auf **Erstellen**. Warten Sie auf die Benachrichtigung, dass das Konto erfolgreich erstellt wurde. 

7. Suchen Sie auf der Homepage die Option **Speicherkonten**, und w�hlen Sie sie aus. Stellen Sie sicher, dass Ihr neues Speicherkonto aufgef�hrt ist.

    ![Screenshot des neu erstellten Speicherkontos im Azure-Portal.](../images/0401.png)

# Aufgabe�2: Arbeiten mit Blob Storage

In dieser Aufgabe erstellen wir einen Blob-Container und laden eine Blob-Datei hoch. 

1. Klicken Sie auf den Namen des neuen Speicherkontos, scrollen Sie zum Abschnitt **Blob-Dienst**, und klicken Sie dann auf **Container**.

2. Klicken Sie auf **+ Container**, und vervollst�ndigen Sie die Informationen. �ber das Informationssymbol erhalten Sie weitere Informationen. Klicken Sie auf **OK**, wenn Sie fertig sind.


    | Einstellung | Wert |
    | --- | --- |
    | Name | **container1**  |
    | �ffentliche Zugriffsebene| **Privat (kein anonymer Zugang)** |
    | | |

    ![Screenshot des neu erstellten Blob-Containers im Speicherkonto im Azure-Portal.](../images/0402.png)

4. Klicken Sie auf den Container **container1** und anschlie�end auf **Hochladen**.

5. Navigieren Sie zu einer Datei auf Ihrem lokalen Computer. 

    **Hinweis**: Sie k�nnen eine leere `.txt`-Datei erstellen oder eine vorhandene Datei verwenden. W�hlen Sie eine kleine Datei, um die Uploadzeit zu minimieren.

6. Klicken Sie auf den Pfeil **Erweitert**, �bernehmen Sie die Standardwerte, �berpr�fen Sie die verf�gbaren Optionen, und klicken Sie dann auf **Hochladen**.

    **Hinweis**: Auf diese Weise k�nnen Sie beliebig viele Blobs hochladen. Neue BLOBs werden im Container aufgelistet.

7. Klicken Sie nach dem Hochladen der Datei mit der rechten Maustaste auf die Datei und beachten Sie die Optionen �Anzeigen/Bearbeiten�, �Herunterladen�, �Eigenschaften� und �L�schen�. 

8. Wenn Sie Zeit haben, �berpr�fen Sie auf dem Blatt �Speicherkonten� die Optionen f�r Dateien, Tabellen und Warteschlangen.

# Aufgabe�3: �berwachung des Speicherkontos

1. Wenn erforderlich, kehren Sie zum Speicherkonto-Blatt zur�ck, und klicken Sie auf **Diagnose und Problembehandlung**. 

2. Erkunden Sie einige der h�ufigsten Speicherprobleme. Beachten Sie, dass es mehrere Ma�nahmen zur Fehlerbehebung gibt.

3. Scrollen Sie auf dem Blatt �Speicherkonten� nach unten zum Abschnitt **�berwachung**, und klicken Sie auf **Insights (Vorschau)**. Beachten Sie, dass Informationen zu Fehlern, Leistung, Verf�gbarkeit und Kapazit�t vorhanden sind. Ihre Informationen werden davon abweichen.

    ![Screenshot der Seite �Insights� des Speicherkontos.](../images/0403.png)

Herzlichen Gl�ckwunsch! Sie haben ein Speicherkonto erstellt und dann mit Speicherblobs gearbeitet.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
