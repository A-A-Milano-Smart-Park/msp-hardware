# Milano Smart Park Hardware

Hardware PCB files for the ESP32-based Milano Smart Park project

## Note: The PCB v7 files are old and deprecated. New design files need to be made to reflect the current state of the project!

- ESP32-DevkitC with ESP32-WROVER-B module with attached:

	- Adafruit's BME680 sensor (IIC)
	- Adafruit's PMS5003 Air Quality sensor (RS232 Serial)
	- seeed's Grove Multichannel Gas Sensor MiCS-6814 v1.0 (IIC) (With custom modifications)
		+ currently implementing the new MultiGas sensor v2.0
	- Winsen's ZE25-O3 Ozone sensor (Analog, using ESP32's own ADC)
	- OLED Display SH1106 1.3" 128X64 (IIC)
	
### Quick schematic of the ESP32 devkit:  
                         ____________________
                        |                     |
               3V3--- o-|-3V3             GND-|-o
                      o-|-EN              D23-|-o --- MOSI SDCARD
                      o-|-VP(D36)         D22-|-o --- SCL OLED + BME + MICS6814
                      o-|-VN(D39)     (D1)TX0-|-o
                      o-|-D34         (D3)RX0-|-o
     ZE25-O3 D0 ----- o-|-D35             D21-|-o --- SDA OLED + BME + MICS6814
     ZE25-O3 A0 ----- o-|-D32             GND-|-o
                      o-|-D33             D19-|-o --- MISO SDCARD + OLED
                      o-|-D25             D18-|-o --- SCK SDCARD
                      o-|-D26             D5 -|-o --- CS SDCARD
                      o-|-D27             D17-|-o  -x-x- protected, don't use
       RX SENS PM --- o-|-D14             D16-|-o  -x-x- protected, don't use
       TX SENS PM --- o-|-D12             D4 -|-o
                      o-|-GND             D0 -|-o
                      o-|-D13             D2 -|-o
                      o-|-SD2  ---xxx     D15-|-o  -x-x- protected, don't use
                      o-|-SD3  ---xxx---  SD1-|-o  -x-x- protected, don't use
                      o-|-CMD  ---xxx---  SD0-|-o  -x-x- protected, don't use
       VCC-SD+OLED--- o-|-5Vin    xxx---  CLK-|-o  -x-x- protected, don't use
                        |                     |
                        |      _______        |
                        |     |       |       |
                        |     |       |       |
                        |_____|       |_______|
                              |_______|
							  
