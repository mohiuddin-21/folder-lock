@ECHO OFF
color A
if EXIST "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" goto UNLOCK
if NOT EXIST Private goto MDPrivate
:CONFIRM
echo Professor Are you sure to lock this folder? (Y/N)
set/p "cho=>"
if %cho%==Y goto LOCK
if %cho%==y goto LOCK
if %cho%==Yes goto LOCK
if %cho%==yes goto LOCK
if %cho%==n goto END
if %cho%==N goto END
if %cho%==No goto END
if %cho%==no goto END
echo Invalid choice.
goto CONFIRM
:LOCK
ren Private "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
attrib +h +s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
echo Folder locked
goto End
:UNLOCK
echo Professor Enter The Passcode to Unlock Your Secure Folder !
set/p "pass=>"
if NOT %pass%== 531910 goto FAIL
attrib -h -s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
ren "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" Private
echo Folder Unlocked !
goto End
:FAIL
echo Sorry Invalid password,
goto UNLOCK

:MDPrivate
md Private
echo Private created successfully | CyberBox21
goto End
:End