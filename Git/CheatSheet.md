# Git Cheat Sheet

## Repository erstellen

### Neues Repository initialisieren

```bash
git init
```

### Repository klonen

```bash
git clone <repository-url>
```

Beispiel:

```bash
git clone https://gitlab.com/projekt.git
```

---

## Status prüfen

Aktuellen Status anzeigen:

```bash
git status
```

Zeigt:
- geänderte Dateien
- neue Dateien
- Dateien im Staging-Bereich

---

## Änderungen committen

### Alle Änderungen hinzufügen

```bash
git add .
```

### Einzelne Datei hinzufügen

```bash
git add Dateiname.cs
```

### Commit erstellen

```bash
git commit -m "Beschreibung der Änderung"
```

Beispiele:

```bash
git commit -m "Add Swagger configuration"
```

```bash
git commit -m "Fix login validation"
```

---

## Änderungen hochladen

### Push

```bash
git push
```

### Erster Push

```bash
git push -u origin main
```

---

## Änderungen herunterladen

```bash
git pull
```

---

## Commit-Historie anzeigen

### Vollständige Historie

```bash
git log
```

### Kompakte Historie

```bash
git log --oneline
```

### Letzte fünf Commits

```bash
git log --oneline -5
```

---

## Letzten Commit anzeigen

```bash
git show HEAD
```

---

## Branches

### Vorhandene Branches anzeigen

```bash
git branch
```

### Branch erstellen

```bash
git branch feature-login
```

### Branch wechseln

```bash
git switch feature-login
```

### Branch erstellen und wechseln

```bash
git switch -c feature-login
```

---

## Änderungen verwerfen

### Einzelne Datei zurücksetzen

```bash
git restore Dateiname.cs
```

### Alle lokalen Änderungen verwerfen

```bash
git restore .
```

---

## Git Ignore

### Warum eine `.gitignore`?

Die `.gitignore` verhindert, dass temporäre Dateien, Build-Dateien oder IDE-spezifische Dateien ins Repository gelangen.

### Best Practice

Die `.gitignore` sollte **vor dem ersten Commit** erstellt werden:

```bash
git init
dotnet new gitignore
git add .
git commit -m "Initial commit"
```

### Typische Visual Studio / .NET Einträge

```gitignore
.vs/
bin/
obj/

*.user
*.suo
```

---

## Remote Repository anzeigen

```bash
git remote -v
```

---

## Typischer Workflow

```bash
git status
git a*d .
git commit -m "Implement new f*ature"
git push
```

---

## Best Practices

✅ Vor dem ersten Commit `.gitignore` anlegen

✅ Regelmäßig committen

✅ Aussagekräftige Commit-Nachrichten verwenden

✅ Vor jedem Push `git status` prüfen

✅ Nur Quellcode und relevante Projektdateien committen

---

### Nicht committen
- `.vs`
- `bin`
- `obj`
- Passwörter
- API-Keys
- Zugangsdaten
- lokale Konfigurationsdateien
