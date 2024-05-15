# Keyence SR-2000 Simulator

## Overview

This project is a simulator for the Keyence SR-2000 scanner. It consists of an HTTP server, a UDP server, and a TCP server, each serving different aspects of the simulation. The server can simulate the scanner from connecting to it, till scanning and returning a dummy scan result.

## Features

- **HTTP Server**: Keeps alive the other services.
- **UDP Server**: Broadcasting the simulated readers and handle the connection to them
- **TCP Server**: Handles reading: ```LON``` and stop: ```LOFF``` commands, respond when scan found.

## Requirements

- Node.js
- npm (Node Package Manager)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ProCat-Solutions-Kft/simulator-keyence-sr-2000
   ```

2. Navigate to the project directory:
   ```bash
    cd keyence-sr-2000-simulator
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

## Configuration
Create a .env file in the root of the project and configure the following environment variables:
   ```
   PORT_UDP=9015
   PORT_TCP=9004
   HTTP_PORT=3000
   CODES_FILE_PATH='codes.json'
   HOST_IP='192.168.1.100'
   DEVICE_INFO='keyence SR-2000,keyence SR-2000'
   ```

The CODES_FILE_PATH should point to a JSON file containing an array of codes to be later one of it randomly sent back by the TCP server as a scan response.

Example codes.json:
   ```json
   {
      "codes" : [
         "ABCDEFGH:A",
         "ABCDEFGH:B",
         "ABCDEFGH:E"
      ]
   }
   ```

The format of one response string: 
- ```ABCDEFGH```: the scanned label's value
- ```A```: the quality of the scan

## Usage
To start the simulator, run the following command:
   ```bash
  npm run dev
   ```
This will start the HTTP, UDP, and TCP servers.

## Author
[ProCat Solutions](https://github.com/ProCat-Solutions-Kft/)

## License
This project is licensed under the MIT License. See the LICENSE file for details.
