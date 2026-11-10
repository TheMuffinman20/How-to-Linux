# FAQ

### Waarom verschijnt mijn USB-stick niet in het opstartmenu?

Controleer of de USB-stick correct is geflasht, of deze is aangesloten en of de BIOS/UEFI het juiste bootmedium ondersteunt. Soms moet je in de BIOS/UEFI handmatig de USB-stick als opstartoptie selecteren.

### Hoe weet ik of mijn computer UEFI of BIOS gebruikt?

Je kunt dit meestal controleren in de BIOS/UEFI-instellingen. UEFI is de modernere standaard en wordt meestal aangeduid als “UEFI”. BIOS is de oudere standaard. Als je de USB-stick met “UEFI” ziet in het opstartmenu, gebruik je waarschijnlijk UEFI.

### Wat als BitLocker voorkomt dat ik Linux start?

Schakel BitLocker uit via Windows. Neem ook de recovery key van je Microsoft-account mee als je de code niet meer weet.

### Wat als de installer Windows niet herkent?

Controleer of je voldoende vrije ruimte hebt gemaakt. Als je dat niet hebt gedaan, maak dan eerst ruimte vrij in Windows. Als de installer nog steeds niet herkent dat er een Windows-installatie aanwezig is, kun je de partities handmatig configureren.

### Hoe kies ik de juiste partitie-indeling?

Bij dual-boot is de keuze meestal: Linux naast Windows. Bij een nieuwe installatie zonder Windows kies je vaak “Schijf wissen en Linux installeren”.

### Wat als ik later Windows opnieuw wil installeren?

Dan moet je de bootloader van Linux opnieuw configureren of de Windows-installatie opnieuw uitvoeren. De volgorde is belangrijk: als je dual-boot gebruikt, is het meestal verstandig om eerst Windows te installeren en daarna Linux.

### Is Secure Boot altijd uitgeschakeld nodig?

Neen, niet voor elke distributie. Schakel Secure Boot alleen uit als de documentatie van je gekozen distro dat aangeeft of als het systeem niet wil booten.

### Wat als ik Linux later weer wil verwijderen?

Dat hangt af van hoe je hebt geïnstalleerd. Als je dual-boot gebruikt, kun je de Linux-partitie later verwijderen en de vrije ruimte teruggeven aan Windows. In sommige gevallen moet je de bootloader opnieuw configureren.

> [!NOTE]
> Bij andere vragen kun je langskomen bij het IT-Lab, waar studenten en lectoren klaarstaan om jou zo snel en zo goed mogelijk te helpen met problemen. Kom gerust eens langs!