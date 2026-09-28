# 🚀 Ollama Subagenten! Modell-Installationsanleitung & Übersicht

Diese Übersicht enthält alle empfohlenen KI-Modelle als Subagenten.

---

## 📊 System-Empfehlung & VRAM-Management

Bei 4 GB VRAM werden kleinere Modelle ($1.5\text{B} - 3.8\text{B}$) vollständig in den GPU-Speicher geladen und antworten blitzschnell. Größere Modelle ($7\text{B} - 14\text{B}$) nutzen Ollamas automatisches CPU/RAM-Offloading und laufen flüssig über den Hauptspeicher.

---

## 🛠️ Modell-Kategorien & Anwendungsbereiche

### 1. Fast-Coder & Patch-Subagenten
*Schnelle Anpassungen, Bugfixes, Refactoring & Syntax-Checks*

* **`qwen2.5-coder:3b`** (ca. 1.9 GB Speicherbedarf)
  * **Vorteil:** Passt komplett in 4 GB VRAM. Antwortet extrem schnell und beherrscht Code-Generierung sowie Tool-Calling hervorragend.
  * **Befehl:** `ollama pull qwen2.5-coder:3b`
* **`qwen2.5-coder:1.5b`** (ca. 1.0 GB Speicherbedarf)
  * **Vorteil:** Ultraleichtgewicht für Mikro-Tasks wie Linter-Fixes, Git-Commit-Messages oder einfache Regex-Aufgaben.
  * **Befehl:** `ollama pull qwen2.5-coder:1.5b`
* **`codegemma:2b`** (ca. 1.6 GB Speicherbedarf)
  * **Vorteil:** Googles kompaktes Code-Modell, sehr stark bei Code-Vervollständigungen (Fill-In-The-Middle) und Inline-Patches.
  * **Befehl:** `ollama pull codegemma:2b`

---

### 2. Planner & Architect Subagenten
*Strategische Planung, System-Design & logische Problemzerlegung*

* **`deepseek-r1:8b`** (ca. 4.9 GB Speicherbedarf)
  * **Vorteil:** Nutzt Chain-of-Thought-Reasoning (Denkprozesse). Ideal, um komplexe Refactorings oder System-Architekturen in nummerierte Schritte zu zerlegen.
  * **Befehl:** `ollama pull deepseek-r1:8b`
* **`phi4:14b`** (ca. 9.1 GB Speicherbedarf)
  * **Vorteil:** Microsofts Phi-4 Modell bietet herausragende logische Genauigkeit und mathematisches Verständnis über RAM-Offloading.
  * **Befehl:** `ollama pull phi4:14b`
* **`phi3.5:3.8b`** (ca. 2.2 GB Speicherbedarf)
  * **Vorteil:** Extrem starke Logik auf kompakter Ebene. Läuft vollständig im VRAM für ultraschnelle Entwürfe.
  * **Befehl:** `ollama pull phi3.5:3.8b`

---

### 3. Reviewer, Test & Security Subagenten
*Qualitätskontrolle, Code-Reviews, Edge-Case-Testing & Security-Audits*

* **`llama3.1:8b`** (ca. 4.7 GB Speicherbedarf)
  * **Vorteil:** Zuverlässig bei allgemeiner Instruktionsbefolgung, Dokumentation und Tool-Calling.
  * **Befehl:** `ollama pull llama3.1:8b`
* **`mistral:7b`** (ca. 4.1 GB Speicherbedarf)
  * **Vorteil:** Sehr präzise bei der Einhaltung strenger Vorgaben, Richtlinien und Linter-Regeln.
  * **Befehl:** `ollama pull mistral:7b`

---

### 4. Vision Subagenten
*UI-Analyse, Visual-Debugging, OCR & Terminal-Screenshots*

* **`moondream`** (ca. 1.8B / 1.5 GB Speicherbedarf)
  * **Vorteil:** Passt komplett in die Grafikkarte. Liest Layouts, Fehler-Screenshots und UI-Elemente extrem schnell aus.
  * **Befehl:** `ollama pull moondream`
* **`qwen2-vl:2b`** (ca. 1.5 GB Speicherbedarf)
  * **Vorteil:** Sehr stark in Dokumenten- und Code-Screenshot-Analyse bei minimalem VRAM-Bedarf.
  * **Befehl:** `ollama pull qwen2-vl:2b`

---

### 5. Vector & RAG Subagenten
*Lokale Code-Einbettungen, Datei-Indexierung & Semantische Suche*

* **`nomic-embed-text`** (ca. 270 MB Speicherbedarf)
  * **Vorteil:** Standard-Modell für lokale Code-Einbettungen und blitzschnelle semantische Suche im Projektordner.
  * **Befehl:** `ollama pull nomic-embed-text`

