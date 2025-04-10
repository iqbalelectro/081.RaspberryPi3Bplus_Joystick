import time
from time import sleep
import Adafruit_ADS1x15
import RPi.GPIO as GPIO
from enum import Enum

class Arah(Enum):
    KIRI = 1
    KANAN = 2
    ATAS = 3
    BAWAH = 4

# Inisialisasi ADS1115
ADC = Adafruit_ADS1x15.ADS1115()

# Set gain ke ±4.096V (sesuaikan jika perlu)
GAIN = 2 / 3

# Tentukan saluran ADC untuk sumbu joystick
X_CHANNEL = 0
Y_CHANNEL = 1

# Tentukan pin GPIO untuk tombol tekan
BUTTON_PIN = 16  # GPIO16

# Inisialisasi pin GPIO untuk tombol
GPIO.setmode(GPIO.BCM)
GPIO.setup(BUTTON_PIN, GPIO.IN, pull_up_down=GPIO.PUD_UP)

# Inisialisasi variabel untuk status tombol sebelumnya
prev_button_state = GPIO.HIGH

def main():
    global prev_button_state
    
    try:
        while True:
            x_value = ADC.read_adc(X_CHANNEL, gain=GAIN)
            y_value = ADC.read_adc(Y_CHANNEL, gain=GAIN)
            button_state = GPIO.input(BUTTON_PIN)

            print(f"X-axis Value: {x_value}, Y-axis Value: {y_value}, Button State: {button_state}")

            # Menentukan arah berdasarkan nilai joystick
            if x_value <= 100:
                my_arah = Arah.KIRI
                print("Arah Kiri")
                print(my_arah)
                print(my_arah.name)
                print(my_arah.value)

            elif x_value >= 17000:
                my_arah = Arah.KANAN
                print("Arah Kanan")
                print(my_arah)
                print(my_arah.name)
                print(my_arah.value)

            if y_value <= 100:
                my_arah = Arah.ATAS
                print("Arah Atas")
                print(my_arah)
                print(my_arah.name)
                print(my_arah.value)

            elif y_value >= 17000:
                my_arah = Arah.BAWAH
                print("Arah Bawah")
                print(my_arah)
                print(my_arah.name)
                print(my_arah.value)

            # Deteksi event tombol tekan (transisi dari HIGH ke LOW)
            if prev_button_state == GPIO.HIGH and button_state == GPIO.LOW:
                print("Button Pressed!")

            # Deteksi event tombol dilepas (transisi dari LOW ke HIGH)
            if prev_button_state == GPIO.LOW and button_state == GPIO.HIGH:
                print("Button Released!")

            prev_button_state = button_state
            
            sleep(0.1)  # Delay sebelum pembacaan berikutnya

    except KeyboardInterrupt:
        print("Program dihentikan oleh pengguna.")
    finally:
        GPIO.cleanup()

if __name__ == "__main__":
    main()
