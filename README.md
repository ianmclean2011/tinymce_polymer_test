# \<tinymce_polymer_test-element\>



## Steps to get started

First, make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. 

After cloning the repo, run 'bower install'

Then run `polymer serve` to serve your element locally.

If you go to http://127.0.0.1:8081/demo/ , you should see the tinymce editor, within a webcomponent, open properly in fullscreen in latest Chrome, but not in FF/Edge/IE11. The commented out code in index.html was used to test creating a fullscreen editor not within a webcomponent, but still on a page loading shadow-dom polyfills, to show that it works fine in all browsers.

The error that shows up in FF is 'TypeError: m is undefined' using the minified file, or 'TypeError: doc is undefined' from InitContentBody.ts:168:4 using the non-minifed file.

In InitIframe.ts, if you change line 133 from 'InitContentBody.initContentBody(editor);' to 'setTimeout(function() {InitContentBody.initContentBody(editor);}, 0);', it appears to work for FF and Edge. It looks like IE11 may need a tweak at line 27 of InitIframe.ts.


