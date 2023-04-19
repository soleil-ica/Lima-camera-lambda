Lambda Tango device
====================

This is the reference documentation of the Lambda Tango device.

you can also find some useful information about the camera models/prerequisite/installation/configuration/compilation in the :ref:`Lambda camera plugin <camera-lambda>` section.

Properties
----------

This camera device has no property.

===================== =============== ========================== ==============================================================
Property name	      Mandatory	      Default value	             Description
===================== =============== ========================== ==============================================================
config_path           Yes             /opt/xsp/config/system.yml path the manufacturer configuration file of the detector
                                                                 should be something like: /opt/xsp/config
DistortionCorrection  Yes			  True						 Set distortion correction		
===================== =============== ========================== ==============================================================

Attributes
----------
======================= ======= ======================= ========================================================================
Attribute name		    RW	    Type			        Description
======================= ======= ======================= ========================================================================
configFile              ro      DevString               The configuration file used to initialize the detector
distortionCorrection    ro      DevBoolean              Return **True** if the distorsion correction is active
temperature             ro      DevDouble               The detector temperature in C
humidity                ro      DevDouble               The detector humitity in %
energyThreshold	        rw	    DevDouble		        The energy threshold  in KeV
high_voltage		    ro	    DevDouble		        The high voltage, relevant only for CdTe model
linearityCorrection     rw      DevBoolean              Return **True** if correction of counts is enabled
saturationFlag          rw      DevBoolean              Return **True** if flagging of saturated pixels is enabled
saturationThreshold     rw      DevBoolean              The detector saturation threshold in counts/sec/pixel
libraryVersion          ro      DevString               The version of the library as a string in the format "major.minor.patch"
======================= ======= ======================= ========================================================================

Distorsion_correction, temperature and humidity are only relevant with detector equiped with the latest harwdare 
and firmware, since mid of 2020.

Commands
--------

=======================	=============== =======================	======================================
Command name		    Arg. in		    Arg. out		        Description
=======================	=============== =======================	======================================
Init			        DevVoid 	    DevVoid			        Do not use
State			        DevVoid		    DevLong			        Return the device state
Status			        DevVoid		    DevString		        Return the device state as a string
=======================	=============== =======================	======================================


