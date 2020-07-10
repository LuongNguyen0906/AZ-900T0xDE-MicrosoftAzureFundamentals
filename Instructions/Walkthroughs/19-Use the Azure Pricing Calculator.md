---
wts:
    title: '19 � Verwenden des Azure-Preisrechners'
    module: 'Modul 04 � Azure-Preise und -Support'
---
# 19 � Verwenden des Preisrechners

In dieser exemplarischen Vorgehensweise verwenden wir den Azure-Preisrechner, um einen Kostenvoranschlag f�r einen virtuellen Azure-Computer und zugeh�rige Netzwerkressourcen zu erstellen.

# Aufgabe�1: Konfigurieren des Preisrechners

In dieser Aufgabe sch�tzen wir die Kosten einer Infrastruktur-Stichprobe mithilfe des Azure-Preisrechners ab. 

**Hinweis**: Um eine Azure-Preisrechnersch�tzung zu erstellen, enth�lt diese exemplarische Vorgehensweise Beispielkonfigurationen f�r den virtuellen Computer und die zugeh�rigen Ressourcen. Verwenden Sie diese Beispielkonfigurationen, oder stellen Sie stattdessen dem Azure-Preisrechner Details zu Ihren *tats�chlichen* Ressourcenanforderungen zur Verf�gung.

