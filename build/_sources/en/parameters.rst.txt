Parameters list
~~~~~~~~~~~~~~~

To get all available parameters of the device send command ``{"cmd":1}``, for example answer for *AX* thermostat with firmware version 2.3:

.. code-block:: json

    {
       "sn":"058016000543464839373520000159",
       "par":[[0,6,"536112000"],[1,6,"536112000"],
              [2,2,"1"],[3,2,"0"],[4,1,"30"],
              [5,1,"30"],[6,1,"25"],[7,1,"5"],
              [18,2,"2"],[19,2,"10"],[21,1,"0"],
              [23,2,"6"],[25,2,"15"],[26,1,"45"],
              [27,1,"5"],[28,2,"16"],[29,1,"0"],
              [17,4,"175"],[114,7,"1"],[115,7,"0"],
              [116,7,"0"],[117,7,"0"],[118,7,"0"],
              [121,7,"0"],[122,7,"0"],[124,7,"0"],
              [125,7,"0"]]
    }

``sn`` - device serial number

``par`` - parameter exchange key

Transfer format is an array of arrays. The first value is number of the parameter, the second its type, the third is string with the parameter value.

For example, turn on the device and set floor temperature in manual mode to 27 °C:

.. code-block:: json

    {
      "sn":"058016000543464839373520000159",
      "par":[[125,7,"0"],[5,1,"27"]]
    }


.. important::
   When changing device parameters, the command must contain the key ``sn``

.. table:: **Data types**
   :widths: auto   

   ===== =====
   Номер  Тип
   ===== =====
   0     CStringType
   1     int8
   2     uint8
   3     int16
   4     uint16
   5     int32
   6     uint32
   7     bool
   ===== =====


.. table:: **Parameters list**
   :widths: auto

   ======   ==========  =======================    ===========
   Number   Type        Name                       Description
   ======   ==========  =======================    ===========
   0        6 (uint32)  startAwayTime              in seconds from 01.01.2000, away start time
   1        6 (uint32)  endAwayTime                in seconds from 01.01.2000, away end time
   2        2 (uint8)   mode                       mode: schedule=0, manual=1
   3        2 (uint8)   controlType                control tupe: by floor=0, by air=1, extended=2
   4        1 (int8)    manualAir                  in °C, уставка ручного режима по воздуху
   5        1 (int8)    manualFloorTemperature     in °C, уставка ручного режима по полу
   6        1 (int8)    awayAirTemperature         in °C, уставка режима отъезда по воздуху
   7        1 (int8)    awayFloorTemperature       in °C, уставка режима отъезда по полу
   14       2 (uint8)   minTempAdvancedMode        in °C, минимальная температура пола в расширенном режиме
   15       2 (uint8)   maxTempAdvancedMode        in °C, максимальная температура пола в расширенном режиме
   17       4 (uint16)  power                      in a.e., P=(power<=150)?(power*10):(1500+power*20), connected power
   18       2 (uint8)   sensorType                 type of connected temperature sensor: 4,7kOhm=0, 6,8kOhm=1, 10kOhm=2, 12kOhm=3, 15kOhm=4, 33kOhm=5, 47kOhm=6
   19       2 (uint8)   histeresis                 in 1/10 °C, hysteresis
   20       1 (int8)    airCorrection              in 1/10 °C, air temperature sensor correction
   21       1 (int8)    floorCorrection            in 1/10 °C, floor temperature sensor correction
   23       2 (uint8)   brightness                 in a.e. (from 0 to 9) brightness 
   25       2 (uint8)   propKoef                   in minutes when load on within 30-minutes cycle of the proportional mode
   26       1 (int8)    upperLimit                 in °C, max setting value of the floor temperature
   27       1 (int8)    lowerLimit                 in °C, min setting value of the floor temperature
   28       2 (uint8)   maxSchedulePeriod          max number of perioods per day
   29       2 (uint8)   tempTemperature            in °C, temporary mode temperature
   31       2 (uint8)	setTemperature			   in °C, setting temperature of current mode (awayFloorTemperature | manualFloorTemperature | tempTemperature)
   33       1 (int8)    upperAirLimit              in °C, max setting value of the air temperature
   34       1 (int8)    lowerAirLimit              in °C, min setting value of the air temperature
   35       4 (uint16)  upperU                     in volts, upper voltage limit
   36       2 (uint8)   lowerU                     in volts, lower voltage limit
   37       2 (uint8)   upperP                     in 100 W, power limit
   38       4 (uint16)  upperI                     in 1/10 A, upper current limit
   39       4 (uint16)  middleI                    in 1/10 A, middle current limit
   40       4 (uint16)  lowerI                     in 1/10 A, lower current limit
   41       4 (uint16)  tOnDelay                   in seconds, relay on delay
   42       2 (uint8)   tOffDelay                  in seconds, delay off delay after current or power limit exceeding
   43       2 (uint8)   middleITime                in 1/10 seconds, delay off after middle current limit exceeding 
   44       2 (uint8)   lowerITime                 in 1/10 seconds, delay off after lower current limit falling
   45       4 (uint16)  lowVoltageTime             in 1/10 seconds, voltage failure duration
   46       1 (int8)    correctionsU               in V, voltage correction
   47       1 (int8)    correctionsI               in percent, current correction
   48       2 (uint8)   repTimes                   number of relay off before device block
   49       2 (uint8)   powerType                  controlled power type: active(W)=0, reactive(VAR)=1, apparent(VA)=2
   50       2 (uint8)   showType                   parameter to show type: current=0, active power=1, reactive power=2, apparent power=3, cosFi=4
   51       2 (uint8)   sensorСontrolNumber        remote temperature sensor number
   52       4 (uint16)  nightBrightStart           in minutes from 00:00, night low bright start time
   53       4 (uint16)  nightBrightEnd             in minutes from 00:00, night low bright end time
   54       2 (uint8)   wifiPower                  lovel 1..3, Wi-Fi power
   55       2 (uint8)   relayOnTimeLimit           in hours, max allowed time load on until error
   112      7 (bool)    proMode                    professional voltage cutoff delay model
   113      7 (bool)    voltageStableDelay         delay on starts after voltage is ok
   114      7 (bool)    androidBlock               local newort control block
   115      7 (bool)    cloudBlock                 cloud control block
   116      7 (bool)    useContactorControl        load through contactor
   117      7 (bool)    NCContactControl           inverted relay
   118      7 (bool)    coolingControlWay          heat/cool mode
   120      7 (bool)    useNightBright  	       activate using night bright
   121      7 (bool)    preControl                 preheat
   122      7 (bool)    windowOpenControl          open window control
   124      7 (bool)    childrenLock               children protect
   125      7 (bool)    powerOff                   power off
   ======   ==========  =======================    ===========

.. note::
   Manual and away settings temperatures can not be higher than parameter 26 (upperLimit) and lower than parameter 27 (lowerLimit).
