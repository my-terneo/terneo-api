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

For example set the 2nd period to 8:00 -> 28C, 18:00 -> 18C on Wednesday:

.. code-block:: json

   {
    "sn":"058016000543464839373520000159",
    "tt":{
           "2":[[480,280],[1080,180]]
         }
   }

.. important::
	Нельзя в одном запросе передавать несколько дней расписания.

..note::
	В версии ПО 2.3 Температура не может быть больше чем параметр 26 (upperLimit), меньше чем параметр 27 (lowerLimit) для пола и не более 35 °С, не менее 5 °С для воздуха.

