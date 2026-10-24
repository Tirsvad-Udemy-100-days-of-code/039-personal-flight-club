[English](Home) · [Dansk](Home-da) · **Bahasa Malaysia**

# Personal Flight Club

Pencari tawaran penerbangan murah dari hari ke-39 kursus Udemy 100 Days of Code. Program ini membaca destinasi dan had harga daripada Google Sheet, mencari penerbangan pergi-balik termurah untuk enam bulan akan datang dan menghantar mesej WhatsApp apabila harga lebih rendah daripada had.

## Cara ia berfungsi

1. Baca baris (bandar, kod IATA, harga terendah) daripada helaian melalui Sheety.
2. Cari penerbangan pergi-balik termurah dari esok hingga enam bulan lagi untuk setiap baris, dengan SerpAPI Google Flights atau perkhidmatan penerbangan olok-olok (mock) kursus.
3. Jika harga lebih rendah daripada harga terendah dalam helaian, kemas kini helaian dan hantar mesej WhatsApp dengan harga, kedua-dua kod lapangan terbang dan kedua-dua tarikh.

## Contoh larian dengan data mock

![Contoh larian dengan data mock](https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/raw/branch/main/docs/images/sample-run.png)

Seterusnya: [Bermula](Getting-Started-ms)
