**MQTT**
========

Starting from firmware version 2.4 there's a possibility to collect telemetry and manage some parameters via MQTT protocol.
MQTT server connection settings are available only via the device web-interface:

``Host``/``Port`` - IP address and port of the MQTT server

``Uer``/``Password`` - username and password to connect

``Keep alive`` - the maximum allowed period of time without data exchange

``QoS`` - quality of service level

``Publish prefix`` - publication prefix for sending telemetry

``Subscribe path`` - name of the way to subscribe to commands

``Client ID`` - device name

In software version 2.4 data are published every minute in the following topics:

``Publish prefix``/``Client ID``/``FloorTemp`` - floor temperature sensor readings (`temetry <telemetry.html>`_ **"t.1"**) in °C as "xx.x".

``Publish prefix``/``Client ID``/``protTemp`` - readings of the internal overheat sensor (`temetry <telemetry.html>`_ **"t.0"**) in °C as "xx.x".

``Publish prefix``/``Client ID``/``setTemp`` - setpoint temperature (`temetry <telemetry.html>`_ **"t.5"**) in °C as "xx.x".

``Publish prefix``/``Client ID``/``load`` - load status `(temetry <telemetry.html>`_ **"f.0"**) by string "0" - off, "1" - on.

The following control topics are available in software version 2.4:

``Subscribe path``/``Client ID``/``setTemp`` - setpoint temperature, similar to ``setTemperature`` `parameter <parameters.html>`_.

``Subscribe path``/``Client ID``/``bright`` - display brightness, similar to ``brightness`` `parameter <parameters.html>`_.

``Subscribe path``/``Client ID``/``powerOff`` - device shutdown, similar to ``powerOff`` `parameter <parameters.html>`_.

``Subscribe path``/``Client ID``/``mode`` - selection of the operation mode, similar to ``mode`` `parameter <parameters.html>`_.
