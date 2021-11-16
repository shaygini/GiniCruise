id: app-development-gini-project-stracture
summary: project stracture
authors: Shay markovich

# What is the project stracture

<!-- ------------------------ -->
##General
In this codelab you will learn about the project stracture, how to put the source classes inside the app

<!-- ------------------------ -->
## Java Project stracture

### packages
packages are used to organize the code and as a privacy method


### accessibilty
- default private - within a package
- private
- public
- protected

<!-- ------------------------ -->
## android project stracture


project stracture tree - 

di - 
data -  
network -  
    Retorofit
    ApiService
ui -
    viewModels -
        FeatureOneViewModel
        FeatureTwoViewModel
    adapters -
        FeatureOneAdapter
        FeatureTwoAdapter
    fragment- 
        FeatureOneFragment
        FeatureTwoFragment
    customView -
        FeatureOneCustomView
        FeatureTwoCustomView



project stracture features
di - 
data - 
    roomDatabase
    roomDao
ui - 
  FeatureOne
    - FeatureOneViewModel
    - FeatureOneAdapter
    - FeatureOneFragment
    - FeatureOneCustomView
   FeatureTwo
    - FeatureTwoViewModel
    - FeatureTwoAdapter
    - FeatureTwoFragment
    - FeatureTwoCustomView


** you will see both ways it should be determain in the begining, please don't mix the two **


### di
here you put all the dependency injection code
this code is responsible to initiate and supply the code for all the app
(there should not have new in the code)
you can use it manualy or with dependncy injection library like dagger / hilt / koin

### data
here you will put all the data manipulation of the coded
and persistens data
data base
repository
persistense
use room data base for database

### network
here you will put all the network related code
all models from the server
all function calls
we usaly use newtwork library like Retrofit - to help us get response from the server and return them

### ui
here you will put all the ui
view models 
addapter
views
fragment
activities


each layer should have it's own models - don't mix them
(models for newtork server / models for data layer room server(ententies) / models for use inside the app (domain) / models inside the ui layer)


<!-- ------------------------ -->
## Return to main
[return to main](../)