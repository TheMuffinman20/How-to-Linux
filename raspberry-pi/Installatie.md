## Raspberry Pi Imager

Raspberry Pi Imager is een tool om SD-kaarten te flashen, zoals Rufus en Ventoy dit doen voor USB-sticks. Hieronder geven we de exacte instellingen die je moet gebruiken om het correcte besturingssysteem en andere te installeren.

Download de laatste versie op de officiele website: https://www.raspberrypi.com/software/

Open de software en kies de onderstaande instellingen:

- Device: Raspberry Pi 5
- OS: Raspberry Pi OS (other)
    - Raspberry Pi Full (64-bit)
    - Raspberry Pi OS Lite (64-bit)
- Opslagapparaat:
    - Hostname: Raspi
    - Username: "GEBRUIKERSNAAM"
    - Password: "WACHTWOORD"

- Localisation:
    - Location: Belgium
    - Language: English (US)
    - Time: Brussels (GMT+1)
    - Keyboard: Qwerty (US)
    
    - WiFi (optioneel)
    - Remote access (SSH)

## Installatie

### Flatpak

Flatpak is een universeel software-installatie- en distributiesysteem voor Linux. Het stelt ontwikkelaars in staat om één applicatie te maken die op vrijwel elke Linux-distributie werkt, ongeacht het onderliggende pakketsysteem (zoals apt bij Ubuntu of dnf bij Fedora).

- `sudo apt update`

Vernieuwt de lijst met beschikbare pakketten en versies.

- `sudo apt full-upgrade`

Update alle geinstalleerde pakketten naar de meest recente versie als die beschikbaar is.

> [!NOTE]
> Bij een versie installatie op een Raspberry Pi is dit aanbevolen, maar het kan enige tijd duren.

- `sudo apt install flatpak`

Installeert flatpak als software-installatieprogramma, waardoor we later Azahar kunnen installeren.

- `flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`

Dit commando voegt Flathub toe als een nieuwe repository voor Flatpak op je Linux-systeem. Na het uitvoeren van dit commando kun je duizenden apps van Flathub zoeken en installeren.

- `flatpak --version`

Controleert en toont de huidige geinstalleerde versie van flatpak.

- `flatpak remotes`

Controleert en toont de toegevoegde repositories.

### Azahar

Azahar is een gratis en open-source Nintendo 3DS-emulator. Met dit programma boots je de hardware van een Nintendo 3DS na op moderne computers en mobiele apparaten, zodat je 3DS-games kunt spelen en software kunt testen zonder de fysieke spelcomputer nodig te hebben.

- `flatpak install flathub org.azahar_emu.Azahar`

Installeert Azahar via flathub op je computer of apparaat.

- `nano ~/.bashrc`

Opent het bestand `.bashrc` met de teksteditor nano, waarna je onderstaande informatie kunt toevoegen bij de rubriek over aliassen.

```bash
alias ds='flatpak run org.azahar_emu.Azahar & disown'
```

> [!NOTE]
> Dit commando zorgt ervoor dat je met een gekozen alias zoals "ds" de Azahar-applicatie kan opstarten vanuit de terminal. Disown zorgt ervoor dat Azahar niet afsluit als de terminal wordt afgesloten.

- `exec bash`

Vervangt de huidige shell en leest daarbij .bashrc opnieuw in, met de alias de we net hebben meegegeven.

- `ds`

Start Azahar op de achtergrond. Je kunt de terminal blijven gebruiken, en Azahar blijft open als je de terminal sluit.

### Autostart

Op een computer waar we geen enkel ander programma moeten runnen is het handig om Azahar op de starten wanneer de computer aangezet wordt. Hiervoor moeten we de instellingen van de Raspberry Pi aanpassen.

- `sudo raspi-config`

Opent het menu om de Raspberry Pi te configureren. Ga daarna naar `System Options` → `Boot/Auto Login` → `Desktop Autologin` om automatisch in te loggen wanneer de Raspberry opstart.

`mkdir -p ~/.config/autostart`

Maakt de map aan waarin de desktop programma’s zoekt die bij het opstarten moeten draaien. Met `-p` geeft het commando geen fout als de map al bestaat.

`nano ~/.config/autostart/azahar.desktop`

Maakt het autostart-bestand aan. Plak dit erin:

```bash
[Desktop Entry]
Type=Application
Name=Azahar
Exec=flatpak run org.azahar_emu.Azahar
```

Sla op met `Ctrl+O`, `Enter` en sluit af met `Crtl+X`.

> [!NOTE]
> Gebruik hier niet de alias `ds`. Aliassen werken alleen in een terminal waarin `.bashrc` is ingelezen, en niet in autostart-bestanden. Schrijf daarom altijd het volledige commando.

- `sudo reboot`

Herstart het systeem om te kunnen testen of het autostart-bestand werkt.
