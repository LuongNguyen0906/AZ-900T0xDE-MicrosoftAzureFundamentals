---
wts:
    title: '22 � Berechnen zusammengesetzter SLAs'
    module: 'Modul 04 � Azure-Preise und -Support'
---
# 22 � Berechnen von Verbund-SLAs


In dieser exemplarischen Vorgehensweise ermitteln wir das Verf�gbarkeits-SLA von Azure-Diensten und berechnen dann die SLA-basierte erwartete Verf�gbarkeit auf Anwendungsbasis.

Unsere Beispielanwendung besteht aus diesen Azure-Diensten. Wir wollen hier nicht auf tiefgreifende architektonische Konfigurationen und �berlegungen eingehen, sondern ein allgemeines Beispiel geben.

+ **App Service**: So hosten Sie die Anwendung.
+ **Azure AD B2C**: Zum Authentifizieren von Benutzeranmeldungen und Verwalten von Profilen.
+ **Application Gateway**: So verwalten Sie den Anwendungszugriff und die Skalierung. 
+ **Azure SQL-Datenbank**: So speichern Sie Anwendungsdaten. 

# Aufgabe�1: Bestimmen der prozentualen SLA-Verf�gbarkeitswerte f�r unsere Anwendung

1. Navigieren Sie in einem Browser zur Seite [DLV-�bersicht f�r Azure-Dienste](https://azure.microsoft.com/de-de/support/legal/sla/summary/).

2. Suchen Sie den SLA-Betriebszeitwert des **App Service**, **99,95 %**. Klicken Sie auf **Alle Details anzeigen**, und erweitern Sie dann **SLA-Details**. Schauen Sie sich den **Prozentsatz der monatlichen Betriebszeit** und die **Servicegutschrift** an.

3. Kehren Sie zur SLA-Webseite zur�ck, suchen Sie den **Azure Active Directory B2C**-Dienst, und bestimmen Sie den SLA-Betriebszeitwert, in diesem Fall **99,9%**. 

4. Suchen Sie den SLA-Verf�gbarkeitswert des **Application Gateway**, **99,95 %**. 

5. Die Azure SQL-Datenbank verwendet Premium-Ebenen, ist jedoch nicht f�r zonenredundante Bereitstellungen konfiguriert. Suchen Sie den SLA-Verf�gbarkeitswert der **Azure SQL-Datenbank** (**99,99 %**). 

    **Hinweis**: Es gibt unterschiedliche Betriebszeitwerte f�r unterschiedliche Konfigurationen und Bereitstellungen der Azure SQL-Datenbank. Es ist wichtig, dass Sie Ihre erforderlichen Betriebszeitwerte genau kennen, wenn Sie Ihre Bereitstellung und Konfiguration planen und die Kosten bestimmen. Kleine �nderungen der Betriebszeit k�nnen sich auf die Dienstkosten auswirken und m�glicherweise die Komplexit�t der Konfiguration erh�hen. Einige andere Dienste, die auf der Azure SLA-Zusammenfassungs-Webseite von Interesse sein k�nnten, w�ren zum Beispiel: **Virtuelle Computer**, **Speicherkonten** und **Cosmos DB**.

# Aufgabe�2: Prozentuale Verf�gbarkeit der Verbund-SLA-Betriebszeit der Anwendung berechnen

1. Wenn einer der Dienste, aus denen unsere Anwendung besteht, nicht verf�gbar ist, steht unsere Anwendung Benutzern nicht zur Anmeldung und Nutzung zur Verf�gung. Daher besteht die Gesamtbetriebszeit f�r unsere Anwendung aus folgenden Elementen:

    **App Service-Betriebszeit in %** X **Azure AD B2C-Betriebszeit in %** X **Azure Application Gateway-Betriebszeit in %** X **Azure SQL-Datenbank--Betriebszeit in %** = **Gesamtbetriebszeit in %**

    was in Prozent wie folgt aussieht:

    **99,95 %** X **99,9 %** X **99,95 %** X **99,99 %** = **99,79 %**

    Dies ist die SLA-basierte erwartete Verf�gbarkeit unserer Anwendung mit den aktuellen Diensten und der aktuellen Architektur.

Herzlichen Gl�ckwunsch! Sie haben die SLA-basierte Betriebszeit f�r jeden der Dienste in unserer Beispielanwendung ermittelt und dann die Verbund-SLA-basierte erwartete Verf�gbarkeit f�r die Anwendung berechnet.