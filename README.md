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
* The 'render' callback receives an object previous returned by 'getData', and it returns html that will get inserted into the DOM.


