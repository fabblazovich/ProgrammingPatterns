# Datenbank-Backup in LocalDB wiederherstellen

Mit den folgenden Befehlen kann ein vorhandenes SQL-Server-Backup (.bak) in der lokalen Entwicklungsdatenbank (LocalDB) wiederhergestellt werden.

## 1. Verbindung zur LocalDB herstellen
````Shell
sqlcmd -S "(localdb)\MSSQLLocalDB"
````

Dieser Befehl startet das SQL Command Line Tool (sqlcmd) und verbindet sich mit der lokalen SQL-Server-Instanz MSSQLLocalDB.


## 2. Datenbank aus Backup wiederherstellen

```SQL
RESTORE DATABASE Hotfixes
FROM DISK = 'C:\Temp\Hotfixes_2026-09-28.bak'
WITH
MOVE 'Hotfixes' TO 'C:\Temp\Hotfixes.mdf',
MOVE 'Hotfixes_log' TO 'C:\Temp\Hotfixes_log.ldf',
REPLACE
GO`
```

### Erklärung der Parameter

- RESTORE DATABASE Hotfixes: Erstellt bzw. überschreibt die Datenbank Hotfixes.

- FROM DISK: Gibt den Pfad zur Backup-Datei (.bak) an.

- MOVE 'Hotfixes': Legt fest, wo die Daten-Datei (.mdf) gespeichert wird.

- MOVE 'Hotfixes_log': Legt fest, wo die Transaktionslog-Datei (.ldf) gespeichert wird.

- REPLACE: Überschreibt eine bereits vorhandene Datenbank mit demselben Namen.

- GO: Führt den SQL-Befehl aus.

## Voraussetzungen

### Backup-Datei

Die Backup-Datei muss sich unter folgendem Pfad befinden:

```
C:\Temp\Hotfixes_2026-09-28.bak
```


Der Benutzer benötigt Schreibrechte auf:

````C:\Temp\````