# WaterSensor
Water sensor PCB design project.


Given: 5V Source
Want: 1'x 1' Water Sensor
Constraints: Vout to have a maximum of 3.3V for analog read in, Minimize current draw to be on the magnitude of 1mA

Use N23904 NPN transistor for low current and high robustness. Open schematic for reference.

Calculations
--------------------------------------------------------------------------------------------------------------------------
Assume forward active region:

If we want Vout to have a maximum of 3.3V and we want to minimize current draw to be on the magnitude of 1mA

R2 = 3.3V/1mA = 3.3k ohm 

Ie = 1mA

From testing 2N3904 (did not know the company that made the provided transistor): For Ic = 1mA @ 25 deg celsius, hfe or betaforward current gain is 300.

Ib = Ie/300 = 3.333micro A

We know that Ie = Ic+Ib so Ic = 299/300Ie. They are roughly equal. From testing 2N3904: For Ic = 1mA @ 25 deg celsius, Vbe = 0.67 V.

Vs-(R2*Ib)-Vbe <= Vout ----> 5V-(R2*3.333micro A)-0.67V <= 3.3V

R2 >= 309.03k ohm ---> R2 = 330k ohm



Discussion
--------------------------------------------------------------------------------------------------------------------------
The water sensor is designed with maximum sensitivity in mind. Per competition requirements: Need to detect a 20mL hit but points are awarded for detection of smaller mL hits.

Sensitivity can be decreased by increasing the spacing between the power lines and the copper fill connected to the base of the transistor. 
Additionally, every other power line can be removed to decrease sensitivity.

One potential issue with such a high level of sensitivity is that there is the possibility of a near hit miss balloon that is able to splatter up and over the board onto the sensor.
A mitigation technique for this issue is to erect walls on the border of the marker to prevent ground splash onto the sensor.

Another potential issue is the usage of deionized water. This design works by causing a "short" between two terminals.
A mitigiation technique for this issue is to place a layer of fine grain salt on the board. Salt itself is not conducting. However, it will provide conductivity when placed inside a medium.

Testing w/o AruCo marker, Vout readings: 1 drop - 2.75V, 2 drop - 2.9V, 3 drop - 2.94V, 4 drop - 2.96, 5 drop - 3V, 6 drop - 3V, 7 drop - 3.03V, 8 drop - 3.06V, 9 drop - 3.07V, 10 drop - 3.08V, 11 drop - 3.09V,  12 drop - 3.11V, Saturated - 3.3V


1mL is roughly 25 drops