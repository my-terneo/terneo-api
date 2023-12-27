Schedule
~~~~~~~~

To get all schedule of the device send command ``{"cmd":1}``, for example answer for *AX* thermostat with firmware version 2.3:

.. code-block:: json

   {
     "sn":"058016000543464839373520000159",
     "tt":{
            "0":[[360,300],[480,250],[1020,300],[1320,250]],
            "1":[[360,300],[480,250],[1020,300],[1320,250]],
            "2":[[360,300],[480,250],[1020,300],[1320,250]],
            "3":[[360,300],[480,250],[1020,300],[1320,250]],
            "4":[[360,300],[480,250],[1020,300],[1320,250]],
            "5":[[480,300],[1380,250]],
            "6":[[480,300],[1380,250]]
          }
   }

``sn`` - device serial number

``tt`` - schedule exchange key 

``0``, ``1``, ``2``, ``3``, ``4``, ``5``, ``6``, ``7`` - day number key, 0-monday. 

The argument is a two-dimensional array with a minimum of one period.

Each period consists of pairs of values:
  * number of minutes since the beginning of the day
  * temperature is 1/10 degree

The maximum number of periods is set by the `maxSchedulePeriod` parameter for version 2.3 is always = 16.

For example, set two periods on Wednesday: *8:00 -> 28 °C*, *18:00 -> 18 °C*:

.. code-block:: json

   {
    "sn":"058016000543464839373520000159",
    "tt":{
           "2":[[480,280],[1080,180]]
         }
   }

.. important::
	 It is impossible to transfer several days of the schedule in one request.

.. note::
	 In firmware version 2.3, temperature cannot be greater than parameter 26 (upperLimit), less than parameter 27 (lowerLimit) for the floor and cannot be greater than 35 °C, less than 5 °C for air.


