![ArduinoLog logo](/Resources/logo.png?raw=true )
Raise3D Pro 3+ for Cura
====================
[![License](https://img.shields.io/badge/license-MIT%20License-blue.svg)](http://doge.mit-license.org)

*Raise3D printer profile for Cura*

This Github is an ongoing effort to create a good printer profile for the Raise3d Pro 3(+) in Cura. It defines, the printer, extruder, nozzles and materials. It also comes with an installer (script) that helps to install the printer profile for all installed instances of Cura. 

It is my hope that other people will try out and help tune the profile untill the quality is as good as can be expected from the printer.

# Directory structure
* **Installer**
The installer requires InnoSetup to be present. It will  install the printer profile for all installed instances of Cura. Currently it has only been tested for Windows 10, but will likely work for other versions as well.  
* **Resources**
Here you can find or place resources that are/were used to create the profile. 
* **Cura**
This contains the actual definitions. **Current** contains the current state of the art, whereas the **Archive** folder holds older versions. Of course all changes are captured by git, but I found it usefull to keep the older versions to easily compare against. Each version has a **Release** folder, containing the definitions and a **Results folder** containing photo's and descriptions of the print results.
   * **Cura/Archive/V1**
The first basic profile created based on IdeaMaker settings and Pro2 efforts. Start & Stop G-code was extracted from Ideamaker (4.2.3). The first 2 benchies failed due to insufficient build plate adhesion. 
   * **Cura/Archive/V2**
Updated profile with settings from Ultimaker S5 & Creatility, added quality variants, nozzle variants & materials (based on Creality). This produced the first succesfull Benchy! The bottom looked good,but the benchy had a very strong  hull line, ugly overhangs and with clear drooping and the bridging locations.

![Benchy hull line](/Cura/Archive/v2/Results/IMG_1433.jpg?raw=true)

 * **Cura/Current**
contains the current state-of-the-art. All notes, issues & todo's below target this version. 

# Current status
* Integrated Ultimaker S5 settings in definitions. This strongly improved the print quality. The benchys first layer was significantly better, the hull was much smoother, no adhesion issues. 
* Added Raise3D base plate
* Set default cooling fan speed to 100% (instead of 50%) significantly improves the benchy test, in particular the hull, overhangs and bridges. 

# To do
* Validate the geometry settings. Try out by placing objects at the edge of the build plate, can we cover the same area as in Ideamaker, this area should be different for nozzle 1 & 2.
* Try "One at a Time" printing. I have little experience with this, but I imagine it requires that when printing the 2nd part, 1) not bumping the gantry into the first part, 2) if the first object is tall enough,  not hitting it with the crossbars. I believe this means getting `gantry_height` and `machine_head_with_fans_polygon` correct. I expect the current values are about correct, but for `machine_head_with_fans_polygon` I'm not clear what origin is. Is it nozzle 1? And how does that work when printing with nozzle 2?
* Try out if the cooling fans are separately adressed. Currently 
* Interpret the Start G-code and improve annotation. Send out G codes manually, what are the moves doing? Is this the best G-code possible, or do we want to for example do what Cura is doing, by printing a test strip before starting.
* Test and tune the profiles for any material, see section validating materials
* Debug possible issue: The benchy print completes without any issues, but the next print will not extrude correctly. Unloading & reloading seems to solve the issue. Is this an issue in the end G-code or is an issue with the (budget) PLA.
* The benchy still has some issues at the infamous the Benchy hull line. Following the [investigation by Prusa](	
https://help.prusa3d.com/article/the-benchy-hull-line_124745) and the [suggestions by GhostKeeper](https://github.com/Ultimaker/Cura/issues/9244), snd see if this will improve the print. Because the line relates to the material shrinkage and the object geometry, this should be a tuning for the benchy only. 

# Want to help?
Picking up any of the items from the todo list would be hugely appreciated! Doing test prints with different materials and different qualities and making pictures would help as well!

Some pointers on editting the definition file:
It's easy to make mistakes in the json syntax, so please use a json lint tool to check it after editting
https://www.jslint.com/

The Start & Stop G-code is defined in definition.json, and is escaped. If you want to change the code you can extract the G-code from definitions.json, unescape it, make your edits, escape it and plug the changes back in
https://www.freeformatter.com/json-escape.html


