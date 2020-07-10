---
wts:
    title: '17 � Implementieren von Ressourcen-Tagging'
    module: 'Modul 03 � Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 17 � Implementieren des Ressourcentaggings

In dieser exemplarischen Vorgehensweise erstellen wir eine Richtlinienzuweisung, f�r die Tagging erforderlich ist, erstellen ein Speicherkonto und testen das Tagging, zeigen Ressourcen mit einem angegebenen Tag an und entfernen die Tagging-Richtlinie.

# Aufgabe�1: Erstellen einer Richtlinienzuweisung

In dieser Aufgabe konfigurieren wir die Richtlinie **Einen Tag f�r Ressourcen anfordern** und weisen sie unserem Abonnement zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und w�hlen Sie diese Option aus.

3. Scrollen Sie nach unten zum Abschnitt **Dokumenterstellung**, klicken Sie  auf **Aufgaben**, und klicken Sie dann oben auf der Seite auf **Richtlinie zuweisen**.

4. Beachten Sie, dass der **Bereich** f�r unsere Richtlinie abonnementweit sein wird. 

5. W�hlen Sie die Schaltfl�che mit den Auslassungspunkten (**Richtliniendefinition**) aus (am Ende des Textfelds rechts). **Suchen** Sie nach Richtliniendefinitionen mit dem Wert **Tag**. Klicken Sie in der Ergebnismenge auf die Definition  **Tag f�r Ressourcen erforderlich**, und klicken Sie dann auf **Ausw�hlen**.

   ![Screenshot des Bereichs �Verf�gbare Definitionen� mit ausgew�hltem Eintrag �Tag f�r Ressourcen erforderlich�.](../images/1701.png)

6. Geben Sie auf dem Blatt **Richtlinie zuweisen** auf der Registerkarte **Parameter** die Zeichenfolge **Unternehmen** als Tag-Name ein. Klicken Sie auf **�berpr�fen + Erstellen** und dann auf **Erstellen**.

    **Hinweis:** Dies ist ein einfaches Beispiel, um das Tagging zu demonstrieren. 

    ![Screenshot des Bereichs �Richtlinie zuweisen� mit ausgef�lltem Tag-Namen.](../images/1702.png)

7. Die Richtlinienzuweisung **Tag f�r Ressourcen erforderlich** ist jetzt vorhanden. Wenn eine Ressource erstellt wird, muss sie ein Tag mit dem Unternehmensschl�ssel enthalten.

   ![Screenshot des Bereichs �Richtlinien � Zuweisungen�, in dem die Zuweisung der zul�ssigen Standorte hervorgehoben ist.](../images/1703.png)

# Aufgabe�2: Erstellen Sie ein Speicherkonto zum Testen des erforderlichen Taggings.

In dieser Aufgabe erstellen wir Speicherkonten, um das erforderliche Tagging zu testen. 

1. Suchen Sie im Azure-Portal auf dem Blatt **Alle Dienste** nach **Speicherkonten**, und w�hlen Sie diese Option aus. Klicken Sie anschlie�end auf **+ Hinzuf�gen**.

2. Geben Sie auf dem Blatt **Speicherkonto erstellen** auf der Registerkarte **Grundlagen** die folgenden Informationen ein (ersetzen Sie **xxxx** im Speicherkontonamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Verwenden Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGTags** (Neu) |
    | Name des Speicherkontos | **storageaccountxxxx** |
    | Ort | **(USA) USA, Osten** |
    | | |

3. Klicken Sie auf **�berpr�fen + Erstellen**. 

    **Hinweis:** Wir testen, was passiert, wenn das Tag nicht angegeben wird. 

4. Sie erhalten eine Nachricht, dass die Validierung fehlgeschlagen ist. Klicken Sie auf die Nachricht **Hier klicken, um Details anzuzeigen**. Auf dem Blatt **Fehler** wird auf der Registerkarte **Zusammenfassung** eine Fehlermeldung angezeigt, die besagt, dass die Ressource von der Richtlinie nicht zugelassen wurde.

    **Hinweis:** Wenn Sie die Registerkarte �Unformatierter Fehler� anzeigen, wird der erforderliche spezifische Tagname angezeigt. 

    ![Screenshot von �aufgrund eines Richtlinienfehlers nicht zul�ssig�.](../images/1704.png)

5. Schlie�en Sie den Bereich **Fehler**, und klicken Sie auf **Zur�ck** (unterer Bildschirmrand). Geben Sie die Tagging-Informationen an. 

    | Einstellung | Wert | 
    | --- | --- |
    | Tag-Name | **Unternehmen** (m�glicherweise nicht in der Dropdownliste) |
    | Tag-Wert | **Contoso** |
    | | |

6. Klicken Sie auf **�berpr�fen + Erstellen**, und �berpr�fen Sie, ob die Validierung erfolgreich war. Klicken Sie auf **Erstellen**, um das Speicherkonto bereitzustellen. 

# Aufgabe�3: Zeigen Sie alle Ressourcen mit einem bestimmten Tag an

1. Suchen Sie im Azure-Portal auf dem Blatt **Alle Dienste** nach **Tags**, und w�hlen Sie diese Option aus.

2. Notieren Sie alle Tags und ihre Werte. Klicken Sie auf **Unternehmen: Contoso** Schl�ssel-Wert-Paar. Daraufhin wird ein Blatt mit dem neu erstellten Speicherkonto angezeigt, sofern Sie das Tag w�hrend der Bereitstellung einbezogen haben. 

   ![Screenshot der Tags mit ausgew�hltem Unternehmen und Contoso.](../images/1705.png)

3. Zeigen Sie im Portal das Blatt **Alle Ressourcen** an.

4. Klicken Sie auf **Filter hinzuf�gen**, und f�gen Sie den Tag-Schl�ssel **Unternehmen** als Filterkategorie hinzu. Wenn der Filter angewendet wird, wird nur Ihr Speicherkonto aufgelistet.

    ![Screenshot des Filters �Alle Ressourcen� mit ausgew�hltem Unternehmen.](../images/1706.png)

# Aufgabe�4: Richtlinienzuweisung l�schen

In dieser Aufgabe werden wir die Richtlinie **Tag f�r Ressourcen erforderlich** entfernen, so dass sie unsere zuk�nftige Arbeit nicht beeinflusst. 

1. Suchen Sie im Portal im Blatt **Alle Dienste** nach dem Punkt **Richtlinie**, und w�hlen Sie ihn aus.

2. Klicken Sie auf den Richtlinieneintrag **Tag f�r Ressourcen erforderlich**.

3. Klicken Sie im obersten Men� auf **Zuweisung l�schen**.

4. Best�tigen Sie, dass Sie die Richtlinienzuweisung l�schen m�chten, indem Sie im Dialogfeld **Zuweisung l�schen** auf **Ja** klicken.

5. Wenn Sie Zeit haben, erstellen Sie eine weitere Ressource ohne Tag, um sicherzustellen, dass die Richtlinie nicht mehr g�ltig ist.

In dieser exemplarischen Vorgehensweise haben wir eine Richtlinienzuweisung erstellt, f�r die Tagging erforderlich ist, ein Speicherkonto erstellt und das Tagging getestet, Ressourcen mit einem angegebenen Tag angezeigt und die Tagging-Richtlinie entfernt.


**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
