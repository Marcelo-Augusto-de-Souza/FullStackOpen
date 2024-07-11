sequenceDiagram
    participant browser
    participant server

    Note right of browser: A javascript function handles the event of form submission that consists of<br> appending the new note in the HTML document and POST the new note<br> using XML HTTP Request

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa <br> content: {"Adobe Systems", date}
    activate server
    Note left of server: Server script appends to data.json and send 201 status code
    server-->>browser: 201 Created
    deactivate server

    Note right of browser: Data is logged into console


  