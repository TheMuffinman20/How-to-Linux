# Introductie

In deze workshop volg je een vast stappenplan van instructies, aangevuld met uitleg en achtergrondinformatie zodat je precies begrijpt wat we doen en waarom sommige keuzes belangrijk zijn. Het doel is om Linux alleen of samen met Windows te installeren je op computer, alsook aan te tonen waarom Linux een krachtig en performant besturingssysteem is.

**Geschatte duur:** 90 tot 120 minuten

## Benodigdheden

- Een USB-stick van minstens 8 GB
- Een stabiele internetverbinding (WiFi of Ethernet)

> [!WARNING]
> Voor je begint, zorg je best voor een back-up van Windows (of je huidige besturingssysteem) en van alle belangrijke bestanden.

> [!CAUTION]
> Alle gegevens die momenteel op de USB-stick staan, worden volledig gewist en kunnen niet worden hersteld.

# Setup

## ISO downloaden

Vooraleer we aan de effectieve installatie kunnen beginnen, kies je eerst welke distro je wil gebruiken of testen. Deze download je als **ISO**-bestand.

Volg daarvoor onderstaande stappen:

1. Ga naar de officiële webpagina, bijvoorbeeld: https://cachyos.org/download/
2. Download de juiste ISO voor je processortype **(x86/ARM)**
3. Controleer de **checksum** van het bestand, als de website er een geeft. Zo weet je zeker dat de download niet beschadigd is.

> [!TIP]
> Als je nogal besluiteloos bent en niet goed weet waarvoor elke distro dient of hoe ze eruit zien, kun je best de andere workshop [**Distributies**](Distributies.md) eens bekijken.

## Hulpprogramma downloaden

Om een Linux-ISO op een USB-stick te plaatsen, hebben we een speciaal hulpprogramma nodig. Een **ISO**-bestand kan namelijk niet zomaar gekopieerd worden; het moet correct worden “geflasht”, zodat de **USB**-stick het bestand correct als opstartbaar medium kan gebruiken.

Hieronder overlopen we drie veelgebruikte tools, elk met hun eigen sterktes en doelpubliek.

### BalenaEtcher

BalenaEtcher is beschikbaar voor **Windows, macOS en Linux**, wat het een populaire keuze maakt. Het programma blinkt uit in eenvoud: je selecteert de **ISO**, kiest je USB-stick en **Balena** doet de rest. De interface is overzichtelijk en werkt goed voor beginners.

1. Ga naar de officiële website: https://etcher.balena.io/
2. Download de meest recente versie

### Rufus

**Rufus** is het hulpprogramma dat we in deze workshop zullen gebruiken. Het is een uitstekende allrounder: snel, betrouwbaar en voorzien van extra opties die handig zijn bij het installeren van Linux in verschillende situaties.

1. Ga naar de officiële website: https://rufus.ie/nl/#download
2. Download de nieuwste versie voor jouw processortype **(x86/ARM)**

### Ventoy

**Ventoy** is het meest geavanceerde programma in deze lijst. In plaats van telkens een USB-stick opnieuw te moeten flashen, maakt Ventoy een speciale omgeving waarin je eenvoudig **ISO**-bestanden kunt kopiëren en later kunt selecteren welke distro je wil starten. Dit werkt goed als je meerdere Linux-versies wil testen op één stick.

1. Ga naar de officiële website: https://www.ventoy.net/en/download.html
2. Download de nieuwste versie voor jouw processortype ***(x86/ARM)**

## Stap 3: USB flashen

Plaats eerst de USB-stick die je wil gebruiken in je computer. Controleer of er geen belangrijke bestanden op staan, want tijdens het flashen wordt de volledige inhoud definitief verwijderd. Open daarna het hulpprogramma dat je hebt gedownload.

Volg deze stappen in Rufus:

1. Selecteer de USB-stick die je wil flashen onder `Apparaat`
2. Klik op `SELECTEREN` en kies de **ISO**
3. Kies als partitieschema `GPT`
4. Controleer dat het doelsysteem op `UEFI (niet-CSM)` staat
5. Negeer de grootte van de persistente partitie, het volumelabel en de clustergrootte

Controleer nog een laatste keer of je de juiste **USB**-stick geselecteerd hebt voordat je het flashproces initialiseert. Zorg er ook voor dat alle instellingen overeenkomen met de instellingen die hierboven zijn beschreven.

