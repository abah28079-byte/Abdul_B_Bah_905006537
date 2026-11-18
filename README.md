# Abdul_B_Bah_905006537
PROG1101_ASSIGNMENT 1
##Pseudocode
Main Program
START WaterWatch
// Constants
SET MAX_REPORTS = 100
// Variables
SET running = TRUE
SET reportCount = 0
// Keep showing the menu again and again until the user chooses Exit
WHILE running = TRUE DO
CALL ShowMenu()
// Ask the user which option they want
INPUT choice
// Decide what to do based on the choice
IF choice = 1 THEN
CALL ReportProblem()
ELSE IF choice = 2 THEN
CALL CheckStatus()
ELSE IF choice = 3 THEN
// Stop the repeating so the program can end
SET running = FALSE
DISPLAY "Thank you for using WaterWatch"
ELSE
DISPLAY "Invalid choice"
END IF
END WHILE
END WaterWatch		

Functions
// This job shows the three options on the screen
FUNCTION ShowMenu()
DISPLAY "1. Report a water problem"
DISPLAY "2. Check report status"
DISPLAY "3. Exit"
END FUNCTION

// This job takes a new water problem from the user
FUNCTION ReportProblem()
INPUT location
INPUT problemType
// Check the answers are sensible before saving
IF location = "" OR problemType < 1 OR problemType > 3 THEN
DISPLAY "Error: please enter a location and a type from 1 to 3"
RETURN
END IF
IF reportCount >= MAX_REPORTS THEN
DISPLAY "System full"
RETURN
END IF
// Work out how urgent it is, then save it
SET priority = SetPriority(problemType)
CALL SaveReport(location, problemType, priority)
DISPLAY "Report saved. ID: " + reportID + " Priority: " + priority
DISPLAY "Alert sent to water officer"
END FUNCTION

// This job decides if the problem is urgent (HIGH) or not so urgent (MEDIUM)
FUNCTION SetPriority(type)
IF type = 1 OR type = 2 THEN
RETURN HIGH
ELSE
RETURN MEDIUM
END IF
END FUNCTION

// This job gives the report a number and stores it as Pending
FUNCTION SaveReport(location, type, priority)
SET reportCount = reportCount + 1
SET reportID = 1000 + reportCount
STORE reportID, location, type, priority, status = "Pending"
END FUNCTION

// This job finds an old report using its number
FUNCTION CheckStatus()
INPUT reportID
SET found = FALSE
// Look at the saved reports one at a time
FOR i = 1 TO reportCount DO
IF savedID[i] = reportID THEN
DISPLAY location[i], priority[i], status[i]
SET found = TRUE
END IF
END FOR
IF found = FALSE THEN
DISPLAY "Report not found"
END IF
END FUNCTION


##Flowchart

<img width="790" height="960" alt="WhatsApp Image 2026-11-18 at 14 30 31" src="https://github.com/user-attachments/assets/471086b4-3d54-47db-8ff4-dfb91372b611" />

##Report

[WaterWatch_PROG101_Assignment1.docx](https://github.com/user-attachments/files/35035274/WaterWatch_PROG101_Assignment1.docx)
