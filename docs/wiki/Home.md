**English** · [Dansk](Home-da) · [Bahasa Malaysia](Home-ms)

# Personal Flight Club

A flight-deal finder from Day 39 of Udemy's 100 Days of Code. It reads destinations and price limits from a Google Sheet, finds the cheapest return flight for the next six months and sends a WhatsApp message when a price is below the limit.

## How it works

1. Read the rows (city, IATA code, lowest price) from the sheet through Sheety.
2. Search the cheapest return flight from tomorrow to six months ahead for every row, with SerpAPI Google Flights or the course's mock flight service.
3. If the price is lower than the sheet's lowest price, update the sheet and send a WhatsApp message with the price, both airport codes and both dates.

## A sample run with mock data

![A sample run with mock data](https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/raw/branch/main/docs/images/sample-run.png)

Next: [Getting started](Getting-Started)
