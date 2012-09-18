media_flow
==========

media_flow.js is a JQuery plugin for creating a continuous flow of elements in a browser.  This effect can work well when browsing a large collection of visual data.  Some examples:

EXAMPLES

Images posted to Reddit:

http://www.tristara.com/reddit_blaster

Images of your friends on FaceBook:

http://www.tristara.com/facebook_blaster

Fashion e-commerce:

http://www.whimsi.com/

WHAT DOES IT DO?

media_flow.js uses CSS transformations to move elements across the browser window

The code also manages which elements are visible, and provides various callback functions for the user to define the behavior.

To use, you must supply your own logic that renders the elements.

USAGE

1) Create a div that will be the parent for all the flowing elements, like:

<div id='#media_flow'>

2) Define options that control the animations, like:

    var flowOpts = {
        speed: 3,
        rows : 4,
        cols : 7,
        width : 160,
        height : 160,
        getData : my_module.getData,
        render : my_module.render
    };            

3) Initialize the media_flow element:

$('#media_flow').media_flow(flowOpts);

4) Start it with

$('#media_flow').media_flow('start');

What then happens is this plugin will call

* The 'getData' callback whenever it needs your application to provide the state required to render an element.  Your callback will return an opaque object that is passed to the 'render' callback.
* The 'render' callback receives an object previously returned by 'getData', and it returns html that will get inserted into the DOM.

OPTIONS

* padding, amount of padding between rendered elements.  Default 0.
* clipWidth and clipHeight, the width and height of the box that clips the rendered elements.  Default 0.
* clipLeft and clipTop, the top left pixel of this clip box.  Default 0.
* speed, the speed of animation (defined as pixels moved every frame).  Default 3.
* offsetLeft and offsetTop, the offset added to all the rendered elements.  Default 0.
* rows and cols, the number of rows and colums to render.  Default 0.
* width and height, the width and height of each rendered element.  Default 0.
* totalWidth, to total width for an entire row of rendered elements.  Only used if 'compressLayout' is true.  Default 0.
* idleFrames, the number of elements who can be rendered without any user interaction before forcing a pause (to prevent resource exhaustion).  Default 100.
* getData, the callback that asks the application to choose the model for what gets rendered.
* render, the callback that asks the application to create the html that renders the model.
* onClick, the callback that tells the application the user clicked on an element.
* idle, the callback that tells the application the media_flow has paused due to inactivity.
* decorateCell, a method that media_flow calls on an element every time the application create it, which calls the application to do things like set hover events.
* compressLayout, if true, media_flow will try to pack elements as tightly as possible (rather than use the 'width' parameter).  Default false.
* useTranslate3d, if true, media_flow will try to use hardware accelated transformations (especially useful for mobile/iPad).  Default false.

METHODS

* 'start', starts the animation.
* 'setSpeed', changes 'speed' option after initialization.
* 'map', maps a function to every element.
* 'pause', pauses animation.
* 'resume', resumes animation.
* 'clear', clears all elements (useful if you want to display a new search criteria).
  