# Hoe kies je de juiste desktopomgeving?

Deze guide helpt je bij het kiezen van een geschikte grafische werkomgeving voor je Linux-installatie. Je desktopomgeving is een compleet pakket met onder andere een vensterbeheerder, taakbalk, bestandsbeheerder, instellingen en standaardprogramma's. De keuze heeft vooral invloed op de bediening, het geheugengebruik en hoeveel je zelf moet instellen.

Een **desktopomgeving** (desktop environment of DE) omvat ook een een **windowmanager**, die voornamelijk de programmavensters op je scherm beheert. Dit heeft veel invloed op het gebruiksgemak, de leercurve en de snelheid.

## 1. Consistentie

De desktop moet voorspelbaar en betrouwbaar blijven.

- Werken de instellingen en sneltoetsen zoals verwacht?
- Zijn de onderdelen goed geïntegreerd?
- Krijg je regelmatig updates zonder dat de hele werkomgeving verandert of breekt?

## 2. Flexibiliteit

Elke desktop biedt een andere balans tussen gebruiksgemak en controle.

- Wil je vooral direct kunnen werken, of alles zelf instellen?
- Gebruik je liever een muis, sneltoetsen of een combinatie?
- Wil je thema's, panelen en vensterindeling uitgebreid kunnen aanpassen?

## 3. Prestaties

Een zware desktop gebruikt meer geheugen en grafische middelen dan een lichte desktop.

- Hoeveel werkgeheugen heeft je systeem?
- Wil je liever een rustige omgeving of snelheid en prestaties?
- Een tiling windowmanager kan licht en snel zijn, maar vraagt meestal meer handmatige configuratie.

## Soorten desktopomgevingen

### Cinnamon

<img src="../images/distributies/Cinnamon_logo.png" alt="Cinnamon" width="100">

Cinnamon gebruikt een vertrouwde indeling met een menu, taakbalk en systeemvak.

- Zeer toegankelijk voor Windows-gebruikers
- Eenvoudig te begrijpen
- Goede balans tussen gebruiksgemak en functies
- Zwaarder dan de lichtste desktopomgevingen

Kies Cinnamon als je zonder grote veranderingen van Windows naar Linux wilt overstappen.

### KDE Plasma

<img src="../images/desktops/KDE_Plasma_logo.png" alt="KDE Plasma" width="100">

KDE Plasma biedt een traditionele desktop met veel mogelijkheden om het uiterlijk en gedrag aan te passen.

- Veel instellingen en aanpassingsmogelijkheden
- Geschikt voor gebruikers die van Windows komen
- Goede ondersteuning voor meerdere schermen en verschillende workflows
- Door de vele opties kan de omgeving overweldigend zijn

Kies KDE Plasma als je een complete desktop wilt die je uitgebreid kunt aanpassen.

### GNOME

<img src="../images/desktops/Gnome_logo.png" alt="Gnome" width="100">

GNOME heeft een eenvoudige en rustige interface met een sterke focus op overzicht en workflow.

- Moderne Wayland-ondersteuning
- Weinig afleiding en een consistente interface
- Geschikt voor beginners
- Minder instellingen en traditionele taakbalkopties dan sommige andere desktops

Kies GNOME als je een moderne omgeving wilt die vooral eenvoudig en overzichtelijk werkt.

### Xfce

<img src="../images/desktops/Xfce_logo.png" alt="Xfce" width="100">

Xfce is een lichte en klassieke desktopomgeving.

- Laag geheugengebruik
- Stabiel en overzichtelijk
- Geschikt voor oudere computers
- Minder modern uiterlijk en minder geïntegreerde functies dan GNOME of KDE Plasma

Kies Xfce als prestaties en stabiliteit belangrijker zijn dan een moderne standaardinterface.

### LXQt

<img src="../images/desktops/LXQt_logo.png" alt="LXQt" width="100">

LXQt is ontworpen om zo weinig mogelijk systeembronnen te gebruiken.

- Zeer licht
- Geschikt voor oudere of beperkte hardware
- Traditionele desktopindeling
- Minder functies en integratie standaard aanwezig

Kies LXQt als je computer weinig geheugen of beperkte grafische prestaties heeft.

### Hyprland

<img src="../images/desktops/Hyprland_logo.png" alt="Hyprland" width="100">

