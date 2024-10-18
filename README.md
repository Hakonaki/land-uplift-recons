# Glacial Land Adjustment Regenerator (GLARE)
A method for QGIS for simulating land uplift of Fennoscandia by recalculating a digital terrain model.

Download the three raster layers from: https://drive.google.com/drive/folders/184nPIZuX83gr3Yd6tVBGXCkpUysNY-CO?usp=drive_link
and follow instructions in GLARE_documentation_v2-0.rtf

# Summary
Load your own DTM and the three default rasters in QGIS, open Raster Calculator tool and paste this equation to Expression:

"User_DTM@1" - ((2 / 3.14159 * ("TIN_gthick@1" * 0.077) * (ATAN("TIN_meltBP@1" / (5 * ("TIN_gthick@1" * 0.077) + 590)) - ATAN(("TIN_meltBP@1" -1950 + [yearCE]) / (5 * ("TIN_gthick@1" * 0.077) + 590)))) + ((("TIN_uplift@1" * 0.075) * ((2020 - [yearCE]) / 100)) - (0.5 * (-0.011 * (("TIN_uplift@1" * 0.075) * ((2020 - [yearCE]) / 100) ^ 2))))) - [sea-level ref]

Replace the three [yearCE] values with the year you want to simulate (in Common Era, negative value indicates Before Common Era; e.g. 4000 BCE = -4000).
Replace User_DTM@1 with the name of your chosen DTM (including @1 for band).
<br>
<br>
<br>
Example (year 6000 BCE):
"User_DTM@1" - ((2 / 3.14159 * ("TIN_gthick@1" * 0.077) * (ATAN("TIN_meltBP@1" / (5 * ("TIN_gthick@1" * 0.077) + 590)) - ATAN(("TIN_meltBP@1" -1950 + -6000) / (5 * ("TIN_gthick@1" * 0.077) + 590)))) + ((("TIN_uplift@1" * 0.075) * ((2020 - -6000) / 100)) - (0.5 * (-0.011 * (("TIN_uplift@1" * 0.075) * ((2020 - -6000) / 100) ^ 2))))) - -17
<br>
<br>
<br>
sea-level ref: https://docs.google.com/spreadsheets/d/1P-ij2DcjX7HwqWG5dtX7Q1SpI779SaRW/edit?usp=drive_link&ouid=102836171977705631382&rtpof=true&sd=true
