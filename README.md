# WindowControls

Project to evaluate the possibilites of dynamic window controls with .Net and JS

Development steps in the develop branch, final version to present in master.


# Major steps i have changed in the code:

Renamed namespace to WindowControls for distinction from other projects.

Moved hard coded values out of the program into Settings file for easier usability.

Established a thread safe dictionary that holds the client connections so the server can broadcast

Designed the control panel after the given conditions and registered event listeners for the elements

Implemented message parsings for changes in the state of the different control panel items.

For having a valid font list available, i used a 2 way approach. When the server (C#) gets a request
for delivering a list of fonts from one of the window elements, he retrieves these from the system
and sends the fonts to the scripting part. (JS). Here every font is again tested against browser support.

The Undo/Redo System is done by two stacks one for redo and one for undo who save actions and their
old and respectively new values together in a bundled State Class. This enables to leave the implementation
details of undo/redo actions to stay in Javascript since the undo rewind only calls a "change" with old values

The data persistence through page reloads is also handled in the same way. When the page reloads a new
handshake with the server is performed and the client windows request the variable stack then.

The main goal through development was to try to keep the fixed implementation out of the C# base.
Meaning that for example the server should be handle all undo/redo actions independent what these
actions perform on the client side then.