# Franz Schnitler Productions — installeren als app

Dit is nu een echte **PWA** (progressive web app): met een `manifest.json` en een
`service-worker.js`-achtig bestand (`sw.js`) zodat Android 'm herkent als installeerbare app,
met eigen icoon, geen browserbalk, en werkt zonder internet zodra hij één keer geladen is.

## Belangrijk: dit moet online staan (geen los bestand)

Voor een PWA-installatie (en voor de achtergrondmeldingen via ntfy) moet de site via **https**
bereikbaar zijn — een los HTML-bestand openen vanaf je telefoon (`file://…`) werkt niet voor de
installatie-knop. De snelste gratis manieren, geen account nodig bij de eerste:

**Optie A — Netlify Drop (30 seconden, geen account)**
1. Ga op je laptop naar https://app.netlify.com/drop
2. Sleep deze hele map (met `index.html`, `manifest.json`, `sw.js`, de 3 icoontjes) erin
3. Je krijgt direct een `https://iets-random.netlify.app` link — open die op je Android-telefoon

**Optie B — GitHub Pages (blijft permanent bestaan)**
1. Maak een (gratis) GitHub-account en een nieuwe repository
2. Upload alle bestanden uit deze map naar de repository
3. Zet in de repository-instellingen "Pages" aan, branch `main`, map `/ (root)`
4. Na een paar minuten is de app bereikbaar op `https://jouwnaam.github.io/repo-naam/`

## App installeren op Android
1. Open de link hierboven in **Chrome** op je telefoon
2. Tik op het menu (⋮) rechtsboven → **"App installeren"** (of je krijgt vanzelf een balkje
   onderin met "Toevoegen aan startscherm")
3. De app staat nu als icoon op je startscherm en opent schermvullend, zonder adresbalk

## Meldingen ook als de app helemaal dicht is
Een gewone webpagina kan geen melding sturen als hij niet open staat — dat geldt voor elke PWA,
niet alleen deze. Daarom gebruikt de app optioneel **ntfy** (gratis, open-source meldingendienst,
geen account nodig):

1. Installeer de gratis **ntfy**-app op Android (Play Store)
2. Open in de Franz-app de instellingen ⚙ → onderaan "Meldingen ook als app dicht is"
3. Vul een uniek kanaal-naampje in (of laat de 🎲-knop er een verzinnen) en zet de schakelaar aan
4. Abonneer je in de ntfy-app op precies datzelfde kanaal-naampje
5. Klaar — Franz belt vanaf nu ook via een echte pushmelding, zelfs met de app dicht

Let op: ntfy-kanalen op de gratis, publieke server zijn niet privé-beveiligd — iedereen die de
kanaalnaam weet/raadt kan meeluisteren. Kies dus geen voorspelbare naam als je dat erg vindt (niet
relevant risico voor deze speluitjes-app, maar goed om te weten).

## Wat er nu al lokaal bewaard blijft (zonder ntfy)
Alle instellingen, de geschiedenis (storyboard), toegevoegde categorie-items en karakters staan al
in `localStorage` op je toestel — die overleven een herstart van je telefoon of het sluiten van de
app vanzelf, zonder dat je iets hoeft in te stellen.
