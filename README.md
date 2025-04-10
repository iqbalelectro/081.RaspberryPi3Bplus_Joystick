 
# Raspberry Pi Joystick Control with ADS1115

Proyek ini menggunakan Raspberry Pi untuk membaca input dari joystick menggunakan modul ADS1115. Dalam panduan ini, Anda akan belajar cara menginstal pustaka yang diperlukan, membuat _virtual environment_, menghubungkan perangkat keras, dan menjalankan skrip Python untuk membaca nilai joystick.

## Daftar Isi

1. [Persyaratan](#persyaratan)
2. [Instalasi Pustaka](#instalasi-pustaka)
3. [Membuat Virtual Environment](#membuat-virtual-environment)
4. [Pengkabelan (Wiring)](#pengkabelan-wiring)
5. [Menjalankan Skrip](#menjalankan-skrip)

## Persyaratan

- Raspberry Pi (model apa pun)
- Joystick analog
- Modul ADS1115
- Kabel jumper
- Python 3.x

## Instalasi Pustaka

1. **Perbarui sistem Anda**:
sudo apt update
sudo apt upgrade

2. **Instal pip dan pustaka yang diperlukan**:
sudo apt install python3-pip python3-dev

3. **Instal pustaka Python yang diperlukan**:
pip install Adafruit-ADS1x15 RPi.GPIO


## Membuat Virtual Environment

1. **Install `venv` jika belum terinstal**:
sudo apt install python3-venv

2. **Buat virtual environment**: (ketik di folder yang sama)
python3 -m venv venvJoystick

3. **Aktifkan virtual environment**:
source venvJoystick/bin/activate

4. **Instal pustaka dalam virtual environment**:
pip install Adafruit-ADS1x15 RPi.GPIO

 
## Pengkabelan (Wiring)

Berikut adalah cara menghubungkan joystick dan modul ADS1115 ke Raspberry Pi:

### Komponen yang Diperlukan

- Joystick dengan 5 pin (VCC, GND, X, Y, Button)
- Modul ADS1115 dengan 4 pin (VCC, GND, SDA, SCL)
- Raspberry Pi dengan pin GPIO

### Skema Pengkabelan

| Joystick Pin | ADS1115 Pin | Raspberry Pi Pin |
|--------------|-------------|-------------------|
| VCC          | VCC         | 3.3V              |
| GND          | GND         | GND               |
| X            | A0          | SDA (GPIO 2)      |
| Y            | A1          | SCL (GPIO 3)      |
| Button       | GPIO16      | GPIO16            |

### Contoh Wiring

Joystick VCC -> Raspberry Pi 3.3V
Joystick GND -> Raspberry Pi GND
Joystick X -> ADS1115 A0
Joystick Y -> ADS1115 A1
Joystick Button -> Raspberry Pi GPIO16
ADS1115 SDA -> Raspberry Pi SDA (GPIO 2)
ADS1115 SCL -> Raspberry Pi SCL (GPIO 3)


## Menjalankan Skrip

1. **Pastikan virtual environment aktif**:
source venvJoystick/bin/activate

2. **Jalankan skrip Python untuk membaca nilai joystick**:
python 081.RaspberryPi3Bplus_Joystick.py

3. **Amati output di terminal**: Anda akan melihat nilai sumbu X dan Y serta status tombol joystick.


## Kesimpulan

Anda sekarang telah berhasil mengatur proyek joystick dengan Raspberry Pi menggunakan modul ADS1115. Anda dapat mengembangkan proyek ini lebih lanjut dengan menambahkan fungsionalitas tambahan sesuai kebutuhan.
