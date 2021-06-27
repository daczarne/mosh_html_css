# Site example

This is the code for building the example site [moshified.com](https://www.moshified.com/). Other additional notes can be found here too.

## Animation

The animations where build using the [Animate on scroll](https://michalsnik.github.io/aos/) library.

## Building for production

We use build tools to minify CSS and JavaScript, combine them into single files, optimize images, etc. The goal is to reduce the number of requests that the browser needs to send in order to get all the resources it needs to display our page.

There are multiple build tools available. Here we'll use [Parcel](https://parceljs.org/). To use it you first need to install [Node.js](https://nodejs.org/en/). To make sure that is was installed correctly run:

``` bash
node -v
```

and the installed version of node should be displayed.

Node comes with a tool called NPM (**Node Package Manager**) which we can use to install third-party libraries (dependencies). To use NPM, first we need to initialize an NPM package in this directory. To do so, run:

``` bash
npm init -y
```

Once this runs, a new file should appear in the current directory called `package.json`. No to install Parcel we run

``` bash
npm i -D parcel-bundler
```

where the `-D` flag means that this is a development dependency, and not something that we want to ship to production. If we want to specify a version of this library we change the `library-name` in the previous command for `library-name@version`.

Once done three things will happen. First, the `parcel-bundler` library will appear in `package.json` in the `devDependencies` section. Second a new JSON file will appear, called `package-lock.json`. This is a very long JSON file that lists all implicit dependencies (that is, the dependencies that we install, plus all dependencies of our dependencies and their dependencies, and so on). It includes all information for this project (like versions of the libraries and their requirements).

All the code for all these libraries can be found in a folder that just got added to the root of our project called `node_modules`. Make sure to add this directory to `.gitignore` (if not there already). We only version control the package files. With just those, the entire environment can be reproduced in any computer.

Now to launch our website with Parcel we run:

``` bash
node_modules/.bin/parcel index.html
```

If we don't want to type all that much every time we need to launch, we can install Parcel globally. To do so, we run (this command might need a `sudo` before it):

``` bash
npm i -g parcel-bundler
```

Now we can call Parcel from any folder in our computer. So we just run

``` bash
parcel index.html
```

After running it, make sure to include the new sub-directories `.cache` and `dist` to the `.gitignore` file.

When we are ready to build it for production we run:

```bash
parcel build index.html
```

## Deployment

When deploying (for example, with Netlify) make sure to specify the build command.

```bash
parcel build index.html
```

Also, specify that the directory to be published is the `dist` directory, since this is the directory with all the minified versions.

## Measuring site performance

To measure site performance you can use [web.dev](https://web.dev/measure/), enter the page's URL, and run an audit.
