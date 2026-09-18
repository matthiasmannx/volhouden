# Volhouden

Een tracker voor wie stopt met drank, drugs, roken of iets anders: dagen vrij, bespaard geld, spaardoelen,
dagritme, weekmenu en een noodknop voor moeilijke momenten.

Iedere gebruiker logt in met zijn eigen Google-account en ziet alleen zijn eigen gegevens, op al zijn apparaten.
Zonder inloggen werkt de pagina ook, dan blijven de gegevens in de browser.

## Bestanden

- `index.html`: de hele app, één bestand.
- `firebase-config.js`: de Firebase-configuratie (in te vullen, zie hieronder).
- `firestore.rules`: de toegangsregels voor de database. Ieder alleen zijn eigen map.

## Eenmalig inrichten (ongeveer 10 minuten)

1. Ga naar https://console.firebase.google.com en log in met je Google-account. Kies **Project toevoegen**,
   noem het `volhouden`, Google Analytics mag uit.
2. In het project: **Build > Authentication > Get started > Sign-in method**. Zet **Google** aan en sla op.
   Ga daarna naar het tabblad **Settings > Authorized domains** en voeg `matthiasmannx.github.io` toe.
3. **Build > Firestore Database > Create database**. Kies een locatie in Europa (bijv. `europe-west4`) en
   **production mode**. Open daarna het tabblad **Rules**, vervang de inhoud door die van `firestore.rules` en publiceer.
4. **Projectinstellingen** (tandwiel) **> Your apps > Web-app toevoegen** (het `</>`-icoon). Noem hem `volhouden`,
   Firebase Hosting niet nodig. Kopieer het blok `firebaseConfig = { ... }`.
5. Zet die waarden in `firebase-config.js` in deze repository (via de GitHub-website: bestand openen, potloodje, plakken,
   Commit). Na een minuut staat de nieuwe versie live.

## Gebruik

- Open https://matthiasmannx.github.io/volhouden/ en tik rechtsboven op **Inloggen**.
- Op de telefoon: Delen > **Zet op beginscherm**, dan opent hij als app.
- Deel dezelfde link met wie mee wil doen. Iedereen logt in met zijn eigen Google-account.

## Privacy

Gegevens staan in Firestore onder `users/<gebruikers-id>/tracker/state`. De regels laten alleen de ingelogde
gebruiker zelf bij zijn map. De beheerder van het Firebase-project kan de database in de Firebase Console
wel bekijken; wie dat niet wil, maakt een eigen Firebase-project aan met dezelfde bestanden.
