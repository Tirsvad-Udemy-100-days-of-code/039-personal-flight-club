[English](Home) · **Dansk** · [Bahasa Malaysia](Home-ms)

# Personal Flight Club

En finder af billige flybilletter fra dag 39 i Udemys 100 Days of Code. Programmet læser destinationer og prisgrænser fra et Google Sheet, finder den billigste returflyvning de næste seks måneder og sender en WhatsApp-besked, når en pris er under grænsen.

## Sådan virker det

1. Læs rækkerne (by, IATA-kode, laveste pris) fra arket via Sheety.
2. Søg efter den billigste returflyvning fra i morgen til seks måneder frem for hver række, med SerpAPI Google Flights eller kursets mock-flyservice.
3. Hvis prisen er lavere end arkets laveste pris, opdateres arket, og der sendes en WhatsApp-besked med pris, begge lufthavnskoder og begge datoer.

## Et eksempel på en kørsel med mock-data

![Et eksempel på en kørsel med mock-data](https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/raw/branch/main/docs/images/sample-run.png)

Næste: [Kom i gang](Getting-Started-da)
