# Introductie

In deze workshop volgen we een vast stappenplan, aangevuld met uitleg zodat je precies begrijpt wat we doen en waarom Linux zo'n krachtig en veelzijdig besturingssysteem is. We installeren Linux naast Windows of als enige besturingssysteem op je computer. Tijdens deze workshop krijg je niet alleen instructies, maar ook de achtergrond van elke stap, zodat je begrijpt waarom sommige keuzes belangrijk zijn.

## Benodigdheden

- Een USB-stick van minstens 8 GB
- Een stabiele internetverbinding (WiFi of Ethernet)

> [!WARNING]
> Voor je begint, zorg je best voor een back-up van Windows (of je huidige besturingssysteem) en van alle belangrijke bestanden.
> Alle gegevens die momenteel op de USB-stick staan, worden volledig gewist en kunnen niet worden hersteld.

# Setup

## Stap 1: Download de ISO

Het leukste deel van deze workshop is kiezen welke distro je graag zou willen gebruiken. Wanneer je besloten hebt welke distro je wilt gebruiken of testen, zul je deze moeten downloaden als ISO-bestand.

Volg daarvoor onderstaande stappen:

1. Ga naar de officiële webpagina, bijvoorbeeld: https://cachyos.org/download/
2. Download de juiste ISO voor je processortype (Intel/AMD64)

> [!TIP]
> Als je nogal besluiteloos bent en niet goed weet waarvoor elke distro dient of hoe ze eruit zien, kun je best de andere workshop [**Distributies**](Distributies.md) eens bekijken.

## Stap 2: Download het hulpprogramma

Om een Linux-ISO op een USB-stick te plaatsen, hebben we een speciaal hulpprogramma nodig. Een ISO-bestand kan namelijk niet zomaar gekopieerd worden; het moet correct worden “geflasht”, zodat de USB-stick het bestand correct als opstartbaar medium kan gebruiken.

Hieronder overlopen we drie veelgebruikte tools, elk met hun eigen sterktes en doelpubliek.

### BalenaEtcher

BalenaEtcher is beschikbaar voor Windows, macOS en Linux, wat het een populaire keuze maakt. Het programma blinkt uit in eenvoud: je selecteert de ISO, kiest je USB-stick en Balena doet de rest. De interface is overzichtelijk en werkt goed voor beginners.

1. Ga naar de officiële website: https://etcher.balena.io/
2. Download de meest recente versie

### Rufus

Rufus is het hulpprogramma dat we in deze workshop zullen gebruiken. Het is een uitstekende allrounder: snel, betrouwbaar en voorzien van extra opties die handig zijn bij het installeren van Linux in verschillende situaties.

1. Ga naar de officiële website: https://rufus.ie/nl/#download
2. Download de nieuwste versie voor jouw processortype (Intel/AMD64)

### Ventoy

Ventoy is het meest geavanceerde programma in deze lijst. In plaats van telkens een USB-stick opnieuw te moeten flashen, maakt Ventoy een speciale omgeving waarin je eenvoudig ISO-bestanden kunt kopiëren en later kunt selecteren welke distro je wilt starten. Dit werkt goed als je meerdere Linux-versies wilt testen op één stick.

1. Ga naar de officiële website: https://www.ventoy.net/en/download.html
2. Download de nieuwste versie voor jouw processortype (Intel/AMD64)

## Stap 3: USB flashen

Plaats eerst de USB-stick die je wilt gebruiken in je computer. Controleer of er geen belangrijke bestanden op staan, want tijdens het flashen wordt de volledige inhoud definitief verwijderd. Open daarna het hulpprogramma dat je hebt gedownload.

Volg deze stappen in Rufus:

1. Selecteer de USB-stick die je wilt flashen onder “Apparaat”
2. Selecteer de ISO door op “SELECTEREN” te klikken
3. Negeer de grootte van de persistente partitie, het doelsysteem en het volumelabel
4. Selecteer als bestandssysteem “GPT”
5. Negeer clustergrootte

Controleer nog een laatste keer of je de juiste USB-stick geselecteerd hebt voordat je het flashproces initialiseert. Zorg er ook voor dat alle instellingen overeenkomen met de instellingen die hierboven zijn beschreven.

6. Klik op “STARTEN”

Wacht tot de tool klaar is met het schrijven van het bestand. Daarna kun je de USB-stick veilig verwijderen van de computer. Goed gedaan, je hebt nu een zogenaamde “Live USB” aangemaakt!

