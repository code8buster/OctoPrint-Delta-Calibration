This is a plugin for the 3D printer host software, OctoPrint (http://www.octoprint.org).

This plugin is designed to accurately calibrate the RAMBo and Mini-Rambo based line of
delta printers manufactured by SeeMeCNC (http://www.seemecnc.com).  This limitation is 
due to the code looking for special output that is generated by SeeMeCNC's accelerometer 
probe and its associated fork of Repetier Firmware.  This plugin can be modified to include
other models of delta printers if the probe information is supplied.  A printer to test on
would be nice too. :)

The "brains" behind this calibration plugin were graciously supplied by David Crocker (dc42).
David's "least squares" calibration algorithm is so good that it's essentially magic.  The calibration
code in this plugin is the same code that can be found behind his website, here: 
http://www.escher3d.com/pages/wizards/wizarddelta.php.  His calibration routines are also found
in the dc42 fork of RepRapFirmware for the Duet controller.

Many thanks also to Ryan Rittenhouse, SeeMeCNC's new cat herder (software developer).  If it wasn't for
his valuable assistance, this plugin simply wouldn't have worked right for a very long time.

The core of this was shamelessly stripped from https://github.com/platsch/OctoPrint-Autocalibration.
Pretty much the only thing left is the routines used to read/write the EEPROM. :)

To use this plugin, you can install it using pip from a shell prompt:

    pip install https://github.com/code8buster/OctoPrint-Delta-Calibration/archive/master.zip

If you're working with an OctoPi distribution, you can sign into the "pi" account and
install the plugin this way:

    /home/pi/oprint/bin/pip install https://github.com/code8buster/OctoPrint-Delta-Calibration/archive/master.zip

You must also be running a version of Repetier 0.92 or later.  (Issue an M115 to see the firmware date, ex.:
Your max Z height should be pre-set and roughly within 5mm of true.

In order to use the plugin, click on the Settings link in OctoPrint and then click on the
"Delta Autocalibration" link that's listed in the Plugins pane on the lower left.

Click the Load EEPROM button and then click the Begin Delta Calibration button.

You may run it as many times as you like, but you MUST click the Load EEPROM button before you begin
the calibration sequence!  If you fail to do this, the calibration routine will NOT know what the current parameters are and you'll get poor, bad, or moderately catastrophic results.

