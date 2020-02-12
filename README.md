# scd30-cli

CLI for interacting with [Sensirion SCD30](
https://www.sensirion.com/en/environmental-sensors/carbon-dioxide-sensors/carbon-dioxide-sensors-co2/), the CO2, temperature, and humidity sensor.

The CLI exposes all of the commands supported by the SCD30, as documented in the official [Interface Description](https://www.sensirion.com/fileadmin/user_upload/customers/sensirion/Dokumente/9.5_CO2/Sensirion_CO2_Sensors_SCD30_Interface_Description.pdf).

Uses [scd30-node](https://github.com/rsmeral/scd30-node) for communication with the SCD30.

## Usage

```
yarn global add scd30-cli
```

```
$ scd30-cli start-continuous-measurement
Continuous measurement started.
Ambient pressure compensation deactivated.

$ scd30-cli read-measurement
╔═══════════════════╤══════════╗
║ CO2 concentration │ 1054 ppm ║
╟───────────────────┼──────────╢
║ Temperature       │ 24.15°C  ║
╟───────────────────┼──────────╢
║ Humidity          │ 31.86%   ║
╚═══════════════════╧══════════╝
```

## Options

 * `-b, --bus <number>`
   * The number of the I2C bus to open.<br/>
     0 for /dev/i2c-0, 1 for /dev/i2c-1, ... <br/>
     (default: 1)
 * `-h, --help`
   * output usage information

## Commands

Refer to [official documentation](https://www.sensirion.com/fileadmin/user_upload/customers/sensirion/Dokumente/9.5_CO2/Sensirion_CO2_Sensors_SCD30_Interface_Description.pdf) for more details on commands.

* [read-measurement](#read-measurement)
* [status](#status)
* [is-data-ready](#is-data-ready)
* [start-continuous-measurement](#start-continuous-measurement-pressure)
* [stop-continuous-measurement](#stop-continuous-measurement)
* [set-measurement-interval](#set-measurement-interval-interval)
* [get-measurement-interval](#get-measurement-interval)
* [start-asc](#start-asc)
* [stop-asc](#stop-asc)
* [get-asc-status](#get-asc-status)
* [set-frc-value](#set-frc-value-co2ppm)
* [get-frc-value](#get-frc-value)
* [set-temp-offset](#set-temp-offset-offset)
* [get-temp-offset](#get-temp-offset)
* [set-altitude-compensation](#set-altitude-compensation-altitude)
* [get-altitude-compensation](#get-altitude-compensation)
* [get-firmware-version](#get-firmware-version)
* [soft-reset](#soft-reset)

### `read-measurement`

Read a measurement of CO2 concentration, temperature, and humidity.

### `status`

Queries for data ready status, ASC status, FRC value, temperature offset, altitude compensation,continuous measurement interval, and firmware version

### `is-data-ready`

Determines if a measurement can be read from the sensor's buffer.

### `start-continuous-measurement [pressure]`

Starts continuous measurement of CO2 concentration, temperature, and humidity.

* `pressure` (optional)
  * Ambient pressure to compensate CO2 measurements, 700–1400 mBar.<br/>
    Overrides altitude compensation.<br/>
    Setting to 0 deactivates ambient pressure compensation.<br/>
    To set new value, re-run `start-continuous-measurement`.

### `stop-continuous-measurement`

Stops continuous measurement of CO2 concentration, temperature, and humidity.

### `set-measurement-interval <interval>`

Sets the interval of continuous measurement.

* `interval`
  * Interval of 2–1800 seconds

<a name="get-measurement-interval"></a>
### `get-measurement-interval`

Returns the interval of continuous measurement.

### `start-asc`

Starts the automatic self-calibration.

### `stop-asc`

Stops the automatic self-calibration.

### `get-asc-status`

Returns the status of automatic self-calibration.

### `set-frc-value <co2ppm>`

Sets the reference CO2 concentration for forced re-calibration.

* `co2ppm`
  * Concentration of CO2, 400-2000 ppm

### `get-frc-value`

Returns the reference CO2 concentration for forced re-calibration.

### `set-temp-offset <offset>`

Sets the temperature offset.

* `offset`
  * Temperature offset in units of 0.01°C

### `get-temp-offset`

Returns the temperature offset.

### `set-altitude-compensation <altitude>`

Sets the altitude compensation value.

* `altitude`
  * Altitude in meters above sea level

### `get-altitude-compensation`

Returns the altitude compensation value.

### `get-firmware-version`

Returns the firmware version.

### `soft-reset`

Performs a soft reset.
