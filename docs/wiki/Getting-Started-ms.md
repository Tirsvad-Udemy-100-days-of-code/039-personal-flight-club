[English](Getting-Started) · [Dansk](Getting-Started-da) · **Bahasa Malaysia**

# Bermula

## Keperluan

- Python 3.13 atau lebih baharu
- Projek Sheety untuk salinan Google Sheet anda (pengesahan Bearer, PUT dihidupkan)
- Kunci SerpAPI atau kelayakan perkhidmatan penerbangan mock
- Pilihan: `pywhatkit`, pelayar dan sesi WhatsApp Web yang telah log masuk

## Pemasangan

Cipta persekitaran maya setempat, naik taraf pip dan pasang projek:

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

## Konfigurasi

Salin `.env.example` ke `.env` dan isi nilainya. Jangan sekali-kali commit `.env`. Kekalkan 3 hingga 5 destinasi dalam helaian supaya kekal dalam had percuma.

| Pemboleh ubah | Maksud |
| --- | --- |
| `SHEETY_ENDPOINT` | Endpoint helaian `prices` |
| `SHEETY_TOKEN` | Token Bearer projek Sheety |
| `FLIGHT_PROVIDER` | `serpapi` atau `mock` |
| `SERPAPI_API_KEY` | Kunci SerpAPI |
| `MOCK_FLIGHTS_APP_ID`, `MOCK_FLIGHTS_APP_KEY` | Kelayakan perkhidmatan penerbangan mock |
| `WHATSAPP_NUMBER` | Nombor anda dengan kod negara |

## Jalankan

Mulakan program. Tanpa nombor WhatsApp atau `pywhatkit`, mesej dicetak sebagai ganti.

```bash
python -m flight_club
```

## Ujian

Ujian tidak menggunakan rangkaian dan tidak membaca `.env` anda.

```bash
python -m pytest
```

![Larian ujian](https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/raw/branch/main/docs/images/tests-run.png)
