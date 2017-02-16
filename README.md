# Toggl-to-google-sheets-integration
This is a google apps script for use with a google spreadsheet, that imports data using the API of toggl (time tracking software).

It accesses the toggl API, pulls the last hundred entries, then adds the ones that aren't yet on the spreadsheets to new lines at the bottom of the chossen sheet (sheet 4, by default).

This needs to be pasted into the script editor attached to a google sheet. You'll need to put in your own toggl account's API key.

Each row has A) a blank colunm, B) the timestamp of the start time in a sheets-readable format C) the time stamp of the start time, D) the timestamp of the end time, E) the elapsed time of the entry in hours, F) the name of the entry, G) all of the tags of he entry, seperated by cammas, H) a blank column, I) another blank column, J) of the entry, and K) the user's id.

some things to note:
In order to prevent double entry on the spreadsheet, the script only adds entries that have an id (all toggl entries have a unique id) greater than the value of cell A:1. In order to get the script to work correctly, set A:1 to be "=max(J:J)", or the max of whatever column is storing the ids of each entry. A:1 will therefore reflect the highest id on the spreadsheet already.Since the ids are in asceending order, this prevents double entry. 

Only entries with at least one tag are added to the sheet, and not entries that are currently running.

I made it so that the time zones are correct. I don't know why toggl's internal data has such a weird timezone. 
