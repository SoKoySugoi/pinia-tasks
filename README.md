To run this application first install the dependencies
open a terminal and run...
  npm install

then, if you don't have json server installed, 
inside the terminal run...
  npm install -g json-server

next, inside the terminal you will open a json server to host the internal db file stored in the project
  json-server --watch src/data/db.json

finally, use 
  npm run dev 
to poke around in the browser
