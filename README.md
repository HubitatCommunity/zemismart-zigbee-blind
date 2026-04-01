# Zemismart Zigbee Blind - NEW HOME!

We would like to express our gratitude to Amos Yuen, the original author of the Zemismart Zigbee Blinds driver, for his valuable contribution to the Hubitat community.

As the original repository is no longer available, the driver has now been relocated to its new home in the Hubitat Community GitHub repository:

https://raw.githubusercontent.com/HubitatCommunity/zemismart-zigbee-blind/refs/heads/main/Zemismart%20Zigbee%20Blind.groovy 

We welcome new contributors to submit Pull Requests on GitHub for new devices or other enhancements!

# Prerequisites

You should follow the instructions that came with your device to set the open and close limits. Some models set the limits using the device, others require the remote. This is needed in order to open or close properly.

This driver can set limits for a very limited number of models only!

# Installation Options

TODO

# Product Links

TODO


# Capabilities

* Open
* Close
* Stop
* Step Open
* Step Close
* Push Button (1 = Open, 2 = Close, 3 = Stop, 4 = Step Open, 5 = Step Close)
* Get and set direction
* Get and set position [0-100]
* Get and set mode (if supported by device)
* Get and set speed [0-100] (if supported by device)
* Presence indicating if the device has responded to commands
* Configurable open and closed position thresholds
* Configurable default step amount

## Supported Devices

TODO

# Google Home Integration

Recommended integrating with Google Home through hubitat [Google Home Community](https://community.hubitat.com/t/alpha-community-maintained-google-home-integration/34957) with the following settings:

* `Device type`: `Window Shade`
* `Google Home device type`: `Curtain`
* `Device traits`
	* `Open/Close`
		* Set `Open/Close attribute` to `windowShade`
		* Set `Open Position Command` to `setPosition`