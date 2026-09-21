# Teststrategie und PR-Gates

## Aktueller Stand

Das Repository ist vor der spielbaren Unity-Implementierung. Es gibt derzeit kein committed Unity-Projekt, keinen eingerichteten Android-Build und keine dokumentierten laufenden GitHub-Actions-Checks für das Spiel. Ein grüner Status darf nicht behauptet werden, solange die Prüfung nicht tatsächlich existiert und ausgeführt wurde.

## Minimale Prüfungen pro Änderungstyp

| Änderung | Erforderliche Prüfung/Abnahme |
| --- | --- |
| Nur Dokumentation/Issue-Templates | Links, YAML/Markdown-Struktur und Prozesswidersprüche prüfen; keine Unity-Tests erforderlich |
| Reine C#-Domänenlogik | Relevante automatisierte Unit-/EditMode-Tests und Regressionstests |
| Gegner, Türme, Helden, Wellen | Unit-/EditMode-Tests plus PlayMode-Tests für Integration |
| Touch, Rendering, Szenen, Android | PlayMode plus manueller Test auf Zielgerät, FPS/Fehlverhalten dokumentieren |
| Backend, Fragmente, Heldenbesitz | Unit-/Integrationstests für Auth, konkurrierende Requests, Idempotenz und unberechtigte Mutationen |
| IAP / Billing | Google-Play-Testkäufe: erfolgreich, pending, abgebrochen, wiederholt, Refund, Wiederherstellung, Backend-Verifikation |

## Prüfnachweise im Pull Request

- Exakter Befehl, Umgebung und Ergebnis je durchgeführtem Test; `NOT RUN` mit Ursache, nie fingierte grüne Checks.
- Akzeptanzkriterien gegen tatsächliche Implementierung abhaken; bei UX/Gamefeel und Android zusätzliche Owner-Abnahme.
- Sobald echte Unity-, Backend- und Billing-Testumgebungen vorhanden sind, die passenden Workflows unter `.github/workflows/` hinzufügen und für `main` konfigurieren. Nicht bereits jetzt leere oder stets erfolgreiche Fake-Gates einrichten.

## Merge-Regeln

Nur Owner nach Review und relevanter Testabnahme. Ein fehlschlagender erforderlicher Check blockiert den Merge. Ein nicht ausführbarer erforderlicher Test muss offen dokumentiert und vor Freigabe geklärt werden; die Dokumentation dieses Zustands ist kein Ersatz für einen bestandenen Test.
