Device search
~~~~~~~~~~~~~

To obtain a list of available devices on the local network UDP broadcast packets are used. After connecting to the network several times per minute, each device sends a UDP packet to port 23500 with JSON data like:

.. code-block:: json

	{
		"sn":"058016000543464839373520000159",
		"hw":"ax",
		"cloud":"true",
		"connection":"cloudCon",
		"wifi":"-71",
		"display":"23.0"
	}


``sn`` - device serial number

``hw`` - device type

``cloud`` - boolean parameter of cloud connection

``connection`` - status of the connection to the cloud
	* wiFiCon - connected to a Wi-Fi network
	* tcpCon, helloCon, readyCon, sslCon - connecting to the cloud
	* cloudCon - connected to the cloud
	* APMode - device in access point mode
	* changeState - switching between modes

``wifi`` - Wi-Fi signal strength in dBm

``display`` - device display reading

