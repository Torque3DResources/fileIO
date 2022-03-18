# Generic file I/O module

## Commands:
```writeSave(%name)```
Opens a sav file to write the save data into. Formatted as ```$prefpath @"/saves/" @ %name @ ".sav"```. Once file is opened, other modules are signaled via a callback function to fill their own data into the ```$saveRecords``` list, which is then written to the file

```saveEntries(%file)```
Saves out the lines in the ```$saveRecords``` array to the file as opened by ```writeSave()```.

```readSave(%name)```
Opens a sav file to load the save data from. Formatted as ```$prefpath @"/saves/" @ %name @ ".sav".``` Once file is opened, ```readEntries()``` is called to parse line data. 

```readEntries(%file) ```
Reads the lines of a sav file as opened by ```readSave()```. Uses <@moduleName> tags to segment loaded data to apply to the correct module code

## Callbacks: 
```insertSaveData()```
A module namespace function that is signaled by ```writeSave()```. Adds records into the ```$saveRecords``` array for writing out to the sav file.

```parseSaveData()```
A module namespace function that is signaled by ```readSave()```. Reads records from the ```$saveRecords``` array for updating game values pulled from the sav file. 

```onSaveLoaded()```
A module namespace function that is signaled by ```readSave()``` once all records have been read and processed. Used for final application of game logic once save loading is completed.