1. Navigieren Sie in einem Browser zur [Azure-Preisrechner](https://azure.microsoft.com/de-de/pricing/calculator/)-Webseite.

2. Klicken Sie auf der Registerkarte **Produkte** auf **Virtual Machines**, um Details zu Ihrer Konfiguration des virtuellen Computers hinzuzuf�gen. Scrollen Sie nach unten, um die Details des virtuellen Computers anzuzeigen. 

3. Ersetzen Sie den Text **Ihre Sch�tzung** und **Virtuelle Computer** mit aussagekr�ftigeren Namen f�r Ihre Azure-Preisrechnersch�tzung und Ihre Konfiguration des virtuellen Computers. In dieser exemplarischen Vorgehensweise wird **Meine Preisrechnersch�tzung** f�r die Sch�tzung und **Virtueller Windows-Computer** f�r die Konfiguration des virtuellen Computers verwendet.

   ![Screenshot des VM-Konfigurationsbereichs auf der Azure-Webseite f�r Preisrechnersch�tzung. Der hervorgehobene Sch�tzungsname und der Konfigurationsname des virtuellen Computers geben an, wie ein Sch�tzungsname und ein Konfigurationsname f�r den virtuellen Computer zu einer Sch�tzung des Azure-Preisrechners hinzugef�gt werden.](../images/1901.png)

4. �ndern Sie die Standardkonfiguration des virtuellen Computers.

    | Region | Betriebssystem | Typ |
    |------|----------------|----|
    | Europa, Norden | Windows | (Nur Betriebssystem) |
    | | |

    | Ebene | Instanz |
    |----|--------|
    | Standard | A2: 2 Kernspeicher, 3,5 GB RAM, 135 GB tempor�rer Speicher |
    | | |

   ![Screenshot des VM-Konfigurationsbereichs auf der Azure-Webseite f�r Preisrechnersch�tzung. Die hervorgehobenen Beispiele f�r vom Benutzer eingegebene Konfigurationseigenschaftswerte des virtuellen Computers geben an, wie eine Konfiguration des virtuellen Computers in einer Azure-Preisrechnersch�tzung angegeben wird.](../images/1902.png)

    **Hinweis**: Die Spezifikationen und Preise der Instanzen des virtuellen Computers k�nnen von denen in diesem Beispiel abweichen. Folgen Sie dieser exemplarischen Vorgehensweise, indem Sie eine Instanz ausw�hlen, die dem Beispiel so genau wie m�glich entspricht. W�hlen Sie im Men� **Mehr Info** rechts **Produktdetails** aus, um Details zu den verschiedenen Produktoptionen des virtuellen Computers anzuzeigen.

5. Legen Sie **Abrechnungsoption** auf **Vorausbezahlung** fest.

   ![Screenshot des Bereichs mit den Abrechnungsoptionen des virtuellen Computers auf der Azure-Webseite f�r Preisrechnersch�tzung. Die hervorgehobene Abrechnungsoption �Vorausbezahlung� gibt an, wie eine Abrechnungsoption f�r einen virtuellen Computer in einer Azure-Preisrechnersch�tzung angegeben wird.](../images/1903.png)

6. In Azure wird ein Monat als 730 Stunden definiert. Wenn Ihr virtueller Computer jeden Monat zu 100 Prozent verf�gbar sein muss, setzen Sie den Wert f�r Stunden pro Monat auf `730`. In diesem exemplarischen Vorgehensweise muss ein virtueller Computer jeden Monat zu 50 Prozent verf�gbar sein.

    Belassen Sie die Anzahl der virtuellen Computer auf `1`, und �ndern Sie den Wert f�r Stunden pro Monat zu `365`.

   ![Screenshot des Bereichs mit den Abrechnungsoptionen des virtuellen Computers auf der Azure-Webseite f�r Preisrechnersch�tzung. Die hervorgehobene Zahl von Instanzen des virtuellen Computers und Stunden pro Monat gibt an, wie die Anzahl von Instanzen und Stunden pro Monat f�r einen virtuellen Computer in einer Sch�tzung des Azure-Preisrechners bestimmt wird.](../images/1904.png)

7. �ndern Sie im Bereich **Verwaltete BS-Datentr�ger** die standardm��ige VM-Speicherkonfiguration.

    | Ebene | Diskgr��e | Zahl der Disks | Momentaufnahme | Speichertransaktionen |
    | ---- | --------- | --------------- | -------- | -------------------- |
    | HDD Standard | S30: 1.024 GiB | 1 | Aus | 10.000 |

   ![Screenshot des Optionsbereichs f�r verwaltete Betriebssystemdatentr�ger auf der Azure-Preisberechnungs-Webseite. Die hervorgehobenen Optionen f�r Stufentyp, Datentr�gergr��e, Anzahl der Datentr�ger und Anzahl der Speichertransaktionen geben an, wie eine Speicherkonfiguration f�r einen virtuellen Computer in einer Azure-Preisrechnersch�tzung angegeben wird.](../images/1905.png)

8. Informationen zum Hinzuf�gen von Netzwerkbandbreite zu Ihrer Sch�tzung finden Sie oben auf der Azure-Preisrechner-Webseite. Klicken Sie auf **Netzwerk** im Produktmen� links und dann auf die Kachel **Bandbreite**. Klicken Sie im Meldungsdialogfeld **Bandbreite hinzugef�gt** auf **Anzeigen**.

   ![Screenshot des Bereichs f�r Netzwerkprodukte auf der Azure-Preisrechner-Webseite. Die hervorgehobenen Kacheln �Netzwerk�, �Bandbreite hinzuf�gen� und �Bandbreite anzeigen� geben an, wie Details einer Netzwerkbandbreiten-Konfiguration in einer Azure-Preisrechnersch�tzung hinzugef�gt und angezeigt werden.](../images/1906.png)

9. F�gen Sie einen Namen f�r die Bandbreitenkonfiguration Ihres virtuellen Computers hinzu. In diesem exemplarischen Beispiel lautet der Name **Bandbreite: Windows-VM**. �ndern Sie die standardm��ige Bandbreitenkonfiguration, indem Sie die folgenden Details hinzuf�gen.

    | Region | Betrag f�r ausgehende Daten�bertragung in Zone 1 |
    | ------ | -------------------------------------- |
    | Europa, Norden | 50 GB |

   ![Screenshot des Konfigurationsbereichs f�r die Netzwerkbandbreite auf der Webseite der Azure-Preisrechners. Die hervorgehobenen Beispiele f�r vom Benutzer eingegebene Bandbreiten-Eigenschaftswerte geben an, wie eine Bandbreitenkonfiguration f�r einen virtuellen Computer innerhalb einer Azure-Preisrechnersch�tzung angegeben wird.](../images/1907.png)

10. Kehren Sie zum Hinzuf�gen eines Application Gateway zum Anfang der Azure-Preisrechner-Webseite zur�ck. Klicken Sie im Produktmen� **Netzwerk** auf die Kachel **Application Gateway**. Klicken Sie im Meldungsdialogfeld **Application Gateway** auf **Anzeigen**.

    ![Screenshot des Bereichs f�r Netzwerkprodukte auf der Azure-Preisrechner-Webseite. In den hervorgehobenen Kacheln �Netzwerk�, �Application Gateway hinzuf�gen� und �Application Gateway anzeigen� wird angegeben, wie Details einer Application Gateway-Konfiguration in einer Azure-Preisrechnersch�tzung hinzugef�gt und angezeigt werden.](../images/1908.png)

11. F�gen Sie einen Namen f�r Ihre Application Gateway-Konfiguration hinzu. In dieser exemplarischen Vorgehensweise ist der Name **App Gateway: Windows-VM**. �ndern Sie die Standardkonfiguration des Application Gateway, indem Sie die folgenden Details hinzuf�gen.

    | Region | Ebene | Gr��e |
    | ------ | ---- | ---- |
    | Europa, Norden | Basic | Klein |
    | | |

    | Instanzen | Stunden |
    | ------- | ------- |
    | 1 | 365 |
    | | |

    | Verarbeitete Daten |
    | -------------- |
    | 50 GB |
    | | |

    | Zone 1: Nordamerika, Europa |
    | ----------------------------- |
    | 50 GB |
    | | |

    ![Screenshot des Application Gateway-Konfigurationsbereichs auf der Webseite f�r die Azure-Preisrechnersch�tzung.](../images/1909.png)


# Aufgabe�2: Preissch�tzung �berpr�fen

In dieser Aufgabe werden die Ergebnisse des Azure-Preisrechners �berpr�ft. 

1. Scrollen Sie zum Ende der Azure-Preisrechner-Webseite, um die Gesamtsumme der **Gesch�tzten monatlichen Kosten** anzuzeigen.

    **Hinweis**: Informieren Sie sich �ber die verschiedenen Optionen, die im Azure-Preisrechner verf�gbar sind. In dieser exemplarischen Vorgehensweise m�ssen Sie beispielsweise die W�hrung auf Euro aktualisieren.

2. �ndern Sie die W�hrung in Euro und w�hlen Sie dann **Export**, um eine Kopie des Kostenvoranschlags f�r die Offline-Anzeige im Microsoft Excel-Format (`.xlsx`) herunterzuladen.

    ![Screenshot der gesch�tzten monatlichen Gesamtkosten auf der Webseite f�r die Azure-Preisrechnersch�tzung. Die hervorgehobene Euro-W�hrungsoption gibt an, wie die in einer Azure-Preisrechnersch�tzung verwendete W�hrung ge�ndert werden kann. Die hervorgehobene Exportoption zeigt, wie Sie eine Kopie eines Kostenvoranschlags f�r die Offline-Anzeige herunterladen.](../images/1910.png)

    ![Screenshot einer Beispielsch�tzung des Azure-Preisrechners in Microsoft Excel.](../images/1911.png)

Herzlichen Gl�ckwunsch! Sie haben einen Kostenvoranschlag aus dem Azure-Preisrechner heruntergeladen.