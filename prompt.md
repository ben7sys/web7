# Project: Web7
A web application with a user-friendly interface that allows Python scripts to be executed on the server and the output returned to the user.

## Example process for the User
 - The user opens the web application in the browser.
 - The user clicks on a button with the description of a python script "python-script-test".
 - A JavaScript event is triggered that sends a request to the Flask server.
 - The Flask server receives the request and executes the Python script.
 - The output of the Python script is returned to the Flask server.
 - The Flask server sends the output back to the frontend.
 - The frontend receives the output and displays it in the designated area.

## Project structure
The project structure should be clear and modular:
 - templates/: Contains HTML files.
 - static/: Contains static files such as CSS and JavaScript (optional, since Bootstrap is included via CDN).
 - app.py: The Python script to be executed.
 - server.py: The Flask web server.

## User guidance
 - The application should be clear and easy to use.
 - Error messages and successes should be displayed to the user in an understandable way.
 - The application should be responsive and work well on different devices.

### Frontend
 - A beautiful and intuitive user interface using Bootstrap.
 - Buttons that executes Python scripts.
 - A pane to display the output of the several Python scripts.

HTML page:
 - Using Bootstrap for layout and styling.
 - A navbar for navigation.
 - A jumbotron or card element for the main content.
 - A button that, when clicked, fires a JavaScript event to execute the Python script.
 - A text area or div that displays the output of the script.

JavaScript:
 - A function that sends a fetch or AJAX request to the Flask server to execute the Python script.
 - Processing the server response and displaying the output in the appropriate area of ​​the HTML page.

### Backend
 - A Flask web server that can accept HTTP requests and execute the Python script.
 - An endpoint structure to handle requests from the frontend.

Flask web server:
 - Flask configuration and setup to run the application in development mode.
 - An endpoint (/) that renders the main HTML page.
 - An endpoint (/run-script) that runs the Python script and returns the output.

Python scripts:
 - The scripts perform specific tasks and returns a string as a result.
 - The output of the script should be designed in such a way that it can be easily displayed on the frontend.
 - The output should be possible to display text, images, contents of json, text and markdown files

### Operations and Deployment
Development environment:
 - Using debug=True in Flask for the development phase to easily identify bugs.

Production environment:
 - Using a production server like gunicorn or uWSGI for deployment.
 - Setting up Nginx or another web server as a reverse proxy to forward requests to the Flask application.

# Python-Script 1: bookmark-convert-json
The First Python script is a function to allow the user to convert a single or multiple bookmark html files to a single json file.
Users can upload single or multiple HTML browser bookmark files or directories containing such files,
and convert them into a JSON format. The converted JSON is then offered to the user for download. 

## Plan for bookmakr-convert-json
Convert a bookmark file into a structured json file.
Ignore Folders, only convert links.
The source and destination should be a variable.

## HTML Structure:
<H3></H3>           - Folder (ignore all folders)
<A></A>             - Link Description
HREF=""             - URL
ICON=""             - image
ADD_DATE=""         - date added
LAST_MODIFIED=""    - last modified

## Example bookmark_example.html
```html
<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1>Bookmarks</H1>
<DL><p>
    <DT><H3 ADD_DATE="1714341278" LAST_MODIFIED="0" PERSONAL_TOOLBAR_FOLDER="true">Toolbar Folder</H3>
    <DL><p>
    </DL><p>
    <DT><A HREF="https://some.link" ADD_DATE="1717122539" ICON="data:image/png;base64,iVBORw0AElFTkSuQmCC">Link Description</A>
    <DT><H3 ADD_DATE="1714683750" LAST_MODIFIED="1714821517">Folder 1</H3>
    <DL><p>
        <DT><A HREF="https://some.link" ADD_DATE="1714683750" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAASUVORK5CYII=">Link Description</A>
    </DL><p>
    <DT><A HREF="https://something.com" ADD_DATE="1665802514" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA6oOCD0rfZHzAAAAAElFTkSuQmCC">Link Description</A>
    <DT><A HREF="https://any.example" ADD_DATE="1714821517" ICON="data:image/png;base64,iVBORmG4DeQn7o9XwoccgAAAABJRU5ErkJggg==">Link Description</A>
    <DT><H3 ADD_DATE="1715043097" LAST_MODIFIED="1715043097">Folder 2</H3>
    <DL><p>
        <DT><H3 ADD_DATE="1715043097" LAST_MODIFIED="1715043097">Subfolder 1</H3>
        <DL><p>
            <DT><A HREF="https://any.example" ADD_DATE="1715043097" ICON="data:image/png;base64,iVBORw0KGgoAv/dmPAbv2kmCC">Link Description</A>
            <DT><A HREF="https://some.link" ADD_DATE="1715043097" ICON="data:image/png;base64,iVBORw0KGAAAAElFTkSuQmCC">Link Description</A>
        </DL><p>
    </DL><p>
</DL><p>
```

# JSON Structure EXAMPLE:
```json
{
    "bookmarks": [
        {
            "url": "https://some.link",
            "description": "Link Description",
            "icon": "data:image/png;base64,iVBORw0AElFTkSuQmCC",
            "add_date": "1717122539",
            "last_modified": "0"
        },
        {
            "url": "https://some.link",
            "description": "Link Description",
            "icon": "data:image/png;base64,iVBORw0KGAAAAElFTkSuQmCC",
            "add_date": "1715043097",
            "last_modified": "1715043097"
        }
    ]
}
```

