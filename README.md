# Hackintosh Atheros Wiffi (Legacy Cards)
Enabling legacy Atheros Wiffi cards in Monterey, Ventura, and Sonoma that are not detected by OpenCoreLegacyPatcher.
Atheros Wiffi (“Legacy” Cards):

Let's keep in mind that the only "Atheros" chips used by Apple in any Mac are:

There are devices that work without adding any properties (they were used in some Mac models) and only following the OCLP guide to enable them, so if we are using a board that contains any of these IDs it is not necessary to perform a Fake-ID. 
These are:

pci168c,30 = 30000000  
pci168c,2a = 2A000000  
pci106b,0086 = 00860000  
pci168c,1c = 1C000000  
pci168c,23 = 23000000  
pci168c,24 = 24000000 

Researching these chips were used in these models:

1- AR9280 = iMac11.X = IOName: pci168c,2a
2- AR9380 = iMac12.X = IOName: pci168c,30

We always assume that to make a Fake-ID we must look for a compatible device that is as similar as possible to the one we are going to fake.

So, as an example, if we have an AR9287 Chip with an IOName “pci168c,2e” the IOName that we must use is “pci168c,2a” and a device-id “2A000000”.

Steps to follow: 

1- It is necessary to rename the device to ARPT in the ACPI configuration. For this we can use the attached SSDT-ARPT.dsl to which we must edit the path and compile it as SSDT-ARPT.aml. 

2- It is essential to add these properties in the Device Properties: IOName, compatible and name (pci168c,XX), and also device-id (XX000000), where the "X" are the value that corresponds to the chip.  

For this I also leave the configuration for two possible chips that, if used, we must edit the device paths.
