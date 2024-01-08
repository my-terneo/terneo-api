Safety
~~~~~~

Possibility of device control with enabled ``LAn`` locking (`Parameter <parameters.html>`_ 114 ``androidBlock`` = **1**; ``bLc`` = **Lan**) is implemented in software version 2.4.

.. note ::
		If both locks are tuned on (``androidBlock`` = **1**, ``cloudBlock`` = **1**; ``bLc`` = **on**) device is locked for any control by network. Only buttons can change device parameters.

TOTP protocol is used for source authentication when sending commands to the device (**rfc4226**, **rfc6238**, Interval = 30second, Digit = 9). 
For this purpose it is necessary to add two fields in front of the data fields:

``time`` - time in seconds from 01.01.2000 00:00

``auth`` - calculated token.
 
 .. code-block:: json
 
	{
	 "sn":"058016000543464839373520000159",
	 "time":"634929122",
	 "auth":"672201707",
	 "par":[[125,7,"0"], [23,2,"1"], [114,7,"1"]]
	}

The key for token generation can be obtained through `Server API <keyGet.html>`_.

If you don't need to use authentication, or if you are using software version 2.3, you must disable ``LAn`` locking (``androidBlock`` = **0**).

You can view the lock status as ``m.3`` key in the telemetry or ``androidBlock`` parameter in the parameters or in the menu item ``bLc``.

The blocking is disabled through the device menu - the ``bLc`` parameter must be changed to **oFF**.

.. note ::
		* 2-button devices you need to hold the menu button to the inscription ``bLc``, then release and select **oFF**
		* Press shortly middle button for 3 or more buttons devices as many times as inscription ``bLc`` is appered, then change the selection buttons to **oFF**