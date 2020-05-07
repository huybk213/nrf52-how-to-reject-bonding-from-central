# nrf52-how-to-reject-bonding-from-central

Demo code how to accept/reject the bonding request from BLE Central

Two examples how to do accept / reject the bonding request
* ble_app_hids_keyboard (pre-set the accept /reject before getting the bonding request)
* ble_app_hids_keyboard_Yes_or_No (realtime to accept or reject bonding request)

## Requirement
* NRF52840 DK Board x 1
* Mobile / nRF Connect Desktop
* SDK 16.0 / S140v7.0.1
* IDE Segger Embedded Studio

## Details
You can find all the details information at [URL](https://jimmywongiot.com/2020/05/04/how-to-allow-reject-the-ble-bonding-request-from-central/).

## Location
The project may need modifications to work with later versions or other boards.
To compile it, clone the repository in the /nRF5_SDK_XX.x.0/examples/ directory.
The application is built to be used with the official nRF5 SDK that can be downloaded from developer.nordicsemi.com
