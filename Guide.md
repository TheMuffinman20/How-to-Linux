# Introductie

Welkom allemaal! Ik ben Thibo Daelman, student in het tweede jaar Toegepaste Informatica, en vandaag begeleid ik jullie door een workshop waarin we Linux installeren op onze computer. Tijdens deze sessie volgen we een vast stappenplan, aangevuld met uitleg zodat je precies begrijpt wat we doen en waarom Linux zo'n krachtig en veelzijdig besturingssysteem is.

In deze workshop installeren we Linux naast je huidige besturingssysteem. Dit heet een dual-boot. Het algemene stappenplan blijft hetzelfde, maar tijdens de installatie voeren we enkele specifieke aanpassingen uit om beide systemen veilig naast elkaar te laten bestaan.

## Benodigdheden

- Een USB-stick van minstens 8 GB
- Een stabiele internetverbinding (WiFi of Ethernet)

> Let op: alle gegevens die momenteel op de USB-stick staan, worden volledig gewist en kunnen niet worden hersteld.

> Belangrijk: maak een back-up. Voor je begint, zorg je best voor een back-up van Windows (of je huidige OS) én alle belangrijke bestanden. Hoewel we zorgvuldig te werk gaan, kan een fout tijdens de installatie leiden tot dataverlies.

# Setup

## Stap 1: Download de ISO

Het leukste deel van deze workshop is kiezen welke distro je graag zou willen gebruiken. Als je nogal besluiteloos bent en niet goed weet waarvoor elke distro dient of hoe ze eruit zien, kun je best de andere workshop "How to pick my distro" herbekijken. Wanneer je besloten hebt welke distro je graag zou willen gebruiken of testen, zul je deze moeten downloaden als ISO-bestand.

Volg daarvoor onderstaande stappen:

- Ga naar de officiële webpagina: https://ubuntu.com/download/desktop
- Download de juiste ISO voor je processortype (Intel/AMD64)

## Stap 2: Download het hulpprogramma

Om een Linux-ISO op een USB-stick te plaatsen, hebben we een speciaal hulpprogramma nodig. Een ISO-bestand kan namelijk niet zomaar gekopieerd worden; het moet correct "geflasht" worden zodat de USB-stick opstartbaar wordt.

Hieronder overlopen we drie veelgebruikte tools, elk met hun eigen sterktes en doelpubliek.

### BalenaEtcher

BalenaEtcher is beschikbaar voor Windows, macOS en Linux, wat het een populaire keuze maakt. Het programma blinkt uit in eenvoud: je selecteert de ISO, kiest je USB-stick en Balena doet de rest. De keerzijde van die eenvoud is dat er weinig geavanceerde instellingen beschikbaar zijn, waardoor je als gebruiker minder controle hebt over het flashproces.

- Ga naar de officiële website: https://etcher.balena.io/
- Download de meest recente versie

### Rufus

Rufus is het hulpprogramma dat we in deze workshop zullen gebruiken. Het is een uitstekende allrounder: snel, betrouwbaar en voorzien van extra opties die handig zijn bij het installeren van Linux in een dual-bootomgeving. Hoewel Rufus alleen beschikbaar is voor Windows, blijft het een van de meest gebruikte tools. De interface is eenvoudig, maar biedt toch voldoende instellingen voor wie meer controle wil.

- Ga naar de officiële website: https://rufus.ie/nl/#download
- Download de nieuwste versie voor jouw processortype (Intel/AMD64)

### Ventoy

Ventoy is het meest geavanceerde programma in deze lijst. In plaats van telkens een USB-stick opnieuw te moeten flashen, maakt Ventoy een speciale omgeving waarin je simpelweg ISO-bestanden kunt kopiëren. Het programma geeft de gebruiker veel vrijheid, maar verwacht ook dat je goed weet wat je doet. Daarom is Ventoy vooral geschikt voor ervaren gebruikers die meerdere systemen willen beheren of testen.

