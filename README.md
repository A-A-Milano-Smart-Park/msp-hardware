# Milano Smart Park Hardware

Hardware PCB files for the ESP32-based Milano Smart Park project

## Note: The PCB v7 files are old and deprecated. New design files need to be made to reflect the current state of the project!

- ESP32-DevkitC with ESP32-WROVER-B module with attached:

	- OLED Display SH1106 1.3" 128X64 (IIC)
	- SD Card Module
	- Adafruit's BME680 sensor (IIC)
	- Plantower's PMS5003 Air Quality sensor (Serial)
	- seeed's Grove Multichannel Gas Sensor MiCS-6814 v1.0 (IIC) (With custom modifications)
		+ currently implementing the new MultiGas sensor v2.0
	- Winsen's ZE25-O3 Ozone sensor (Analog, using ESP32's own ADC)
	
### Quick schematic of the ESP32 /w WROVER-B devkit:  
						   _____________________
						  |                     |
						o-|-3V3             GND-|-o
						o-|-EN           GPIO23-|-o --- MOSI SDCARD
						o-|-VP(GPIO36)   GPIO22-|-o --- IIC SCL
						o-|-VN(GPIO39)(GPIO1)TX-|-o (UART0 debug)
						o-|-GPIO34    (GPIO3)RX-|-o (UART0 debug)
		 ZE25-O3 D0 --- o-|-GPIO35       GPIO21-|-o --- IIC SDA
         ZE25-O3 A0 --- o-|-GPIO32          GND-|-o
						o-|-GPIO33       GPIO19-|-o --- MISO SDCARD
						o-|-GPIO25       GPIO18-|-o --- SCK SDCARD
						o-|-GPIO26       GPIO5 -|-o --- CS SDCARD
						o-|-GPIO27       GPIO17-|-x reserved, don't use!
		 PMS5003 RX --- o-|-GPIO14       GPIO16-|-x reserved, don't use!
		 PMS5003 TX --- o-|-GPIO12       GPIO4 -|-o
						o-|-GND          GPIO0 -|-o
						o-|-GPIO13       GPIO2 -|-o
   reserved, don't use! x-|-D2(SD)       GPIO15-|-o
   reserved, don't use! x-|-D3(SD)       (SD)D1-|-x reserved, don't use!
   reserved, don't use! x-|-CMD(SD)      (SD)D0-|-x reserved, don't use!
                VCC --- o-|-5V          (SD)CLK-|-x reserved, don't use!
						  |                     |
                          |      _______        |
                          |     |       |       |
                          |     |       |       |
                          |_____|       |_______|
                                |_______|