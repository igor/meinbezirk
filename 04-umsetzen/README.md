# Umsetzen

Gestaltungsprinzipien und technische Umsetzung. Keine Schritt-für-Schritt-Anleitung. Leitlinien dafür, wie man über den Bau nachdenkt.

## Gestaltungsprinzipien

Adaptiert von den [GDS Design Principles](https://www.gov.uk/guidance/government-design-principles), angewendet auf kommunale Transparenz.

**Mach die harte Arbeit, damit es einfach wird.** Die Komplexität von Verwaltungsdaten ist nicht das Problem der Bürger. Übersetzen, filtern, vereinfachen. Die Arbeit der Vereinfachung passiert hinter den Kulissen. Wenn eine Drucksache drei Seiten hat, hat die Karte drei Sätze.

**Das ist für alle.** Barrierefreiheit ist kein Nachgedanke. Semantisches HTML. Ausreichender Kontrast. Tastaturnavigation. Screenreader-Kompatibilität. Leichte Sprache und Einfache Sprache dort, wo sie die Verständlichkeit erhöhen.

**Sei konsistent, nicht uniform.** Verwende gemeinsame Muster, wo sie helfen: Kartenlayouts, Filter-Chips, einheitliche Farbcodierung für Entscheidungsebenen. Aber passe an den lokalen Kontext an. Ein Toolkit für Hamburg muss nicht aussehen wie das für Berlin.

**Fang mit Nutzer:innen-Bedürfnissen an.** Nicht mit dem, wie die Daten aussehen. Nicht mit dem, was das System kann. Sondern mit dem, was Menschen tatsächlich wissen müssen. Die Datenstruktur folgt der Frage, nicht umgekehrt.

**Mach es offen.** Open Source. Offene Methodik. Offene Einladung zum Mitmachen. Offenheit verbessert die Qualität. Wenn jemand einen Fehler findet, kann er ihn korrigieren. Wenn jemand eine bessere Lösung hat, kann er sie beitragen.

## Sprache

Verwaltungssprache ist für die Verwaltung geschrieben. Nicht für Bürger.

Amtsdeutsch ist Konvention, keine Notwendigkeit. "Große Anfrage zur Umsetzung der Maßnahmen gemäß Schulentwicklungsplan" ist korrekt. Aber niemand sucht danach. Menschen fragen: "Wie weit ist die Sanierung der Schulen im Bezirk?"

### Vorher/Nachher

| Amtsdeutsch | Verständliche Sprache |
|---|---|
| Große Anfrage zur Umsetzung der Maßnahmen gemäß Schulentwicklungsplan | Wie weit ist die Sanierung der Schulen im Bezirk? |
| Vorlage zur Kenntnisnahme: Umsetzung des Kitaförderungsgesetzes | Mehr Kita-Plätze: Was sich ändert |
| Dringlichkeitsantrag betr. verkehrsberuhigende Maßnahmen | Tempo 30 in Wohnstraßen: Was beantragt wurde |

### KI als Übersetzungshilfe

KI kann bei der Übersetzung von Amtsdeutsch helfen. Aber ein Mensch muss prüfen, ob die Bedeutung erhalten bleibt. Vereinfachung darf nicht Verfälschung werden. Der Kontext einer Drucksache geht schnell verloren, wenn man zu stark kürzt.

### Einfache und Leichte Sprache

Für breitere Zugänglichkeit: Einfache Sprache und Leichte Sprache in Betracht ziehen. Einfache Sprache ist verständlicher Alltagsstil. Leichte Sprache folgt festen Regeln und richtet sich an Menschen mit kognitiven Einschränkungen. Beides hat seinen Platz. Siehe [Leichte Sprache](../quellen/) in den Quellen.

### Das Ziel

Jede Karte sollte ohne Vorwissen über Verwaltungsprozesse verständlich sein. Wenn jemand erst googeln muss, was eine "Drucksache" ist, hat die Übersetzung nicht stattgefunden.

## Technische Umsetzung

Fang einfach an. Nicht über-engineeren.

### Statisches HTML reicht

Der Berliner Prototyp ist eine einzelne HTML-Datei. Etwa 44 KB. Kein Framework, kein Build-Step, kein Datenbank-Backend. Das ist eine bewusste Entscheidung, keine Einschränkung. Eine statische Datei kann jeder hosten. Jeder lesen. Jeder forken.

Kein externes Abhängigkeits-Management nötig. Vanilla JavaScript reicht für Filterlogik. Vanilla CSS reicht für responsives Layout.

### Progressive Enhancement

Komplexität nur hinzufügen, wenn sie gebraucht wird. Nicht vorher. Ein Framework einführen, bevor man das Problem kennt, löst das falsche Problem. Wenn die statische Version funktioniert, funktioniert sie. Wenn sie nicht mehr reicht, weißt du dann, warum.

### Barrierefreiheit

Nicht optional. Grundanforderungen:

- Semantisches HTML: `<main>`, `<nav>`, `<article>`, `<button>` statt `<div>` für alles
- ARIA-Attribute dort, wo semantisches HTML nicht ausreicht
- Ausreichender Farbkontrast (mindestens 4.5:1 für Text, 3:1 für große Schrift)
- Tastaturnavigation: alle interaktiven Elemente erreichbar und bedienbar
- Screenreader-Tests mit tatsächlichen Screenreadern, nicht nur im Code

Referenz: [WCAG 2.1](https://www.w3.org/TR/WCAG21/) — der internationale Standard für barrierefreie Webinhalte. Siehe [Quellen](../quellen/).

### Mobile First

Bürger werden das auf dem Handy nutzen. Nicht am Desktop in einem Rathaus. Design für kleine Bildschirme zuerst. Dann erweitern. Nicht umgekehrt.

## Die Referenzimplementierung

Der Prototyp liegt im Repo-Root: [`index.html`](../index.html).

Was er zeigt:

- Single-File HTML mit eingebettetem CSS und Vanilla JavaScript
- Drei-Achsen-Filterung mit Echtzeit-Updates
- Mobil-responsiv mit einklappbaren Filtern und aktiven Filter-Chips
- Zwei Governance-Ebenen (Landesentscheidung vs. Bezirksentscheidung), visuell unterschieden
- Keine externen Abhängigkeiten

Live-Version: [igorschwarzmann.com/meinbezirk](https://igorschwarzmann.com/meinbezirk/)

Das ist eine Möglichkeit. Nicht die einzige. Die Architektur, das Design, die Filterlogik — alles kann anders gelöst werden. Der Prototyp zeigt einen Weg. Er definiert keinen Standard.

## Weiterdenken

Ideen für später. Nicht für den ersten Tag. Erst bauen, was funktioniert. Dann erweitern, was gebraucht wird.

**CMS für Redakteur:innen.** Eine Oberfläche, über die Karten ohne technische Kenntnisse gepflegt werden können. Redakteur:innen sollten nicht in HTML arbeiten müssen.

**Datenpipelines.** Automatische Imports aus OParl, PARDOK oder anderen Ratsinformationssystemen. Statt manueller Recherche ein Feed, der neue Beschlüsse erkennt und zur Aufbereitung vorschlägt.

**Benachrichtigungssystem.** E-Mail oder Push-Benachrichtigungen für abonnierte Themen, Ortsteile oder Lebenslagen. "Benachrichtige mich, wenn es neue Entscheidungen zu Schulen in Friedenau gibt."

**Automatische Zusammenfassungen.** KI-generierte Zusammenfassungen neuer Ratsbeschlüsse. Als Entwurf für redaktionelle Prüfung, nicht als fertiger Output.

Das sind Möglichkeiten, keine Anforderungen. Fang mit dem Einfachsten an, das funktioniert.

## Quellen

Siehe [Quellen](../quellen/) für alle Referenzen.

Für dieses Kapitel besonders relevant:

- [GDS Design Principles](../quellen/) — 10 Prinzipien für digitale öffentliche Dienste. Grundlage für den Gestaltungsansatz dieses Toolkits.
- [WCAG 2.1](../quellen/) — Internationaler Standard für barrierefreie Webinhalte. Referenz für alle Anforderungen an Barrierefreiheit.
- [Leichte Sprache](../quellen/) — Regelwerk für leicht verständliche Texte. Relevant für die sprachliche Aufbereitung.
