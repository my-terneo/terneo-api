Introduction
~~~~~~~~~~~~

This document describes the protocol for the interaction of third-party applications with ** DS Electronics ** devices.

For Wi-Fi devices with a firmware version higher than 2.3, direct control via a local network is available. Information is exchanged through POST requests at http: // `` dev_ip``/api.cgi, where `` dev_ip`` is the ip address of the device on the local network. To detect new devices on the local network broadcast packets is used. Data is presented in JSON format.

.. important ::
In version 2.3, the ability to control the local network by default `blocked <safety.html>` _ for security reasons.

In version 2.3 the following keys are available:

`` sn`` - the serial number of the device, required when transferring new parameters.

`` cmd`` - send `commands <comands.html>`_ to receive data from the device (`parameters <parameters.html>`_, `schedule <schedule.html>`_, `telemetry <telemetry.html>`_)

`` par`` - change device `parameters <parameters.html>`_

`` tt`` - transfer new `schedule <schedule_ru.html>`_

.. important ::
	It is impossible to transfer the schedule and parameters in one request, as well as several days of the schedule.

.. note ::
   The device has a page http://``dev_ip``/api.html, where you can check requests and test the exchange protocol.