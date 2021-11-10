id: app-development-gini-callbacks-livedata-corutines-flow
summary: callbacks livedata corutines flow
authors: Shay markovich

# callbacks livedata corutines flow

<!-- ------------------------ -->
##General
In this codelab you will learn about several ways we use to call functions

<!-- ------------------------ -->
## Callbacks

### What it used for
This is used for pass code that will be executed in feauter time.

### How its done
- defning and interface
- implement the interface and pass the object that implement the interface so that the fuction can be called in feauter time
- in kotlin - you can also pass a lambda - passing the function itself


<!-- ------------------------ -->
## LiveData

### What it used for
This is used to pass data to ui componnents

### How its done
- pass the data just in time for the ui owner (when the lifecicle owner is in at least resume state)
- pass the data in the main ui thread
- auto unObserbe when the lifecycleOwner is destroyed


<!-- ------------------------ -->
## Flow

### What it used for
This is used to pass data to in all application

can be canceld using the coutotines cancel machenizem

- flow
- shared flow
- state flow

based on kotlin courotiens, not supported in java

### How its done
-



<!-- ------------------------ -->
## event bus


### What it used for
publish events thorout the application

### How its done
- use a publish subscribre model for events

[communicating with an event bus](https://guides.codepath.com/android/communicating-with-an-event-bus)


