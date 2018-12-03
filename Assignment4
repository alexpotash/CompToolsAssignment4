# CompToolsAssignment4


### Question 1:

|Column | Description|
|---|---|
| Site |	Two letter string referring to the name of the exclosure or control site (HP – Holt Pond, GG – Green Grove) |
| Treatment |	Single letter string referring to whether the site is an exclosure (X) or control (C) |
| Transect |	A 4 character alphanumeric string referring to a 3-tray transect of experimental foraging patches. First two letters refer to site, third letter refers to treatment, and final number refers to the order the treatment was deployed. |
| Tray |	A single number (1, 2, or 3) that refers to the position of the tray in the transect. “1” is closest to a tree, “2” is 1-3m farther away, and “3” is the farthest from a tree. |
| TranBlock |	The name of the transect block that accounts for spatial autocorrelation for all transects located within 100m of | each other. |
| Name |	A 6 character alphanumeric string that refers to specific tray within a transect. |
| GUDDate |	Experimental date (yyyy-mm-dd) |
| ID |	Concatenation of Name and Date. |
| C_GUD |	Mass (g) of pecans consumed by fox squirrels on experimental date. Float. |
| Dist |	Distance (m) of tray from nearest tree. Float. |
| VegDate |	Date vegetation was measured (dd-mm-yyyy). |
| Robel_Mean |	Mean Robel Pole measurements from 4 cardinal directions (float) |
| Wiregrass |	Percent cover of wiregrass in a 1x1m quadrat around experimental tray. Integer. |
| Other_Grass |	Percent cover of other grass (not wiregrass) in a 1x1m quadrat around experimental tray. Integer. |
| Forb |	Percent cover of forbs in a 1x1m quadrat around experimental tray. Integer. |
| WoodVeg |	Percent cover of woody vegetation in a 1x1m quadrat around experimental tray. Integer. |
| Litter |	Percent cover of vegetation litter in a 1x1m quadrat around experimental tray. Integer. |
| Other |	Percent cover of other in a 1x1m quadrat around experimental tray. Integer.Percent_Canopy	Percent canopy cover directly above experimental tray measured using a spherical densiometer. Float. |


### Question 2:

2. To normalize the data I will break the data into a GUD table and a Veg Table. This is because the vegetation metrics for each tray are the same as they were only measured once during the season. By making a separate vegetation table I will reduce the redundancy of having 10 vegetation columns repeated for every line.

The GUD table will contain the columns: 

Site
Treatment
Transect
Tray
TranBlock
Name
GUDDate
ID
C_GUD

ID will be the primary key because it is a unique identifier since each tray could only be measured once per day. The Name column will be a foreign key that connects to the Veg table.

The Veg table will contain the columns

Name
Dist
VegDate
Robel_Mean
Wiregrass
Other_Grass
Forb
WoodVeg
Litter
Other
Percent_Canopy

Name will be the primary key, because the vegetation at each tray was only measured once. The Name column will also be a foreign key for the GUD table, allowing me to connect the daily GUD data to the environmental conditions at each tray.


### Question 3 and 4:

###### Create SQL database from GUD data
```
from sqlalchemy import create_engine
from sqlalchemy import Table, Column, Integer, String, MetaData, ForeignKey
from sqlalchemy import DateTime, Boolean
from sqlalchemy import exists
from sqlalchemy import sql, select, join, desc
import csv
import os
import pandas as pd

# Create a sqlite database
engine = create_engine('sqlite:///GUD.sqlite')

metadata=MetaData(engine)

# Try to load GUD info from database, if not there, create it.
try:
    GUD=Table('GUD', metadata, autoload=True)
except:
    Airports = Table ('GUD', metadata,
                Column('Key', Integer, primary_key=True, autoincrement=True),
                Column('Site', String),
                Column('Treatment', String),
                Column('Transect', String),
                Column('Tray', Integer),
                Column('TranBlock', String),
                Column('Name', String),
                Column('GUDDate', String),
                Column('ID', String),
                Column('C_GUD', Numeric)
               )

try:
    Veg=Table('Veg', metadata, autoload=True)
except:
    Veg = Table ('Veg', metadata,
                 Column('Name', String, ForeignKey("GUD.Name"), primary_key=True),
                 Column('Dist', Numeric),
                 Column('VegDate', String),
                 Column('Robel_Mean', Numeric),
                 Column('Wiregrass', Integer),
                 Column('Other_Grass', Integer),
                 Column('Forb', Integer),
                 Column('WoodVeg', Integer),
                 Column('Litter', Integer),
                 Column('Other', Integer),
                 Column('Bare', Integer),
                 Column('Percent_Canopy', Numeric),
                )

metadata.create_all(engine)

conn = engine.connect()

GUDTable=open("/Users/alexpotash/GradSchool/Classes/PhD/Fall2018/Programming/Assignment4/GUD_Table2.csv")
reader = csv.DictReader(GUDTable)

Veg_dict={}

for Line in reader:
    if Line['Name'] not in Veg_dict:
        Veg_dict[Line['Name']]=[Line['Name'], 
                                Line['VegDate'],
                               Line['Robel_Mean'],
                               Line['Wiregrass'],
                               Line['Other_Grass'],
                               Line['Forb'],
                               Line['WoodVeg'],
                               Line['Litter'],
                               Line['Bare'],
                               Line['Other'],
                               Line['Percent_Canopy']]



conn = engine.connect()


for Line in reader:
    
    ins=Veg_dict.insert().values(Name = Line['Name'],
                            Dist = Line['Dist'],
                            VegDate = Line['VegDate'],
                            Robel_Mean = Line['Robel_Mean'],
                            Wiregrass = Line['Wiregrass'],
                            Other_Grass = Line['Other_Grass'],
                            Forb = Line['Forb'],
                            WoodVeg = Line['WoodVeg'],
                            Litter = Line['Litter'],
                            Other = Line['Other'],
                            Bare = Line['Bare'],
                            Percent_Canopy = Line['Percent_Canopy']
```

