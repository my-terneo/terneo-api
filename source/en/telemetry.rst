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
		* ``3`` - reserved
		* ``4`` - reserved
		* ``5`` - current setting
		* ``6`` - reserved
		* ``7`` - microcontroller temperature		
	* ``m`` - modes
		* ``0`` - control type: floor = 0, air = 1, extended = 2
		* ``1`` - control type: schedule = 0, manual = 3, away = 4, temporary = 5
		* ``2`` - the number of the current period of the schedule (the first period of Monday = 0, Tuesday = maxSchedulePeriod ...)
		* ``3`` - blocking type: no blocking = 0, blocking changes from the cloud = 1, blocking changes from the local network = 2, both = 3
		* ``4`` - reserved
		* ``5`` - heating mode (0 - heating, 1 - cooling)
	* ``o`` - other parameters
		* ``0`` - Wi-Fi signal strength in dBm
		* ``1`` - the reason for the last reboot. Depending on the hardware version of the platform, there can be two types of values: First - mask: power off = 0x04, soft reset = 0x08, watchdog timer = 0x10, low voltage = 0x40. Second: 9 - software reboot due to low MK supply voltage; 3 - software reboot; 1 - power reset.
	* ``par`` - duplication of some device parameters
		* ``n`` - parameter number
	* ``te`` - extra temperatures
	* ``f`` - bit parameters
		* ``0`` - load status
		* ``1`` - reserved
		* ``2`` - floor restriction action
		* ``3`` - no floor sensor
		* ``4`` - short circuit floor sensor
		* ``5`` - no air sensor
		* ``6`` - short circuit air sensor
		* ``7`` - preheat algorithm is active 
		* ``8`` - an open window function is active
		* ``9`` - internal overheating
		* ``10`` - reserved
		* ``11`` - problems with the clock
		* ``12`` - no overheat control
		* ``13`` - proportional mode is active
		* ``14`` - digital floor sensor is used
		* ``15`` - reserved
		* ``16`` - power off state
		* ``17`` - reserved
		* ``18`` - reserved
		* ``19`` - reserved
		* ``20`` - reserved
		* ``21`` - problems with the zero crossing sensor

