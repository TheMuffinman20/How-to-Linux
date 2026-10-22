# Introductie

In deze workshop volgen we een vast stappenplan, aangevuld met uitleg zodat je precies begrijpt wat we doen en waarom Linux zo'n krachtig en veelzijdig besturingssysteem is. We installeren Linux naast[...]

## Benodigdheden

- Een USB-stick van minstens 8 GB
- Een stabiele internetverbinding (WiFi of Ethernet)

> [!NOTE]  
> Voor je begint, zorg je best voor een back-up van Windows (of je huidige OS) én alle belangrijke bestanden.  

> [!CAUTION]  
> Alle gegevens die momenteel op de USB-stick staan, worden volledig gewist en kunnen niet worden hersteld.

# Setup

## Stap 1: Download de ISO

Het leukste deel van deze workshop is kiezen welke distro je graag zou willen gebruiken. Wanneer je besloten hebt welke je zou willen gebruiken of testen, zul je deze moeten downloaden als ISO-bestand[...]

Volg daarvoor onderstaande stappen:

1. Ga naar de officiële webpagina: vb. https://cachyos.org/download/
2. Download de juiste ISO voor je processortype (Intel/AMD64)

> [!TIP]  
> Als je nogal besluiteloos bent en niet goed weet waarvoor elke distro dient of hoe ze eruit zien, kun je best de andere workshop [**Distributies**](Distributies.md) eens bekijken.

## Stap 2: Download het hulpprogramma

Om een Linux-ISO op een USB-stick te plaatsen, hebben we een speciaal hulpprogramma nodig. Een ISO-bestand kan namelijk niet zomaar gekopieerd worden; het moet correct "geflasht" worden zodat de USB-s[...]

Hieronder overlopen we drie veelgebruikte tools, elk met hun eigen sterktes en doelpubliek.

### BalenaEtcher

BalenaEtcher is beschikbaar voor Windows, macOS en Linux, wat het een populaire keuze maakt. Het programma blinkt uit in eenvoud: je selecteert de ISO, kiest je USB-stick en Balena doet de rest. De[...]

1. Ga naar de officiële website: https://etcher.balena.io/
2. Download de meest recente versie

### Rufus

Rufus is het hulpprogramma dat we in deze workshop zullen gebruiken. Het is een uitstekende allrounder: snel, betrouwbaar en voorzien van extra opties die handig zijn bij het installeren van Linux in [...]

1. Ga naar de officiële website: https://rufus.ie/nl/#download
2. Download de nieuwste versie voor jouw processortype (Intel/AMD64)

### Ventoy

Ventoy is het meest geavanceerde programma in deze lijst. In plaats van telkens een USB-stick opnieuw te moeten flashen, maakt Ventoy een speciale omgeving waarin je simpelweg ISO-bestanden kunt kopi�[...]

1. Ga naar de officiële website: https://www.ventoy.net/en/download.html
2. Download de nieuwste versie voor jouw processortype (Intel/AMD64)

## Stap 3: USB flashen

Plaats eerst de USB-stick die je wilt gebruiken in je computer. Controleer dat er geen belangrijke bestanden op staan, want tijdens het flashen wordt de volledige inhoud definitief verwijderd. Ope[...]

1. Selecteer de USB om te flashen onder Apparaat
2. Selecteer de ISO door op SELECTEREN te klikken
3. Negeer de grootte van de persistente partitie, het doelsysteem en het volumelabel
4. Selecteer als bestandssysteem GPT
5. Negeer clustergrootte

Controleer nog een laatste keer of je de correcte USB-stick geselecteerd hebt voordat je de flash initialiseert. Zorg er ook voor dat alle instellingen geselecteerd zijn zoals hierboven aangegeven.

6. Klik op STARTEN

Wacht tot de tool klaar is met schrijven van het bestand, daarna kun je hem veilig verwijderen van de computer. Goed gedaan, je hebt nu een zogeheten "Live USB" aangemaakt!

> [!NOTE]  
> Als je de USB weer wilt gebruiken om data op te slaan na de volledige dual-boot, kun je hem in de computer inpluggen en via Windows Verkenner formatteren door op de usb rechts te klikken en formatte[...]

# Schijfruimte vrijmaken

## Dual boot

Wanneer je Linux naast Windows wilt installeren, moet je eerst vrije ruimte voorzien op je harde schijf of SSD. Dat doen we door de bestaande Windows-partitie te verkleinen zodat er plaats ontstaat vo[...]

