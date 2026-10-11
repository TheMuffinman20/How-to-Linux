# Hoe kies ik mijn bootloader?

Deze guide helpt je bij het kiezen van een geschikte bootloader voor jouw Linux-installatie. De bootloader start op voordat het besturingssysteem wordt geladen. Bij een dual-boot geeft hij je de keuze tussen bijvoorbeeld Linux en Windows.

De beste keuze hangt vooral af van je firmware, het aantal besturingssystemen en hoeveel je zelf wilt aanpassen. Controleer eerst of je computer in **UEFI-modus** of in de oudere **BIOS/Legacy-modus** opstart. Voor moderne computers en een dual-boot met Windows gebruik je bij voorkeur UEFI.

### 1. Consistentie

De bootloader moet betrouwbaar blijven en zonder verrassingen het juiste besturingssysteem starten.

- Werkt de bootloader goed met jouw Linux-distributie?
- Kan hij Windows automatisch herkennen?
- Blijft het opstartmenu werken na een kernel- of systeemupdate?

### 2. Flexibiliteit

Een bootloader kan eenvoudig zijn, maar ook veel opties bieden voor thema's, herstelopties en meerdere kernels.

- Wil je alleen Linux starten, of ook Windows en andere systemen?
- Wil je zelf opstartopties en thema's kunnen instellen?
- Heb je ondersteuning nodig voor meerdere Linux-kernels?

### 3. Overdraagbaarheid

De bootloader moet passen bij de firmware en de schijfindeling van je computer.

- **UEFI** gebruikt een EFI-systeempartitie, meestal geformatteerd als FAT32.
- **BIOS/Legacy** gebruikt een andere opstartmethode en is minder geschikt voor een nieuwe dual-bootinstallatie.
- Installeer Linux en de bootloader in dezelfde modus. Start de Linux-USB dus ook op via de optie die met **UEFI** begint.

## Windows en Linux

### Limine, (GRUB)

Limine is een moderne bootloader met ondersteuning voor UEFI en BIOS/Legacy.

- Duidelijk en modern opstartmenu
- Geschikt voor Linux en Windows in een dual-boot
- Veel mogelijkheden zonder dat de basisconfiguratie ingewikkeld is
- Minder standaard aanwezig in distributies dan GRUB

In deze workshop kiezen we voor **Limine**, omdat hij een moderne en flexibele keuze is voor een systeem met Linux en eventueel Windows.

## Alleen Linux

### systemd-boot

systemd-boot is een lichte bootloader voor moderne UEFI-systemen.

- Eenvoudig en snel
- Past goed bij een installatie met alleen Linux
- Weinig configuratie nodig
- Niet bedoeld voor BIOS/Legacy
- Minder geschikt wanneer je veel verschillende systemen automatisch wilt beheren

Kies systemd-boot als je een moderne UEFI-computer hebt en een eenvoudige Linux-installatie wilt. Limine

## Meerdere besturingssystemen

### rEFInd (Limine, GRUB)

rEFInd toont de beschikbare besturingssystemen als duidelijke opstartopties.

- Handig wanneer je meerdere besturingssystemen gebruikt
- Visueel overzichtelijk menu
- Vooral gericht op UEFI
- Kan extra configuratie nodig hebben bij bijzondere installaties

Kies rEFInd als je meerdere UEFI-besturingssystemen naast elkaar gebruikt en een visueel menu belangrijk vindt.

## Oudere computers

### GRUB

GRUB is de meest gebruikte en breedst ondersteunde keuze.

- Geschikt voor dual-boot met Windows
- Werkt op zowel UEFI als BIOS/Legacy
- Veel documentatie en hulp beschikbaar
- Meer configuratie en een complexere standaardinstelling

Kies GRUB als je vooral compatibiliteit en uitgebreide ondersteuning belangrijk vindt.

# Welke bootloader past bij mij?

## Windows en Linux (dual-boot)

Kies **Limine** of **GRUB**.

- Kies Limine als je een modern en overzichtelijk menu wilt.
- Kies GRUB als je maximale compatibiliteit en documentatie wilt.
- Installeer Windows bij voorkeur eerst en Linux daarna. Windows kan anders de bootloader overschrijven.

## Alleen Linux (single-boot)

Kies **systemd-boot** voor een eenvoudige UEFI-installatie, of **Limine** wanneer je meer configuratiemogelijkheden wilt. GRUB blijft een veilige keuze als je distributie die standaard aanbiedt.

## Meerdere Linux-installaties

Kies **GRUB**, **Limine** of **rEFInd**. Deze keuzes maken het eenvoudiger om meerdere systemen of kernels in één opstartmenu te beheren.

### Aanbevolen keuze

Voor deze workshop:

- Gebruik **UEFI** als je computer dit ondersteunt.
- Kies **Limine** voor een moderne dual-boot of een flexibele Linux-installatie.
- Gebruik een **FAT32 EFI-systeempartitie** voor de bootbestanden.
- Maak altijd een back-up voordat je partities of bootinstellingen wijzigt.

Een verkeerde bootloaderkeuze verwijdert normaal gesproken niet automatisch je bestanden, maar een verkeerde partitie of firmware-instelling kan er wel voor zorgen dat een besturingssysteem niet meer opstart. Controleer daarom de schijf, opstartmodus en EFI-partitie zorgvuldig voordat je de installatie bevestigt.
