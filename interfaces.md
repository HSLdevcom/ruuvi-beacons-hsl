# BLE Interfaces
The usual mode of operation of beacons is "connectable beacon". The beacons broadcast their advertisement data 

## Connectable GATT profile
### Configuration service
Configuring the beacon is done via Nordic UART Service, NUS.
The NUS is described in [Nordic Infocenter]http://infocenter.nordicsemi.com/topic/com.nordic.infocenter.sdk5.v12.3.0/structble__nus__c__s.html?resultof=%22%6e%75%73%22%20%22%6e%75%22%20). 

Only iBeacon transmissions are configurable.

### Buttonless DFU Service
Buttonless DFU service is used to put tag into bootloader mode. 

### DIS Service
Device Information Service provides read-only access to
device information, such as hardware model, software revision and manufacturer. DIS is a [Bluetooth SIG standard](https://www.bluetooth.com/specifications/gatt/viewer?attributeXmlFile=org.bluetooth.service.device_information.xml).

### DFU service
DFU service is available only in the bootloader mode. The DFU service allows uploading a new firmware to the tag. 

### Security
A passcode must be entered via NUS service before configuring the device? 

## Advertisement formats
### iBeacon

The tags are identified with iBeacon data format as described in [Apple's developer documentation](https://developer.apple.com/ibeacon/Getting-Started-with-iBeacon.pdf)

The sensor is in connectable and discoverable mode for configuration and firmware updating. 

Transmission power is TBD dBm and transmission interval is TBD ms. 

### Sensor data
The beacon sends advertisement data in Ruuvi's Manufacturer specific format known as RAWv2. The data has temperature,
air pressure, relative humidity, battery voltage and "activity" readings. 

Transmission power is same as with iBeacon format, transmission interval is TBD.

# NFC interface
The tags will ship without a plastic cover in the battery, in deep sleep. NFC field will activate the tag. 
The tag will transmit it's ID via NFC upon activation.

# Flash storage
Settings are stored to flash and loaded on boot. This allows setup to survive possible power distruption caused by shock or
battery change. 

# Task status
Please follow Issues on this repository to track proggress.