> [!TIP]
> Als je de USB-stick later weer wilt gebruiken om bestanden op te slaan, kun je hem opnieuw in de computer stoppen en via Windows Verkenner formatteren door met de rechtermuisknop op de USB-stick te klikken en vervolgens “Formatteren” te kiezen.

# Schijfruimte vrijmaken

## Dual boot

Wanneer je Linux naast Windows wilt installeren, moet je eerst vrije ruimte voorzien op je harde schijf of SSD. Dat doen we door de bestaande Windows-partitie te verkleinen, zodat er plaats ontstaat voor Linux.

Volg deze stappen:

1. Zoek in het Start-menu naar **Schijfbeheer** (**Create and format hard disk partitions**)
2. Klik bovenaan met de rechtermuisknop op de hoofdpartitie (meestal de C:-schijf)
3. Kies **Volume verkleinen** (**Shrink Volume**)
4. Geef aan hoeveel ruimte je wilt afstaan aan Linux
   - Minimaal 50 GB
   - 100+ GB is aangeraden
5. Klik op **Verkleinen** (**Shrink**)

Als alles goed is, verschijnt nu een blok **Niet-toegewezen ruimte** (**Unallocated space**). Je hoeft hier geen nieuwe partitie van te maken; Linux zal dit tijdens de installatie zelf correct indeelen.

## Single boot

Als je ervoor kiest om alleen Linux te installeren, hoef je geen ruimte vrij te maken in Windows. Tijdens de Linux-installatie kun je ervoor kiezen om de volledige schijf te gebruiken.

> [!CAUTION]
> Deze optie verwijdert alle Windows-data permanent!

Wil je later Windows opnieuw installeren, dan moet je weten dat Windows de neiging heeft om de bootloader te overschrijven. Daarom installeer je in de praktijk:

1. Eerst Windows
2. Daarna Linux

Bij single-boot maakt dit niet uit, maar bij dual-boot is de volgorde belangrijk.

# Opstartomgeving

Je hebt nu een Live USB met daarop de Linux-ISO, én een stuk niet-toegewezen ruimte op je schijf waar Linux straks geïnstalleerd kan worden. Voordat we kunnen opstarten vanaf de USB-stick, moeten we nog drie belangrijke dingen regelen.

## BitLocker

BitLocker is een beveiligingsfunctie van Windows die je systeempartitie kan versleutelen. Als BitLocker merkt dat er iets verandert aan de opstartomgeving, zoals het gebruik van een andere schijf, een andere bootloader of een andere opstartvolgorde, kan het voorkomen dat Windows de boot blokkeert of om een herstelcode vraagt.

Schakel BitLocker uit met de volgende stappen:

1. Zoek in het Start-menu naar **Apparaatversleuteling** (**Device Encryption**)
2. Schakel dit uit

Het uitschakelen van BitLocker kan enige tijd duren, afhankelijk van de grootte van je schijf, maar je kunt het apparaat in de tussentijd wel blijven gebruiken.

### Ben je BitLocker vergeten uit te schakelen?

Geen paniek. Als BitLocker geactiveerd wordt tijdens het opstarten, zal Windows vragen om een herstelcode. Deze kun je als volgt terugvinden:

1. Ga naar https://account.microsoft.com/devices/recoverykey
2. Log in met hetzelfde Microsoft-account dat je op de computer gebruikt
3. Zoek de herstelcode die overeenkomt met jouw apparaat
4. Voer de code in op de computer

Daarna kun je BitLocker deactiveren en verdergaan met de installatie.

## Opstarten vanaf de Live USB

De USB-stick is klaar. Je moet de computer nu laten opstarten vanaf die stick. De precieze stappen verschillen per computer. **BIOS/UEFI** is het instellingenmenu van de computer; **UEFI** is de modernere standaard en **BIOS** is de oudere variant.

Volg deze stappen:

1. Laat de USB-stick aangesloten en start de computer opnieuw op.
2. Open tijdens het opstarten het opstartmenu of de **BIOS/UEFI**-instellingen. De juiste toets verschilt per fabrikant van je moederbord; vaak is dit **F2, F12, F11, F8, Esc of Del**. Meestal kun je dit zien tijdens het opstarten in een korte melding.
3. Kies in het opstartmenu de USB-stick. Kies bij voorkeur de vermelding die met **UEFI** begint, als die beschikbaar is.

