# EspCloudUpdatePlatformIo [![N|Solid](http://sanusb.blogspot.com.br/favicon.ico)](http://sanusb.org/)

This project for all shows an ESP32 and ESP266 microcontrollers Update Environment for Internet programming with same generic sketch using the website  [sanusb.org/espupdate](http://sanusb.org/espupdate). In this project, the free version of Firebase (Google JSON objects Database) was implemented to generate the cloud update trigger for .bin files. To use this tool, download and and use this project with PlatformIO and VScode.

The update (OTA) transmits the compiled binary *.bin* files via Internet. To generate a .bin file from your sketch, go to Sketch menu of the Arduino IDE > Export compiled Binary. To perform this cloud firmware update, the users need to write in the sketch only the Wifi ssid, the password and the same name as the profile entered on the site and when uploading the .bin to site, remote firmware update of ESP microcontrollers via the Internet takes place. The user profile name entered on the website [sanusb.org/espupdate](http://sanusb.org/espupdate) may be alphanumeric (for example: sandro190575 or sandrojuca).

It is possible to test this transmission application via the Internet, accessing the site http://sanusb.org/espupdate/ through the laboratory or residence network and the ESP32/ESP8266 microcontroller anchored to the smartphone connected to the 4G mobile network, or vice versa.

 The dependencies of the EspCloudUpdatePlatformIo tool in the Arduino IDE libraries folder are the Firebase libraries. For ESP8266:
 
 * https://github.com/mobizt/Firebase-ESP8266
  
 For ESP32:
 
 * https://github.com/mobizt/Firebase-ESP32
 
 To install all the libraries, including https://github.com/SanUSB/EspCloudUpdatePlatformIo , follow the steps: 

Arduino IDE -> Sketch -> Include Library -> Add .zip Libraries.
 
 You can usually find the installed ESP32 and ESP8266 libraries at:
  
 On Windows:    
*        C:\Users\UserName\Documents\Arduino\libraries (tested)
     
 On Linux:   
*       /home/UserName/Arduino/Libraries (tested).

On OSX:
*       ~/Documents/Arduino/libraries.

 In the installed **EspCloudUpdatePlatformIo** library folder there is an example for testing this proposed tool called **EspUpdateStart.ino**.
 
It is worth considering that, through tests carried out, files compiled .bin as with the same name and with sequential downloads for updating in the cloud, it may happen that the .bin file sent last for the update is not downloaded by ESP microcontroller, but a .bin file previously submitted, because they have the same name and the same download URL. For this reason, in this project, the name of the .bin files submitted on the site has versioned (modified) names, consequently the download URL address as well, this prevents a previously sent file or another file with the same name from being downloaded, generating a unique and exclusive URL. In this case, to version the name and download URL of the .bin file, it was used: year, month, day, hour and the upload cyclic order.

For the update condition {if (newVersionInt> InitialVersionInt)}, it is considered between the variables greater than (>) and not different (!=), to ensure that the latest .bin file version is always greater than the previous .bin version and to prevent that variables reading can generate unwanted update trigger during operation.

In summary, download, unzip and open the project  https://github.com/SanUSB/EspCloudUpdatePlatformIo in VScode with PlattformIo and install the libraries .zip available on dependencies for ESP8266 (https://github.com/mobizt/Firebase-ESP8266) or ESP32 (https://github.com/mobizt/Firebase-ESP32). To install the librarys, follow the steps: Arduino IDE -> Sketch -> Include Library -> Add .zip Libraries. Unzip the .zip folder. Write the name of your profile and WiFi network in the sketch. Update the sketch only the first time using the USB port. So it is now possible to transfer over the internet generating the .bin file.  For this, go to Sketch menu of the Arduino IDE > Export compiled Binary.

After the update of the .bin file is finished and the microcontroller is automatically reset, the new verification code is sent to http://sanusb.org/espupdate/*YourProfile*/conf.php in order to confirm the update on the website.

This project, the loop sketch function is practically free so you can implement your projects and be able to update them in a simple and remote way over the Internet. Tutorial video: https://www.youtube.com/watch?v=zpY4lm-7KJs and https://www.youtube.com/watch?v=En_hFO5f4U8.
 
*Have fun!*
