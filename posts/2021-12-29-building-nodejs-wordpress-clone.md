# WordPress Clone in Node.js

On December 15th I decided to rewrite WordPress in Node.js.

You will find the current dev version on [wordpress-clone-demo.herokuapp.com](https://wordpress-clone-demo.herokuapp.com/).

## Why

Before I learned how to program, I used WordPress to build my Websites. Now that I'm a JavaScript/TypeScript/Node.js expert, I know how slow WordPress really is and what it needs to be as fast as possible.

I already wrote an amazingly fast isomorphic JSX library ([Nano JSX](http://nanojsx.io)) and have a great understanding of Node's http module (gained while re-written [Express.js in TypeScript](https://www.npmjs.com/package/express6)), I thought it should be an easy task.

Within few days, NordPress (how I call it now), has already the possibility to edit pages, upload themes and plugins. It is amazing and I love working on it.

## Architecture

I will use only my own libraries to build NordPress.

- SSR-Renderer: Nano JSX
- Dashboard build using client-side Nano JSX
- tiny-http2-server as WebServer
- unnamed editor (currently working on) as WYSIWYG.

Plugins and Themes will be lazy-loaded on Node.js start. Once a plugin/theme gets installed, activated or deactivated, the Node.js server will restart and load the new configurations.

Plugins are completely isolated from the core. They will get a separate static route (e.g. http://example.com/api/plugins/NAME/...) and will be able to register an express.js like middleware.

...more
