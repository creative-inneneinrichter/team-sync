# VS Code Team-Konfiguration

Gemeinsame Einstellungen und Erweiterungen für VS Code. Die Erweiterung [Marnis Team Sync](https://marketplace.visualstudio.com/items?itemName=marnis-tech.marnis-team-sync) lädt diese Konfiguration, installiert fehlende Erweiterungen und setzt die Einstellungen. Andere Erweiterungen werden nie entfernt.

## Einrichtung (einmalig pro Rechner)

1. **Marnis Team Sync installieren**: In VS Code links auf Erweiterungen klicken, nach „Marnis Team Sync“ suchen und installieren. Oder im Terminal:

   ```
   code --install-extension marnis-tech.marnis-team-sync
   ```

2. **Konfiguration eintragen**: `Strg+Shift+P` (Mac: `Cmd+Shift+P`) drücken, „Einstellungen öffnen (JSON)“ bzw. „Preferences: Open User Settings (JSON)“ wählen und diese Zeile innerhalb der geschweiften Klammern einfügen:

   ```json
   "teamSync.configUrl": "https://raw.githubusercontent.com/creative-inneneinrichter/team-sync/main/team-config.json",
   ```

3. Speichern. Nach wenigen Sekunden werden die Erweiterungen installiert und die Einstellungen gesetzt. Unten rechts in der Statusleiste steht dann „Team v…“.

## Danach

- Änderungen an der Konfiguration kommen automatisch an, spätestens nach einer Stunde. Sofort geht es über einen Klick auf „Team v…“ in der Statusleiste oder den Befehl „Team Sync: Jetzt synchronisieren“.
- Eigene Anpassungen bleiben erhalten, solange die Team-Konfiguration nicht geändert wird.
- Bei Problemen: Befehl „Team Sync: Log anzeigen“.

## Konfiguration ändern

1. `settings.json` (Einstellungen) oder `extensions.json` (Erweiterungen) anpassen.
2. `team-config.json` neu erzeugen, mit dem Generator aus [marnis-tech/team-sync](https://github.com/marnis-tech/team-sync):

   ```
   npm run team-config -- --dir <Pfad zu diesem Repo>
   ```

   Die Version wird nur erhöht, wenn sich Inhalte geändert haben.
3. Alle drei Dateien committen und pushen.

Die GitHub Action prüft bei jedem Push, ob `team-config.json` zu `settings.json` und `extensions.json` passt.

Dieses Repo ist öffentlich: hier gehören nur Einstellungen hinein, keine Zugangsdaten.
