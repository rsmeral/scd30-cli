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
* [start-continuous-measurement](#start-continuous-measurement)
* [stop-continuous-measurement](#stop-continuous-measurement)
* [set-measurement-interval](#set-measurement-interval)
* [get-measurement-interval](#get-measurement-interval)
* [start-asc](#start-asc)
* [stop-asc](#stop-asc)
* [get-asc-status](#get-asc-status)
* [set-frc-value](#set-frc-value)
* [get-frc-value](#get-frc-value)
* [set-temp-offset](#set-temp-offset)
* [get-temp-offset](#get-temp-offset)
* [set-altitude-compensation](#set-altitude-compensation)
* [get-altitude-compensation](#get-altitude-compensation)
* [get-firmware-version](#get-firmware-version)
* [soft-reset](#soft-reset)

<a name="read-measurement"></a>
### `read-measurement`

Read a measurement of CO2 concentration, temperature, and humidity.

<a name="status"></a>
### `status`

Queries for data ready status, ASC status, FRC value, temperature offset, altitude compensation,continuous measurement interval, and firmware version

<a name="is-data-ready"></a>
### `is-data-ready`

Determines if a measurement can be read from the sensor's buffer.

<a name="start-continuous-measurement [pressure]"></a>
### `start-continuous-measurement [pressure]`

Starts continuous measurement of CO2 concentration, temperature, and humidity.

* `pressure` (optional)
  * Ambient pressure to compensate CO2 measurements, 700–1400 mBar.<br/>
    Overrides altitude compensation.<br/>
    Setting to 0 deactivates ambient pressure compensation.<br/>
    To set new value, re-run `start-continuous-measurement`.

<a name="stop-continuous-measurement"></a>
### `stop-continuous-measurement`

Stops continuous measurement of CO2 concentration, temperature, and humidity.

<a name="set-measurement-interval <interval>"></a>
### `set-measurement-interval <interval>`

Sets the interval of continuous measurement.

* `interval`
  * Interval of 2–1800 seconds

<a name="get-measurement-interval"></a>
### `get-measurement-interval`

Returns the interval of continuous measurement.

<a name="start-asc"></a>
### `start-asc`

Starts the automatic self-calibration.

<a name="stop-asc"></a>
### `stop-asc`

Stops the automatic self-calibration.

<a name="get-asc-status"></a>
### `get-asc-status`

Returns the status of automatic self-calibration.

<a name="set-frc-value <co2ppm>"></a>
### `set-frc-value <co2ppm>`

Sets the reference CO2 concentration for forced re-calibration.

* `co2ppm`
  * Concentration of CO2, 400-2000 ppm

<a name="get-frc-value"></a>
### `get-frc-value`

Returns the reference CO2 concentration for forced re-calibration.

<a name="set-temp-offset <offset>"></a>
### `set-temp-offset <offset>`

Sets the temperature offset.

* `offset`
  * Temperature offset in units of 0.01°C

<a name="get-temp-offset"></a>
### `get-temp-offset`

Returns the temperature offset.

<a name="set-altitude-compensation <altitude>"></a>
### `set-altitude-compensation <altitude>`

Sets the altitude compensation value.

* `altitude`
  * Altitude in meters above sea level

<a name="get-altitude-compensation"></a>
### `get-altitude-compensation`

Returns the altitude compensation value.

<a name="get-firmware-version"></a>
### `get-firmware-version`

Returns the firmware version.

<a name="soft-reset"></a>
### `soft-reset`

Performs a soft reset.
