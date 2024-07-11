sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note left of server: Server script appends the note and sends redirect command
    server-->>browser: 302 Found https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server

    Note right of browser: Browser redirects the page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: Browser executes main.js code that fetches the JSON from the server and call a function when data is received

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Data from the JSON from the Server which contain the newly added note
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes in the html page
  


  