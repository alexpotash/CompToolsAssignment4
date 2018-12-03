# CompToolsAssignment4
Script and datafile for Comp Tools Assignment4
1. Data

Column | Description
-------|--------------------------------------------------------------------------------------------------------------
| Site |	Two letter string referring to the name of the exclosure or control site (HP – Holt Pond, GG – Green Grove) |
-------|--------------------------------------------------------------------------------------------------------------
| Treatment |	Single letter string referring to whether the site is an exclosure (X) or control (C) |
-------------|--------------------------------------------------------------------------------------------------------
| Transect |	A 4 character alphanumeric string referring to a 3-tray transect of experimental foraging patches. First two letters refer to site, third letter refers to treatment, and final number refers to the order the treatment was deployed. |
-----------|----------------------------------------------------------------------------------------------------------
| Tray |	A single number (1, 2, or 3) that refers to the position of the tray in the transect. “1” is closest to a tree, “2” is 1-3m farther away, and “3” is the farthest from a tree. |
--------|-------------------------------------------------------------------------------------------------------------
| TranBlock |	The name of the transect block that accounts for spatial autocorrelation for all transects located within 100m of | each other. |
---------|------------------------------------------------------------------------------------------------------------
| Name |	A 6 character alphanumeric string that refers to specific tray within a transect. |
----------|-----------------------------------------------------------------------------------------------------------
| GUDDate |	Experimental date (yyyy-mm-dd) |
-----------|----------------------------------------------------------------------------------------------------------
| ID |	Concatenation of Name and Date. |
-----------|---------------------------------------------------------------------------------------------------------
| C_GUD |	Mass (g) of pecans consumed by fox squirrels on experimental date. Float. |
-----------|---------------------------------------------------------------------------------------------------------
| Dist |	Distance (m) of tray from nearest tree. Float. |
------------|---------------------------------------------------------------------------------------------------------
| VegDate |	Date vegetation was measured (dd-mm-yyyy). |
-------------|--------------------------------------------------------------------------------------------------------
| Robel_Mean |	Mean Robel Pole measurements from 4 cardinal directions (float) |
--------------|-------------------------------------------------------------------------------------------------------
| Wiregrass |	Percent cover of wiregrass in a 1x1m quadrat around experimental tray. Integer. |
---------------|------------------------------------------------------------------------------------------------------
| Other_Grass |	Percent cover of other grass (not wiregrass) in a 1x1m quadrat around experimental tray. Integer. |
----------------|-----------------------------------------------------------------------------------------------------
| Forb |	Percent cover of forbs in a 1x1m quadrat around experimental tray. Integer. |
-----------------|----------------------------------------------------------------------------------------------------
| WoodVeg |	Percent cover of woody vegetation in a 1x1m quadrat around experimental tray. Integer. |
------------------|---------------------------------------------------------------------------------------------------
| Litter |	Percent cover of vegetation litter in a 1x1m quadrat around experimental tray. Integer. |
-------------------|--------------------------------------------------------------------------------------------------
| Other |	Percent cover of other in a 1x1m quadrat around experimental tray. Integer.Percent_Canopy	Percent canopy cover directly above experimental tray measured using a spherical densiometer. Float. |
--------------------|-------------------------------------------------------------------------------------------------