6. Klik op `STARTEN`

Wacht tot de tool klaar is met het schrijven van het bestand. Daarna kun je de USB-stick veilig verwijderen van de computer. Je hebt nu een zogenaamde **Live USB** aangemaakt!

> [!TIP]
> Wil je de stick later weer als gewone opslag gebruiken? Klik er in Windows Verkenner met de rechtermuisknop op en kies `Formatteren`.

# Voorbereiding

In dit hoofdstuk bereid je Windows voor, zodat Linux er later zonder problemen naast past. Sla je dit over, dan lukt de installatie vaak niet of start Windows daarna niet meer.

> [!NOTE]
> Kies je voor **single boot** (alleen Linux), dan hoef je alleen het gedeelte over [BitLocker](#bitlocker-uitschakelen) te volgen als Windows nog op de schijf staat.

## BitLocker uitschakelen

BitLocker is een beveiligingsfunctie van Windows die je systeempartitie kan versleutelen. Als BitLocker merkt dat er iets verandert aan de opstartomgeving, zoals het gebruik van een andere schijf of een andere opstartvolgorde, kan het voorkomen de boot blokkeert of om een herstelcode vraagt.

Schakel het dus eerst uit, ook vóór je de partitie verkleint.

**Windows Home** (*Apparaatversleuteling*):

1. Open **Instellingen** → **Privacy en beveiliging** → **Apparaatversleuteling**
2. Zet de schakelaar uit

**Windows Pro** (*BitLocker-stationsversleuteling*):

1. Zoek in het Startmenu naar **BitLocker beheren**
2. Klik bij je C:-schijf op **BitLocker uitschakelen**

Het uitschakelen van BitLocker kan enige tijd duren, afhankelijk van de grootte van je schijf, maar je kunt het apparaat in de tussentijd wel blijven gebruiken.

### Ben je BitLocker vergeten uit te schakelen?

Geen paniek. Als BitLocker geactiveerd wordt tijdens het opstarten, zal Windows vragen om een herstelcode. Deze kun je als volgt terugvinden:

1. Ga naar https://account.microsoft.com/devices/recoverykey
2. Log in met hetzelfde Microsoft-account dat je op de computer gebruikt
3. Zoek de herstelcode die overeenkomt met jouw apparaat
4. Voer de code in op de computer

Daarna kun je BitLocker deactiveren en verdergaan met de installatie.

## Snel opstarten uitschakelen

Windows heeft een functie *Snel opstarten*, waarbij het afsluiten eigenlijk een soort slaapstand is. Daardoor blijft je Windows-schijf "vergrendeld" en kan Linux er soms niet goed bij.

1. Zoek in het Startmenu naar **Configuratiescherm** → **Energiebeheer**
2. Klik op **Kiezen wat de aan/uit-knoppen doen**
3. Klik op **Instellingen wijzigen die momenteel niet beschikbaar zijn**
4. Haal het vinkje weg bij **Snel opstarten inschakelen**
5. Klik op **Wijzigingen opslaan** en sluit Windows daarna volledig af

## Schijfruimte vrijmaken

### Dual boot

Wanneer je Linux naast Windows wil installeren, moet je eerst vrije ruimte voorzien op je harde schijf of SSD. Dat doen we door de bestaande Windows-partitie te verkleinen, zodat er plaats ontstaat voor Linux.

Volg deze stappen:

1. Zoek in het Start-menu naar **Schijfbeheer** (**Create and format hard disk partitions**)
2. Klik bovenaan met de rechtermuisknop op de hoofdpartitie (meestal de C:-schijf)
3. Kies **Volume verkleinen** (**Shrink Volume**)
4. Geef aan hoeveel ruimte je wil afstaan aan Linux
   - Minimaal 50 GB
   - 100 GB of meer is aangeraden
5. Klik op **Verkleinen** (**Shrink**)

Er verschijnt nu een blok **Niet-toegewezen ruimte** (**Unallocated space**). Je hoeft hier geen nieuwe partitie van te maken; Linux zal dit tijdens de installatie zelf correct indelen.

### Single boot

Kies je om enkel Linux te installeren, hoef je geen ruimte vrij te maken in Windows. Tijdens de Linux-installatie kun je ervoor kiezen om de volledige schijf te gebruiken.

> [!CAUTION]
> Deze optie verwijdert alle Windows-data permanent!

Wil je later Windows opnieuw installeren, dan moet je weten dat Windows de neiging heeft om de bootloader te overschrijven. Daarom installeer je in de praktijk:

1. Eerst Windows
2. Daarna Linux

Bij single-boot maakt dit niet uit, maar bij dual-boot is de volgorde belangrijk.

Je hebt nu een **Live USB** met daarop de Linux-**ISO**, én een stuk niet-toegewezen ruimte op je schijf waar Linux straks geïnstalleerd kan worden. Voordat we kunnen opstarten vanaf de USB-stick, moeten we nog drie belangrijke dingen regelen.

# Opstarten

## BIOS/UEFI openen

Om vanaf de USB-stick te starten, moet je naar de **BIOS/UEFI**, het instellingenmenu van je computer. De precieze stappen verschillen per computer.

- **UEFI** is de modernere standaard
- **BIOS** is de oudere variant

Volg deze stappen om de **BIOS/UEFI** te openen:

1. Laat de USB-stick aangesloten en start de computer opnieuw op.
2. Open tijdens het opstarten het opstartmenu door op de **BIOS/UEFI**-toets te drukken.
3. Ga naar het tabblad **Boot**.
4. Zet de **USB-stick** bovenaan de opstartvolgorde, vóór de **Windows Boot Manager**. Kies bij voorkeur de vermelding die met **UEFI** begint.

> [!NOTE]
> De **BIOS/UEFI**-toets verschilt per fabrikant van je moederbord, maar vaak is dit **F2, F12, F11, F8, Esc** of **Del**. Soms kun je dit zien tijdens het opstarten in een korte melding, maar je kunt het ook opzoeken als je het merk van je moederbord of computer kent.

## Secure Boot

**Secure Boot** zorgt ervoor dat een computer alleen opstart vanaf software met een goedgekeurde handtekening. Veel Linux-distributies hebben die niet standaard, waardoor de USB-stick geweigerd wordt.

> [!IMPORTANT]
> Secure Boot hoeft niet voor elke Linux-distributie uitgeschakeld te worden. Schakel het alleen uit als de documentatie van je gekozen distributie dat aangeeft of als het opstarten anders niet lukt. Als je niet zeker bent, controleer dan eerst de officiële installatiestappen van je distro.

1. Ga in de BIOS/UEFI naar het menu **Security** (soms staat het onder **Boot**).
2. Zoek **Secure Boot** en zet dit **uit**.
3. Sluit af met **F10** (of **Save Changes & Exit**).

> [!WARNING]
> Sommige games met kernel-level anti-cheat (bijvoorbeeld Valorant) weigeren in Windows te starten als Secure Boot uit staat. Wil je die spelen, zet Secure Boot dan na de installatie weer aan als dat voor je distro kan.

## Live-omgeving

Na het opslaan start de computer op vanaf de USB-stick. Je ziet een opstartmenu waarin je kan kiezen welke versie van je distro je start.

- De standaardoptie heet gewoon naar je distro, bijvoorbeeld **CachyOS**. 
- Soms staat er ook een **LTS**-optie, dat is de stabiele versie van de kernel.

> [!TIP]
> **LTS** staat voor _Long Term Support_ en betekent dat een versie langere tijd updates krijgt. Deze versies van het besturingssysteem zijn ideaal voor servers en voor gebruikers die een stabiele, langdurig ondersteunde installatie willen.

Kies de standaardoptie. Je komt dan in een **tijdelijke Linux-omgeving** waarin je de distro kan uitproberen of verdergaan met de definitieve installatie.

# Installatie

## Installer

Meestal start de installer automatisch op in de liveomgeving van je Linux-distributie. Als dat niet zo is, kies je het opstartmenu van Linux **Try or Install Linux** (of de vergelijkbare optie voor jouw distributie).

Volg de aanwijzingen van de installer:

1. Maak verbinding met het internet via WiFi of Ethernet
2. Kies de geprefereerde taal voor jouw systeem
3. Kies de regio en tijdzone
4. Kies de juiste toetsenbordindeling

## Bootloader

De bootloader is het programma dat voor het besturingssysteem opstart om je de keuze te geven met welk OS je de computer wil besturen. Er zijn doorgaans veel verschillende bootloaders, met elk een eigen manier van werken en een eigen voorkeur voor verschillende systemen.

In deze guide zullen we kiezen voor **Limine**, een simpele maar snelle bootloader.

> [!TIP]
> Ben je wat onzeker over deze keuze? Bekijk dan de workshop [**Bootloaders**](Bootloaders.md).

## Partities

Bij de keuze voor de schijf- of partitie-indeling zijn er meerdere opties. Afhankelijk van jouw gebruiksdoeleinden kunnen we hier de juiste keuze maken. Kies een optie hieronder om verder te gaan voor jouw situatie.

### Dual boot (Linux naast Windows)

Als de installer Windows herkent, kies dan **Installeer Linux naast Windows** (**Install Linux alongside Windows**).

Als die optie niet beschikbaar is of de installer geeft een foutmelding, kun je mogelijk **Iets anders** of **Manueel instellen** (**Something else** of **Manual Partitioning**) kiezen om de partities handmatig te configureren.

#### Handmatig partitioneren

**1. Opstartpartitie (EFI)**

De eerste partitie is voorbehouden voor de bootloader en is essentieel voor elk besturingssysteem dat een dual-boot wil gebruiken. Hierin zal het programma komen dat mee opstart wanneer de computer wordt aangezet. Deze partitie is nodig zodat de computer weet welke besturingssysteeminstellingen moeten worden geladen.

1. Selecteer de **Niet-toegewezen ruimte** die je in Windows hebt gemaakt.
2. Klik op **Create**
3. Geef als grootte **4096 MB** in
4. Kies als bestandssysteem **FAT32**
5. Geef als mountpoint **/boot** in
6. Zet de vlag **boot** aan

**2. Hoofdpartitie**

Hierop komt Linux zelf te staan, samen met al je bestanden.

1. Selecteer opnieuw de **Unallocated space**. De vorige grootte zou nu verkleind moeten zijn met 4 GB.
2. Klik op **Create**
3. Laat het bestandssysteem staan op **Btrfs**
4. Mount deze partitie door **/** in te geven
5. Zet geen vlaggen aan

Controleer je keuzes zorgvuldig en bevestig daarna de installatie.

### Single boot (alleen Linux)

Kies **Schijf wissen en Linux installeren** (of **Erase disk and install Linux**) als je Linux als enige besturingssysteem op de gekozen schijf wil gebruiken.

> [!CAUTION]
> Deze optie verwijdert alle gegevens op de geselecteerde schijf, waaronder Windows en persoonlijke bestanden. Controleer zorgvuldig welke schijf is geselecteerd en zorg vooraf voor een back-up.

# Configuratie

## Desktopomgeving

Sommige installers vragen welke desktopomgeving je wil gebruiken. Dat is wat je ziet na het inloggen: bureaublad, taakbalk, menu's en vensters. Je kan dit later nog wijzigen. 

In deze guide zullen we kiezen voor **KDE Plasma**.

e kan ook kiezen voor **Hyprland**, een op Wayland-gebaseerde windowmanager die een flexibele omgeving en hogere snelheid biedt in vergelijking met sommige andere desktopomgevingen.

Als je **Hyprland** kiest, zal de desktopomgeving opstarten met **Noctalia Shell**. Wil je toch **Caelestia Shell**? Dan kies je hier voor **No Desktop** en volg je na de laatste stap van deze installatie de guide over [**Caelestia**](Caelestia.md).

> [!TIP]
> Ben je wat onzeker over deze keuze? Volg dan de guide over [**Desktops**](Desktops.md).

> [!WARNING]
> Je zal geen desktopomgeving hebben wanneer je inlogt in de computer, enkel een TTY om zelf je omgeving te installeren. 

## Pakketten

Je krijgt ook een meerkeuzemenu dat handige pakketten bevat om te installeren nog voordat de setup is voltooid. Enkele pakketten die je kunt overwegen:

- HP Printer Support
- General Printer Support
- Accessibility tools (screenreader, mouse tweaks)

## Gebruikers

Als laatste zal de installer vragen welke gebruiker het systeem zal beheren. Hiervoor zijn verschillende gegevens nodig, die je hieronder kunt volgen:

1. Geef je (volledige) naam in
2. Geef je gebruikersnaam in
3. Geef de naam van de computer in
4. Geef het wachtwoord voor de gebruiker in

> [!TIP]
> Als je hetzelfde wachtwoord voor root wil gebruiken, vink je de optie **Use the same password for root** aan.

# Afronding

Nu we alle opties correct hebben aangeduid, kunnen we de installatie starten. Wacht tot deze is voltooid, verbreek de internetverbinding niet en zet de computer **niet** uit.

De duur van de installatie verschilt per computer en distributie. Kies `Herstarten` (of de vergelijkbare optie) als de installer hierom vraagt. Verwijder de USB-stick als het scherm compleet **leeg** en **zwart** is en je computer opnieuw opstart.

## Installatie voltooien

Linux is nu geïnstalleerd. Bij een dual-boot toont de computer doorgaans een **opstartmenu** waarin je Linux of Windows kunt kiezen. Als dat menu niet verschijnt, ga dan naar de **BIOS/UEFI** van je computer en controleer of de juiste bootoptie is geselecteerd.

Als je Linux enkel als hoofdbesturingssysteem hebt geïnstalleerd, start de computer direct in Linux op.

## Eerste start

Bij **dual boot** toont de computer meestal een **opstartmenu** waarin je Linux of Windows kiest. Verschijnt dat menu niet, ga dan naar de **BIOS/UEFI** en controleer of de juiste bootoptie bovenaan staat.

Bij **single boot** start de computer meteen in Linux.

## Volgende stappen

Je hebt nu een werkende basisinstallatie. Vanaf hier kan je je systeem personaliseren en software installeren. Enkele populaire keuzes:

| Programma | Waarvoor |
|---|---|
| **Spotify & Spicetify** | Muziek en een aanpasbare Spotify |
| **Discord** | Chatten met vrienden en communities |
| **Zen** | Webbrowser |
| **Kitty** | Terminal |
| **Neovim (nvim)** | Teksteditor voor in de terminal |
| **Btop** | Overzicht van je processor, geheugen en processen |

# FAQ

## Waarom verschijnt mijn USB-stick niet in het opstartmenu?

Controleer of de USB-stick correct is geflasht, of deze is aangesloten en of de BIOS/UEFI het juiste bootmedium ondersteunt. Soms moet je in de BIOS/UEFI handmatig de USB-stick als opstartoptie selecteren.

## Hoe weet ik of mijn computer UEFI of BIOS gebruikt?

Je kunt dit meestal controleren in de BIOS/UEFI-instellingen. UEFI is de modernere standaard en wordt meestal aangeduid als “UEFI”. BIOS is de oudere standaard. Als je de USB-stick met “UEFI” ziet in het opstartmenu, gebruik je waarschijnlijk UEFI.

## Wat als BitLocker voorkomt dat ik Linux start?

Schakel BitLocker uit via Windows. Neem ook de recovery key van je Microsoft-account mee als je de code niet meer weet.

## Wat als de installer Windows niet herkent?

Controleer of je voldoende vrije ruimte hebt gemaakt. Als je dat niet hebt gedaan, maak dan eerst ruimte vrij in Windows. Als de installer nog steeds niet herkent dat er een Windows-installatie aanwezig is, kun je de partities handmatig configureren.

## Hoe kies ik de juiste partitie-indeling?

Bij dual-boot is de keuze meestal: Linux naast Windows. Bij een nieuwe installatie zonder Windows kies je vaak “Schijf wissen en Linux installeren”.

## Wat als ik later Windows opnieuw wil installeren?

Dan moet je de bootloader van Linux opnieuw configureren of de Windows-installatie opnieuw uitvoeren. De volgorde is belangrijk: als je dual-boot gebruikt, is het meestal verstandig om eerst Windows te installeren en daarna Linux.

## Is Secure Boot altijd uitgeschakeld nodig?

Neen, niet voor elke distributie. Schakel Secure Boot alleen uit als de documentatie van je gekozen distro dat aangeeft of als het systeem niet wil booten.

## Wat als ik Linux later weer wil verwijderen?

Dat hangt af van hoe je hebt geïnstalleerd. Als je dual-boot gebruikt, kun je de Linux-partitie later verwijderen en de vrije ruimte teruggeven aan Windows. In sommige gevallen moet je de bootloader opnieuw configureren.

> [!NOTE]
> Bij andere vragen kun je langskomen bij het IT-Lab, waar studenten en lectoren klaarstaan om jou zo snel en zo goed mogelijk te helpen met problemen. Kom gerust eens langs!
