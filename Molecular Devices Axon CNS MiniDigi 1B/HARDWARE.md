
## Hardware

* U14: Cypress CY7C68013A-56PVXC, SSOP-56
  * EZ-USB FX2LP USB microcontroller
  * https://www.infineon.com/cms/en/product/universal-serial-bus/usb-2.0-peripheral-controllers/ez-usb-fx2lp-fx2g2-usb-2.0-peripheral-controller/cy7c68013a-56pvxc/
* U10: Oscillator
* D2: Activity LED
  * R23: 390R
* U15: Microchip 24AA64T, SO-8
  * EEPROM, 64KBit
  * I2C, 400kHz
  * https://www.microchip.com/en-us/product/24AA64
  * https://ww1.microchip.com/downloads/en/DeviceDoc/21189T.pdf
* U7, U8: Analog Devices AD7685BRMZ, MSOP-10
  * 16-Bit, 250 kSPS analog-to-digital converter with pseudo-differential input
  * https://www.analog.com/en/products/ad7685.html
  * https://www.analog.com/media/en/technical-documentation/data-sheets/AD7685.pdf
* U2: Analog Devices AD8642, SO-8
  * Low power, rail-to-rail output, precision dual JFET operational amplifier
  * https://www.analog.com/en/products/ad8642.html
  * https://www.analog.com/media/en/technical-documentation/data-sheets/AD8641_8642_8643.pdf
  * https://www.analog.com/en/resources/technical-articles/biopotential-electrode-sensors-ecg-eeg-emg.html
* U6: Analog Devices REF198, SO-8
  * 4.096V precision, micropower, low dropout, low voltage reference
  * https://www.analog.com/en/products/ref198.html
  * https://www.analog.com/media/en/technical-documentation/data-sheets/REF19xSeries.pdf
* U11: Texas Instruments TPS3836, SOT-23-5
  * Undervoltage monitor with manual reset and reset time delay
  * https://www.ti.com/product/TPS3836
  * https://www.ti.com/lit/gpn/tps3836
* U13: Texas Instruments LM3940, SOT-223
  * 1A low-dropout regulator for 5V to 3.3V conversion
  * https://www.ti.com/product/LM3940
  * https://www.ti.com/lit/ds/symlink/lm3940.pdf

## Schematic

* input from two BNC connectors connects to amplifier U2 via resistor networks
  * J1 to U2 input A
  * J2 to U2 input B
* U7 and U8 are wired up similarly to one another
  * REF, VDD, IN-, GND, VIO, SDI and CNV are shared
  * VDD is supplied by a filter stage 
  * REF is sourced from U6 and bypassed: by C18 at U7 and C19 at U8
  * SDI is tied to VIO
  * VIO is sourced from U13 and bypassed: by C20 at U7 and C21 at U8
  * IN+ connects to amplifier U2: U7 to output A, U8 to output B
  * thus, U7 samples J1 and U8 samples J2
  * IN- is tied to GND
* VDD supply circuit
  * U1 ("333"), U4, C1, C3, C4, C7, C11, C16, C22, C26, L1, L2 ("560K")
  * connected to USB
* VIO supply circuit
  * U12 ("333"), U5 ("333"), U13, C33, C34, C39, C42, C23
  * connected to USB
* U6 supplies a reference voltage on pin 6, used by U7 and U8 on their REF input
  * input is bypassed by C15 and C17
  * output is bypassed by C27
  * nSLEEP as well as pins 1, 4, 7 and 8 are not connected
* U14 connects...
  * to U7 SDO via R13 (100R) on pin 40
  * to U8 SDO via R14 (100R) on pin 47
  * to CNV via R21 (100R) on pin 31
  * to SCK via R22 (100R) on pin 32
  * to U11 output on pin 49
  * to U11 supply on pin 50
  * to D2 on pin 27
  * to U15...
* EEPROM
  * WP is controlled by U14 pin 28
  * SCL connects to U14 pin 22
  * SDA connects to U14 pin 23
  * A0, A1 and A2 are tied to GND
* Undervoltage lockout circuit
  * U11, D1, R17, C30
