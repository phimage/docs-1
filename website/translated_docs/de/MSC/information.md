---
id: Information
title: Seite Information
sidebar_label: Seite Information
---

Die Seite “Information” liefert Informationen über die 4D Umgebung und die Systemumgebung, die Dateien der Datenbank und der Anwendung. Über die Registerkarten am oberen Rand können Sie die einzelnen Seiten aufrufen.

## Programm

Der obere Bereich gibt Name, Version und Speicherort des Programms und des aktiven 4D Ordners an. Weitere Informationen dazu finden Sie im Handbuch *4D Programmiersprache* unter der Funktion **Get 4D folder**. ```Get 4D folder``` command in the *4D Language Reference* manual).

Der mittlere Bereich gibt Name und Speicherort der Projektdatei und der Datendatei der Datenbank und des Logbuchs (wenn vorhanden) an. Der untere Bereich zeigt den Namen des 4D Lizenzinhabers, die Art der Lizenz, und bei aktivierten Kennwörtern auch den Anwendernamen. Ist das nicht der Fall, erscheint als Anwendername Designer.

- **Pfadnamen anzeigen und auswählen**: Auf der Seite **Programm** erscheinen die Pfadnamen in PopUp-Menüs mit der Ordnerfolge, so wie sie auf der Festplatte angeordnet ist:  
    ![](assets/en/MSC/MSC_popup.png) Wählen Sie einen Eintrag (Festplatte oder Ordner), erscheint er in einem neuen Systemfenster. Der Eintrag **Pfad kopieren** kopiert den vollständigen Pfadnamen als Text mit den Trennern der aktuellen Plattform in die Zwischenablage.

- **"Licenses" Ordner** Diese Schaltfläche zeigt den Inhalt des aktiven Licenses Ordner in einem neuen Systemfenster an. Alle Lizenzdateien, die in Ihrer 4D Umgebung installiert sind, sind in diesem Ordner auf Ihrer Festplatte zusammengefasst. Beim Öffnen über einen Web Browser erscheinen die Informationen über die enthaltenen Lizenzen und ihre Merkmale. Der Speicherort des Ordners Licenses kann je nach Version Ihres Betriebssystems variieren. Weitere Informationen dazu finden Sie unter der 4D Funktion **Get 4D folder**. ```Get 4D folder``` command. ***Hinweis:** Sie können auf diesen Ordner auch zugreifen, wenn Sie im Menü Hilfe>Lizenz aktualisieren aufrufen.*</p></li> </ul> 
    
    ## Tables
    
    Diese Seite gibt einen Überblick über die Tabellen in Ihrer Anwendung:
    
    ![](assets/en/MSC/MSC_Tables.png)
    
    > Information auf dieser Seite ist im Standardmodus und im Wartungsmodus verfügbar.
    
    Die Seite listet alle Tabellen der Datenbank - auch die ausgeblendeten - mit den dazugehörigen Merkmalen:
    
    - **ID**: Interne Nummer der Tabelle.
    - **Tabellen**: Name der Tabelle. Namen von gelöschten Tabellen erscheinen in Klammern (wenn sie noch im Papierkorb sind).
    - **Datensätze**: Gesamtanzahl der Datensätze in der Tabelle. Ist ein Datensatz beschädigt oder nicht lesbar, erscheint *Error* anstelle der Zahl. Dann können Sie abwägen, ob Sie die Tools zum Prüfen und Reparieren einsetzen.
    - **Felder**: Anzahl der Felder in der Tabelle. Ausgeblendete Felder werden mitgezählt, gelöschte Felder dagegen nicht.
    - **Indizes**: Anzahl der verschiedenen Indizes in der Tabelle
    - **Verschlüsselbar**: Ist dieses Attribut aktiv, wird es für die Tabelle auf der Strukturebene ausgewählt (siehe unter Abschnitt Verschlüsselbar).
    - **Verschlüsselt**: Ist dieses Attribut aktiv, werden die Datensätze der Tabelle in der Datendatei verschlüsselt. **Hinweis:** Besteht Inkonsistenz zwischen der Option Verschlüsselbar und Verschlüsselt, müssen Sie den Verschlüsselungsstatus der Datendatei auf der Seite **Verschlüsseln** der Anwendung prüfen. *
    - **Größe der Adresstabelle**: Größe der Adresstabelle für jede Tabelle. In der Adresstabelle wird pro angelegtem Datensatz in der Tabelle intern ein Element gespeichert. Es verbindet Datensätze mit ihrer physikalischen Adresse. Aus Performance Gründen wird sie beim Löschen von Datensätzen nicht angepasst, so dass ihre Größe von der aktuellen Anzahl der Datensätze in der Tabelle abweichen kann. Bei einem deutlichen Unterschied können Sie die Größe der Adresstabelle über die Option "Komprimiere Adresstabelle" optimieren (siehe Seite [Kompakt](compact.md)). ***Note:** Differences between address table size and record number can also result from an incident during the cache flush.*
    
    ## Data
    
    The **Data** page provides information about the available and used storage space in the data file.
    
    > This page cannot be accessed in maintenance mode
    
    The information is provided in graph form:
    
    ![](assets/en/MSC/MSC_Data.png)
    
    > This page does not take into account any data that may be stored outside of the data file (see "External storage").
    
    Files that are too fragmented reduce disk, and thus, database performance. If the occupation rate is too low, 4D will indicate this by a warning icon (which is displayed on the Information button and on the tab of the corresponding file type) and specify that compacting is necessary:![](assets/en/MSC/MSC_infowarn.png)
    
    A warning icon is also displayed on the button of the [Compact](compact.md) page: ![](assets/en/MSC/MSC_compactwarn.png)