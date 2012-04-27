# webos-events package for Enyo 2

This package provides support for standard webOS events for Enyo 2.0 using the Signals kind.

## Installation and usage

Add this project as a submodule in your project's `lib` folder, clone it into a shared `lib` folder, or copy the files into your project's `lib` folder, then make sure your project's `package.js` file links against the package:

    enyo.depends(
        // Also link against your other files, of course
        '$lib/webos-events/'
    );

After you have installed the package, you can access the following events using enyo.Signals:

* onapplicationrelaunch
* onwindowactivated
* onwindowdeactivated
* onwindowhidden
* onwindowshown

For instance, you might want to know when your app moves to the background:

    components: [
        {kind: "Signals", onwindowdeactivated: "deactivateApp"}
    ],
    
    deactivateApp: function(sender, event) {
        // Deactivate timers and so forth
    }

Except for `onapplicationrelaunch` all events receive standard empty event objects. For relaunch events, though, you can access `event.windowParams` to see if there were any window paramaters passed through:

    applicationRelaunch: function(sender, event) {
        if (event.windowParams && event.windowParams.dockMode) {
            // Launched in Exhibition mode
        }
    }

**Please note:** the application relaunch event is not triggered when your app first launches! I have not yet figured out how to make this happen, so for now that event will only handle relaunching the app after it is already launched.

## License

Mojo property code from Enyo 1.0, released under an Apache v2 License: <https://github.com/enyojs/enyo-1.0>

All other code copyright (c) 2012 Ian Beck, released under an MIT license

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