Hyprland is een dynamische windowmanager voor Wayland. Vensters worden automatisch geranschikt en de workflow is sterk op sneltoetsen gericht.

- **Niet geschikt voor nieuwe gebruikers**
- Flexibele indeling en uitgebreide configuratie
- Moderne Wayland-basis
- Efficiënt voor gebruikers die met sneltoetsen werken
- Geen volledige desktopomgeving; panelen, notificaties en andere onderdelen moeten vaak apart worden ingesteld
- Minder geschikt als je direct een volledig ingerichte desktop wilt

Kies Hyprland omdat je controle, snelheid en maatwerk belangrijk vindt. Je bent ook bereid om zelf de werkomgeving op te bouwen.

### Sway

<img src="../images/desktops/Sway_logo.png" alt="Sway" width="100">

Sway is een minimalistische dynamische windowmanager en compositor voor Wayland. De configuratie en sneltoetsen zijn grotendeels compatibel met i3, waardoor bestaande i3-configuraties vaak als uitgangspunt kunnen dienen.

- **Niet geschikt voor beginners**
- Licht, stabiel en efficiënt
- Vertrouwde i3-achtige workflow met sneltoetsen
- Minder visuele effecten en standaardfuncties dan Hyprland
- Geen volledige desktopomgeving; panelen, notificaties en andere onderdelen moeten vaak apart worden ingesteld
- Geschikt voor gebruikers die een eenvoudige Wayland-workflow willen

Kies Sway als je een lichte en stabiele Wayland-windowmanager wilt met een i3-achtige configuratie en workflow.

### Dwm

<img src="../images/desktops/Dwm_logo.png" alt="Dwm" width="100">

Dwm is een minimalistische en dynamische windowmanager voor X11. Vensters worden automatisch gerangschikt en de bediening is voornamelijk op sneltoetsen gericht.

- **niet geschikt voor beginners**
- Zeer licht en snel
- Eenvoudige basis zonder overbodige functies
- Configuratie gebeurt meestal door de broncode aan te passen en dwm opnieuw te compileren
- Geschikt voor gebruikers die hun workflow volledig zelf willen bepalen
- Panelen, launchers, notificaties en andere onderdelen moeten vaak apart worden geïnstalleerd

Kies dwm als je een uiterst lichte, toetsenbordgerichte windowmanager wilt en het geen probleem vindt om technische configuratie zelf te beheren.

## Welke desktop past bij mij?

### Windows-gebruikers en beginners

Kies **Cinnamon** of **KDE Plasma**.

- **Cinnamon** heeft een eenvoudige en vertrouwde indeling, zoals de klassieke Windows-omgeving.
- **KDE Plasma** heeft meer functies en aanpassingsmogelijkheden, zoals de moderne Windows-omgeving.

### Stabiliteit

Kies **GNOME** of **Xfce**.

- **GNOME** is geschikt voor een moderne en geïntegreerde workflow.
- **Xfce** is beter als je een lichte en klassieke desktopomgeving wilt.

### Prestaties

Kies **Hyprland** of **Dwm**.

- **Hyprland** werkt met Wayland en sneltoetsen of shortcuts. 
- **Dwm** is een zeer minimalistische maar snelle tiling-windowmanager.

> [!IMPORTANT]
> Houd er rekening mee dat je na de installatie zelf een taakbalk, applauncher, notificatiesysteem, achtergrondprogramma en vergrendelscherm moet installeren en instellen.

## Aanbevolen keuze

In deze workshop kiezen we voor **KDE Plasma**, omdat deze desktopomgeving een goede balans biedt tussen gebruiksgemak, prestaties en aanpasbaarheid.

Als je distributie tijdens de installatie naar een desktopomgeving vraagt, kies je voor **KDE Plasma**. Je krijgt dan meteen een volledige grafische desktop met onder andere een taakbalk, bestandsbeheerder, instellingen en ondersteuning voor meerdere schermen. Voor KDE Plasma kun je, afhankelijk van je distributie, kiezen tussen een Wayland-sessie en een X11-sessie.

> [!WARNING]
> Kies **No desktop environment** alleen als je bewust zelf een windowmanager en de overige onderdelen van je werkomgeving wilt installeren. 
