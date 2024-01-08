Commands
~~~~~~~~

To get device parameters use ``cmd`` key.
Possible values:

	* 1 - `parameters <parameters.html>`_ request
	* 2 - `schedule <schedule.html>`_ request
	* 3 -  time getting request (available in firmware versiom 2.4 and higher)	
	* 4 - `telemetry <telemetry.html>`_ request
	* 5 - `parameters <parameters.html>`_ reset request
	* 6 - `schedule <schedule.html>`_ reset request
	
 

Example ``{"cmd":1}``

`Parameters <parameters.html>`_ request

Answer: 

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

Example ``{"cmd":2}``

`Schedule <schedule.html>`_ request

Answer:

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

Example ``{"cmd":3}``

Time getting request (available in firmware versiom 2.4 and higher)

Answer: 

.. code-block:: json
 
	{
		"sn":"058016000543464839373520000159",
		"time":"634993283"
	}

Where ``time`` - time in seconds from 01.01.2000 00:00

Example ``{"cmd":4}``

`Telemetry <telemetry.html>`_ request

Answer:

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

Example ``{"cmd":5}``

`Parameters <parameters.html>`_ reset request. Request must include «sn». When blocking changes from the local network ([114,7,»1»]) is set, the «auth» and «time» keys must be included in the request `Security  <safety.html>`_.

Answer:

.. code-block:: json

 	{
	 "sn":"058016000543464839373520000159", "par":[[0,6,"536112000"],[1,6,"536112000"],
	 [2,2,"1"],[3,2,"0"],[4,1,"30"],[5,1,"30"][6,1,"25"],[7,1,"5"],[18,2,"2"],[19,2,"10"],
	 [21,1,"0"],[23,2,"6"],[25,2,"15"],[26,1,"45"],[27,1,"5"],[28,2,"16"],[29,1,"0"],
	 [17,4,"175"],[114,7,"1"],[115,7,"0"],[116,7,"0"],[117,7,"0"],[118,7,"0"],[121,7,"0"],
         [122,7,"0"],[124,7,"0"],[125,7,"0"]]
	}

Example ``{"cmd":6}``

`Schedule <schedule.html>`_ reset request reset request. Request must include «sn». When blocking changes from the local network ([114,7,»1»]) is set, the «auth» and «time» keys must be included in the request `Security  <safety.html>`_.

Answer:

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

At [114,7,"1"]

Answer:

.. code-block:: json

	{"success":"block"}