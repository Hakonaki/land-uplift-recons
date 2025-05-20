# Post-Glacial Land Adjustment Regenerator (GLARE)
A method for QGIS for simulating land uplift of Fennoscandia by recalculating a digital terrain model.

Instructions for Toolbox-option and Manual-option.
Access model documentation and materials: https://drive.google.com/drive/folders/184nPIZuX83gr3Yd6tVBGXCkpUysNY-CO?usp=drive_link
Follow instructions in GLARE_documentation_v2-2.docx (https://docs.google.com/document/d/1KKpa7Z7H3h_X3z2UrM-_kJwN3z0yTR9H/edit?usp=drive_link&ouid=102836171977705631382&rtpof=true&sd=true)

# Summary
Load your own DTM and default rasters in QGIS and :

-----------------------------------------------------------------------

a. Add model to Toolbox, match raster and band inputs and apply Year-in-CE.

-----------------------------------------------------------------------

or b. Open Raster Calculator tool and paste this equation to Expression:

"User_DTM@1" - ((2 / 3.14159 * ("Base Raster@1" * 0.075) * (ATAN("Base Raster@2" / (5 * ("Base Raster@1" * 0.075) + 500)) - ATAN(("Base Raster@2" -1950 + [yearCE]) / (5 * ("Base Raster@1" * 0.075) + 500)))) + ((("Base Raster@3" * 0.072) * ((2020 - [yearCE]) / 100)) - (0.5 * (-0.014 * (("Base Raster@3" * 0.072) * ((2020 - [yearCE]) / 100) ^ 2))))) - [sea-level ref]

Replace the three [yearCE] values with the year you want to simulate (in Common Era, negative value indicates Before Common Era; e.g. 4000 BCE = -4000).
Replace User_DTM@1 with the name of your chosen DTM (including @1 for band).
<br>
<br>
<br>
Example (year 6000 BCE):
"User_DTM@1" - ((2 / 3.14159 * ("Base Raster@1" * 0.075) * (ATAN("Base Raster@2" / (5 * ("Base Raster@1" * 0.075) + 500)) - ATAN(("Base Raster@2" -1950 + -6000) / (5 * ("Base Raster@1" * 0.075) + 500)))) + ((("Base Raster@3" * 0.072) * ((2020 - -6000) / 100)) - (0.5 * (-0.014 * (("Base Raster@3" * 0.072) * ((2020 - -6000) / 100) ^ 2))))) - -19
<br>
<br>
<br>
sea-level ref: https://docs.google.com/spreadsheets/d/1P-ij2DcjX7HwqWG5dtX7Q1SpI779SaRW/edit?usp=drive_link&ouid=102836171977705631382&rtpof=true&sd=true
