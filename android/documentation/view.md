# ti.dfp.View

## Description

A view for displaying ads delivered through DFP.

## Properties

### string adUnitId

The ad Unit ID for DFP.

### string adWidth (optional)
### string adHeight (optional)

Width and height of desired ad banner (in pixels -- you cannot use unit modifiers here).

If both adWidth and adHeight are non-zero, the module will use them to
explicitly specify the ad size.

Otherwise, use DFP's SMART_BANNER mechanism to find the appropriate creative size.

### string adBackgroundColor (optional)

The background color used for the ad.  

Must be a 6-digit hex string.  Can be specified with or without the "#" symbol, 
e.g. "#ffffff" or "ffffff" are valid.

### string borderColor (optional)

The border color surrounding the ad.

Must be a 6-digit hex string.  Can be specified with or without the "#" symbol, 
e.g. "#ffffff" or "ffffff" are valid.

### string textColor (optional)

The color of text used in text ads.

Must be a 6-digit hex string.  Can be specified with or without the "#" symbol, 
e.g. "#ffffff" or "ffffff" are valid.

### string urlColor (optional)

The color of URLs used in text ads.

Must be a 6-digit hex string.  Can be specified with or without the "#" symbol, 
e.g. "#ffffff" or "ffffff" are valid.

### string linkColor (optional)

The color of links used in text ads.

Must be a 6-digit hex string.  Can be specified with or without the "#" symbol, 
e.g. "#ffffff" or "ffffff" are valid.

### Array[String] testDevices (optional)

An array of test device ids. Adding the id of a test device to this array 
will allow that device to be served test ads. 

Use the module constant `SIMULATOR_ID` to use the simulator as a test device. 
If you do not know the id for your device, launch your app and request an ad 
like you normally would, then look in the console for the id. 

eg. <Google> To get test ads on this device, call: request.testDevices = @[ @"980bb6fbbb6687047c631fe21136869b" ];

Add the id to the array passed to `testDevices`.

### object location (optional)

A dictionary with the location of the user for location-based ads:

* float latitude
* float longitude
* float accuracy

### object customTargeting (optional)

A dictionary with custom key-value pairs used for targeting ads.

## Events

### ad_received

Sent when an ad request loaded an ad.  This is a good opportunity to add this
view to the hierarchy if it has not yet been added.  If the ad was received
as a part of the server-side auto refreshing, you can examine the
hasAutoRefreshed property of the view.

### ad_not_received

Sent when an ad request failed.  Normally this is because no network
connection was available or no ads were available (i.e. no fill).

### ad_opened

Called when an ad opens an overlay that covers the screen.

Use this opportunity to stop animations, time sensitive interactions, etc.

### ad_closed

Called when the user is about to return to the application after clicking on an ad.

Use this opportunity to restart anything you may have stopped as part of "ad_opened".

### leave_application

Called when an ad leaves the application (e.g., to go to the browser).
