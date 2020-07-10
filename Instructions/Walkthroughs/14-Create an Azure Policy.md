---
wts:
    title: '14 � Erstellen einer Azure-Richtlinie'
    module: 'Modul 03 � Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 14 � Erstellen einer Azure-Richtlinie

In dieser exemplarischen Vorgehensweise erstellen wir eine Azure-Richtlinie, um die Bereitstellung von Azure-Ressourcen auf einen bestimmten Standort zu beschr�nken.

# Aufgabe�1: Erstellen einer Richtlinienzuweisung

In dieser Aufgabe konfigurieren wir die zul�ssige Standortrichtlinie und weisen sie unserem Abonnement zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und w�hlen Sie sie diese Option aus. Klicken Sie im Abschnitt **Dokumenterstellung** auf **Definitionen**.  Nehmen Sie sich einen Moment Zeit, um die Liste der integrierten Richtliniendefinitionen zu �berpr�fen. W�hlen Sie zum Beispiel in der Dropdownliste **Kategorie** nur **Compute** aus. Beachten Sie mithilfe der Definition **Zul�ssige SKUs f�r virtuelle Computer** eine Reihe von SKUs f�r virtuelle Computer angeben k�nnen, die Ihre Organisation bereitstellen kann.

3. Wechseln Sie zur�ck zur Seite **Richtlinie**, und klicken Sie im Abschnitt **Dokumenterstellung** auf **Aufgaben**. Eine Zuweisung ist eine Richtlinie, die so zugewiesen wurde, dass sie innerhalb eines bestimmten Bereichs erfolgt. Beispielsweise k�nnte dem Abonnementbereich eine Definition zugewiesen werden. 

4. Klicken Sie auf **Richtlinie zuweisen** im oberen Bereich der Seite **Richtlinie - Aufgaben**.

5. W�hlen Sie auf der Seite **Richtlinie zuweisen** die Bereichsauswahl aus, indem Sie auf die Auslassungspunkte klicken.

    ![Screenshot der Ausgangspunkte der Bereichsauswahl.](../images/1401.png)

6. Stellen Sie sicher, dass Ihr Abonnement ausgew�hlt ist. Ihr Abonnementname kann abweichen. Beachten Sie, dass Sie die Richtlinie optional auf eine Ressourcengruppe beschr�nken k�nnen. �bernehmen Sie die Standardeinstellungen, und klicken Sie auf **Ausw�hlen**. 

    **Hinweis**: Ein Bereich bestimmt, f�r welche Ressourcen oder Gruppen von Ressourcen die Richtlinienzuweisung gilt. In unserem Fall k�nnten wir diese Richtlinie einer bestimmten Ressourcengruppe zuweisen. Wir haben uns jedoch daf�r entschieden, die Richtlinie auf Abonnementebene zuzuweisen. Beachten Sie, dass Ressourcen basierend auf der Bereichskonfiguration ausgeschlossen werden k�nnen. Ausschl�sse sind optional.

    ![Screenshot des Bereichs �Bereich� mit ausgef�llten Feldwerten und hervorgehobener Schaltfl�che �Ausw�hlen�. ](../images/1402.png)

