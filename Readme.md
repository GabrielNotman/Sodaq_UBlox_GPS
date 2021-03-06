# Sodaq_UBlox_GPS

Arduino library for using the UBlox EVA7M.

## Usage

Quick example:

```c
#include <Arduino.h>
#include <Sodaq_UBlox_GPS.h>

#define MySerial        SERIAL_PORT_MONITOR

void setup()
{
    delay(3000);
    while (!SerialUSB) {
        // Wait for USB to connect
    }

    MySerial.begin(57600);

    MySerial.println("SODAQ LoRaONE test_gps is starting ...");

    sodaq_gps.init(GPS_ENABLE);
    sodaq_gps.setDiag(MySerial);
}

void loop()
{
    sodaq_gps.scan(120000); // 120s timeout
    MySerial.println("waiting in loop() ...");
    delay(60000);
}

```

Method|Description
------|------
**init ()**|Initializes the UBlox, and switches it on.
**scan (bool leave_on, uint32_t timeout)**|Scans all NMEA messages until lat/long is seen.  It returns true when a fix is found.


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

## History

v0.0.1 Pre-Alpha Release
v0.9.0 Beta Release

## License

Copyright (c) 2016 SODAQ. All rights reserved.

This file is part of Sodaq_UBlox_GPS.

Sodaq_UBlox_GPS is free software: you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation, either version 3 of the
License, or(at your option) any later version.

Sodaq_UBlox_GPS is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with Sodaq_UBlox_GPS.  If not, see
<http://www.gnu.org/licenses/>.