1. Zoek in het Start-menu naar **Schijfbeheer** (**Create and format hard disk partitions**)
2. Klik bovenaan met de rechtermuisknop op de hoofdpartitie (meestal de C:-schijf)
3. Kies **Volume verkleinen** (**Shrink Volume**)
4. Geef aan hoeveel ruimte je wilt afstaan aan Linux
  - Minimaal 50 GB
  - 100+ GB is aangeraden
5. Klik op **Verkleinen** (**Shrink**)

Als alles goed is, verschijnt nu een blok **Niet-toegewezen ruimte** (**Unallocated space**). Je hoeft hier geen nieuwe partitie van te maken — Linux zal dit tijdens de installatie zelf correct inde[...]

## Single boot

Als je ervoor kiest om enkel Linux te installeren, hoef je geen ruimte vrij te maken in Windows. Tijdens de Linux-installatie kun je ervoor kiezen om de volledige schijf te gebruiken.

> [!CAUTION]  
> Dit verwijdert alle Windows-data permanent!

Wil je later Windows opnieuw installeren, dan moet je weten dat Windows de neiging heeft om de bootloader te overschrijven. Daarom installeer je in de praktijk:

1. Eerst Windows
2. Daarna Linux

Bij single-boot maakt dit niet uit, maar bij dual-boot is de volgorde belangrijk.

# Opstartomgeving

Je hebt nu een Live USB met daarop de Linux-ISO, én een stuk niet-toegewezen ruimte op je schijf waar Linux straks geïnstalleerd kan worden. Voor we kunnen opstarten vanaf de USB, moeten we nog drie[...]

## BitLocker

