# Apple Wallet Pass — Immo Solutions (Gabriel Zekry)

Diese Dateien sind die **Bausteine** für einen echten Apple-Wallet-Pass (`.pkpass`).
Ein `.pkpass` muss mit einem **Apple Pass Type ID Zertifikat** signiert werden — das
geht nur mit einem Apple-Developer-Account und lässt sich nicht rein statisch erzeugen.

## Enthalten
- `pass.json` — Passinhalt (Name, Position, Kontakt, QR-Code auf die digitale Karte)
- `icon.png`, `icon@2x.png` — Pass-Icon (Rauten-Logo, Immo-Blau)
- `logo.png` — Logo-Strip

## Fertig signieren (einmalig, mit Apple-Developer-Account)
1. Im [Apple Developer Portal](https://developer.apple.com/account/resources/identifiers/list/passTypeId)
   eine **Pass Type ID** anlegen, z. B. `pass.ch.immosolutions.card`.
2. Zugehöriges Zertifikat erstellen und als `.p12` exportieren.
3. Das **Apple WWDR**-Zwischenzertifikat laden.
4. In `pass.json` `teamIdentifier` (Team-ID aus dem Developer-Account) und ggf.
   `passTypeIdentifier` eintragen.
5. `manifest.json` (SHA1 je Datei) + `signature` erzeugen und alles zippen —
   z. B. mit dem npm-Tool [`passkit-generator`](https://github.com/alexandercerutti/passkit-generator)
   oder Apples `signpass`.
6. Ergebnis: `ImmoSolutions_GabrielZekry.pkpass` — per E-Mail/AirDrop teilen,
   Antippen fügt die Karte zu Apple Wallet hinzu.

## Ohne Apple-Zertifikat
Die **digitale Visitenkarte** unter `../index.html`
(live: https://kaito-blip.github.io/immosolutions-card/) funktioniert sofort,
plattformübergreifend und ohne Signierung — teilbar per Link oder QR-Code,
mit „Zum Home-Bildschirm hinzufügen" und vCard-Download.
