---
wts:
    title: '12 � Sicherer Netzwerkdatenverkehr'
    module: 'Modul 03 � Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 12 � Sicherer Netzwerkdatenverkehr

In dieser Anleitung konfigurieren wir eine Netzwerksicherheitsgruppe.

# Aufgabe�1: Erstellen eines virtuellen Computers

In dieser Aufgabe erstellen wir einen virtuellen Windows Server 2019 Datacenter-Computer. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Virtuelle Computer**, und w�hlen Sie diese Option aus. Klicken Sie dann auf **+ Hinzuf�gen**.

3. Auf der Registerkarte **Grundlagen** geben Sie die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellungen | Werte |
    |  -- | -- |
    | Abonnement | **W�hlen Sie Ihr Abonnement**|
    | Ressourcengruppe | **myRGSecure** (Neu erstellen) |
    | Name des virtuellen Computers | **SimpleWinVM** |
    | Ort | **(US) East US**|
    | Bild | **Windows Server 2019 Datacenter**|
    | Gr��e | **Standard D2s v3**|
    | Benutzername des Administratorkontos | **azureuser** |
    | Kennwort f�r das Administratorkonto | **Pa$$w0rd1234**|
    | Regeln f�r eingehende Ports | **Keine**|
    | | |

4. Wechseln Sie zur Registerkarte **Netzwerk**, und konfigurieren Sie die folgende Einstellung:

    | Einstellungen | Werte |
    | -- | -- |
    | NIC-Netzwerksicherheitsgruppe | **Keine**|
    | | |

5. Wechseln Sie zur Registerkarte **Verwaltung**, und w�hlen Sie im Abschnitt **�berwachung** die folgende Einstellung aus:

    | Einstellungen | Werte |
    | -- | -- |
    | Startdiagnose | **Aus**|
    | | |

6. �bernehmen Sie die verbleibenden Standardeinstellungen, und klicken Sie dann auf die Schaltfl�che **�berpr�fen + Erstellen** am unteren Rand der Seite.

7. Sobald die Validierung bestanden ist, klicken Sie auf die Schaltfl�che **Erstellen**. Es kann etwa f�nf Minuten dauern, den virtuellen Computer bereitzustellen.

8. �berwachen Sie die Bereitstellung. Das Erstellen der Ressourcengruppe und des virtuellen Computers kann einige Minuten dauern. 

9. Klicken Sie im Bereitstellungsblatt oder im Infobereich auf **Zu Ressource wechseln**. 

10. Klicken Sie auf dem **SimpleWinVM**-Blatt des virtuellen Computers auf **Netzwerk** und �berpr�fen Sie die Registerkarte **Regeln f�r eingehende Ports**. Beachten Sie, dass der Netzwerkschnittstelle des virtuellen Computers oder dem Subnetz, an das die Netzwerkschnittstelle angeschlossen ist, keine Netzwerksicherheitsgruppe zugeordnet ist.

    **Hinweis**: Identifizieren Sie den Namen der Netzwerkschnittstelle. Sie werden dies in der n�chsten Aufgabe ben�tigen.

# Aufgabe�2: Netzwerksicherheitsgruppe erstellen

In dieser Aufgabe erstellen wir eine Netzwerksicherheitsgruppe und ordnen sie der Netzwerkschnittstelle zu.

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Netzwerksicherheitsgruppen**, und w�hlen Sie diese Option aus. Klicken Sie anschlie�end auf **+ Hinzuf�gen**.

2. Geben Sie die folgenden Einstellungen auf der Registerkarte **Grundlagen** des Blatts **Netzwerksicherheitsgruppe erstellen** an.

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGSecure** |
    | Name | **myNSGSecure** |
    | Region | **(USA) USA, Osten**  |
    | | |

3. Klicken Sie auf **�berpr�fen + Erstellen** und nach der Validierung auf **Erstellen**.

4. Klicken Sie nach dem Erstellen des NSG auf **Zu Ressource wechseln**.

5. Klicken Sie unter **Einstellungen** auf **Netzwerkschnittstellen** und dann auf **+ Zuordnen**.

6. W�hlen Sie die in der vorherigen Aufgabe identifizierte Netzwerkschnittstelle aus. 

# Aufgabe�3: Eingehende Sicherheitsportregel konfigurieren, um RDP zuzulassen

In dieser Aufgabe erlauben wir den RDP-Verkehr zum virtuellen Computer, indem wir eine eingehende Sicherheitsportregel konfigurieren. 

