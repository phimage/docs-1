---
id: repair
title: Repair Page
sidebar_label: Repair Page
---

This page is used to repair the data file when it has been damaged. Generally, you will only use these functions at the request of 4D, when anomalies have been detected while opening the database or following a [verification](verify.md).

**Warning:** Each repair operation involves the duplication of the original file, which increases the size of the application folder. Sie sollten darauf achten (besonders auf macOS, wo 4D Anwendungen als Package erscheinen), dass die Größe der Anwendung nicht exzessiv ansteigt. Manually removing the copies of the original file inside the package can be useful to minimize the package size.

> Repairing is only available in maintenance mode. If you attempt to carry out this operation in standard mode, a warning dialog will inform you that the database will be closed and restarted in maintenance mode.
> 
> When the database is encrypted, repairing data includes decryption and encryption steps and thus, requires the current data encryption key. If no valid encryption key has already been provided, a dialog requesting the passphrase or the encryption key is displayed (see Encrypt page).

## File overview

### Data file to be repaired

Pathname of the current data file. The **[...]** button can be used to specify another data file. When you click on this button, a standard Open document dialog is displayed so that you can designate the data file to be repaired. If you perform a [standard repair](#standard_repair), you must select a data file that is compatible with the open project file. If you perform a [recover by record headers](#recover-by-record-headers) repair, you can select any data file. Once this dialog has been validated, the pathname of the file to be repaired is indicated in the window.

### Original files backup folder

By default, the original data file will be duplicated before the repair operation. It will be placed in a subfolder named “Replaced files (repairing)” in the database folder. The second **[...]** button can be used to specify another location for the original files to be saved before repairing begins. This option can be used more particularly when repairing voluminous files while using different disks.

### Repaired files

4D creates a new blank data file at the location of the original file. The original file is moved into the folder named "\Replaced Files (Repairing) date time" whose location is set in the "Original files backup folder" area (database folder by default). The blank file is filled with the recovered data.

## Standard repair

Standard repair should be chosen when only a few records or indexes are damaged (address tables are intact). The data is compacted and repaired. This type of repair can only be performed when the data and structure file match.

When the repair procedure is finished, the "Repair" page of the MSC is displayed. A message indicates if the repair was successful. If so, you can open the database immediately. ![](assets/en/MSC/MSC_RepairOK.png)

## Recover by record headers

Use this low-level repair option only when the data file is severely damaged and after all other solutions (restoring from a backup, standard repair) have proven to be ineffective.

4D Datensätze sind unterschiedlich groß. Deshalb muss die Stelle, wo sie auf der Festplatte in einer spezifischen Tabelle, genannt Adresstabelle, gespeichert sind, beibehalten werden, um sie wieder zu finden. Das Programm greift deshalb auf die Adresse des Datensatzes über einen Index und eine Adresstabelle zu. Sind nur Datensätze oder Indizes beschädigt, reicht die Standardreparatur in der Regel aus, um das Problem zu lösen. Ist dagegen die Adresstabelle selbst betroffen, ist ein komplexeres Wiederherstellen erforderlich, da diese Tabelle wiederhergestellt werden muss. Dazu verwendet das MSC die Marker, die im Kopfteil jedes Datensatzes angelegt sind. Sie sind vergleichbar mit einem Inhaltsverzeichnis des Datensatzes, inkl. aller wichtigen Informationen, über die sich die Adresstabelle rekonstruieren lässt.

> Haben Sie in der Datenbankstruktur in den Tabelleneigenschaften die Option </strong>Datensätze definitiv löschen</strong> deaktiviert, können nach dem Wiederherstellen nach Datensatzheader zuvor gelöschte Datensätze wieder erscheinen. Wiederherstellen nach Kopfteil berücksichtigt keine Einschränkungen zur Datenintegrität. More specifically, after this operation you may get duplicated values with unique fields or NULL values with fields declared **Never Null**.

When you click on **Scan and repair...**, 4D performs a complete scan of the data file. When the scan is complete, the results appear in the following window:

![](assets/en/MSC/mscrepair2.png)

> If all the records and all the tables have been assigned, only the main area is displayed.

The "Records found in the data file" area includes two tables summarizing the information from the scan of the data file.

- The first table lists the information from the data file scan. Each row shows a group of recoverable records in the data file:
    
    - The **Order** column indicates the recovery order for the group of records. 
    - The **Count** column indicates the number of the records in the table.
    - The **Destination table** column indicates the names of tables that were automatically assigned to the groups of identified records. The names of tables assigned automatically appear in green. Groups that were not assigned, i.e. tables that could not be associated with any records appear in red.
    - The **Recover** column lets you indicate, for each group, whether you want to recover the records. By default, this option is checked for every group with records that can be associated with a table.
- The second table lists the tables of the project file.

### Manual assigning

If several groups of records could not be assigned to tables due to a damaged address table, you can assign them manually. To do this, first select an unassigned group of records in the first table. The "Content of the records" area then displays a preview of the contents of the first records of the group to make it easier to assign them:

![](assets/en/MSC/mscrepair3.png)

Next select the table you want to assign to the group in the "Unassigned tables" table and click on the **Identify table** button. You can also assign a table using drag and drop. The group of records is then associated with the table and it will be recovered in this table. The names of tables that are assigned manually appear in black. Use the **Ignore records** button to remove the association made manually between the table and the group of records.

## Logbuch öffnen

After repair is completed, 4D generates a log file in the Logs folder of the database. Hier können Sie alle ausgeführten Operationen ansehen. It is created in XML format and named: *DatabaseName**_Repair_Log_yyyy-mm-dd hh-mm-ss.xml*" where:

- *DatabaseName* ist der Name der Projektdatei ohne Endung, zum Beispiel "Rechnungen"
- *yyyy-mm-dd hh-mm-ss* ist der Zeitstempel der Datei. Er basiert auf der lokalen Systemzeit, zur der die Wartungsoperation gestartet wurde, zum Beispiel "2019-02-11 15-20-45".

Klicken Sie auf die Schaltfläche **Logbuch öffnen**, zeigt 4D das neueste Logbuch im standardmäßigen Browser des Rechners.