# Hardware Pinout and Interfaces

> **Prototype:** Prototype 2 -- Multivariate NIR Sensing Configuration\
> **Controller:** ESP32 DevKit V1\
> **Source:** Prototype 2 circuit schematic supplied with the project\
> **Status:** Pin connections transcribed from the schematic.
> Connections marked *verify* should be checked against the original
> editable schematic or assembled hardware before firmware
> implementation.

------------------------------------------------------------------------

## 1. System Overview

The circuit integrates the following hardware:

  -----------------------------------------------------------------------
  Component               Function                Interface
  ----------------------- ----------------------- -----------------------
  ESP32 DevKit V1         Main controller and     GPIO, I²C
                          sensor coordination     

  ADS1115                 External 16-bit ADC     I²C

  MCP6002                 Dual operational        Analog
                          amplifier / photodiode  
                          signal conditioning     

  BPW34                   NIR photodetection      Analog front end

  850 nm LED              NIR illumination        GPIO-controlled LED
                                                  circuit

  940 nm LED              NIR illumination        GPIO-controlled LED
                                                  circuit

  TMP117                  Temperature measurement I²C

  MAX30102                PPG acquisition         I²C
  -----------------------------------------------------------------------

The digital sensors and ADC are connected to the ESP32 through the I²C
interface shown in the schematic. The MCP6002 conditions the photodiode
signal, which is routed to the ADS1115 analog inputs.

## 2. ESP32 DevKit V1 Pinout

The ESP32 DevKit V1 is the central controller. The schematic shows the
following connections.

  --------------------------------------------------------------------------
  ESP32 signal   GPIO / board   Connected      Function       Notes
                 label          device                        
  -------------- -------------- -------------- -------------- --------------
  D21            GPIO21         ADS1115,       I²C SDA        Shared data
                                TMP117,                       line
                                MAX30102                      

  D22            GPIO22         ADS1115,       I²C SCL        Shared clock
                                TMP30102,                     line; verify
                                TMP117                        net tracing

  3V3            3.3 V          Supply rails   Power          Common 3.3 V
                                and sensor                    supply
                                modules                       

  GND            GND            All modules    Ground         Common ground
                                               reference      
  --------------------------------------------------------------------------

**Important:** The schematic's shared I²C wiring should be checked
carefully before assigning firmware pins. The expected ESP32 DevKit V1
I²C convention is GPIO21 (SDA) and GPIO22 (SCL); confirm both nets
against the original schematic.

Other ESP32 GPIO pins are present in the symbol, but their exact
peripheral assignments are not sufficiently clear in the supplied raster
image. Do not treat unlisted GPIO pins as confirmed connections.

## 3. I²C Bus

The schematic connects the following devices to a common I²C bus:

-   ADS1115 ADC
-   TMP117 temperature sensor
-   MAX30102 PPG sensor

  I²C signal     ESP32 GPIO Connected devices
  ------------ ------------ ---------------------------
  SDA                GPIO21 ADS1115, TMP117, MAX30102
  SCL                GPIO22 ADS1115, TMP117, MAX30102

All devices share the same SDA and SCL lines. Each device must have a
unique I²C address on the bus.

### 3.1 I²C Address Notes

  -----------------------------------------------------------------------
  Device                              Address information
  ----------------------------------- -----------------------------------
  ADS1115                             Configurable through ADDR pin;
                                      confirm its connection and
                                      resulting address

  TMP117                              Depends on ADD0 strap; confirm the
                                      schematic connection

  MAX30102                            Use the device's documented I²C
                                      address
  -----------------------------------------------------------------------

The exact address straps should be verified against the schematic and
the assembled modules. Firmware should scan the bus during initial
bring-up rather than assume an unverified address.

## 4. ADS1115 -- 16-bit ADC

The ADS1115 digitises the analog signal-conditioning output and
communicates with the ESP32 over I²C.

  -----------------------------------------------------------------------
  ADS1115 pin             Signal                  Connection / purpose
  ----------------------- ----------------------- -----------------------
  1                       ADDR                    Address selection;
                                                  verify strap

  3                       GND                     Common ground

  4                       AIN0                    Analog input; trace to
                                                  the corresponding
                                                  amplifier output

  5                       AIN1                    Analog input; trace to
                                                  the corresponding
                                                  amplifier output

  6                       AIN2                    No confirmed external
                                                  connection in the
                                                  supplied schematic

  7                       AIN3                    No confirmed external
                                                  connection in the
                                                  supplied schematic

  8                       VDD                     +3.3 V

  9                       SDA                     Shared I²C SDA

  10                      SCL                     Shared I²C SCL

  2                       ALERT/RDY               No confirmed connection
  -----------------------------------------------------------------------

The schematic appears to route the conditioned analog signal(s) to the
ADS1115 input section. Confirm the exact amplifier-output-to-AIN channel
mapping from the original schematic before defining ADC channel names in
firmware.

## 5. MCP6002 -- Photodiode Signal Conditioning

The MCP6002 is a dual operational amplifier used in the photodiode
signal-conditioning stage.

    MCP6002 pin Signal   Function
  ------------- -------- ---------------------------------
              1 VOUTA    Amplifier A output
              2 VINA−    Amplifier A inverting input
              3 VINA+    Amplifier A non-inverting input
              4 VSS      Ground
              5 VINB+    Amplifier B non-inverting input
              6 VINB−    Amplifier B inverting input
              7 VOUTB    Amplifier B output
              8 VDD      +3.3 V

The BPW34 photodiode is connected to the analog front end. The MCP6002
conditions the resulting signal before it is digitised by the ADS1115.

The schematic also shows passive components around the analog front end,
including resistors and capacitors. Their values and exact roles should
be taken from the complete circuit design rather than inferred from this
pinout document.

