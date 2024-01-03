# land-uplift-recons
A method for QGIS for simulating land uplift of Fennoscandia with a digital elevation model.

Download three raster layers from: https://drive.google.com/drive/folders/184nPIZuX83gr3Yd6tVBGXCkpUysNY-CO?usp=drive_link
and follow instructions in Documentation_v1-0.rtf

# Summary
Load your own DTM and the three default rasters in QGIS, open Raster Calculator tool and paste this equation to Expression:

User_DTM@1 - (((("TIN_uplift_rate@1" / 8.6) * 0.705) * ((2011 - -9999) / 100)) - (0.5 * (-0.01 * (("TIN_uplift_rate@1" / 8.6) * 0.705)) * ((2011 - -9999) / 100) ^ 2)) + (2 / 3.14159 * ("TIN_glacial_weight@1" * 1.5) * (ATAN("TIN_glacial_retreat@1" / (6.6 * ("TIN_glacial_weight@1" * 1.5) + 335)) - ATAN(("TIN_glacial_retreat@1" -1950 + -9999) / (6.6 * ("TIN_glacial_weight@1" * 1.5) + 335))))

Replace the three -9999 values with the year you want to simulate (in Common Era, negative value indicates Before Common Era; e.g. 4000 BCE = -4000).
Replace User_DTM@1 with the name of your chosen DTM (including @1 for band).
