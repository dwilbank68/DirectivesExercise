# Directives Exercise

Building a collection of directives you can reuse elsewhere.

### 1 - Open the following in Firefox

because Chrome will enforce its CORS policy and refuse to work unless you install
a special extension or take the time to tweak it

    // index.html

    <!doctype html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.8/angular.js"></script>
        <script>

            angular
                .module('mainApp',[])
                .directive('element01', element01Fn)                        // 1a
                .controller('Element01Controller', Element01ControllerFn)   // 2a

            function element01Fn() {                                        // 1b
                return {
                    templateUrl: './element01.html',                        // 1c
                    controller: 'Element01Controller as el01'               // 1d
                }
            }

            function Element01ControllerFn () {                             // 2b
                var vm = this;
                vm.user_age = 28;                                           // 2c
            }

        </script>
    </head>
    <body ng-app="mainApp">

        <element01></element01>                                             // 3

    </body>
    </html>

### 2 - For each new piece of UI you build

    1. Create a directive and a directive function. (1a, 1b)

    2. Note that the directive function (1b) calls for a new
     controller. Write that new controller and its function. (2a, 2b).
     Create some mock data that you want to send to your directive. (2c)

    3. Note that your directive also names a separate file (1c) that will
     sit in the same folder as index.html. Create that file and use html
     and whatever classes and styles you want to make it pretty.

    // element01.html
    <div class="pretty-circle">
        <h1>
            Peanut is {{el01.user_age}} years old
        </h1>
    </div>

    4. Wherever you want to allow through data from your controller, use
    the double curly braces, and prefix the variable with the 'as' name you
    chose in your controller function above. (1d)
    When we do it this way, we are using the 'controller as' syntax instead of
    using '$scope'.

    5. Make your directive visible in the browser as seen in line 3. You can
    place your directives anywhere on the page by wrapping them in a grid system
    like Bootstrap or Foundation.

    6. Create a new html file for each directive, and write the
    corresponding angular code in your index.html file. Repeat several times
    until you have learned the process.

##### * note

    * Professionals would never write their angular code inside of script tags
    like we do in this example. Controllers and directives would also be in separate files
    and seperate folders. This way, though, gives us a good way to practice for beginners.
    * directives are normally placed in their own folder, and line 1c
    would give the path to that folder
    * some coders will not write seperate 'named' functions for their controllers
    and directives. They will instead combine lines 1a and 1b, and combine lines 2a and 2b using
    anonymous functions.
    Using Live Templates (a topic for another day), there is no extra typing involved
    in doing it the way we do it, with 'named' functions.
