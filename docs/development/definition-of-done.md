# Definition of Ready & Done

## Definition of Ready — bevor Codex ein Issue umsetzt

- [ ] Ein GitHub Issue existiert, trägt eine BMAD-Story-ID und verlinkt die **geprüfte, im Repo verfügbare** BMAD-Story (Ausnahmen: klar definierter Bug/Technik-Task).
- [ ] User Story bzw. Ziel und überprüfbare Akzeptanzkriterien sind eindeutig; Issue und BMAD-Story widersprechen sich nicht.
- [ ] Abhängigkeiten sind erfüllt, notwendige Dateien/Toolchains stehen bereit oder sind explizite Aufgabe des Issues.
- [ ] Scope und Nicht-Scope sind notiert; notwendige Testarten sowie ggf. Android-/Unity-Abnahme sind bestimmt.
- [ ] Owner hat das Issue ausdrücklich zur Umsetzung freigegeben (`Ready`); weder neue Issue-Erstellung noch ein offener PR bedeutet automatisch Ready.

## Definition of Done — vor Story-Abschluss

- [ ] Alle Akzeptanzkriterien umgesetzt; notwendige Produkt-/Architekturentscheidungen abgestimmt.
- [ ] Relevante Tests ergänzt und tatsächlich ausgeführt; fehlende Tests/Toolchain klar als `NOT RUN` dokumentiert und vor Merge durch Owner bewertet.
- [ ] Unity-Editor-/Android-Verhalten manuell abgenommen, wenn die Story Touch, Rendering, Performance oder Geräteintegration betrifft.
- [ ] Bei Economy/IAP/Backend: Authentifizierung, autoritative Zustände, Idempotenz, Offline- und Rückerstattungsfälle geprüft, soweit relevant.
- [ ] PR dokumentiert Issue/Story, Änderungen, Testergebnisse, Risiken und offene Grenzen; keine Credentials/Originalitätsverletzungen.
- [ ] Owner hat den PR geprüft und **nach seiner Abnahme** nach `main` gemergt.
- [ ] Issue ist geschlossen; BMAD-Sprintstatus auf `done` entsprechend dem tatsächlichen Merge aktualisiert.

Ein PR mit nicht gelaufenen Pflichtprüfungen ist **nicht automatisch Done**. Für das initiale Dokumentations-/Workflow-PR gelten nur die auf die Änderungen anwendbaren Prüfungen; Unity-/Android-Tests sind ohne Unity-Projekt nicht möglich.
