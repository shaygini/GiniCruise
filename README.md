# GiniCruise

This repository build a codelab that intened to used by new devlopers at gini for there first days.

The codelab static files that are published here:
https://shaygini.github.io/GiniCruise/

## build process
The html static files is created from md files that are "compiled" to html files using docker container

### prerequisite
please download docker container `bpetetot/claat` and open docker before run the build script 

### use
`npm run watchMe`
This will execute docker command every time a md file is update and update the html code

`npm run serve`
This will open local server that can be opened in
http://0.0.0.0:9090/

## more info
- Codelab formatting: https://github.com/googlecodelabs/tools/blob/master/FORMAT-GUIDE.md
- When adding new topic don't forget to add it in the index.html 
