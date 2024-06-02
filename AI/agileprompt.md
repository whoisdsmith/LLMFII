---
aliases:
  - AgilePrompt
tags:
  - "#developer-tools"
  - "#software-development"
  - "#open-source"

  - "#prompt-builder"
  - "#web-development"
  - "#form-handling"
---

# Agile Prompt Builder

## Overview

The Agile Prompt Builder is a simple and easy-to-use tool that helps you create customized prompts based on your specific needs. You can define the active user, action, expected result, conditions, and choose whether to include a code snippet in your prompt.

## Features

-   User-friendly interface
-   Customizable input fields
-   Dynamic prompt generation
-   Option to include a code snippet
-   Responsive design for various screen sizes

## Getting Started

### Prerequisites

-   A modern web browser (e.g., Chrome, Firefox, Safari)

### Running the project

1.  Clone the repository or download the source code as a ZIP file.

`git clone https://github.com/silviotorre/Agile-Prompt-Builder.git` 

2.  Navigate to the project folder and open the `index.html` file in your preferred web browser.

`cd Agile-Prompt-Builder` 

3.  Start using the Agile Prompt Builder by entering your desired values in the input fields and clicking the "Generate Prompt" button.

## File Structure

-   `index.html`: The main HTML file that contains the structure of the web page.
-   `styles.css`: The external CSS file that contains the styling for the web page.
-   `script.js`: The external JavaScript file that handles the form submission and generates the prompt.

## How Work
This code is creating a form in a web page and adding an event listener to the form submission. When the form is submitted, the event listener function is called.

The function first prevents the default form submission behavior by calling `event.preventDefault()`. It then retrieves the values of several form elements using the `form.elements` object and stores them in variables.

Next, the function constructs a prompt message by concatenating the values of the form elements together using string interpolation. If the "add code" checkbox is checked, the message will also include a code snippet.

Finally, the function creates a new paragraph element and sets its text content to the prompt message. The paragraph element is then appended to the end of the document body.

### UML Diagram

Here's a UML diagram to illustrate the structure of this code:

         +--------------------------+
         |      EventTarget         |
         +--------------------------+
         | addEventListener()       |
         | removeEventListener()    |
         +--------------------------+
                        |
                        |
                        v
         +--------------------------+
         |          Element         |
         +--------------------------+
         | querySelector()          |
         | addEventListener()       |
         +--------------------------+
                        |
                        |
                        v
         +--------------------------+
         |     HTMLFormElement      |
         +--------------------------+
         | elements                 |
         +--------------------------+
                        |
                        |
                        v
         +--------------------------+
         |         Function         |
         +--------------------------+
         | event.preventDefault()   |
         | form.elements[]          |
         | string interpolation     |
         | createElement()          |
         | textContent              |
         | appendChild()            |
         +--------------------------+

## Contributing

We welcome contributions to this project. If you find a bug or want to suggest a new feature, please create an issue on the [GitHub repository](https://github.com/silviotorre/Agile-Prompt-Builder/issues).

## License

This project is licensed under the MIT License. 

## Acknowledgments

-   You all 