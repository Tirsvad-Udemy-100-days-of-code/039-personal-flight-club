**English** · [Dansk](Getting-Started-da) · [Bahasa Malaysia](Getting-Started-ms)

# Getting started

## Requirements

- Python 3.13 or newer
- A Sheety project for your copy of the Google Sheet (Bearer authentication, PUT enabled)
- A SerpAPI key or the mock flight service credentials
- Optional: `pywhatkit`, a browser and a logged-in WhatsApp Web session

## Setup

Create a local virtual environment, upgrade pip and install the project:

```powershell
py -3.13 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -e ".[dev]"
```

```bash
python3.13 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -e ".[dev]"
```

## Configuration

Copy `.env.example` to `.env` and fill in the values. Never commit `.env`. Keep 3 to 5 destinations in the sheet to stay inside the free tiers.

| Variable | Meaning |
| --- | --- |
| `SHEETY_ENDPOINT` | Endpoint of the `prices` sheet |
| `SHEETY_TOKEN` | Bearer token of the Sheety project |
| `FLIGHT_PROVIDER` | `serpapi` or `mock` |
| `SERPAPI_API_KEY` | SerpAPI key |
| `MOCK_FLIGHTS_APP_ID`, `MOCK_FLIGHTS_APP_KEY` | Mock flight service credentials |
| `WHATSAPP_NUMBER` | Your own number with country code |

## Run

Start the program. Without a WhatsApp number or `pywhatkit` the message is printed instead.

```bash
python -m flight_club
```

## Tests

The tests use no network and never read your `.env`.

```bash
python -m pytest
```

![Test run](https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/raw/branch/main/docs/images/tests-run.png)
