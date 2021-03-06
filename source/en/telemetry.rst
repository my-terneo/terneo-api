Telemetry
~~~~~~~~~

Telemetry is used to obtain the current state of device.
To get telemetry, send command ``{"cmd": 4}``, for example, the answer for AX thermostat with firmware version 2.3 will be:

.. code-block:: json

     {
      "sn":"058016000543464839373520000159",
      "t.0":"450","t.1":"416","t.5":"480",
      "m.0":"0","m.1":"3","m.2":"34","m.3":"2",
      "f.0":"1","f.1":"0","f.2":"0","f.3":"0",
      "f.4":"0","f.7":"0","f.8":"0","f.9":"0",
      "f.13":"0","f.14":"0","f.10":"0","f.11":"1",
      "f.12":"0","o.0":"-83","o.1":"6","f.15":"0",
      "par.26":"45","par.27":"5"
     }

``sn`` - device serial number

``x.n`` is the parameter key, where ``x`` is a group of parameters, ``n`` is the number in the group

Parameter groups:
	* ``t`` - temperature is 1/16 °C
		* ``0`` - internal overheating sensor
		* ``1`` - floor
		* ``2`` - air
		* ``3`` - precipitation sensor
		* ``4`` - external object
		* ``5`` - current setting
		* ``6`` - correction
	* ``u`` - voltage
		* ``0`` - maximum voltage during telemetry period, volts
		* ``1`` - the minimum voltage during telemetry period, volts
		* ``2`` - supply voltage 3.3V, 1/100 volt
		* ``3`` - battery voltage, 1/10 volt
		* ``4`` - upper threshold, volts
		* ``5`` - lower threshold, volts
		* ``6`` - medium voltage, volt
	* ``i`` - current
		* ``0`` - maximum current during telemetry period, 1/10 ampere
		* ``1`` - average current during telemetry period, 1/10 ampere
		* ``2`` - minimum current during telemetry period, 1/10 ampere
		* ``3`` - upper current limit, 1/10 ampere
		* ``4`` - average current limit, 1/10 ampere
		* ``5`` - lower current limit, 1/10 ampere
	* ``w`` - power
		* ``0`` - upper power limit, watt
		* ``1`` - maximum total load power during telemetry period, VA
		* ``2`` - average total load power during telemetry period, VA
		* ``3`` - minimum total load power during telemetry period, VA
		* ``4`` - maximum cosine fi during telemetry period, 1/100 degree
		* ``5`` - average cosine fi during telemetry period, 1/100 degree
		* ``6`` - the minimum cosine fi during telemetry period, 1/100 degree
	* ``r`` - resistance
		* ``0`` - ground moisture sensor, 100 Ohm
	* ``p`` - active and reactive parameters
		* ``0`` - the maximum active load power during telemetry period, watts
		* ``1`` - average active load power during telemetry period, watts
		* ``2`` - the minimum active load power during telemetry period, watts
		* ``3`` - maximum reactive load power during period of telemetry, VAR
		* ``4`` - average reactive load power during telemetry period, VAR
		* ``5`` - minimum reactive load power during telemetry period, VAR
	* ``m`` - modes
		* ``0`` - control type: floor = 0, air = 1, extended = 2
		* ``1`` - control type: schedule = 0, manual = 3, away = 4, temporary = 5
		* ``2`` - the number of the current period of the schedule (the first period of Monday = 0, Tuesday = maxSchedulePeriod ...)
		* ``3`` - blocking type: no blocking = 0, blocking changes from the cloud = 1, blocking changes from the local network = 2, both = 3
		* ``4`` - controlled power type: active power = 0, reactive power = 1, apparent power = 2
	* ``o`` - other parameters
		* ``0`` - Wi-Fi signal strength in dBm
		* ``1`` - the cause of the last reboot, mask: power off = 0x04, soft reset = 0x08, watchdog timer = 0x10, low voltage = 0x40
	* ``par`` - duplication of some device parameters
		* ``n`` - parameter number
	* ``te`` - extra temperatures
	* ``f`` - bit parameters
		* ``0`` - load status
		* ``1`` - waiting for load is being changed
		* ``2`` - floor restriction action
		* ``3`` - no floor sensor
		* ``4`` - short circuit floor sensor
		* ``5`` - no air sensor
		* ``6`` - short circuit air sensor
		* ``7`` - preheat algorithm is active 
		* ``8`` - an open window function is active
		* ``9`` - internal overheating
		* ``10`` - the battery is low
		* ``11`` - problems with the clock
		* ``12`` - no overheat control
		* ``13`` - proportional mode is active
		* ``14`` - digital floor sensor is used
		* ``15`` - restart by watchdog timer
		* ``16`` - power off state
		* ``17`` - long time load on error

