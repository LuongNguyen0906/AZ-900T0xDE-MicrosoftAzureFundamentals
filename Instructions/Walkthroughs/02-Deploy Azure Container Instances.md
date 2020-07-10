---
wts:
    title: '02 � Bereitstellen von Azure Container Instances'
    module: 'Modul 02 � Core Azure Services'
---

# 02 � Bereitstellen von Azure Container Instances

In dieser exemplarischen Vorgehensweise erstellen, konfigurieren und stellen wir einen Docker-Container mithilfe von Azure Container Instances (ACI) im Azure-Portal bereit. Der Container ist eine �Welcome to ACI�-Webanwendung, die eine statische HTML-Seite anzeigt. 

# Aufgabe�1: Containerinstanz erstellen

In dieser Aufgabe erstellen wir eine neue Containerinstanz f�r die Webanwendung. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Container Instances**, und w�hlen Sie diese Option aus. Klicken Sie anschlie�end auf **+ Hinzuf�gen**. 

3. Geben Sie die folgenden grundlegenden Details f�r die neue Containerinstanz an (belassen Sie die Standardeinstellungen f�r alles andere so, wie sie sind): 

	| Einstellung| Wert|
	|----|----|
	| Abonnement | **W�hlen Sie Ihr Abonnement** |
	| Ressourcengruppe | **myRGContainer** (Neu erstellen) |
	| Containername| **mycontainer**|
	| Region | **(USA) USA, Osten** |
	| Bildquelle| **Docker Hub oder andere Registrierung**|
	| Bildtyp| **�ffentlich**|
	| Bild| **microsoft/aci-helloworld**|
	| BS-Typ:| **Linux** |
	| Gr��e| ***Belassen Sie die Standardeinstellung***|
	|||


4. Konfigurieren Sie die Registerkarte �Netzwerk� (ersetzen Sie **xxxx** durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie f�r alle anderen Einstellungen die Standardwerte.

	| Einstellung| Wert|
	|--|--|
	| DNS-Namensbezeichnung| **mycontainerdnsxxxx** |
	|||
	
	**Hinweis**: Ihr Container ist unter �dns-name-label.region.azurecontainer.io� �ffentlich erreichbar. Wenn Sie die Fehlermeldung **DNS-Namensbezeichnung nicht verf�gbar** nach der Bereitstellung erhalten, geben Sie eine andere DNS-Namensbezeichnung an und stellen Sie sie erneut bereit.

	![Screenshot des Konfigurationsbereichs des Blatts zum Erstellen von Container Instances im Azure-Portal mit eingegebener DNS-Namensbezeichnung. ](../images/0201.png)

5. Klicken Sie auf **�berpr�fen + Erstellen**, um den automatischen Validierungsprozess zu starten.

6. Klicken Sie auf **Erstellen**, um die Containerinstanz zu erstellen. 

7. �berwachen Sie die Bereitstellungsseite und die Seite **Benachrichtigungen**. 

8. W�hrend Sie warten, k�nnten Sie daran interessiert sein, den [Beispielcode hinter dieser einfachen Anwendung](https://github.com/Azure-Samples/aci-helloworld) anzuzeigen. Durchsuchen Sie den Ordner �\App�. 

# Aufgabe�2: �berpr�fen Sie die Bereitstellung der Containerinstanz

In dieser Aufgabe �berpr�fen wir, ob die Containerinstanz ausgef�hrt wird, indem wir sicherstellen, dass die Willkommensseite angezeigt wird.

1. Klicken Sie nach Abschluss der Bereitstellung auf **Zu Ressource wechseln**, verkn�pfen Sie das Blatt �Bereitstellung� oder die Verkn�pfung mit der Ressource im Benachrichtigungsbereich.

2. Stellen Sie im Blatt **�berblick** von **meincontainer** sicher, dass der **Status** Ihres Containers auf **wird ausgef�hrt** steht. 

3. Suchen Sie den vollqualifizierten Dom�nennamen (FQDN).

	![Screenshot des �bersichtsbereichs f�r den neu erstellten Container im Azure-Portal mit hervorgehobenem FQDN. ](../images/0202.png)

2. Kopieren Sie den vollqualifizierten Dom�nennamen des Containers in das URL-Textfeld des Webbrowsers, und dr�cken Sie die EINGABETASTE****. Die Startseite sollte angezeigt werden. 

	![Screenshot der ACI-Begr��ungsnachricht, die in einem Webbrowser angezeigt wird.](../images/0203.png)

**Hinweis**: Sie k�nnen auch die Container-IP-Adresse in Ihrem Browser verwenden. 

Herzlichen Gl�ckwunsch! Sie haben Azure-Portal verwendet, um eine Anwendung erfolgreich in einem Container in Azure Containerinstanz bereitzustellen.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