Als de USB-stick niet in het opstartmenu staat, open dan de BIOS/UEFI-instellingen en controleer of de USB-opstartoptie is ingeschakeld. De namen en locaties van instellingen verschillen per fabrikant, maar het idee is hetzelfde: de USB-stick moet als opstartmedium worden toegelaten.

> [!IMPORTANT]
> Secure Boot hoeft niet voor elke Linux-distributie uitgeschakeld te worden. Schakel het alleen uit als de documentatie van je gekozen distributie dat aangeeft of als het opstarten anders niet lukt. Als je niet zeker bent, controleer dan eerst de officiële installatiestappen van je distro.

## Installatie

Meestal start de installer automatisch op in de liveomgeving van je Linux-distributie. Als dat niet zo is, kies je het opstartmenu van Linux **Try or Install Linux** (of de vergelijkbare optie voor jouw distributie).

Wanneer je klaar bent om Linux te installeren, open je **Install Linux** of **Launch Installer** vanaf het bureaublad of vanuit het installatiemenu. De precieze naam en weergave kunnen per distributie verschillen.

> [!TIP]
> **LTS** staat voor _Long Term Support_ en betekent dat een versie langere tijd updates krijgt. Deze versies van het besturingssysteem zijn ideaal voor servers en voor gebruikers die een stabiele, langdurig ondersteunde installatie willen.

Volg de aanwijzingen van de installer:

1. Maak verbinding met het internet via WiFi of Ethernet
2. Kies de geprefereerde taal voor jouw systeem
3. Kies de regio en tijdzone
4. Kies de juiste toetsenbordindeling

## Bootloader

De bootloader is het programma dat voor het besturingssysteem opstart om je de keuze te geven met welk OS je de computer wilt besturen. Er zijn doorgaans veel verschillende bootloaders, met elk een eigen manier van werken en een eigen voorkeur voor verschillende systemen.

> [!TIP]
> Ben je wat onzeker over deze keuze? Bekijk dan de workshop [**Bootloaders**](Bootloaders.md).

## Partities

Bij de keuze voor de schijf- of partitie-indeling zijn er meerdere opties. Afhankelijk van jouw gebruiksdoeleinden kunnen we hier de juiste keuze maken. Kies een optie hieronder om verder te gaan voor jouw situatie.

### Optie A: Dual boot (Linux naast Windows)

Als de installer Windows herkent, kies dan **Installeer Linux naast Windows** (**Install Linux alongside Windows**).

Als die optie niet beschikbaar is of de installer geeft een foutmelding, kun je mogelijk **Iets anders** of **Manueel instellen** (**Something else** of **Manual Partitioning**) kiezen om de partities handmatig te configureren.

#### Manuele partitionering

##### Eerste partitie (EFI)

De eerste partitie is voorbehouden voor de bootloader en is essentieel voor elk besturingssysteem dat een dual-boot wilt gebruiken. Hierin zal het programma komen dat mee opstart wanneer de computer wordt aangezet. Deze partitie is nodig zodat de computer weet welke besturingssysteeminstellingen moeten worden geladen.

Volg deze stappen:

1. Selecteer de **Unallocated space** die je in Windows hebt gemaakt. Controleer of de grootte overeenkomt met de grootte die jij aan je Linux-besturingssysteem wilt geven.
2. Klik op **Create**
3. Geef als grootte **4096 MB** in
4. Kies als bestandssysteem **FAT32**
5. Geef als mountpoint **/boot** in
6. Kies als vlag **boot**

##### Tweede partitie