---

## 🧰 Ollama Modell Installer (GUI)

Grafischer Installer (CustomTkinter) für die **komplette Ollama-Bibliothek**: **238 Modellfamilien** der offiziellen Ollama-Bibliothek (Stand 2026-09-28) mit Suche, Kategorie-Filter (Allgemein, Code, Reasoning, Vision, Embeddings), Größenauswahl je Modell, Installiert-Status, Speicherschätzung und Batch-Installation. Die oben aufgeführten Pandora-Subagenten-Modelle sind alle in der Bibliothek enthalten (Suche z. B. nach `qwen2.5-coder`, `phi4` oder `nomic-embed-text`).

**Wichtig zur Bibliothek:** „Alle Modelle“ komplett zu laden würde viele Terabyte belegen. Deshalb wird nur installiert, was du per Häkchen auswählst. „Gefilterte auswählen“ wählt je Modell die **größte Variante innerhalb des Größenlimits** (Standard: ≤ 8B; wählbar bis „Unbegrenzt“). Modelle ohne Größenangabe werden nur bei „Unbegrenzt“ gewählt. Vor dem Download zeigt ein Dialog die geschätzte Gesamtgröße (grob, Q4) und den freien Speicher.

**Cloud-Modelle** (12 Stück, z. B. `kimi-k3`) sind standardmäßig ausgeblendet. Sie laufen über Ollamas Cloud (`name:cloud`) und benötigen ein Konto (`ollama signin`).

Der Katalog ist ein fest eingebauter Schnappschuss (`ollama_library.py`). Neue Modelle kommen mit einem Update dazu; beliebige Tags lassen sich weiterhin mit `ollama pull <name>` laden.

### Updates

Mit jedem Ollama-Update bemühe ich mich, auch dieses Tool zu aktualisieren (Modellkatalog und Kompatibilität).

### Plattformen

Läuft unter **Windows, Linux und macOS** (Python 3.9+, Tk 8.6). Ollama selbst muss separat installiert sein (<https://ollama.com/download>); der Installer findet `ollama` auch dann, wenn es nicht im PATH liegt (z. B. bei einer per Finder gestarteten macOS-App).

### Start aus dem Quellcode

```bash
pip install -r requirements.txt     # unter Debian/Kali/Pi: ggf. zuerst  sudo apt install python3-tk
python ollama_model_installer.py
python -m unittest -v
```

### Builds

| Plattform | Befehl | Ergebnis |
|---|---|---|
| Windows | `build.bat` | `dist\OllamaModelInstaller.exe` |
| Debian / Kali / Raspberry Pi OS | `./build_deb.sh` | `dist/ollama-modell-installer_<Version>_all.deb` |
| macOS | `./build_mac.sh` (optional `--dmg`, `--universal2`) | `dist/OllamaModelInstaller.app` |

**Linux (.deb):** Das Paket ist architekturunabhängig (`Architecture: all`) – ein einziges `.deb` läuft auf dem Raspberry Pi 4B (arm64/armhf) und auf dem Acer Aspire 5930G mit Kali (amd64). Installation mit `sudo apt install ./dist/ollama-modell-installer_1.0.0_all.deb` (zieht `python3-tk` automatisch nach). Ohne Internet beim Bauen: `./build_deb.sh --wheels ./wheels`. Start über das Menü „Ollama Modell Installer“ oder `ollama-modell-installer`.

**macOS:** Build nur auf einem Mac. Braucht Python mit Tk 8.6 (python.org-Installer oder `brew install python-tk`). Das Icon `.icns` wird bei Bedarf aus `ollama_model_installer_icon.png` erzeugt; liegt eine eigene `ollama_model_installer_icon.icns` im Ordner, wird diese verwendet. Die App ist nicht notarisiert: auf anderen Macs erst per Rechtsklick → „Öffnen“ starten.

**Modell-Ordner:** `OLLAMA_MODELS`, sonst unter Linux `/usr/share/ollama/.ollama/models` (systemd-Dienst), sonst `~/.ollama/models` – daran orientiert sich die Prüfung des freien Speichers.

---

## ⚡ Quick-Install Batch (Alle Modelle nacheinander herunterladen)

Führe den folgenden Befehl in deiner Windows Eingabeaufforderung (CMD) oder PowerShell aus:

```cmd
ollama pull qwen2.5-coder:3b && ollama pull qwen2.5-coder:1.5b && ollama pull codegemma:2b && ollama pull deepseek-r1:8b && ollama pull phi4:14b && ollama pull phi3.5:3.8b && ollama pull llama3.1:8b && ollama pull mistral:7b && ollama pull moondream && ollama pull qwen2-vl:2b && ollama pull nomic-embed-text
```