- Ga naar de officiële website: https://www.ventoy.net/en/download.html
- Download de nieuwste versie voor jouw processortype (Intel/AMD64)

## Stap 3: USB flashen

Plaats eerst de USB-stick die je wilt gebruiken in je computer. Controleer dat er geen belangrijke bestanden op staan, want tijdens het flashen wordt de volledige inhoud definitief verwijderd. Open daarna het gekozen hulpprogramma (in deze workshop: Rufus) en volg de stappen hieronder zorgvuldig:

- Selecteer de USB om te flashen onder Apparaat
- Selecteer de ISO door op SELECTEREN te klikken
- Negeer de grootte van persistente partitie, doelsysteem en volumelabel
- Selecteer als bestandssysteem GPT
- Negeer clustergrootte

Controleer nog een laatste keer of je de correcte USB-stick geselecteerd hebt voordat je de flash initialiseert. Zorg er ook voor dat alle instellingen geselecteerd zijn zoals hierboven aangegeven.

- Klik op STARTEN

Wacht tot de tool klaar is met schrijven van het bestand, daarna kun je hem veilig verwijderen van de computer. Goed gedaan, je hebt nu een zogeheten "Live USB" aangemaakt!

> Extra: als je de USB weer wilt gebruiken om data op te slaan na de volledige dual-boot, kun je hem in de computer inpluggen en via Windows Verkenner formatteren naar FAT32 of exFAT. Dit zal opnieuw alle data wissen die werd geschreven door het hulpprogramma, en de USB weer klaarmaken voor dataopslag.

# Schijfruimte vrijmaken

## Dual boot

Wanneer je Linux naast Windows wilt installeren, moet je eerst vrije ruimte voorzien op je harde schijf of SSD. Dat doen we door de bestaande Windows-partitie te verkleinen zodat er plaats ontstaat voor Linux. Windows blijft gewoon werken op zijn eigen partitie, terwijl Linux later geïnstalleerd wordt in de vrijgemaakte ruimte.

- Zoek in het Start-menu naar Schijfbeheer (Create and format hard disk partitions)
- Klik met de rechtermuisknop op de hoofdpartitie (meestal de C:-schijf)
- Kies Volume verkleinen (Shrink Volume)
- Geef aan hoeveel ruimte je wilt afstaan aan Linux
  - Minimaal 50 GB
  - 100 GB is aangeraden
- Klik op Verkleinen (Shrink)

Als alles goed is, verschijnt nu een blok Niet-toegewezen ruimte (Unallocated space). Je hoeft hier geen nieuwe partitie van te maken — Linux zal dit tijdens de installatie zelf correct indelen. Je mag Schijfbeheer nu sluiten.

## Single boot

Als je ervoor kiest om enkel Linux te installeren, hoef je geen ruimte vrij te maken in Windows. Tijdens de Linux-installatie kun je ervoor kiezen om de volledige schijf te gebruiken.

> Let op: dit verwijdert alle Windows-data permanent.

Wil je later Windows opnieuw installeren, dan moet je weten dat Windows de neiging heeft om de bootloader te overschrijven. Daarom installeer je in de praktijk meestal:

1. Eerst Windows
2. Daarna Linux

Bij single-boot maakt dit niet uit, maar bij dual-boot is de volgorde belangrijk.

# Opstartomgeving

Je hebt nu een Live USB met daarop de Linux-ISO, én een stuk niet-toegewezen ruimte op je schijf waar Linux straks geïnstalleerd kan worden. Voor we kunnen opstarten vanaf de USB, moeten we nog twee belangrijke zaken controleren: BitLocker en de bootvolgorde.

## BitLocker

BitLocker is een beveiligingsfunctie van Windows die je systeempartitie kan versleutelen. Wanneer BitLocker merkt dat er iets verandert aan de opstartomgeving (zoals het gebruik van een andere schijf, een gewijzigde bootvolgorde of het opstarten via USB), kan Windows vragen om een herstelcode. Dit is een beveiligingsmaatregel om te voorkomen dat iemand jouw Windows-schijf uitleest via een ander besturingssysteem zoals Linux.