1. Navigieren Sie im Azure-Portal zum Blatt des virtuellen Computers **SimpleWinVM**. 

2. Klicken Sie im Bereich **�bersicht** auf **Verbinden**.

3. Versuchen Sie, �ber RDP eine Verbindung zum virtuellen Computer herzustellen. Standardm��ig erlaubt die Netzwerksicherheitsgruppe kein RDP. Schlie�en Sie das Fehlerfenster. 

    ![Screenshot der Fehlermeldung, die besagt, dass die Verbindung zum virtuellen Computer fehlgeschlagen ist.](../images/1201.png)

4. Scrollen Sie im Blatt �Virtueller Computer� nach unten zum Abschnitt **Einstellungen** und klicken Sie auf **Netzwerk**. Beachten Sie, dass die eingehenden Regeln f�r die Netzwerksicherheitsgruppe **myNSGSecure (an die Netzwerkschnittstelle angeschlossen: myVMNic)** den gesamten eingehenden Datenverkehr mit Ausnahme des Datenverkehrs innerhalb des virtuellen Netzwerks und der Load Balancer-Tests verweigert.

5. Klicken Sie auf der Registerkarte **Regeln f�r eingehende Ports** auf **Regel f�r eingehende Ports hinzuf�gen**. Klicken Sie auf **Hinzuf�gen**, wenn Sie fertig sind. 

    | Einstellung | Wert |
    | -- | -- |
    | Quelle | **Beliebig**|
    | Quellportbereiche | **\*** |
    | Ziel | **Beliebig** |
    | Zielportbereiche | **3389** |
    | Protokoll | **TCP** |
    | Aktion | **Zulassen** |
    | Priorit�t | **300** |
    | Name | **AllowRDP** |
    | | |

6. Warten Sie bis zum Bereitstellen der Regel, und versuchen Sie dann erneut sich per RDP mit dem virtuellen Computer zu verbinden. Diesmal sollten Sie Erfolg haben. Denken Sie daran, der Benutzername ist **azureuser**, und das Passwort lautet **Pa$$w0rd1234**.

# Aufgabe�4: Ausgehende Sicherheitsportregel konfigurieren, um den Internetzugriff zu verweigern

In dieser Aufgabe erstellen wir eine NSG-Regel f�r ausgehende Ports, die den Internetzugriff verweigert, und testen dann, ob die Regel funktioniert.

1. Fahren Sie in der RDP-Sitzung Ihres virtuellen Computers fort. 

2. �ffnen Sie nach dem Start der Maschine den **Internet Explorer**-Browser. 

3. Stellen Sie sicher, dass Sie auf **https://www.bing.com** zugreifen k�nnen, und schlie�en Sie dann Internet Explorer. Sie m�ssen sich durch die erweiterten Sicherheits-Popups von IE durcharbeiten. 

    **Hinweis**: Wir konfigurieren nun eine Regel, um den ausgehenden Internetzugang zu verweigern. 

4. Navigieren Sie im Azure-Portal zur�ck zum Blatt des virtuellen Computers **SimpleWinVM**. 

5. Klicken Sie unter **Einstellungen** auf **Netzewerk** und dann auf **Regeln f�r ausgehende Ports**.

6. Beachten Sie, dass es die Regel **AllowInternetOutbound** gibt. Dies ist eine Standardregel und kann nicht entfernt werden. 

7. Klicken Sie auf **Regel f�r ausgehende Ports hinzuf�gen** rechts von der Netzwerksicherheitsgruppe **myNSGSecure (an die Netzwerkschnittstelle angeschlossen: myVMNic)** und konfigurieren Sie eine neue ausgehende Sicherheitsregel mit einer h�heren Priorit�t, die den Internetverkehr verweigert. Klicken Sie auf  **Hinzuf�gen**, wenn Sie fertig sind. 

    | Einstellung | Wert |
    | -- | -- |
    | Quelle | **Beliebig**|
    | Quellportbereiche | **\*** |
    | Ziel | **Diensttag** |
    | Zieldiensttag | **Internet** |
    | Zielportbereiche | **\*** |
    | Protokoll | **TCP** |
    | Aktion | **Verweigern** |
    | Priorit�t | **4000** |
    | Name | **DenyInternet** |
    | | |

8. Kehren Sie zu Ihrer RDP-Sitzung zur�ck. 

9. Wechseln Sie zu **https://www.microsoft.com**. Die Seite sollte nicht angezeigt werden. M�glicherweise m�ssen Sie sich durch zus�tzliche erweiterte Sicherheits-Popups im IE durcharbeiten.  

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
