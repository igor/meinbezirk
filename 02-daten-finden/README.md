# Daten finden

Wo kommunale Entscheidungsdaten liegen. Wie man sie findet, verarbeitet und verifiziert. Und wie das Muster auf andere Städte übertragen werden kann.

Dieses Dokument hat drei Teile:

1. **Fallstudie Berlin** — Wie der MeinBezirk-Prototyp seine Daten gefunden hat.
2. **Recherche-Tools** — Welche Werkzeuge zusammenspielen.
3. **Muster für andere Städte** — Wie du das Vorgehen auf deine Stadt überträgst.

## Teil 1: Fallstudie Berlin

### Zwei Ebenen, zwei Systeme

Berlin hat zwei relevante Verwaltungsebenen für kommunale Entscheidungen:

- **Land** — Senat und Abgeordnetenhaus. Zuständig für Landesgesetze, Haushalt, bezirksübergreifende Planung.
- **Bezirk** — Bezirksamt und Bezirksverordnetenversammlung (BVV). Zuständig für lokale Entscheidungen: Kitas, Spielplätze, Straßen, Bebauungspläne.

Für Bürger ist die Grenze zwischen diesen Ebenen oft nicht erkennbar. Eine Kita-Entscheidung kann ein Landesgesetz sein (Förderung), eine Bezirksentscheidung (Standort) oder beides. MeinBezirk muss beide Ebenen abdecken.

### PARDOK — Landesebene

