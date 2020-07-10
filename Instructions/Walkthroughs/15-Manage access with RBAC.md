---
wts:
    title: '15 � Zugriff mit RBAC verwalten'
    module: 'Modul 03 � Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 15 � Verwalten des Zugriffs mit RBAC

In dieser exemplarischen Vorgehensweise werden wir Rollen zuweisen und Aktivit�tsprotokolle anzeigen. 

# Aufgabe�1: Anzeigen und Zuweisen von Rollen

In dieser Aufgabe weisen wir die Rolle �Mitwirkender f�r virtuelle Computer� zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Ressourcengruppen**, und w�hlen Sie diese Option aus. Klicken Sie anschlie�end auf **+ Hinzuf�gen**.

3. Erstellen Sie eine neue Ressourcengruppe. Klicken Sie auf **Erstellen**, wenn Sie fertig sind. 

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **W�hlen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGRBAC** |
    | Region | **(USA) USA, Osten** |
    | | |

4. Erstellen Sie **�berpr�fen + Erstellen**, und klicken Sie dann auf **Erstellen**.

5. **Aktualisieren** Sie die Seite �Ressourcengruppe�, und klicken Sie auf den Eintrag, der die neu erstellte Ressourcengruppe darstellt.

6. Klicken Sie auf das Blatt **Zugriffssteuerung (IAM)**, und wechseln Sie dann auf die Registerkarte **Rollen**. Bl�ttern Sie durch die gro�e Anzahl an Rollendefinitionen, die verf�gbar sind. Verwenden Sie die Informationssymbole, um eine Vorstellung von den Berechtigungen der einzelnen Rollen zu erhalten. Beachten Sie, dass es auch Informationen zur Anzahl der Benutzer und Gruppen gibt, die jeder Rolle zugewiesen sind.

    ![Screenshot des Blatts �IAM-Rollen�. Besitzer-, Mitwirkende- und Leserrollen werden angezeigt.](../images/1501.png)

7. Wechseln Sie zur Registerkarte **Rollenzuweisungen** des Blattes **myRGRBAC - Zugriffssteuerung (IAM)**, klicken Sie auf **Hinzuf�gen** und dann auf **Rollenzuweisung hinzuf�gen**. Weisen Sie Ihrem Benutzerkonto die Rolle �Mitwirkender f�r virtuelle Computer� zu, und klicken Sie dann auf **Speichern**. 

    | Einstellung | Wert |
    | -- | -- |
    | Rolle | **Mitwirkender f�r virtuelle Computer** |
    | Zugriff zuweisen | **Azure AD-Benutzer, -Gruppe oder -Dienstprinzipal** |
    | Ausw�hlen | Ihr Benutzerkonto |
    | | |

    **Hinweis:** Mit der Rolle des Mitwirkenden f�r virtuelle Computer k�nnen Sie virtuelle Computer verwalten, jedoch nicht auf deren Betriebssystem zugreifen oder das virtuelle Netzwerk und das Speicherkonto verwalten, mit denen sie verbunden sind.

    ![Screenshot der Seite �Rollenzuweisung hinzuf�gen� mit den erforderlichen Informationen.](../images/1502.png)

8.  **Aktualisieren** Sie die Seite �Rollenzuweisungen� und stellen Sie sicher, dass Sie jetzt als Mitwirkender eines virtuellen Computers aufgef�hrt sind. 

    **Hinweis**: Diese Zuweisung gew�hrt Ihnen keine zus�tzlichen Berechtigungen, da Ihr Konto bereits �ber die Besitzerrolle verf�gt, die alle mit der Teilnehmerrolle verbundenen Berechtigungen enth�lt.

# Aufgabe�2: Rollenzuweisungen �berwachen und eine Rolle entfernen

In dieser Aufgabe �berpr�fen wir anhand des Aktivit�tsprotokolls die Rollenzuweisung entfernen anschlie�end die Rolle. 

1. Klicken Sie auf dem Blatt �myRGRBAC Ressourcengruppen� auf **Aktivit�tsprotokoll**.

2. Klicken Sie auf **Filter hinzuf�gen**, w�hlen Sie **Vorgang** und dann **Rollenzuweisung erstellen** aus.

    ![Screenshot der Aktivit�tsprotokollseite mit konfiguriertem Filter.](../images/1503.png)

3. �berpr�fen Sie, ob Ihre Rollenzuweisung im Aktivit�tsprotokoll angezeigt wird. 

    **Hinweis**: Wissen Sie, wie Sie Ihre Rollenzuweisung entfernen k�nnen?

Herzlichen Gl�ckwunsch! Sie haben Rollen zugewiesen und Aktivit�tsprotokolle angezeigt. 

**Hinweis**: Um zus�tzliche Kosten zu vermeiden, k�nnen Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe l�schen**. �berpr�fen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **L�schen**. �berwachen Sie die **Benachrichtigungen**, um zu sehen, wie der L�schvorgang abl�uft.


