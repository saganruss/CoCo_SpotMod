# CoCo (Spotting Mod)
Bacterial colony counter written in ImageJ macro language

This macro enables easy counting of bacterial colonies on plates with multiple rows and columns of spots. 
Images are first processed in using standard ImageJ commands such as Subtract Background, Enhance Contrast etc.
Then, choose between two different counting processes: 
- Auto Count: for faster, entirely automated, but less accurate counting.
- Precision Count: for guided, accurate counting with manual edits.


# **CoCo User Guide**

## Install the macro

This permanently installs the macros to your ImageJ toolbar so you do not have to re-install it every time FIJI starts up.
1.	Find your ImageJ directory, under the macros folder, open StartupMacros.fifi.ijm in TextEdit (or your word editor of choice).
2.	Open CoCo_SpotMod.fiji in TextEdit (or your word editor of choice).
3.	Copy the contents of CoCo_SpotMod.ijm to the end of StartupMacros.ijm.

## Run the macro

1.	Open your image containing a plate with colonies to be counted.
2.	Locate and select the Process Image command (Plugins > Macros > Process Images) or press F1 with the ImageJ toolbar in focus.
3.	Select the area of the image containing the spots to be counted. Ensure that the borders fit closely to the edge of the spots without touching them. 
	Input the number of rows and columns of spots that will be counted within the area. Press "OK" to crop and process the image. 

**To use the Auto Counting Feature:**
1.	Locate and select the Auto Count Colonies command (Plugins > Macros > Auto Count Colonies) or press F2 with the ImageJ toolbar in focus. 
2.	Input a value for prominence. Then, press "OK" to continue.
This is the parameter that ImageJ’s “Find Maxima” function uses to define bright spots. For densely packed colonies or to increase detection of small/faint colonies, use a lower prominence value. For colonies spaced further apart or to reduce background noise, use a higher prominence value. These values can be approximated to mean “how much brighter should a region of pixels be compared to its surroundings, before it is recognized as a bright spot”. The default is set to 20.

*Note: Using a prominence that is too high will result in false positive colony selections. Using a prominence that is too low will result in missed colony selections.*

3. The colony count of each spot will be displayed in the Log window. Do no edit the Log window or close the Image window until every spot has been processed.
4. When colony counting is complete, import the counts into Excel by selecting the Log window, pressing Command + S and changing ".txt" to ".csv".

**To use the Precision Counting Feature:**
1. Locate and select the Precision Count Colonies command (Plugins > Macros > Precision Count Colonies) or press F3 with the ImageJ toolbar in focus. 
2. A window will display the image of the first spot to be counted. Input a value for prominence, sample name, and dilution number. Then, press "OK" to continue.
3. Red "+" symbols will indicate the location of detected colonies on the spot. Click to add a colony that wasn't detected, and Ctrl + Click to remove a falsely detected colony. Then, press "OK" to continue. Repeat for every spot.
4. The colony count of each spot will be displayed in the Log window. Do no edit the Log window or close the Image window until every spot has been processed.
5. When colony counting is complete, import the counts into Excel by selecting the Log window, pressing Command + S and changing ".txt" to ".csv".

*Tip: To transpose the list of colony counts into a table with multiple rows and columns, copy the following formula into the Excel sheet and drag to copy it across all the cells that you would like the table to cover:*

=INDEX($B$2:$B$81,ROW(D1)+(10*(COLUMNS($E$1:E$1)-1))). 

*Change B2 to the first cell in the input list and B81 to the final cell in the input list. Change 10 to the number of rows in your plate.*

## Reset the macro
To reset the macro before the next run, close the Log Window and any open image windows. Locate and select the Process Image command (Plugins > Macros > Reset CoCo) or press F4 with the ImageJ toolbar in focus.

author: Jia Xuan Leong, modified by: Sagan Russ