PARDOK ist das Parlamentsdokumentationssystem des Berliner Abgeordnetenhauses. Es steht unter [pardok.parlament-berlin.de](https://pardok.parlament-berlin.de).

Was PARDOK enthält:

- Gesetzentwürfe und verabschiedete Gesetze
- Anträge und Beschlüsse
- Schriftliche Anfragen und Antworten
- Plenarprotokolle

Die Daten reichen bis 1989 zurück. PARDOK bietet offene Daten im XML-Format, täglich aktualisiert. Der Zugang: [parlament-berlin.de/dokumente/open-data](https://www.parlament-berlin.de/dokumente/open-data).

Für MeinBezirk war PARDOK die Quelle für Landesentscheidungen mit Bezug zu Tempelhof-Schöneberg. Beispiel: Schriftliche Anfragen zum Zustand von Schulgebäuden im Bezirk, Landesgesetze zur Kitaförderung.

### ALLRIS — Bezirksebene

ALLRIS ist das Ratsinformationssystem, das die Berliner Bezirke für ihre BVV-Arbeit nutzen. Jeder Bezirk betreibt eine eigene ALLRIS-Instanz.

Was ALLRIS enthält:

- BVV-Sitzungen und Tagesordnungen
- Ausschusssitzungen und Protokolle
- Drucksachen (Anträge, Beschlüsse, Anfragen)
- Abstimmungsergebnisse

Für Tempelhof-Schöneberg war ALLRIS die primäre Quelle. Hier liegen die Entscheidungen, die den Bezirk direkt betreffen: Verkehrsberuhigung im Kiez, Sanierung einer Schule, neue Spielplatzplanung.

### Wie der Prototyp gebaut wurde

Der Prozess hatte vier Schritte:

1. **Suche in den Quellsystemen.** PARDOK und ALLRIS nach Entscheidungen mit Bezug zu Tempelhof-Schöneberg durchsucht. Suchbegriffe: Bezirksname, Ortsteile (Schöneberg, Tempelhof, Mariendorf, Marienfelde, Lichtenrade), Themen (Schule, Kita, Verkehr, Bauen).

2. **Relevanz filtern.** KI eingesetzt, um aus der Masse bürokratischer Dokumente die Einträge zu identifizieren, die Bürger tatsächlich betreffen. Nicht jede Drucksache ist relevant. Viele betreffen Verwaltungsinterna.

3. **Sprache übersetzen.** Amtsdeutsch in verständliche Sprache umgewandelt. Eine Drucksache mit dem Titel "Große Anfrage zur Umsetzung der Maßnahmen gemäß Schulentwicklungsplan" wird zu: "Wie weit ist die Sanierung der Schulen im Bezirk?"

4. **Fakten verifizieren.** Jede KI-generierte Zusammenfassung gegen das Originaldokument geprüft. Zahlen, Daten, Beschlüsse mit der Quelle abgeglichen.

### Was funktioniert hat

- **KI erkennt Relevanz.** Aus hunderten Drucksachen kann KI die zehn identifizieren, die Bürger tatsächlich betreffen. Das ist manuell kaum leistbar.
- **KI übersetzt Amtsdeutsch.** Die Übersetzung von Verwaltungssprache in verständliche Sprache ist eine Stärke aktueller Sprachmodelle.
- **Offizielle Quellen geben Autorität.** Weil jede Information auf ein konkretes Dokument in PARDOK oder ALLRIS zurückführbar ist, bleibt die Quelle nachprüfbar.

### Was schwieriger war

- **Nicht alle Entscheidungen sind digital zugänglich.** Manche Ausschussprotokolle existieren nur als PDF ohne Volltextsuche. Einige ältere Beschlüsse sind nicht in den digitalen Systemen erfasst.
- **Manuelle Durchsicht bleibt nötig.** Sitzungsprotokolle enthalten oft relevante Diskussionen, die in den strukturierten Daten (Drucksachen, Beschlüsse) nicht auftauchen. Das erfordert Lesen.
- **Die Zuständigkeitsgrenze ist unscharf.** Bürger denken nicht in Verwaltungsebenen. Ob eine Verkehrsentscheidung vom Bezirk oder vom Senat kommt, ist für sie irrelevant. Für die Datenrecherche ist es entscheidend, weil die Daten in verschiedenen Systemen liegen.

## Teil 2: Recherche-Tools

### Offizielle Quellen als Grundlage

Offizielle Quellen sind die Grundlage. Recherche-Tools helfen, Kontext zu finden, Zusammenhänge zu erkennen und Lücken in den offiziellen Daten zu schließen.

Ratsinformationssysteme, Parlamentsdokumentationen und Open-Data-Portale liefern die Primärdaten. Sie sind autoritativ und nachprüfbar. Alles andere baut darauf auf.

### KI-gestützte Recherche

KI-Recherche-Tools ergänzen die offiziellen Quellen. Sie helfen bei:

- **Kontext finden.** Nachrichtenberichterstattung zu einer Entscheidung finden. Hintergründe recherchieren.
- **Zusammenhänge erkennen.** Verwandte Entscheidungen über Verwaltungsebenen hinweg identifizieren. Ein Landesgesetz mit einer Bezirksentscheidung verbinden.
- **Lücken schließen.** Wenn offizielle Systeme unvollständig sind, können Presseberichte und andere öffentliche Quellen fehlendes Wissen liefern.
- **Verifizieren.** Gegenprüfung von Informationen über mehrere Quellen.

### KI-Tools für die Verarbeitung

Neben der Recherche sind KI-Werkzeuge für die Verarbeitung der gefundenen Daten nützlich:

- **Zusammenfassen.** Lange Sitzungsprotokolle und Drucksachen auf die relevanten Punkte verdichten.
- **Übersetzen.** Amtsdeutsch in verständliche Sprache umwandeln. Das ist die Kernfunktion für Bürgerkommunikation.
- **Strukturieren.** Aus unstrukturierten PDFs strukturierte Daten extrahieren: Daten, Zuständigkeiten, Orte, betroffene Personengruppen.

### Werkzeuge

**Kommerziell:**

- [Perplexity](https://perplexity.ai) — KI-gestützte Recherche mit Quellenangaben. Gut für die strukturierte Suche in öffentlichen Quellen.
- [Claude](https://claude.ai) — Textaufbereitung, Zusammenfassungen, Übersetzung in verständliche Sprache.
- [Mistral](https://chat.mistral.ai) — Alternative für Textaufbereitung und Zusammenfassungen.

**Quelloffen und lokal:**

- [Ollama](https://ollama.com) — Lokale KI-Modelle. Läuft ohne Cloud-Anbindung auf eigener Hardware.
- [LM Studio](https://lmstudio.ai) — Lokale KI-Modelle mit Benutzeroberfläche.

Alles, was in diesem Toolkit beschrieben wird, kann mit quelloffenen, lokalen Werkzeugen umgesetzt werden. Kommerzielle Dienste sind bequemer, aber nicht erforderlich.

### Verifizierung ist Pflicht

KI-generierte Zusammenfassungen können Fehler enthalten. Sprachmodelle halluzinieren Details: falsche Zahlen, erfundene Daten, nicht existierende Beschlüsse.

Deshalb gilt:

- Jede KI-generierte Information gegen das Originaldokument prüfen.
- Zahlen, Daten und Beschlussformulierungen aus der Originalquelle übernehmen, nicht aus der KI-Zusammenfassung.
- Im Zweifelsfall das Originaldokument verlinken, damit Leser selbst prüfen können.

Offizielle Dokumente sind die Wahrheitsgrundlage. KI ist das Werkzeug zur Aufbereitung. Nicht umgekehrt.

## Teil 3: Muster für andere Städte

### Die deutsche Datenlandschaft

Deutschland hat kein einheitliches Ratsinformationssystem. Jede Kommune entscheidet selbst. Die Landschaft allein in Nordrhein-Westfalen:

| System | Kommunen in NRW |
|---|---|
| SD.net | 175+ |
| Session | 114 |
| more-rubin | 27 |
| Provox | 22 |
| ALLRIS | 21 |
| Eigenlösungen | diverse |

In anderen Bundesländern sieht es ähnlich fragmentiert aus. Das ist die Realität, mit der jede Adaption umgehen muss.

### OParl: Der offene Standard

[OParl](https://oparl.org) ist eine standardisierte API-Spezifikation für den Zugriff auf Ratsinformationssysteme. Städte, deren System OParl unterstützt, bieten maschinenlesbaren Zugang zu ihren kommunalen Entscheidungsdaten.

Das vereinfacht die Datenabfrage erheblich. Statt die Weboberfläche eines Ratsinformationssystems zu scrapen, kann man strukturierte Daten über eine API abrufen.

Ob deine Stadt OParl unterstützt, prüfst du über die API unter [oparl.politik-bei-uns.de](https://oparl.politik-bei-uns.de/system).

### Politik bei uns

[Politik bei uns](https://politik-bei-uns.de) aggregiert Daten aus OParl-kompatiblen Systemen und macht sie durchsuchbar. Es ist ein guter erster Anlaufpunkt, um zu sehen, ob Daten deiner Stadt bereits aufbereitet verfügbar sind.

### Checkliste: Daten in deiner Stadt finden

1. **Ratsinformationssystem suchen.** Suche "[Stadt] Ratsinformationssystem" in einer Suchmaschine. Die meisten Kommunen haben eins.

2. **Open-Data-Portal prüfen.** Viele Städte betreiben eigene Open-Data-Portale mit strukturierten Datensätzen zu Verwaltung, Planung und Infrastruktur.

3. **OParl-Unterstützung prüfen.** Unter [oparl.politik-bei-uns.de](https://oparl.politik-bei-uns.de/system) nachsehen, ob deine Stadt eine OParl-kompatible Schnittstelle anbietet.

4. **Sitzungsprotokolle suchen.** BVV-, Stadtrat- oder Gemeinderatsprotokolle auf der Website deiner Stadt suchen. Oft sind sie unter "Politik" oder "Bürgerservice" verlinkt.

5. **Politik bei uns prüfen.** Unter [politik-bei-uns.de](https://politik-bei-uns.de) nachsehen, ob deine Stadt bereits abgedeckt ist.

6. **KI-Recherche nutzen.** Perplexity oder ähnliche Werkzeuge verwenden, um nach aktuellen Ratsentscheidungen und Berichterstattung in deiner Stadt zu suchen.

7. **Code-for-Germany-Lab kontaktieren.** Unter [codefor.de](https://codefor.de) findest du lokale Labs in vielen Städten. Die Menschen dort kennen die lokale Datenlandschaft.

### Die Recherche anpassen

Das Grundmuster ist überall gleich:

1. Identifiziere die offiziellen Systeme deiner Stadt.
2. Durchsuche sie nach Entscheidungen, die Bürger betreffen.
3. Nutze KI, um Relevanz zu filtern und Sprache zu vereinfachen.
4. Verifiziere gegen die Originalquellen.

Was sich ändert, sind die konkreten Systeme und Zugangswege. Die Methodik bleibt.

Siehe [Quellen](../quellen/) für alle Referenzen und Links.
