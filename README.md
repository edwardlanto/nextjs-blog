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

Using classnames library to toggle classes
classnames is a simple library that lets you toggle class names easily. You can install it using npm install classnames or yarn add classnames

Out of the box, with no configuration, Next.js compiles CSS using PostCSS which autoprefixes CSS styles.

By default, Next.js pre-renders every page. This means that Next.js generates HTML for each page in advance, instead of having it all done by client-side JavaScript. Pre-rendering can result in better performance and SEO.

Each generated HTML is associated with minimal JavaScript code necessary for that page. When a page is loaded by the browser, its JavaScript code runs and makes the page fully interactive. (This process is called hydration.)

Next.js has two forms of pre-rendering: Static Generation and Server-side Rendering. The difference is in when it generates the HTML for a page.

Static Generation is the pre-rendering method that generates the HTML at build time. The pre-rendered HTML is then reused on each request.
Server-side Rendering is the pre-rendering method that generates the HTML on each request.

When to Use Static Generation v.s. Server-side Rendering
We recommend using Static Generation (with and without data) whenever possible because your page can be built once and served by CDN, which makes it much faster than having a server render the page on every request.

You can use Static Generation for many types of pages, including:

Marketing pages
Blog posts
E-commerce product listings
Help and documentation
You should ask yourself: "Can I pre-render this page ahead of a user's request?" If the answer is yes, then you should choose Static Generation.

On the other hand, Static Generation is not a good idea if you cannot pre-render a page ahead of a user's request. Maybe your page shows frequently updated data, and the page content changes on every request.

In that case, you can use Server-side Rendering. It will be slower, but the pre-rendered page will always be up-to-date. Or you can skip pre-rendering and use client-side JavaScript to populate frequently updated data.

getStaticProps runs at build time in production, and…
Inside the function, you can fetch external data like an API and send it as props to the page.

SWR
The team behind Next.js has created a React hook for data fetching called SWR. We highly recommend it if you’re fetching data on the client side. It handles caching, revalidation, focus tracking, refetching on interval, and more. We won’t cover the details here, but here’s an example usage: