# RPi-cam-gpio
A web page where rpi camera streams video and click buttons available to control gpio of rpi

Firstly, give a static IP address to your Pi 
http://weworkweplay.com/play/automatically-connect-a-raspberry-pi-to-a-wifi-network/
Reboot the Pi for the changed IP to make effect.

Before starting, your Raspberry Pi should be a web server to host a web page so install Apache2.

$ sudo apt-get update <br>
$ sudo apt-get install apache2 -y

We're gonna work with PHP so RPi should be installed with required packages.

$ sudo apt-get install php5 libapache2-mod-php5 -y <br>
Note: No need of using 'sudo' before commands when operating as a root user.

Now open the browser in any of the devices connected to the same network and type the IP address of your Pi.
You should see a html page saying "It's done" which means apache2 is installed successfully and your Pi is a web server now.

Now delete that html file <br>
$ sudo rm /var/www/html/index.html <br>
If using Raspbian Wheezy or older versions, use /var/www/ instead /var/www/html/

# Dependencies
WiringPi
-------------------------
$ git clone https://github.com/WiringPi/WiringPi.git <br>
$ cd WiringPi <br>
$ ./build

To check whether the firmware is correctly installed, try any one of the commands <br>
$ gpio -v <br>
$ gpio readall

RPi_Cam_Web_Interface
-------------------------
$ git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git <br>
$ cd RPi_Cam_Web_Interface <br>
$ chmod u+x RPi_Cam_Web_Interface_Installer.sh <br>
$ ./RPi_Cam_Web_Interface_Installer.sh 

A simple UI will appear in the command line <br>
select the first option (apache web server) <br>
set installation path as /var/www/html/ or any subfolders inside this (for Raspbian Jessie) <br>
then click yes for reboot.

Connect your RPi camera carefully and again type the IP address of Pi in your browser. <br>
You should able to see your RPi camera streaming live video.

Now lets control gpio additionally.

RPi-web-cam-gpio (this repo)
--------------------------
$ git clone https://github.com/SikkandarSulaiman/RPi-web-cam-gpio.git <br>
$ sudo cp RPi-web-cam-gpio/* /var/www/html

Go to IP address of Pi in your browser and see the buttons for all gpio pins along with the camera stream.