BitLocker is een beveiligingsfunctie van Windows die je systeempartitie kan versleutelen. Als BitLocker merkt dat er iets verandert aan de opstartomgeving (zoals het gebruik van een andere schijf, een[...]

Schakel BitLocker uit met volgende stappen:

1. Zoek in het Start-menu naar **Apparaatversleuteling** (**Device Encryption**)
2. Schakel dit uit

Het uitschakelen van BitLocker kan enige tijd duren, afhankelijk van de grootte van je schijf, maar je kunt het apparaat in de tussentijd wel blijven gebruiken.

### Ben je BitLocker vergeten uit te schakelen?

Geen paniek. Als BitLocker geactiveerd wordt tijdens het opstarten, zal Windows vragen om een herstelcode. Deze kun je zo terugvinden:

1. Ga naar https://account.microsoft.com/devices/recoverykey
2. Log in met hetzelfde Microsoft-account dat je op de computer gebruikt
3. Zoek de herstelcode die overeenkomt met jouw apparaat
4. Voer de code in op de computer

Daarna kan je bitlocker deactiveren en verdergaan met de installatie.

## Opstarten vanaf de Live USB

De USB-stick is klaar. Je moet de computer nu laten opstarten vanaf die stick. De precieze stappen verschillen per computer. **BIOS/UEFI** is het instellingenmenu van de computer; **UEFI** is de moder[...]

1. Laat de USB-stick aangesloten en start de computer opnieuw op.
2. Open tijdens het opstarten het opstartmenu of de **BIOS/UEFI**-instellingen. De juiste toets verschilt per fabrikant van je moederbord; vaak is dit **F2, F12, F11, F8, Esc of Del**. Meestal verschi[...]
3. Kies in het opstartmenu de USB-stick. Kies bij voorkeur de vermelding die met **UEFI** begint, als die beschikbaar is.

Als de USB-stick niet in het opstartmenu staat, open dan de BIOS/UEFI-instellingen en controleer of de USB-opstartoptie is ingeschakeld. De namen en locaties van instellingen verschillen per fabrikant[...]

Secure Boot hoeft niet voor elke Linux-distributie uitgeschakeld te worden. Schakel het alleen uit als de documentatie van je gekozen distributie dat aangeeft of als het opstarten anders niet lukt. No[...]

## Installatie

Meestal start de installer automatisch op in de liveomgeving van je linux distributie, als dit niet zo is kies je het opstartmenu van Linux **Try or Install Linux** (of de vergelijkbare optie voor jou[...]

Wanneer je klaar bent om Linux te installeren, open je **Install Linux** of **Launch Installer** vanaf het bureaublad of vanuit het installatiemenu. De precieze naam en weergave kunnen per distributie[...]

> [!TIP]  
> LTS staat voor _Long Term Support_ en betekent dat een versie langere tijd updates krijgt. Deze versies van het OS zijn ideaal voo servers.

Volg de aanwijzingen van de installer:

1. Maak verbinding met het internet via WiFi of Ethernet
2. Kies de geprefereerde taal voor jouw systeem
3. Kies de regio en tijdzone
4. Kies de correcte toetsenbordindeling

## Bootloader

De bootloader is het programma dat opstart nog voor het besturingssysteem om je de keuze te geven met welk OS je de computer wilt besturen. Er zijn doorgaans veel verschillende bootloaders, met elk ee[...]

> [!NOTE]  
> Ben je wat onzeker over deze keuze? Bekijk dan de workshop [**Bootloaders**](Bootloaders.md).

## Partities

Bij de keuze voor de schijf- of partitie-indeling zijn er meerdere opties, afhakelijk van jouw gebruiksdoeleinden kunnen we hier de correcte keuze maken. Kies een optie hieronder om verder te gaan voo[...]

### Optie A: Dual boot (Linux naast Windows)

Als de installer Windows herkent, kies dan **Installeer Linux naast Windows** (**Install Linux alongside Windows**).

Als die optie niet beschikbaar is of de installer geeft een error, kun je mogelijk **Iets anders** of **Manueel Instellen** (**Something else** of **Manual Partitioning**) kiezen om de partities handm[...]
## Manuele Partitionering

#### Eerste partitie (EFI)
De eerste partitie is voorbehouden voor de bootloader is is essentieel voor elk besturingssysteem dat een dual-boot wilt gebruiken. Hierin zal het programma komen dat mee opstart wanneer de compu[...]

1. Selecteer de **Unallocated space** die je in Windows aanmaakte. Controleer of de grootte overeenkomt met de grootte die jij aan je Linux-besturingssysteem wou geven.
2. Klik op Create
3. Geef als grootte **4096MB** in
4. Kies als bestandssysteem **FAT32**
5. Geef als mountpoint **/boot** in
6. Kies als vlag **boot**

#### Tweede partitie

1. Selecteer opniew de **Unallocated space**. De vorige grootte zou nu verkleint moeten zijn met 4GB.
2. Klik op Create
3. Verander het bestandsysteem niet
4. Mount deze partitie door **/** in te geven
5. Kies geen vlag

Controleer je keuzes zorgvuldig en bevestig daarna de installatie.

### Optie B: Single boot (Linux als enige besturingssysteem)

Kies Schijf wissen en Linux installeren (of **Erase disk and install Linux**) als je Linux als enige besturingssysteem op de gekozen schijf wilt gebruiken.

> [!CAUTION]  
> Deze optie verwijdert alle gegevens op de geselecteerde schijf, waaronder Windows en persoonlijke bestanden. Controleer zorgvuldig welke schijf is geselecteerd en zorg vooraf voor een back-up.

## Desktopomgeving

Sommige installers vragen welke desktopomgeving je wilt gebruiken. In deze guide zullen we opteren voor KDE plasma, een op Wayland-gebaseerde windowmanager die een flexibele omgeving en hogere snelhei[...]

> [!NOTE]  
> Ben je wat onzeker over deze keuze? Volg dan de guide [**Desktops**](Desktops.md).  

## Pakketten

Je krijgt ook een meerkeuzemenu dat handige pakketten bevat om te installeren nog voor de setup is voltooid. Enkele pakketten die je kunt overwegen:

- HP Printer Support
- General Printer Support
- Accessability tools (screenreader, mouse tweaks)

## Gebruikers

Als laatste zal de installer vragen welke gebruiker het systeem zal beheren. Hiervoor zijn een aantal data nodig, die je hieronder kunt volgen:

1. Geef je (volledige) naam in
2. Geef je gebruikersnaam in
3. Geef de naam van de computer in
4. Geef het wachtwoord voor de gebruiker in

> [!TIP]  
> Als je hetzelfde wachtwoord voor root wilt gebruiken, vink je de optie **Use the same password for root** aan.

## Afronding en eerste start

Nu we alle opties correct hebben aangeduid kunnen we de installatie starten. Wacht tot deze is voltooid, verbreek de internetverbinding niet en zet de computer niet uit.

De duur van de installatie verschilt per computer en distributie. Kies **Nu herstarten** (of de vergelijkbare optie) als de installer er om vraagt. Verwijder de USB-stick als het scherm zwart is en vo[...]

## Conclusie

Linux is nu geïnstalleerd. Bij een dual-boot toont de computer doorgaans een opstartmenu waarin je Linux of Windows kunt kiezen. Als dat menu niet verschijnt, open dan het opstartmenu van je computer[...]


## FAQ

...

> [!NOTE]  
> Bij andere vragen kun je langskomen bij het IT-Lab waar studenten en lectoren klaarstaan om jou zo snel en zo goed mogelijk te helpen met problemen. Kom gerust eens langs!
