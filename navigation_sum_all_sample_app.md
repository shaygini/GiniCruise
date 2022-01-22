id: app-development-gini-create-app-spacex
summary: creating simple spacex launch info app 
authors: Shay markovich

# App project
<!-- ------------------------ -->
##General
In this codelab you we will create simple spacex launch info app

<!-- ------------------------ -->
## App coding instractions
### Code
1. Create a new repository
2. Every feature in the app will need a new pull request and review

### Spec ###
1. The spec of the App is in the next part
2. Before coding please read the spec and verify you understeds all the requements and app behaviour, you don't want to do the same work twice
3. Write the code in such a why that it will be easy to add new features.


### Documantation
**Before** and **During** writing the code, create a documantaion helping you and other to understend the code
You can use [drao.io](https://app.diagrams.net/) to create umls diagrams

1. Create a high level blocks diagram of your app incluing classes from all layers

2. Create ui app diagram flow (navigation flow between screens)

2. Create data uml describing all the database ententies and the relationship between ententies

<!-- ------------------------ -->
## App
In this section you will build app with all the thing you learn so far

### Porpuse
The app allow us to see spacex lanches details

The app contains 4 screens: launchs screen, launch details screen, ships screen, ships details screen.

The app contains drawer to let us choose between lanunches screen and ships screens


![image](images/spacex_screens.png)

### Screens:
1. launches list
2. launch details
2. ships list
4. ships detail


#### 1. Lanches list:
title = launch list
filter by (search line):
  - title

sorting by: 
  - date
  - title
(default sorting by date from new to old)

cell: 
  - badge
  - title
  - date

behaviour:
  - when pressing a launch cell - go to the launch detail screen
  - refresh to reload

#### 2. Launch details:
title = name of the lanch
    - title
    - badge 
    - date
    - ship list
    - farring list

behaviour:
  - when pressing a ship inside the ship list - go to the ship detail screen

#### 3. Ship list:
title = ship list
filter by (search line):
- title

sorting by:
- title

cell:
- pic
- title

behaviour:
  - when pressing a ship cell - go to the ship detail screen
  - refresh to reload

#### 4. Ship detail:
title = name of the ship
- pic
- title
- more info
- list of all the lanches

behaviour:
  - when pressing a launch inside the launch list - go to the launch detail screen

#### drawer menu with
1. latest lanches
2. ships

### API

Use https://github.com/r-spacex/SpaceX-API
Documantation is in repository main readme file

### Add work manager:
every day check for changes in lanches, 
If changed - notification the user
when press the notification - the lanch details will be opened, 
when press back the launch list will oppened

### Tests
[tarining testing](https://developer.android.com/codelabs/advanced-android-kotlin-training-testing-basics#0)


### Stack:

- navigation components - navigation between fragment
- newtwork calls retrofit - calls to the api
- room database - save data in room database for online and offline use
- Usecases - insde the domain layer
- view model
- fragments
- single activity
- live data - pass data to the ui - from the view model to the fragment
- flow - pass data betweens layers


<!-- ------------------------ -->
## Return to main
[return to main](../)