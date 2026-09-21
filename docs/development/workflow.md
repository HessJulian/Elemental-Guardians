# BMAD → GitHub Issues → Codex → Owner merge

## Zweck und verbindliche Rollen

- `docs/` enthält die überprüfte Produktbasis; BMAD-generierte PRD-/Architektur-/Epic-/Story-Artefakte liegen im installer-konfigurierten Ausgabeordner (`_bmad-output/`, sobald erzeugt). Diese Projektkonvention ersetzt **keine** offizielle BMAD-Workflow-Anweisung.
- **BMAD** plant/validiert die Stories und erzeugt die vollständigen Implementierungsspezifikationen. **GitHub Issues** sind die operativen Tickets; der Issue-Text spiegelt die Akzeptanzkriterien und verlinkt die versionierte BMAD-Story, ersetzt sie aber nicht. **Codex** implementiert genau ein freigegebenes Ticket pro Session und öffnet einen PR. **Der Repository-Owner** prüft/testet und mergt.
- Für Bugs oder isolierte Infrastrukturarbeiten darf ein Issue ohne BMAD-Story angelegt werden, wenn Ziel, Scope, überprüfbare Akzeptanzkriterien und Testplan ausreichen. Größere neue Features durchlaufen BMAD.

## Planung und Übergabe

1. Vorhandene `docs/game-design.md`, `docs/architecture.md`, `docs/data-contracts.md`, `docs/mvp-roadmap.md` als Baseline nutzen. Derzeit existieren **noch keine genehmigten BMAD-Planungsartefakte**; die installierten BMAD-Skills sind jedoch vorhanden. Offiziellen Skill `bmad-help` zur Auswahl der nötigen Workflows verwenden; keine Schritte überspringen, die der installierte Workflow voraussetzt.
2. Bei fehlenden Voraussetzungen zuerst PRD/Architektur über die offiziellen Skills erzeugen und prüfen; danach `bmad-create-epics-and-stories`. Epics nach Nutzerwert strukturieren und Stories in kleine, unabhängig abnehmbare vertikale Arbeitspakete schneiden. Identifikatoren aus BMAD beibehalten (z. B. `1.1`); **GitHub-Issue-Nummern werden erst beim Erstellen vergeben, niemals vorwegnehmen**.
3. User prüft Epic-Zuschnitt, Umfang und frühe Stories. Danach einmalig ein GitHub Issue je freigegebener Story mit `.github/ISSUE_TEMPLATE/story.yml` bzw. denselben Feldern via GitHub API/CLI erstellen: BMAD-ID, Link auf die versionierte Story-Datei, Nutzen, ACs, Abhängigkeiten, Testplan, Risiken. Optional Epic-Issues als Übersichten, nicht als zweite Implementierungsaufgabe. Bereits vorhandene Issues vor dem Anlegen über BMAD-ID/Story-Link suchen; Duplikate vermeiden.
4. Neue Stories beginnen im **Backlog**; der Owner kennzeichnet durch ein ausdrückliches Ready-Signal die zur Arbeit freigegebenen Issues. Labels oder GitHub Projects dürfen Status visualisieren, werden hier aber **nicht** automatisch erstellt oder synchronisiert.

## Implementation und PR-Gate

1. Genau ein Ready-Issue wählen; Abhängigkeiten/Referenz prüfen; neuesten `main` holen. Branch `feature/<issue-number>-<slug>` oder `fix/<issue-number>-<slug>` erstellen. Keine direkten Codeänderungen in `main`.
2. Implementierung auf Issue/Story-Scope begrenzen, Tests ergänzen und tatsächlich ausführen, gegebenenfalls Unity-Editor-/Android-Test festhalten. Fehlendes Tooling als `NOT RUN` mit Ursache deklarieren.
3. PR gegen `main` öffnen; den Issue-Link sowie `Closes #<nummer>` bei vollständig gelöster Story und Link auf BMAD-Story angeben. PR-Template ausfüllen, Testergebnisse und manuelle Abnahme benennen. Codex darf Review-Befunde beheben, aber **nicht mergen**.
4. Owner testet und prüft Review/Checks. Bei Problemen bleibt PR offen und Issue In Review/In Progress; bei Erfolg führt **nur der Owner** den Merge aus. `Closes` wird beim Merge in den Standardbranch wirksam; erst dann Done. BMAD-Sprintstatus danach auf tatsächlichen Zustand aktualisieren; keine erfundene automatische Synchronisierung.
5. Bei Änderungen an Anforderungen: geprüfte BMAD-Story, Issue-Akzeptanzkriterien und relevante `docs/` vor Umsetzung abgleichen. Widersprüche nicht stillschweigend lösen; signifikante Entscheidungen als ADR festhalten.

## Operative Statusdefinition

| Status | Bedeutung | Zuständig |
| --- | --- | --- |
| Backlog | Story dokumentiert, noch nicht zur Umsetzung freigegeben | BMAD / Owner |
| Ready | Definition of Ready erfüllt; Owner gibt frei | Owner |
| In Progress | Codex implementiert auf eigenem Branch | Codex |
| In Review | PR offen, Tests und Owner-Abnahme ausstehend | Codex / Owner |
| Done | Erfolgreich abgenommen und durch Owner nach `main` gemergt | Owner |

Ein Issue ist keine zweite Quelle fachlicher Wahrheit. Bei Abweichungen von einer freigegebenen BMAD-Story erst klären, dann beide Darstellungen konsistent halten.

## Tooling und Sicherheit

- Kein CI-Workflow und keine GitHub-Branch-Protection wird allein durch diese Dokumente eingerichtet. Sobald Unity-Projekt/Test-Runner vorhanden sind, tatsächliche Checks definieren; der Owner aktiviert bei Bedarf Branch-Schutz/Ruleset und geforderte Tests in GitHub-Settings. Bis dahin ist die manuelle Abnahme verbindlich.
- Agenten erhalten keine eigenständige Merge-Freigabe. Falls die technische GitHub-Berechtigung eines Agenten trotzdem einen Merge erlauben würde, gilt das dokumentierte Verbot als Prozessregel; eine harte Durchsetzung erfordert separat konfigurierte Rechte/Rulesets.
- Ein erstelltes Issue startet nicht von selbst eine Codex-Session; der Owner weist Codex ein Ready-Issue zu oder startet eine entsprechende Codex-Aufgabe.

## Kontext- und Tokenbudget

Root-`AGENTS.md` kurz halten; pro Coding-Session Issue + verlinkte BMAD-Story + betroffene Quelldateien laden. Vollständige PRD/Architektur nur bei relevanten Entscheidungen laden. Planung pro Epic bündeln, Statusupdates kurz und wahrheitsgemäß halten; Sicherheits- und Testprüfung nicht auslassen.
