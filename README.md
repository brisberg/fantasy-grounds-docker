Run on OSX

Requires XQuartz running

docker run -e DISPLAY=host.docker.internal:0 firefox



----

Notes to install wine in docker

Docker run ubuntu:14.04
sudo apt-get update
sudo apt-get install wget
wget -qO - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -

sudo apt-get install software-properties-common
sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ trusty main'


--

// Build and run current image
docker run -it --rm -e DISPLAY:host.docker.internal:0 .

FG is a 32 bit app, so we need the i386 architecture base image
Attempt at i386/ubuntu:18

docker run i386/ubuntu:18.04
dpkg --add-architecture i386 &&
  apt-get update &&
  apt-get install wine32

apt-get install curl
curl -O https://www.fantasygrounds.com/filelibrary/FGWebInstall.exe
wine FGWebInstall.exe (Doesn't work, needs XDisplay)
