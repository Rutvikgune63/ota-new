# ota-new
OTA Firmware Update for ESP32

This repository contains an example code for performing Over-The-Air (OTA) firmware updates for an ESP32 microcontroller. The device connects to a specified WiFi network, checks for a new firmware version from a github repository, and updates itself if a new version is available.
-------------------------------------------------------------------------------------------------------------------------------------
Starting 
Prerequisites
•	ESP32 development bord (ESP32 DEVKITV1)
•	Arduino IDE with ESP32 board support (Should be installed)
•	WiFi network credentials(Prefer wifi network not mobile hotspot)
•	GitHub repository to host the firmware and version file
-------------------------------------------------------------------------------------------------------------------------------------
Libraries Used

WiFi.h                  : For connecting to a WiFi network.
ArduinoJson.h           : For parsing JSON data.
HTTPClient.h            : For making HTTP requests.
Update.h                : For performing OTA updates.

Note: If you are using Arduino IDE 1.x.x use ESP32httpUpdate.h it both update.h, HTTPClient.h 
-------------------------------------------------------------------------------------------------------------------------------------
Installation

Download the source code.
Open the code in the Arduino IDE.
Install the required libraries via the Arduino Library Manager if you haven't already:
	WiFi
	HTTPClient
	ArduinoJson
	Update
-------------------------------------------------------------------------------------------------------------------------------------
Configuration

•	WiFi Credentials: Update the SSID and Password variables with your WiFi network name and password.
•	Current Firmware Version: Update the Current Firmware Version variable with the current firmware version.
•	Version URL: Ensure the Version URL points to the JSON file containing the version information on your GitHub repository.
-------------------------------------------------------------------------------------------------------------------------------------
Version File Format

The version file(version.json) should be hosted on a Github server and must contain the following fields:
version: The latest firmware version available.
url: The direct URL to the firmware binary file.

Example:
{
  "version": "1.3.0",
  "url": "https://github.com/Rutvikgune63/ota-new/raw/main/fw130.bin"
}

-------------------------------------------------------------------------------------------------------------------------------------
Uploading Firmware

•	Build and export the firmware binary (.bin) file from the Arduino IDE.
•	Upload the binary file to your GitHub repository.
•	Update the version.json file with the new version number and firmware URL.
-------------------------------------------------------------------------------------------------------------------------------------
Running the Code

•	Connect your ESP32 DEVKIT V1 to your computer through cable.
•	Upload the code to the ESP32 using the Arduino IDE.
•	Open the Serial Monitor to view the output.
•	The ESP32 will connect to the specified WiFi network and check for firmware updates. If a new version is available, it will download and install the update, then restart through program only.
-------------------------------------------------------------------------------------------------------------------------------------
Example Output
Connecting to WiFi...
Connected to WiFi

Free heap memory: : 256604  bytes
Current version: 1.2.0
Available version: 1.3.0

New version available. Starting update...
HTTP GET code: 200
Firmware content length: 123456 bytes
Written: 123456 successfully
OTA done!
Update successfully completed. Rebooting.

Free heap memory: 255524 bytes
Current version: 1.3.0
Available version: 1.3.0
Firmware is up to date.

----------------------------------------------If your provided link redirects--------------------------------------------------------------------------------- 
Free heap memory: 256604 bytes
Current version: 1.2.0
Available version: 1.3.0
New version available. Starting update...
HTTP GET code: 302

Redirected to: https://raw.githubusercontent.com/Rutvikgune63/ota-new/main/fw130.bin
HTTP GET code: 200
Firmware content length: 1022688
Written: 1022688 successfully
OTA done!
Update successfully completed. Rebooting

Free heap memory: 255524 bytes
Current version: 1.3.0
Available version: 1.3.0
Firmware is up to date.
