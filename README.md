Next.js has a file-system based router built on the concept of pages.

When a file is added to the pages directory it's automatically available as a route.

The files inside the pages directory can be used to define most common patterns.

Index routes
The router will automatically route files named index to the root of the directory.

pages/index.js → /
pages/blog/index.js → /blog

Code splitting and prefetching
Next.js does code splitting automatically, so each page only loads what’s necessary for that page. That means when the homepage is rendered, the code for other pages is not served initially.

Next.js supports CSS Modules using the [name].module.css file naming convention.

CSS Modules locally scope CSS by automatically creating a unique class name. This allows you to use the same CSS class name in different files without worrying about collisions.


Global Styles
CSS Modules are useful for component-level styles. But if you want some CSS to be loaded by every page, Next.js has support for that as well.

To load global CSS files, create a file called _app.js under pages and add the following content: