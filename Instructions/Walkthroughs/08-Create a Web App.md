---
wts:
    title: '08 � Erstellen einer Web-App'
    module: 'Modul 02 � Core Azure Services'
---
# 08 � Erstellen einer Web-App

In dieser exemplarischen Vorgehensweise erstellen wir eine neue Web-App, in der ein Docker-Container ausgef�hrt wird. Der Container zeigt eine Begr��ungsnachricht an. 

# Aufgabe�1: Eine Web-App erstellen

Azure App Service ist eine Sammlung von vier Diensten, die alle zum Hosten und Ausf�hren von Webanwendungen dienen. Die vier Dienste (Web-Apps, Mobile Apps, API-Apps und Locic Apps) sehen unterschiedlich aus, funktionieren jedoch letztendlich alle sehr �hnlich. Web-Apps ist der am h�ufigsten verwendete Dienst der vier Dienste. Diesen Dienst werden wir in diesem Lab verwenden.

In dieser Aufgabe erstellen Sie eine Azure App Service-Web-App. 

1. Melden Sie sich beim [Azure-Portal](http://portal.azure.com/) an. 

2. Suchen Sie im Blatt **Alle Dienste** den Eintrag **App Services**, w�hlen Sie ihn aus, und klicken Sie auf **+ Hinzuf�gen**.

3. Geben Sie auf der Registerkarte **Grundlagen** auf dem **Web-App**-Blatt die folgenden Einstellungen an (Ersetzen Sie **xxxx** im Namen der Web-App mit Buchstaben und Ziffern, so dass der Name global eindeutig ist). Behalten Sie ansonsten die Standardeinstellungen bei, auch f�r den App Service-Plan. 

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGWebApp1** (Neu erstellen) |
    | Name | **myDockerWebAppxxxx** |
    | Ver�ffentlichen | **Docker-Container** |
    | Betriebssystem | **Linux** |
    | Region | **USA, Osten** (ignorieren Sie alle Warnungen zur Verf�gbarkeit von Dienstpl�nen) |
    | | |	

4. Klicken Sie auf **Weiter > Docker** und konfigurieren Sie die Containerinformationen. Der Startupbefehl ist optional und wird in dieser �bung nicht ben�tigt. 

    **Hinweis:** Dies ist derselbe Container, der in der exemplarischen Vorgehensweise f�r Container Instances verwendet wurde, um eine Hallo Welt-Meldung anzuzeigen. 

    | Einstellung | Wert |
    | -- | -- |
    | Optionen | **Einzelner Container** |
    | Bildquelle | **Docker Hub** |
    | Zugriffstyp | **�ffentlich** |
    | Bild und Tag | **Microsoft / Aci-Helloworld** |
    | | |	


5. Klicken Sie auf **�berpr�fen + Erstellen **, und klicken Sie dann auf **Erstellen**. 

# Aufgabe�2: Web-App testen

In dieser Aufgabe testen wir die Web-App.

1. Warten Sie, bis die Web-App bereitgestellt ist.

2. Klicken Sie in **Benachrichtigungen** auf **Zur Ressource gehen**. 

3. Suchen Sie im Blatt **�berblick** den Eintrag **URL**. 

    ![Screenshot des Web-App-Eigenschaftenblatts. Die URL wird hervorgehoben.](../images/0801.png)

4. Klicken Sie auf **URL**, um die neue Browser-Registerkarte zu �ffnen und die Seite �Willkommen bei Azure Container Instances� anzuzeigen.

    ![Screenshot der Seite �Willkommen bei Azure Container Instances�.](../images/0802.png)

5. Wechseln Sie wieder zum Blatt **�bersicht** Ihrer Web-App, und beachten Sie, dass es mehrere Diagramme enth�lt. Wenn Sie Schritt 4 einige Male wiederholen, sollte die entsprechende Telemetrie in den Diagrammen angezeigt werden. Dies umfasst die Anzahl der Anfragen und die durchschnittliche Antwortzeit. 

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.

