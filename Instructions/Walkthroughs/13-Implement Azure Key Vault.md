---
wts:
    title: '13 � Implementieren von Azure Key Vault'
    module: 'Modul 03 � Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 13 � Implementieren von Azure Key Vault

In dieser exemplarischen Vorgehensweise erstellen wir einen Azure Key Vault und erstellen dann ein Kennwortgeheimnis in diesem Schl�sseltresor. Dabei wird ein sicher gespeichertes, zentral verwaltetes Kennwort f�r die Verwendung mit Anwendungen bereitgestellt.

# Aufgabe�1: Einen Azure Key Vault erstellen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie im Blatt **Alle Dienste** die Option **Schl�sseltresore**, und w�hlen Sie sie aus. W�hlen Sie dann **+ Hinzuf�gen** aus.

3. Konfigurieren Sie den Schl�sseltresor (ersetzen Sie **xxxx** im Namen des Schl�sseltresors durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Verwenden Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGKV** (Neu erstellen) |
    | Schl�sseltresorname | **keyvaulttestxxx** |
    | Ort | **USA, Osten** |
    | Tarif | **Standard** |
    | | |

4. Klicken Sie auf **�berpr�fen + Erstellen **, und klicken Sie dann auf **Erstellen**. 

5. Wenn der neue Schl�sseltresor bereitgestellt ist, klicken Sie auf **Zu Ressource wechseln**. Sie k�nnen aber auch nach Ihrem neuen Schl�sseltresor suchen. 

6. Klicken Sie auf die Schl�sseltresor-Registerkarte **�bersicht**, und beachten Sie die Angabe f�r **DNS-Name**. Anwendungen, die Ihren Tresor �ber die REST-API verwenden, werden diesen URI ben�tigen.

7. Nehmen Sie sich einen Moment Zeit, um einige der anderen wichtigen Schl�sseltresoroptionen zu durchsuchen. Pr�fen Sie unter **Einstellungen** die Eintr�ge **Schl�ssel**, **Geheimnisse**, **Zertifikate**, **Zugriffsrichtlinien** und **Firewalls und virtuelle Netzwerke**.

    **Hinweis**: Ihr Azure-Konto ist das einzige, das berechtigt ist, Vorg�nge f�r diesen neuen Tresor auszuf�hren. Wenn Sie w�nschen, k�nnen Sie dies im Abschnitt **Einstellungen** unter **Zugriffsrichtlinien** �ndern.

# Aufgabe�2: Dem Schl�sseltresor einen geheimen Schl�ssel hinzuf�gen
        
In dieser Aufgabe f�gen wir dem Schl�sseltresor ein Kennwort hinzu. 

1. Klicken Sie unter **Einstellungen** auf **Geheimnisse** und dann auf **Generieren / Importieren**.

2. Konfigurieren Sie das Geheimnis. Belassen Sie f�r die anderen Werte die Standardeinstellungen. Beachten Sie, dass Sie ein Aktivierungs- und Ablaufdatum festlegen k�nnen. Beachten Sie, dass Sie das Geheimnis auch deaktivieren k�nnen.

    | Einstellung | Wert | 
    | --- | --- |
    | Uploadoptionen | **Manuell** |
    | Name | **ExamplePassword** |
    | Wert | **hVFkk96** |
    | | |

3. Klicken Sie auf **Erstellen**.

4. Sobald der geheime Schl�ssel erfolgreich erstellt wurde, klicken Sie auf **ExamplePassword**. Beachten Sie, dass der Status **Aktiviert** lautet.

5. Klicken Sie auf die aktuelle Version, und beachten Sie die **Geheimnis-ID**. Dies ist der URL-Wert, den Sie jetzt mit Anwendungen verwenden k�nnen. Er bietet ein zentral verwaltetes und sicher gespeichertes Kennwort.

6. Klicken Sie auf die Schaltfl�che **Geheimniswert anzeigen**, um das zuvor angegebene Kennwort anzuzeigen.

Herzlichen Gl�ckwunsch! Sie haben einen Azure Key Vault erstellt und anschlie�end in diesem Schl�sseltresor ein Kennwortgeheimnis erstellt. Damit steht ein sicher gespeichertes, zentral verwaltetes Kennwort f�r die Nutzung mit Anwendungen zur Verf�gung.

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.
