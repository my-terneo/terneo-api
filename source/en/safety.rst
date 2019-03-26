Safety
~~~~~~

Devices with software version 2.3 don't have authentication and data encryption when controlling via LAN, so this feature is disabled by default.

You can view the lock status: ``m.3`` key in telemetry or ``androidBlock`` parameter in the settings.

The blocking is disabled only through the device menu - the ``bLc`` parameter must be changed to **oFF**.

.. note ::
	To disable blocking in software version 2.3:
		* 2-button devices you need to hold the menu button to the inscription ``bLc``, then release and select **oFF**
		* Press shortly middle button for 3 or more buttons devices as many times as inscription ``bLc`` is appered, then change the selection buttons to **oFF**