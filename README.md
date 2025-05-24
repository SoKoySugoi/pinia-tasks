Pinia Tasks

This application is a Pinia tutorial built to practice using the Store Setup model.
It is a simple application that allows a user to add, favorite, filter, and delete specific tasks tasks to and from a list.
In addition, It utilizes a local JSon file to create persistent data and practice async/await functionality.

To run this application first install the dependencies
open a terminal in VS Code and run...

"npm install"

then, if you don't have json server installed already, 
open a new terminal and run...

"npm install -g json-server"

next, inside the terminal, you will open a json server to host the internal db file stored with the project 
by running...

"json-server -w src/data/db.json"

finally, run...

"npm run dev"

in a terminal to host a local link, and control+click the provided url
to poke around the project in a web browser
