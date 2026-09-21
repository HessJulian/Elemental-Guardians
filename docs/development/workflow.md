# BMAD → GitHub Issues → Codex → Owner merge

## Zuständigkeiten und Quellen

- `docs/` beschreibt freigegebene **Produktanforderungen und Architekturentscheidungen**, nicht den aktuellen Implementierungsstand. Offizielle BMAD-Artefakte bilden die fachliche Planung und die versionierte Story-Spezifikation ab.
- GitHub Issues und verknüpfte PRs sind die **einzige operative Quelle** für Priorisierung, Freigaben und Arbeitsstatus; der aktuelle Code und die Konfiguration auf `main` zeigen, was tatsächlich integriert ist. Aktuelle Testergebnisse/Checks auf dem jeweiligen Commit belegen die Verifikation.
- BMAD plant und validiert; Codex arbeitet ein freigegebenes Issue pro Session ab und öffnet einen PR; der Owner prüft, testet und mergt. Isolierte Bugs/Technikaufgaben dürfen ohne BMAD-Story bearbeitet werden, wenn Ziel, Scope, Kriterien und Testplan klar sind.
- Kein dauerhaft gepflegter Fortschrittsabschnitt in README, Roadmap, Architektur, AGENTS.md oder BMAD-Planungsdokumenten. Bei jedem neuen Auftrag Status und Existenz von Unity-Projekt, Tools, Stories, CI, Backend usw. **live ermitteln**. Historische Planungsannahmen und vergangene Testberichte sind kein Nachweis über den aktuellen Branch.

## Planung und Übergabe

1. `docs/game-design.md`, `docs/architecture.md`, `docs/data-contracts.md`, `docs/mvp-roadmap.md` sind Entwurfsgrundlage. Aktuelle Planungsartefakte im installer-konfigurierten BMAD-Ausgabeordner und vorhandene GitHub Issues prüfen. Offiziellen `bmad-help` Skill für die erforderliche Planung und Validierung verwenden; keine offiziellen Voraussetzungen überspringen.
2. Nach Validierung von PRD/Architektur den installierten Skill `bmad-create-epics-and-stories` nutzen. Epics nach Nutzerwert, Stories als kleine unabhängig prüfbare Aufgaben schneiden. BMAD-IDs erhalten, GitHub-Issue-Nummern nicht vor der tatsächlichen Erstellung erfinden.
3. Owner prüft Epic-/Story-Zuschnitt. Vor dem Erstellen jedes Issues nach vorhandener BMAD-ID/Story-Referenz suchen, um Duplikate zu vermeiden. Pro freigegebener Story ein Issue mit Referenz auf die versionierte BMAD-Spezifikation und spiegelbildlichen Akzeptanzkriterien, Abhängigkeiten und Testplan erstellen. Keine zusätzliche Fortschrittsdatei generieren.
4. Ein Issue ist zunächst Backlog. Der Owner gibt explizit Ready frei. Issue-/PR-Status wird auf GitHub verwaltet, nicht in statischen Markdown-Tabellen. Ein Issue startet Codex nicht automatisch.

## Implementierung und PR-Gate

1. Genau ein Ready-Issue auswählen; Issue, BMAD-Story, Abhängigkeiten und **aktuellen Stand von `main`** prüfen. Branch `feature/<issue-number>-<slug>` oder `fix/<issue-number>-<slug>` von `main` erstellen. Keine direkten Implementierungs-Commits auf `main`.
2. Scope und Kriterien umsetzen; relevante Tests tatsächlich ausführen und Ergebnisse auf dem jeweiligen Commit dokumentieren. Nicht verfügbare Tests als `NOT RUN` samt Grund ausweisen. Einen offenen PR niemals als bereits integrierte Funktion behandeln.
3. PR gegen `main` öffnen, Issue und BMAD-Story verlinken. `Closes #<nummer>` nur bei vollständig erfülltem Issue. PR-Vorlage mit echten Testnachweisen ausfüllen. Codex behebt bei Bedarf Review-Befunde, **mergt aber nie selbst**.
4. Owner prüft Code, Tests und gegebenenfalls Android/Unity-Verhalten und führt den Merge aus. Erst dann ist die Story Done. Bei einer neuen Aufgabe erneute Live-Prüfung von `main` und Issues, keine Übernahme alter Chat-/Dokumentenstatus.
5. Anforderungen nur nach Freigabe ändern und relevante fachliche/technische Dokumente sowie Story und Issue konsistent halten. Signifikante Entscheidungen in ADRs festhalten; Statuswechsel dagegen nicht in Design-Dokumente schreiben.

## Status in GitHub

Backlog → Ready (explizite Owner-Freigabe) → In Progress (Codex-Branch) → In Review (PR offen) → Done (Owner hat nach Abnahme nach `main` gemergt). Die aktuellen Werte werden **in GitHub** ermittelt. Labels oder Projects sind optionale Visualisierung, kein separat zu pflegender Markdown-Tracker. Offiziell erforderliche BMAD-Sprintdateien sind abgeleitete Planungsartefakte: vor Verwendung mit GitHub abgleichen und nie als unabhängig authoritative Ist-Zustände behandeln.

## Technische Schutzmaßnahmen und Tokenbudget

Dokumentierte Merge-Regeln sind zunächst Prozessvorgaben; tatsächliche technische Erzwingung erfordert passende GitHub-Berechtigungen, Branch-Regeln und konfigurierte Checks. Ob diese existieren, live prüfen. Pro Implementierung nur Issue, verlinkte Story, betroffene Code-/Testdateien und nötige Designabschnitte laden; keine vollständigen Dokumentationsscans oder Status-Nacherzählungen. Sicherheits- und Testprüfungen nicht zur Tokenersparnis auslassen.
