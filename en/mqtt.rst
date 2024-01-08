**MQTT**
========

Starting from firmware version 2.4 there's a possibility to collect telemetry and manage some parameters via MQTT protocol.
MQTT server connection settings are available only via the device web-interface, which is available at its local IP address:

``Host``/``Port`` - IP address and port of the MQTT server

``User``/``Password`` - username and password to connect

``Keep alive`` - the maximum allowed period of time without data exchange

``QoS`` - quality of service level

``Publish prefix`` - publication prefix for sending telemetry

``Subscribe path`` - name of the way to subscribe to commands

``Client ID`` - device name

.. note::
		If no authorization is configured on the MQTT server, the ``User``/``Password`` fields are ignored.

In software version 2.5 data are published every minute in the following topics:

``Publish prefix``/``Client ID``/``get``/``floorTemp`` - floor temperature sensor readings (`temetry <telemetry.html>`_ **"t.1"**) in °C as "xx.x" (models with floor temperature sensor).

``Publish prefix``/``Client ID``/``get``/``airTemp`` - air temperature sensor readings (`temetry <telemetry.html>`_ **"t.2"**) in °C as "xx.x" (models with air temperature sensor).

``Publish prefix``/``Client ID``/``get``/``protTemp`` - readings of the internal overheat sensor (`temetry <telemetry.html>`_ **"t.0"**) in °C as "xx.x".

``Publish prefix``/``Client ID``/``get``/``setTemp`` - setpoint temperature (`temetry <telemetry.html>`_ **"t.5"**) in °C as "xx.x".

``Publish prefix``/``Client ID``/``get``/``powerOff`` - device is turned off `(temetry <telemetry.html>`_ **"f.16"**) by string "0" - on, "1" - off.

``Publish prefix``/``Client ID``/``get``/``load`` - load status `(temetry <telemetry.html>`_ **"f.0"**) by string "0" - off, "1" - on.

The following control topics are available in software version 2.5:

``Subscribe path``/``Client ID``/``set``/``setTemp`` - setpoint temperature, similar to ``setTemperature`` `parameter <parameters.html>`_.

``Subscribe path``/``Client ID``/``set``/``bright`` - display brightness, similar to ``brightness`` `parameter <parameters.html>`_.

``Subscribe path``/``Client ID``/``set``/``powerOff`` - device shutdown, similar to ``powerOff`` `parameter <parameters.html>`_.

``Subscribe path``/``Client ID``/``set``/``mode`` - selection of the operation mode, similar to ``mode`` `parameter <parameters.html>`_.