7. W�hlen Sie die Schaltfl�che mit den Auslassungspunkten **Richtliniendefinition** aus. Geben Sie in das Feld **Suche** die Zeichenfolge **Standort** ein, und klicken Sie auf die Definition **Zul�ssige Standorte** und dann auf **Ausw�hlen**.

    **Hinweis**: Die Richtliniendefinition **Zul�ssige Standorte** gibt einen Speicherort an, an dem alle Ressourcen bereitgestellt werden m�ssen. Wenn ein anderer Speicherort ausgew�hlt wird, ist die Bereitstellung nicht zul�ssig. Weitere Informationen finden Sie auf der Seite [Azure Policy-Beispiele](https://docs.microsoft.com/de-de/azure/governance/policy/samples/index).

   ![Screenshot des Bereichs �Verf�gbare Definitionen� mit verschiedenen hervorgehobenen Feldern und ausgew�hlter Option ��berwachungs-VMs, die keine verwalteten Datentr�ger verwenden�.](../images/1403.png)

8.  Wechseln Sie im Bereich **Richtlinie zuweisen** zur Registerkarte **Parameter**, klicken Sie auf den Pfeil am Ende des Felds **Zul�ssige Standorte**, und w�hlen Sie aus der nachfolgenden Liste **Japan, Westen** aus. Lassen Sie alle anderen Werte unver�ndert, und klicken Sie auf **�berpr�fen + Erstellen** und dann auf **Erstellen**.

    ![Screenshot des Bereichs �Richtlinie zuweisen� mit verschiedenen Feldern, die zusammen mit dem angegebenen Standort �Japan, Westen� und der Schaltfl�che �Zuweisen� hervorgehoben sind.](../images/1404.png)

9. Die Richtlinienzuweisung **Zul�ssige Standorte** ist jetzt auf der Liste **Richtlinie - Aufgaben** aufgef�hrt und in Kraft getreten und setzt die Richtlinie auf der von uns angegebenen Bereichsebene (Abonnementebene) durch.

# Aufgabe�2: Testen der Richtlinie f�r zul�ssige Standorte

In dieser Aufgabe testen wir die Richtlinie f�r zul�ssige Standorte. 

1. Suchen Sie im Azure-Portal auf dem Blatt **Alle Dienste** nach **Speicherkonten**, und w�hlen Sie diese Option aus. Klicken Sie anschlie�end auf **+ Hinzuf�gen**.

2. Konfigurieren Sie das Speicherkonto (ersetzen Sie **xxxx** im Namen des Speicherkontos mit Buchstaben und Ziffern, so dass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen. 

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Verwenden Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGPolicy** (Neu erstellen) |
    | Name des Speicherkontos | **storageaccountxxxx** |
    | Ort | **(USA) USA, Osten** |
    | | |

3. Klicken Sie auf **�berpr�fen + Erstellen** und dann auf **Erstellen**. 

4. Sie erhalten die Fehlermeldung �Bereitstellung fehlgeschlagen�, die besagt, dass die Ressource von der Richtlinie nicht zugelassen wurde, einschlie�lich des Richtliniennamens **Zul�ssige Standorte**.

# Aufgabe�3: Richtlinienzuweisung l�schen

In dieser Aufgabe entfernen wir die Zuweisung und den Test der zul�ssigen Richtlinienzuweisung. 

Wir werden die Richtlinienzuweisung l�schen, um sicherzustellen, dass wir bei zuk�nftigen Arbeiten, die wir ausf�hren m�chten, nicht blockiert werden.

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und w�hlen Sie diese Option aus. Klicken Sie anschlie�end auf Ihre Richtlinie **Zul�ssige Standorte**.

    **Hinweis**: Auf dem Blatt **Richtlinie** k�nnen Sie den Konformit�tszustand der verschiedenen Richtlinien anzeigen, die Sie zugewiesen haben.

    **Hinweis**: Mit der Richtlinie �Zul�ssiger Standort� werden m�glicherweise nicht konforme Ressourcen angezeigt. In diesem Fall handelt es sich um Ressourcen, die vor der Richtlinienzuweisung erstellt wurden.

2. Klicken Sie im obersten Men� auf **Arbeitsauftrag l�schen**.

   ![Screenshot des Men�elements �Zuweisung l�schen�.](../images/1407.png)

3. Best�tigen Sie, dass Sie die Richtlinienzuweisung l�schen m�chten, indem Sie im Dialogfeld **Zuweisung l�schen** auf **Ja** klicken.

4. Versuchen Sie, ein anderes Speicherkonto zu erstellen, um sicherzustellen, dass die Richtlinie nicht mehr g�ltig ist.

    **Hinweis**: H�ufige Szenarien, in denen die Richtlinie **Zul�ssige Standorte** n�tzlich sein kann, w�ren: 
    - *Kostenverfolgung*: Sie k�nnen unterschiedliche Abonnements f�r unterschiedliche regionale Standorte haben. Die Richtlinie wird sicherstellen, dass alle Ressourcen in der vorgesehenen Region bereitgestellt werden, um die Kostenverfolgung zu unterst�tzen. 
    - *Datenresidenz und Sicherheitskonformit�t*: Sie k�nnen auch Anforderungen an die Datenaufbewahrung haben und Abonnements pro Kunde oder bestimmten Workloads erstellen und festlegen, dass alle Ressourcen in einem bestimmten Rechenzentrum bereitgestellt werden m�ssen, um die Complianceanforderungen bez�glich Daten und Sicherheit zu gew�hrleisten.

Herzlichen Gl�ckwunsch! Sie haben eine Azure-Richtlinie erstellt, die die Bereitstellung von Azure-Ressourcen auf ein bestimmtes Rechenzentrum beschr�nkt.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.