## 6. BPW34 Photodiode

  Connection              Function
  ----------------------- -----------------------------------------
  Photodiode terminal 1   Connected to the analog sensing network
  Photodiode terminal 2   Connected to the +3.3 V side as drawn

The photodiode generates a current in response to incident optical
radiation. The analog front end converts and conditions this signal for
ADC acquisition.

**Polarity note:** Confirm the BPW34 symbol orientation and physical
package pinout before assembly or replacement.

## 7. NIR LED Connections

The schematic contains two NIR illumination channels.

  -------------------------------------------------------------------------
  Channel               LED wavelength      Series resistor Control
                                                      shown connection
  --------------- -------------------- -------------------- ---------------
  NIR channel 1                 850 nm           220 Ω (R3) ESP32 control
                                                            net -- GPIO
                                                            mapping to
                                                            verify

  NIR channel 2                 940 nm           220 Ω (R4) ESP32 control
                                                            net -- GPIO
                                                            mapping to
                                                            verify
  -------------------------------------------------------------------------

The LEDs are intended to be activated sequentially so that the optical
response at each wavelength can be acquired separately.

The exact ESP32 GPIO numbers driving the LED circuits are not
confidently legible from the supplied schematic image. Confirm the two
control nets in the editable schematic before implementing LED-control
firmware.

## 8. TMP117 -- Temperature Sensor

The TMP117 is used for skin-temperature measurement.

    TMP117 pin Signal   Connection
  ------------ -------- ---------------------------------
             1 SCL      Shared I²C SCL
             2 GND      Common ground
             3 ALERT    No confirmed connection
             4 ADD0     Address selection; verify strap
             5 V+       +3.3 V
             6 SDA      Shared I²C SDA

The temperature readings are associated with the corresponding NIR and
PPG measurements during data acquisition.

## 9. MAX30102 -- PPG Sensor

The MAX30102 is used to acquire photoplethysmography (PPG) data.

    MAX30102 pin Signal   Connection
  -------------- -------- ----------------------------------------------------------
               1 VDD      +3.3 V as drawn
               2 SCL      Shared I²C SCL
               3 SDA      Shared I²C SDA
               4 NC       No connection
               5 NC       No connection
               6 NC       No connection
               7 NC       No connection
               8 NC       No connection
               9 NC       No connection
              10 NC       No connection
              11 LED+     Supply connection as drawn; verify module implementation
              12 GND      Ground
              13 INT      No confirmed connection
              14 NC       No connection

**Module warning:** The drawing appears to use a MAX30102 device-level
symbol. Commercial breakout boards may expose different pin labels and
may include onboard regulators or level shifting. Match the actual
module documentation before wiring it.

## 10. Power and Ground

The schematic uses a +3.3 V rail and a common ground reference.

  -----------------------------------------------------------------------
  Supply                              Connected sections
  ----------------------------------- -----------------------------------
  +3.3 V                              ESP32 3V3, ADS1115 VDD, TMP117 V+,
                                      MAX30102 supply and analog
                                      circuitry as shown

  GND                                 ESP32, ADS1115, MCP6002, TMP117,
                                      MAX30102 and analog sensing ground
  -----------------------------------------------------------------------

Check the power requirements of the specific MAX30102 breakout board and
the ESP32 board. Do not assume every breakout board is safe to power
directly from 3.3 V without checking its documentation.

## 11. Firmware Interface Summary

The following table is a starting point for firmware development.
Confirm the uncertain mappings before relying on them.

  -----------------------------------------------------------------------
  Firmware          Hardware          Interface         Firmware
  subsystem                                             responsibility
  ----------------- ----------------- ----------------- -----------------
  I²C bus           ADS1115, TMP117,  I²C               Initialise bus
                    MAX30102                            and communicate
                                                        with devices

  Optical           BPW34 + MCP6002 + Analog front      Read digitised
  acquisition       ADS1115           end + I²C         optical
                                                        measurements

  850 nm            850 nm LED        GPIO control      Switch LED and
  illumination                                          coordinate
                                                        measurement

  940 nm            940 nm LED        GPIO control      Switch LED and
  illumination                                          coordinate
                                                        measurement

  Temperature       TMP117            I²C               Read temperature

  PPG               MAX30102          I²C               Acquire red/IR
                                                        PPG samples and
                                                        process as
                                                        required
  -----------------------------------------------------------------------

## 12. Verification Checklist

Before finalising the pinout or writing firmware, verify:

-   [ ] ESP32 GPIO21 is connected to the common SDA net.
-   [ ] ESP32 GPIO22 is connected to the common SCL net.
-   [ ] ADS1115 AIN0/AIN1 connections to the MCP6002 outputs are
    confirmed.
-   [ ] ADS1115 ADDR strap and resulting I²C address are confirmed.
-   [ ] TMP117 ADD0 strap and resulting I²C address are confirmed.
-   [ ] Both NIR LED control GPIOs are identified from the original
    schematic.
-   [ ] LED polarity and series-resistor values are checked against the
    physical circuit.
-   [ ] MAX30102 breakout-board supply requirements are checked.
-   [ ] All modules share a suitable ground reference.
-   [ ] I²C pull-up arrangement is checked, including any pull-ups
    already present on breakout boards.
-   [ ] The final assembled hardware is checked for continuity and
    shorts before power is applied.

------------------------------------------------------------------------

## 13. Documentation Notes

This document is a pinout transcription of the supplied schematic image,
not a replacement for the editable circuit schematic or component
datasheets. Where a net could not be identified reliably from the image,
it is explicitly marked for verification.

Update this document whenever the circuit, ESP32 GPIO assignment, sensor
module, or board revision changes.

