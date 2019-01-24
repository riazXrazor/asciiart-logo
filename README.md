# ASCIIart Logo

_asciiart-logo_ creates a splash screen with logo from ASCII characters in text console. Splash screen is a rectangular panel and logo is the application name rendered by [ASCII-art fonts](gallery.txt) extended by optional additional information (author, application version, short desctiption, etc).

_asciiart-logo_ can be used by starting of command line tools, web servers or REST API microservices as a visual feedback to the user or administrator about successful start of the application.

## Quick Start

1. Download and install with command `npm install asciiart-logo`
1. See in action with command `node example.js`

## Simple Usage: Default Splash Screen

[Simplest usage](./example.js)  is to provide the `package.json` file:

``` JavaScript
const logo = require('asciiart-logo');
const config = require('./package.json');
console.log(logo(config).render());
```

## Rich Usage: Explicit Parametrization

The main impression of the splash screen is shaped by the selection of the right [ASCII-art font](gallery.txt).

Number of characters of the logo in single line (parameter `lineChars`) controls word wrapping logic in logo rendering and indirectly the width of the panel.

You can adjust also padding and margin of the panel.

* __name__ - applicaiton name in ascii-art logo (name parameter in project.json defines name of the application)
* __font__ - ASCII-art font from the [font gallery](gallery.txt) - default font is `Standard`
* __lineChars__ - length of line in name (ascii-art logo) for word wrapping
* __padding__ - space around the panel around text (like in CSS) - default is 5
* __margin__ - left space outside of the panel - default is 2

## Text functions

The text in splash screen is wrapped according the size of logo. Spaces, new lines, tabs are squeezed into single space. Text can be programmatically writen with functions:

* __left__ - text is alligned to left or wrapped
* __right__ - text is alligned to right or wrapped
* __center__ - text is alligned to center or wrapped
* __wrap__ - synonym to function _left_
* __emptyLine__ - add empty line into the panel

## Example with parametrization and text functions

``` JavaScript
const longDescription = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, ' +
    'sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. ' +
    'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris ' +
    'nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor ' +
    'in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. ' +
    'Excepteur sint occaecat cupidatat non proident, sunt in culpa qui ' +
    'officia deserunt mollit anim id est laborum.';

console.log(
    logo({
        name: 'Just a simple example',
        font: 'Speed',
        lineChars: 10,
        padding: 2,
        margin: 3
    })
    .emptyLine()
    .right('version 3.7.123')
    .emptyLine()
    .center(longDescription)
    .render()
);
```

... and the output on the console:

``` console

   ,---------------------------------------------------------.
   |                                                         |
   |  _________             _____                            |
   |  ______  /___  __________  /_   ______ _                |
   |  ___ _  /_  / / /_  ___/  __/   _  __ `/                |
   |  / /_/ / / /_/ /_(__  )/ /_     / /_/ /                 |
   |  \____/  \__,_/ /____/ \__/     \__,_/                  |
   |                                                         |
   |  ____________                   ______                  |
   |  __  ___/__(_)______ ______________  /____              |
   |  _____ \__  /__  __ `__ \__  __ \_  /_  _ \             |
   |  ____/ /_  / _  / / / / /_  /_/ /  / /  __/             |
   |  /____/ /_/  /_/ /_/ /_/_  .___//_/  \___/              |
   |                         /_/                             |
   |  __________                                ______       |
   |  ___  ____/___  _______ _______ ______________  /____   |
   |  __  __/  __  |/_/  __ `/_  __ `__ \__  __ \_  /_  _ \  |
   |  _  /___  __>  < / /_/ /_  / / / / /_  /_/ /  / /  __/  |
   |  /_____/  /_/|_| \__,_/ /_/ /_/ /_/_  .___//_/  \___/   |
   |                                    /_/                  |
   |                                                         |
   |                                        version 3.7.123  |
   |                                                         |
   |   Lorem ipsum dolor sit amet, consectetur adipiscing    |
   |   elit, sed do eiusmod tempor incididunt ut labore et   |
   |   dolore magna aliqua. Ut enim ad minim veniam, quis    |
   |  nostrud exercitation ullamco laboris nisi ut aliquip   |
   |    ex ea commodo consequat. Duis aute irure dolor in    |
   |   reprehenderit in voluptate velit esse cillum dolore   |
   |    eu fugiat nulla pariatur. Excepteur sint occaecat    |
   |    cupidatat non proident, sunt in culpa qui officia    |
   |          deserunt mollit anim id est laborum.           |
   |                                                         |
   `---------------------------------------------------------'

```
