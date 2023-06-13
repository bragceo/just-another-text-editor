# Lavell's Just Another NoteTaker

## Description 

Lavell's Just Another NoteTaker is a text editor that can work both online and offline. It serves to allow developers to write code snippets or notes which they can retrieve later, even if they're disconnected from the internet. The application utilizes IndexedDB for local storage to persist the data, which ensures the data remains intact when the application is reopened. The application also has functionality for installing itself as a Progressive Web Application (PWA) for offline use.


## User Story

AS A developer <br>
I WANT to create notes or code snippets with or without an internet connection <br>
SO THAT I can reliably retrieve them for later use <br>

## Acceptance Criteria

GIVEN a text editor web application <br>
WHEN I open my application in my editor <br>
THEN I should see a client server folder structure <br>
WHEN I run `npm run start` from the root directory <br>
THEN I find that my application should start up the backend and serve the client <br>
WHEN I run the text editor application from my terminal <br>
THEN I find that my JavaScript files have been bundled using webpack <br>
WHEN I run my webpack plugins <br>
THEN I find that I have a generated HTML file, service worker, and a manifest file
WHEN I use next-gen JavaScript in my application <br>
THEN I find that the text editor still functions in the browser without errors <br>
WHEN I open the text editor <br>
THEN I find that IndexedDB has immediately created a database storage <br>
WHEN I enter content and subsequently click off of the DOM window <br>
THEN I find that the content in the text editor has been saved with IndexedDB <br>
WHEN I reopen the text editor after closing it <br>
THEN I find that the content in the text editor has been retrieved from our IndexedDB <br>
WHEN I click on the Install button <br>
THEN I download my web application as an icon on my desktop <br>
WHEN I load my web application <br>
THEN I should have a registered service worker using workbox <br>
WHEN I register a service worker <br>
THEN I should have my static assets pre cached upon loading along with subsequent pages and static assets <br>
WHEN I deploy to Heroku <br>
THEN I should have proper build scripts for a webpack application <br>






## Deployed URL

https://text-editor--jave.herokuapp.com/



## Github Repository

https://github.com/bragceo/just-another-text-editor



## Overview of Code structure and its components:

Here is a detailed overview of each file:

server.js: This is the main entry point for the server side of the application. It sets up an Express.js server that listens on a defined port. It also uses Express's middleware functions to serve static files and parse request bodies in URL-encoded and JSON formats. Lastly, it imports route definitions from the htmlRoutes.js file.

htmlRoutes.js: This file exports a function which defines HTTP routes for the app. In this case, a single route for the base URL ("/") is defined. When a GET request is made to the base URL, the server responds by sending the file index.html.

Database.js: This file establishes a connection with the IndexedDB and exports functions to manipulate the data in the database. The database is used for storing and retrieving content entered in the text editor, which enables offline functionality.

Editor.js: This file imports the database functions from Database.js and implements the editor functionality using CodeMirror. The constructor of the exported class initializes the editor, loads the initial content from IndexedDB (or from local storage as a fallback), and sets up event listeners to save changes to both local storage and IndexedDB.

Index.js: This file is the entry point for the client-side JavaScript code. It initiates the editor, sets up the page content, implements a loading spinner, and sets up a service worker if the browser supports it. Service workers are crucial for PWAs as they enable caching and offline functionality.

Install.js: This file handles the installation of the application as a PWA. When the beforeinstallprompt event is fired, it enables an installation button and saves the event. When the user clicks the button, it triggers the installation prompt. After the user accepts or declines the installation, the outcome is logged and the saved event is cleared.

Consistent with the User Story and Acceptance Criteria, the sequence of operation for the application is as follows:

Upon startup (npm run start), server.js starts the Express server, serving static files and initializing HTML routes.

When the text editor application is run, JavaScript files are bundled using webpack, as per the Acceptance Criteria.

Webpack plugins generate an HTML file, service worker, and a manifest file.

The index.js file initializes the application and sets up the service worker if supported. This includes loading the editor, loading the spinner, registering the service worker, and adding the logo image.

On initialization, the Editor.js file attempts to load data from IndexedDB (or local storage as a fallback), then sets up event listeners to save changes to the local storage and IndexedDB when the text editor changes or loses focus.

Install.js provides the ability to install the application as a PWA and handles events related to this functionality.

Finally, the service worker set up in index.js ensures the static assets are pre-cached for offline use and improves load times.
 

## How to run the application
 
Running the application locally:

Running the application locally will require Node.js and npm (Node Package Manager) to be installed on your system.

Once that is done, clone or download the Repository and in the root directory of the Repository install dependencies (i.e., npm install).

Note: If the application uses environment variables (like in the server.js file for the PORT), you will need to set these up. This can be done by creating a .env file in the root of your project and specifying the variables there, like PORT=3000. 

Once everything is set up, you can start the application by running an npm start in the command line.

Lastly open a web browser and visit http://localhost:<PORT> (note: replace <PORT> with the port number your server is running on, e.g., http://localhost:3000). You should see your application running.



## Special Thanks 

Shout out to the awesome Instructors and TAs who worked with me through numerous challenges. These individuals include: Diego, Enrique Gomes, and Erik Hoverstein. 



## Authors 

Lavell Juan <br>



## Credits 

N/a

## License 

Please refer to license in repo 






