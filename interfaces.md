# BLE Interfaces
The usual mode of operation of beacons is "connectable beacon". The beacons broadcast their advertisement data for everyone,
and generally users don't have to connect to the beacon. 

BLE GATT connection is formed for configuration of the beacons. While anyone can connect to the beacon and read basic information
such as hardware and firmware version and serial number, configuring is protected with a passcode.

## Connectable GATT profile
### Configuration service
Configuring the beacon is done via Nordic UART Service, NUS.
The NUS is described in [Nordic Infocenter](http://infocenter.nordicsemi.com/topic/com.nordic.infocenter.sdk5.v12.3.0/structble__nus__c__s.html?resultof=%22%6e%75%73%22%20%22%6e%75%22%20). 

Only iBeacon transmissions are configurable.

### Buttonless DFU Service
Buttonless DFU service is used to put tag into bootloader mode. Please see [Nordic's specification](https://infocenter.nordicsemi.com/topic/com.nordic.infocenter.sdk5.v14.2.0/group__ble__dfu.html?cp=4_0_0_6_3_8) for details of the service. 

Sample code for entering DFU mode with [Android](https://github.com/NordicSemiconductor/Android-nRF-Connect) is available at Nordic's GitHub.
iOS version of nRF Connect might not support the buttonless DFU. 

### DIS Service
Device Information Service provides read-only access to
device information, such as hardware model, software revision and manufacturer. DIS is a [Bluetooth SIG standard](https://www.bluetooth.com/specifications/gatt/viewer?attributeXmlFile=org.bluetooth.service.device_information.xml).

### DFU service
DFU service is available only in the bootloader mode. The DFU service allows uploading a new firmware to the tag.
Source code for [Android](https://github.com/NordicSemiconductor/Android-DFU-Library) and [iOS](https://github.com/NordicSemiconductor/IOS-Pods-DFU-Library) to enter upload packages via DFU is available at Nordic's GitHub.

### Security
A passcode must be entered via NUS service before configuring the device? TODO: Discuss.

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
Please follow issues on this repository to track progress.