Schakel BitLocker uit met volgende stappen:

- Zoek in het Start-menu naar Apparaatversleuteling (Device Encryption)
- Schakel dit uit

Het uitschakelen van BitLocker kan enige tijd duren, afhankelijk van de grootte van je schijf, maar je kunt het apparaat in de tussentijd wel blijven gebruiken.

Ben je BitLocker vergeten uit te schakelen?

Geen paniek. Als BitLocker geactiveerd wordt tijdens het opstarten, zal Windows vragen om een herstelcode. Deze kun je terugvinden via:

- https://account.microsoft.com/devices/recoverykey
- Log in met hetzelfde Microsoft-account dat je op de computer gebruikt
- Zoek de herstelcode die overeenkomt met jouw apparaat
- Voer de code in op de computer

Daarna kun je verdergaan met de installatie.

## Secure Boot

Secure Boot is een beveiligingsfunctie die ervoor zorgt dat alleen vertrouwde software tijdens het opstarten mag worden geladen. Sommige Linux-installaties werken het beste met Secure Boot ingeschakeld, maar afhankelijk van de distro kan het ook nodig zijn om deze functie tijdelijk uit te schakelen.

Controleer daarom in de BIOS/UEFI-instellingen of Secure Boot wel of niet ondersteund en/of uitgeschakeld moet worden voor je installatie.

# Opstarten vanaf de Live USB

1. Laat de USB-stick in de computer zitten en herstart het systeem.
2. Tijdens het opstarten druk je herhaaldelijk op de bootmenu-toets (meestal F12, F11, F8 of Del, afhankelijk van je moederbord of merk laptop).
3. Kies de USB-stick uit de lijst met opstartapparaten.
4. Je komt nu terecht in het Linux-startmenu. Kies de optie "Try or Install Linux".
5. Je wordt nu opgestart in een tijdelijke Linux-omgeving. Hier kun je het systeem eerst testen. Ben je er klaar voor? Dubbelklik dan op het icoon "Install Linux" op het bureaublad.

## Het installatieproces en partities kiezen

Doorloop de eerste schermen: kies je taal, toetsenbordindeling en verbind eventueel met Wi-Fi.

Bij het scherm Installatietype kies je het type installatie dat je wilt uitvoeren:

## Optie A: Single Boot (Volledige overstap)

- Selecteer "Schijf wissen en Linux installeren" (Erase disk and install Linux)
- Let op: dit verwijdert alle bestaande gegevens, inclusief Windows of oude bestanden
- Klik op "Nu installeren"

## Optie B: Dual Boot (Linux naast Windows)

- Kies de optie "Installeer Linux naast Windows" (Install Linux alongside Windows). De installer herkent Windows automatisch en gebruikt de niet-toegewezen ruimte die je eerder hebt aangemaakt.
- Alternatief: kies "Iets anders" (Something else) als je handmatig partities wilt aanmaken, zoals een gescheiden /boot, / (root) en /home-partitie.
- Controleer de geselecteerde schijf zorgvuldig en klik op "Nu installeren".

# Afronding en eerste start

1. Vul je locatie/tijdzone in.
2. Maak een gebruikersaccount aan met je naam, computernaam, gebruikersnaam en een sterk wachtwoord.
3. Wacht tot de installatie is voltooid (dit duurt meestal 5 tot 15 minuten).
4. Wanneer de melding verschijnt dat de installatie klaar is, klik je op "Nu herstarten".
5. Verwijder de USB-stick wanneer het scherm hierom vraagt en druk op Enter.

## Conclusie

Je computer start nu op in je nieuwe Linux-omgeving. Als je voor een dual-boot hebt gekozen, krijg je bij het opstarten een keuzemenu (GRUB) waarin je kunt kiezen of je Linux of Windows wilt opstarten.
