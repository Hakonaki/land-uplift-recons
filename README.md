# land-uplift-recons
A method for QGIS for simulating land uplift of Fennoscandia with a digital terrain model.

Download the three raster layers from: https://drive.google.com/drive/folders/184nPIZuX83gr3Yd6tVBGXCkpUysNY-CO?usp=drive_link
and follow instructions in Documentation_v1-7.rtf

# Summary
Load your own DTM and the three default rasters in QGIS, open Raster Calculator tool and paste this equation to Expression:

User_DTM@1 - ((2 / 3.14159 * ("TIN_ice_thickness@1" * 0.061) * (ATAN("TIN_ice_meltBP@1" / (4 * ("TIN_ice_thickness@1" * 0.061) + 350)) - ATAN(("TIN_ice_meltBP@1" -1950 + -4000) / (4 * ("TIN_ice_thickness@1" * 0.061) + 350)))) + ((("TIN_uplift@1" * 0.079) * ((2011 - -4000) / 100)) - (0.5 * (-0.018 * (("TIN_uplift@1" * 0.079) * ((2011 - -4000) / 100) ^ 2)))))

Replace the three -4000 values with the year you want to simulate (in Common Era, negative value indicates Before Common Era; e.g. 4000 BCE = -4000).
Replace User_DTM@1 with the name of your chosen DTM (including @1 for band).

After computation apply sea-level either through Symbology or by addition through Raster Calculator.
