![Alt text](https://github.com/Rootthecause/HVI/blob/main/doc/Pictures%20and%20Renderings/HVI%201%20Title.png?raw=true)

Dear Formula Student Teams,

I've designed a High Voltage Indicator in accordance with [EV 5.4.8](https://www.formulastudent.de/fileadmin/user_upload/all/2024/rules/FS-Rules_2024_v1.1.pdf#subsubsection.4.5.4.8) to replace our heavy and bulky voltmeter. This device can supply between 5 V and 24 V (depending on the configuration) at a maximum of 1 W (isolated) or 3 W (non-isolated) from a 40 V to 800 V source. Two LEDs on the back indicate the presence of high voltage, so it can be mounted either directly to a viewing window in the TSAC or elsewhere with a cable to an external LED. As it is basically an HV step-down converter, it can also be used for any other application, e.g. to start a DC/DC (for LVS supply) from HV with the added benifit of significantly higher efficiency (50-80%) compared to an LDO (few percent).<br>

Most components used are standard parts, but key components include URLs linking to Mouser or datasheets (for quick access: highlight part, press "D").<br>

This design is published as open-source hardware under the CERN-OHL-W license and can be found on GitHub: https://github.com/Rootthecause/HVI<br>
If you have received any files from me directly, please do not share or publish them, as I don't want others to share files which may be incomplete or contain errors.<br>

Although this design has passed FSG scrutineering and has been operating without any issues for over 3 months, always manufacture at your own risk!<br>

If you encounter any bugs or have suggestions for improvement, please feel free to use the GitHub [issues form](https://github.com/Rootthecause/HVI/issues/new). For discussions and technical questions, kindly use the [discussion bord](https://github.com/Rootthecause/HVI/discussions).<br>

Best regards,
Rootthecause

![Alt text](https://github.com/Rootthecause/HVI/blob/main/doc/Pictures%20and%20Renderings/HVI%203%20Top%20angle%20transparent.png?raw=true)

![Alt text](https://github.com/Rootthecause/HVI/blob/main/doc/Pictures%20and%20Renderings/Efficiency%20vs.%20Input%20Power.png?raw=true)

**Backside**
![Alt text](https://github.com/Rootthecause/HVI/blob/main/doc/Pictures%20and%20Renderings/HVI%20Bottom.jpeg?raw=true)

**Front with case (SLA printed)**
![Alt text](https://github.com/Rootthecause/HVI/blob/main/doc/Pictures%20and%20Renderings/HVI%20with%20case%20size.jpg?raw=true)

# VERSION HISTORY
```
v0	DIY etched prototype. Working, but not optimized
v1.0	commercial PCB with optimized components, tested for more than 3 months.
v1.1	Small layout changes and improvements, not tested but should be fine
```

# FILE STRUCTURE
```
- Readme
- LICENSE
- KiCAD Files
v doc
	> 3D Printing
	v bom	
		- ibom.html
	v Gerber for JLC Order
		> Gerber
		- JLC Order Settings
		- Gerber for JLC Order.zip
	> HV Generator
	- HVI Dimensions.pdf
	- HVI Schematic.pdf
	> LTSPice Simulation
	> Pictures and Renderings
```

Have fun. 
Do not lick things with spark symbols on :) 


# Q&A
Q: 	&ensp;Which KiCAD Version was used?<br>
A: 	&ensp;Curently it's KiCAD 8.0.5<br>

Q: 	&ensp;Why are 2x 4.7 mH inductors used instead of a 10 mH inductor?<br>
A: 	&ensp;You will rarely find maximum voltage values for SMD inductors, so just an extra precaution.<br>

Q: 	&ensp;Why is there no output fuse?<br>
A: 	&ensp;The VIPER06 can be short-circuited indefinitely.<br>

Q: 	&ensp;I need [insert voltage here], can I do that?<br>
A: 	&ensp;You can either change PS1 (12 V to 3.3 V to 24 V converters available) 
	or (when used directly without PS1) the feedback voltage divider can be altered.
	I do not reccomend going above 23.5 V because the IC's VDD voltage will be clamped, 
	which could lead to high losses or destruction of the IC. Going below 11.5 V 
	will use the internal high-voltage generator as IC's VDD supply (higher losses).
	So ideally, stay between 12 V and 23 V.<br>

Q: 	&ensp;Where do I get a cheap high voltage source for testing?<br>
A: 	&ensp;I have been using one for 10€ from amazon for many years, which can generate up to 
	800 V (when both -+400 V rails are used) from a 8 to 32 V source (15 V input delivers most HV power, 25 W max.).
	If you want to support me, you can use my affiliate link where I get a small commission 
	when a purchase is made: https://amzn.to/3TRJJif<br>
	In the docs there is an additional folder 'HV Source' for a 3D-printed case which also 
	uses a rotary potentiometer instead of the trim pot. If there is enough interest, I will make a build guide for it.<br> 
	Please add 100 uF (check voltage rating!) or more externally to the output, otherwise the feedback loop can be unstable.<br> 
	
Q: 	&ensp;I need more Power!<br>
A: 	&ensp;A smaller Inductor value could help, but be aware that the minimum on-time is 400 ns.
	At high input voltages this could lead to overcurrent when using small inductro values.<br>

Q: 	&ensp;Why is the text "Voltage Indicator", "Designed by XXX" and "HVI vX.X" not editable?<br>
A:	&ensp;I like to use a font (Futured) for visuals which is not pre-installed on most systems. 
	Importing it as a logo is easier to retain it.<br> 

Q: 	&ensp;Some 3D models on the PCB are missing.<br>
A:	&ensp;They are not inluded due to licence terms. However, you can download them from https://www.samacsys.com/ using the Mouser link provided in the properties of the KiCAD components.<br> 

Q:	&ensp;This is open source. Can I modify it? Can I sell it?<br>
A:	&ensp;Sure! But please use your own version numbering and change "Designed by Rootthecause" 
	to "Designed by [Your Name] based on a design by Rootthecause". 
	As this is licensed under CeRN OHL v2 Weakly Reciprocal, you must disclose the source, 
	state changes and use the same license if used for non private projects.
	Learn more about this here: https://choosealicense.com/licenses/cern-ohl-w-2.0/<br>

Q:	&ensp;I've got a question not listed here, can I contact you?<br>
A:	&ensp;Please use the [issues form](https://github.com/Rootthecause/HVI/issues/new) on GitHub for techical related questions.<br> 

Q:	&ensp;Is there a way to support your projects?<br>
A:	&ensp;Yes: https://ko-fi.com/rootthecause<br>
