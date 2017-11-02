#  Wormhole

A simple application that allows you to simulate any location across all applications on your iOS device. Useful for testing a location-aware iOS application in a realistic environment.

## Setup

1. Add any [destinations](#destinations) you want to simulate.
1. Build and run the included Xcode project on an iOS device.
1. In Xcode, use the Debug ‣ Simulate Location menu or the Simulate Location icon in the debugger toolbar to select a simulated location.
1. On your device, grant Wormhole the Location Services permissions it asks for, so that you can easily see the locations that are being simulated.
1. Switch to any other location-aware application.

**Important:** Once you are done, terminate the debugging session within Xcode **before** unplugging your device. Otherwise, the wormhole will close, trapping you and your phone at the last simulated location, even after restarting. Hope you like the weather there!

## Destinations

A few stationary simulated locations have been provided in the Destinations group, but you can also provide your own GPX tracks:

1. Go to File ‣ New ‣ File and choose the “GPX File” template.
1. Add the file to the Wormhole target.
1. Stop the debugger (if it is running) and rebuild and run the application under the debugger.

Note that Xcode only recognizes `<wpt>` elements, not `<trkpt>` elements. By default, the simulation steps through each waypoint in a .gpx file in order at a rate of one waypoint per second. Recent versions of Xcode can interpolate between the waypoints based on the specified timestamps, as long as the waypoints are sorted in chronological order. Core Location’s heading, course, and speed readings are not simulated, even if the relevant data is included in the GPX track.

You can find freely available GPX tracks [at OpenStreetMap](https://www.openstreetmap.org/traces/), but note that these tracks must be converted to an Xcode-compatible format as detailed above.

## See also

* [PokemonGoMove](https://github.com/huacnlee/PokemonGoMove/) takes this concept a step further to facilitate _Pokémon GO_ gameplay.
* [GuideDog](https://github.com/frederoni/GuideDog/) is a library for simulating location updates from within an application. It offers more control over the location updates but only works in applications that you can build from source code.
