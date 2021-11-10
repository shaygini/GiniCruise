id: app-development-gini-persistence
summary: persistence
authors: Shay markovich

# Persistence

<!-- ------------------------ -->
##General
In this codelab you will learn about common persistence we used in our projects

<!-- ------------------------ -->
## What are persistnce for
 - Use persistnce to save data that need to be saved in the device

### SharedPreferences
- key value pair
- using 

### EncryptedSharedPreferences

### DataStore
[DataStore](https://developer.android.com/topic/libraries/architecture/datastore)

### Room
save data in sqlite data base
- Easy to use
- Support liveData, susspend function, flow
- Have migration support

Example of using:
get data from server and save it to the room data base
read from the room database and show the data to the user

when the user is offline, we can see the data