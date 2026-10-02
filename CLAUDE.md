@AGENTS.md

# Projektregeln

Kontext: Solo-Gründer, technisch versiert, aber kein Entwickler. Der Code
wird nicht manuell reviewt. Daraus folgt alles Weitere.

## Arbeitsweise

- Einfachste funktionierende Lösung zuerst. Keine Abstraktion auf Vorrat,
  keine Konfigurierbarkeit für hypothetische Fälle.
- Vor jeder Implementierung: kurzer Plan in Prosa, auf Bestätigung warten.
  Bei trivialen Änderungen entfällt das.
- Test schreiben, bevor Code geschrieben wird.
- Keine neuen Dependencies ohne Rückfrage. Wenn doch nötig:
  `npx expo install <paket>`, nie `npm install`.
- Nach jedem abgeschlossenen Schritt: `git commit` mit klarer Message.
  Kleine Commits, damit jeder Fehlschlag mit einem Befehl rückgängig ist.

## Verifikation

Nichts gilt als fertig, weil es plausibel aussieht.

- `npx expo lint` und `npx tsc --noEmit` laufen lassen, bevor eine Aufgabe
  als erledigt gemeldet wird.
- Vor jedem Commit laufen Lint, Typecheck und Tests automatisch
  (`.githooks/pre-commit`). Schlägt der Hook fehl: Ursache beheben.
  Nie mit `--no-verify` umgehen, Hook nie abschalten oder abschwächen.
- Jedes UI-Feature muss gestartet und angesehen werden: im iOS-Simulator,
  solange der noch nicht eingerichtet ist über `npx expo start --web`
  und einen Screenshot.
- Anforderungen nicht stillschweigend ändern. Wenn etwas nicht wie
  besprochen umsetzbar ist: sagen, nicht umbauen.
- Sag explizit, wenn du etwas nicht verifizieren konntest. Ein ehrliches
  "ungeprüft" ist mehr wert als ein zuversichtliches "fertig".

## Sicherheit

- Keine Schlüssel, Tokens oder Passwörter im Client-Code. Alles über
  Umgebungsvariablen bzw. EAS Secrets.
- Alles in einer Mobile App ist auslesbar. Was geheim bleiben muss,
  gehört ins Backend, nicht in die App.
- Jede neue Supabase-Tabelle bekommt Row Level Security, bevor sie
  benutzt wird.

## Kommunikation

- Erkläre Entscheidungen so, dass ein technisch interessierter
  Nicht-Entwickler sie beurteilen kann. Fachbegriffe beim ersten
  Auftreten kurz einordnen.
- Nenne Kompromisse und was sie später kosten, nicht nur die Lösung.
- Antworte auf Deutsch.
