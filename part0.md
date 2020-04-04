This shows my answers on exercises 0.4 - 0.6 of part 0 (Fundamentals of Web apps).

This exercise mainly focus on how the web apps works. It'll familiarize the students on how browser and the server communicate with each other.

Exercise 0.4: new note
    I have a sequence diagram which was used in the discussion/lesson of the part 0.

        browser->server: HTTP POST https://fullstack-exampleapp.herokuapp.com/new_note
        server-->browser: main.js
        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/notes
        server-->browser: HTML-code
        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/main.css
        server-->browser: main.css
        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/main.js
        server-->browser: main.js

        note over browser:
        browser starts executing js-code
        that requests JSON data from server 
        end note

        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/data.json
        server-->browser: [{ content: "HTML is easy", date: "2019-05-23" }, ...]

        note over browser:
        browser executes the event handler
        that renders notes to display
        end note

    So, in this exercise the situation is what will happen when you entered texts in the form element and click the submit button.
    In this kind of events, there will be a URL redirect which refresh the entire page. This means that all other elements in the web page will be requested again at the server-side. Aside from the POST method, all the GET method will also be run when posting a new note.

Exercise 0.5 - 0.6:
    The difference between the traditional web page and the single page is the rendering of elements. Here's the sequence diagram for a SPA.

        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/notes
        server-->browser: HTML-code
        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/main.css
        server-->browser: main.css
        browser->server: https://fullstack-exampleapp.herokuapp.com/main.js
        server-->browser: main.js

        note over browser:
        browser starts executing js-code
        that requests JSON data from server 
        end note

        browser->server: HTTP GET https://fullstack-exampleapp.herokuapp.com/data.json
        server-->browser: [{ content: "HTML is easy", date: "2019-05-23" }, ...]

        note over browser:
        browser executes the event handler
        that renders notes to display
        end note
    
    For a SPA, when the page is entirely loaded and you have a post event (as for this kind of app), the only thing that will be rendered is that specific element. In the example app the form element is going to do the event method and will add the text you add in the form element when clicking the submit button. After the process, the text will be reflected in the web page without requesting all the items of the entire page.