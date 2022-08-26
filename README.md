# Arma-3-External-Radar
Arma 3 external radar.  Built using C++, NodeJS, socket.io and Leaflet!

* Memory RPM/WPM Client (/arma_dma)
* Radar and Communication Server (/nodejs)

## Main Features

* Live radar (player coords, player side, player dead, player direction, player in vehicle)
* Arma 3 Altis map files, multi-user browser access for the radar using LAN/VPN.
* No weapon recoil (not setUnitRecoilCoefficient should bypass most script-based anti-cheats)
* No weapon sway (not setCustomAimCoef should bypass most script-based anti-cheats)

## How it works
<b>Linux Memory RPM/WPM Client</b><br/>
On the host machine, we are able to read and write to our guest machine's memory efficiently and safely using C++ and the memflow connector, arma_dma reads the guest's memory and searches for Arma 3, once found it reads the game's data we need and stores it into an array, the array then gets converted into JSON format using nlohmann/json and then is sent over to our NodeJS server using socket.io.

<b>Radar and Communication Server</b><br/>
The radar relies on NodeJS and socket.io to receive the JSON data from the Memory RPM/WPM Client (arma_dma). Once received socket.io emits a signal to the front-end containing our player data, it filters through the JSON and tells Leaflet to set up custom markers for each player.

## Dependencies
<b>Memory RPM/WPM Client (/arma_dma):</b>
* [memflow](https://github.com/memflow/memflow)
* [Socket.IO C++ Client](https://github.com/socketio/socket.io-client-cpp)
* [websocketpp](https://github.com/memflow/memflow)
* [asio](https://github.com/chriskohlhoff/asio)
* [Catch2](https://github.com/catchorg/Catch2/tree/9c07718b5f779bc1405f98ca6b5b693026f6eac7)
* [rapidjson](https://github.com/Tencent/rapidjson/tree/a36110e11874bcf35af854940e0ce910c19a8b49)

<b>Radar and Communication Server (/nodejs):</b>
* [Leaflet](https://github.com/Leaflet/Leaflet)
* [express](https://www.npmjs.com/package/express)
* [socket.io](https://www.npmjs.com/package/socket.io)

## Building



My setup: </br>
OS: Manjaro 21.3 KDE </br>
Kernel: x86_64 Linux 5.18.19 </br>
CPU: i5-12600K </br>
GPU: RTX 3070ti </br>
RAM: 16gb </br>

<b>Memory RPM/WPM Client (/arma_dma):</b>
1. Download and install the required dependencies.
2. Navigate to arma_dma and compile the source by running the script "build.sh". You need to have Rust installed and updated:
`cd arma_dma`
`sudo ./build.sh`

3. Navigate to the newly created /build folder and run arma_dma as root:
`cd build`
`sudo ./arma_dma`

<b>Radar and Communication Server (/nodejs):</b>
1. Download and install NodeJS and npm.
2. Navigate to NodeJS and run:
`npm install`
`node server.js`

## To do
* Implement server and user authentication.
* Add other Arma 3 maps

## Credits
* [apex_dma_kvm_pub](https://github.com/MisterY52/apex_dma_kvm_pub)
* [Guided Hacking Youtube](https://www.youtube.com/c/GuidedHacking)
* [ARMA 3 Reversal, Structs and Offsets](https://www.unknowncheats.me/forum/arma-3-a/114242-arma-3-reversal-structs-offsets.html)
* [memflow](https://github.com/memflow/memflow)


## Related
[passthrough_helper_manjaro](https://github.com/pavolelsig/passthrough_helper_manjaro)
[PCI passthrough via OVMF](https://wiki.archlinux.org/title/PCI_passthrough_via_OVMF)
[Arma-3-reverse-engineering](https://github.com/Apex-master/Arma-3-reverse-engineering)