1. Selecteer opnieuw de **Unallocated space**. De vorige grootte zou nu verkleind moeten zijn met 4 GB.
2. Klik op **Create**
3. Verander het bestandssysteem niet
4. Mount deze partitie door **/** in te geven
5. Kies geen vlag

Controleer je keuzes zorgvuldig en bevestig daarna de installatie.

### Optie B: Single boot (Linux als enige besturingssysteem)

Kies **Schijf wissen en Linux installeren** (of **Erase disk and install Linux**) als je Linux als enige besturingssysteem op de gekozen schijf wilt gebruiken.

> [!CAUTION]
> Deze optie verwijdert alle gegevens op de geselecteerde schijf, waaronder Windows en persoonlijke bestanden. Controleer zorgvuldig welke schijf is geselecteerd en zorg vooraf voor een back-up.

## Desktopomgeving

Sommige installers vragen welke desktopomgeving je wilt gebruiken. In deze guide zullen we kiezen voor **KDE Plasma**, een op Wayland-gebaseerde windowmanager die een flexibele omgeving en hogere snelheid biedt in vergelijking met sommige andere desktopomgevingen.

> [!TIP]
> Ben je wat onzeker over deze keuze? Volg dan de guide over [**Desktops**](Desktops.md).

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
> Als je hetzelfde wachtwoord voor root wilt gebruiken, vink je de optie **Use the same password for root** aan.

## Afronding en eerste start

Nu we alle opties correct hebben aangeduid, kunnen we de installatie starten. Wacht tot deze is voltooid, verbreek de internetverbinding niet en zet de computer niet uit.

De duur van de installatie verschilt per computer en distributie. Kies **Nu herstarten** (of de vergelijkbare optie) als de installer hierom vraagt. Verwijder de USB-stick als het scherm zwart is en je computer opnieuw opstart.

## Conclusie

Linux is nu geïnstalleerd. Bij een dual-boot toont de computer doorgaans een opstartmenu waarin je Linux of Windows kunt kiezen. Als dat menu niet verschijnt, open dan het opstartmenu van je computer en controleer of de juiste bootoptie is geselecteerd. Als je Linux enkel als hoofdbesturingssysteem hebt geïnstalleerd, start de computer direct in Linux op.

Je hebt nu een basisinstallatie van Linux draaien. Vanaf hier kun je je systeem verder personaliseren, software installeren en ontdekken welke tools en toepassingen het beste bij jouw workflow passen.

## FAQ

### Waarom verschijnt mijn USB-stick niet in het opstartmenu?

Controleer of de USB-stick correct is geflasht, of deze is aangesloten en of de BIOS/UEFI het juiste bootmedium ondersteunt. Soms moet je in de BIOS/UEFI handmatig de USB-stick als opstartoptie selecteren.

### Hoe weet ik of mijn computer UEFI of BIOS gebruikt?

Je kunt dit meestal controleren in de BIOS/UEFI-instellingen. UEFI is de modernere standaard en wordt meestal aangeduid als “UEFI”. BIOS is de oudere standaard. Als je de USB-stick met “UEFI” ziet in het opstartmenu, gebruik je waarschijnlijk UEFI.

### Wat als BitLocker voorkomt dat ik Linux start?

Schakel BitLocker uit via Windows. Neem ook de recovery key van je Microsoft-account mee als je de code niet meer weet.

### Wat als de installer Windows niet herkent?

Controleer of je voldoende vrije ruimte hebt gemaakt. Als je dat niet hebt gedaan, maak dan eerst ruimte vrij in Windows. Als de installer nog steeds niet herkent dat er een Windows-installatie aanwezig is, kun je de partities handmatig configureren.

### Hoe kies ik de juiste partitie-indeling?

Bij dual-boot is de keuze meestal: Linux naast Windows. Bij een nieuwe installatie zonder Windows kies je vaak “Schijf wissen en Linux installeren”. Voor gevorderde gebruikers is handmatige partitionering mogelijk, maar dat is meestal niet nodig voor beginners.

### Wat als ik later Windows opnieuw wil installeren?

Dan moet je de bootloader van Linux opnieuw configureren of de Windows-installatie opnieuw uitvoeren. De volgorde is belangrijk: als je dual-boot gebruikt, is het meestal verstandig om eerst Windows te installeren en daarna Linux.

### Is Secure Boot altijd uitgeschakeld nodig?

Nee. Niet voor elke distributie. Schakel Secure Boot alleen uit als de documentatie van je gekozen distro dat aangeeft of als het systeem niet wil booten.

### Wat als ik Linux later weer wilt verwijderen?

Dat hangt af van hoe je hebt geïnstalleerd. Als je dual-boot gebruikt, kun je de Linux-partitie later verwijderen en de vrije ruimte teruggeven aan Windows. In sommige gevallen moet je de bootloader opnieuw configureren.

> [!NOTE]
> Bij andere vragen kun je langskomen bij het IT-Lab, waar studenten en lectoren klaarstaan om jou zo snel en zo goed mogelijk te helpen met problemen. Kom gerust eens langs!
