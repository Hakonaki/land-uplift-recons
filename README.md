# land-uplift-recons
A method for QGIS for simulating land uplift of Fennoscandia with a digital terrain model.

Download the three raster layers from: https://drive.google.com/drive/folders/184nPIZuX83gr3Yd6tVBGXCkpUysNY-CO?usp=drive_link
and follow instructions in Documentation_v1-6.rtf

# Summary
Load your own DTM and the three default rasters in QGIS, open Raster Calculator tool and paste this equation to Expression:

User_DTM@1 - ((2 / 3.14159 * ("TIN_ice_thickness@1" * 0.0575) * (ATAN("TIN_ice_meltBP@1" / (4 * ("TIN_ice_thickness@1" * 0.0575) + 200)) - ATAN(("TIN_ice_meltBP@1" -1950 + -9999) / (4 * ("TIN_ice_thickness@1" * 0.0575) + 200)))) + ((("TIN_uplift@1" * 0.078) * ((2011 - -9999) / 100)) - (0.5 * (-0.015 * (("TIN_uplift@1" * 0.078) * ((2011 - -9999) / 100) ^ 2)))))

Replace the three -9999 values with the year you want to simulate (in Common Era, negative value indicates Before Common Era; e.g. 4000 BCE = -4000).
Replace User_DTM@1 with the name of your chosen DTM (including @1 for band).

After computation apply sea-level either through Symbology or by addition through Raster Calculator.
