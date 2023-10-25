# overview of this branch by Tak
## notes
this branch is used for testing firmware like fast Iridium test mode and changing frequency bins.
At the moment, change freq\_bins also has push to buffer or not in L266 wave\_analyzer.cpp.
changing frequency bins can be done by making a function at L54 wave\_analyzer.h


## from the OpenMetBuoy repo

A disclaimer first:

- these firmwares work well, but they are messy; I have had very little time to improve code quality / re-factor, so things have grown up "as things went", features were added continuously, and the firmware was developed as an experiment rather than a well engineered piece of software

- the different versions of the firmware are largely copies of each other with small changes; this is of course not ideal (it violates the "dont repeat yoursel principle", but it works well enough for now, and I have no time at the moment to make things better).

The main firmware versions:

- **plain_gps_drifter**: a plain gps drifter, no wave measurements
- **standard_gps_waves_drifter**: a standard gps and waves drifter, with both drift and waves measurements
- **steval_gps_waves_drifter**: the gps and waves drifter adapted to the 6dof sensor, ie the replacement chip for when the Adafruit 9dof is not available, using the ISM330DHCX 6dof sensor; basically, the same code, but without the magnetometer
- **steval_LSM6DSOX_gps_waves_drifter**: the gps and waves drifter adapted to the 6dof sensor, ie the replacement chip for when the Adafruit 9dof is not available, using the LSM6DSOX 6dof sensor; basically, the same code, but without the magnetometer
- **standard_gps_waves_thermistors_drifter**: a standard gps and waves and thermistor drifter, with up to 6 DS18B20 thermistors
- **two_ways_gps_waves_drifter**: the gps and waves drifter, with the 2-ways communication added to be able to change the frequency of GPS / waves measurements.
- **functionality_test_mode**: the gps and waves drifter, set up in such a way that it tests that the GPS, IMU, and Iridium components are well working and showing it on the serial output.
- **steval_gps_waves_pcbtraces_2ways**: the gps and waves drifter, set up for the ISM330DHCX IMU, using the AGT SDA SCL pins / PCB traces for the I2C port to the IMU (ie shared with the GPS with current AGT configuration), and the 2 ways communications; this is a slightly less version by myself, but some partners have used it in depth; sidenote: the code was copied from the private repo: https://github.com/tnn77/tracker_and_waves_instrument/tree/feat/waves_in_ice_ISM330 .

Of course, all versions of the firmware can be tuned to your needs; see in particular the **params.h** file.
