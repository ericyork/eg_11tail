# eg_11tail
This repository contains a basic scaffolded starter repo for the [11ty](https://www.11ty.dev/) static site generator (SSG), with [TailwindCSS](https://tailwindcss.com/installation) and [DaisyUI](https://daisyui.com/) for interface styles and components.

## Requirements
Both 11ty and TailwindCSS require [node.js](https://nodejs.org) version 14 or higher. You can check this in your terminal by running ```node --version```. Additionally, it's helpful to have at least basic knowledge of node, npm, HTML, CSS, and JS, and knowledge of markdown and nunjucks is useful too. 

## Usage
  1. Download (or clone) the repo and, in your terminal, ```cd``` to the repo directory 
  2. Run ```npm install``` (downloads packages and dependencies)
  3. Run ```npm run compile``` (builds the css files)
  4. Open a second terminal session and run ```npm run start``` (builds the 11ty files)
  5. Visit the URL shown in the terminal, by default [localhost:8080](localhost:8080)

## Summary and Notes
Files in the ```/src``` directory are processed by 11ty and Tailwindcss and output to ```/_site```, which is the build directory. These are specified in the following config files: ```/tailwind.config.js```, ```/.eleventy.js```, and in the "compile" script in ```/package.json```.

Because the contents of ```node_modules``` are excluded by ```.gitignore```, you will need to use ```npm install``` the first time you download the repo in order to add all the core packages and their dependencies, and to generate an updated ```package-lock.json```. This is done in Step #2, above.

The scripts, ```npm run compile``` and ```npm run start```, are defined in ```/package.json``` and are comprised of the default tailwind and eleventy commands. If you add a new script, you'll need to rebuild ```package-lock.json``` with npm. These are Steps #3 and #4, respectively.

## Configurations

The site theme is controlled by DaisyUI and is set inside ```tailwind.config.js```; see [https://daisyui.com/docs/themes/](https://daisyui.com/docs/themes/) for instructions. It's currently set to Retro for light and Coffee for dark, in hopes you will change them ;) The link above has a lot more information about themeing.

Tailwind's typography plugin is already installed, so you can use the ```.prose``` class, and the compile step includes postcss and autoprefixer as is standard.

The eleventy config, ```.eleventy.js```, specifies that html, markdown, and nunjucks can be used as templating files, and it also adds ```/src/assets``` and ```/src/css``` as pass throughs; see [https://www.11ty.dev/docs/copy/](https://www.11ty.dev/docs/copy/) for more information on this important function.

The ```/src/_includes``` directory contains page template layouts (just a base layout so far), as well as components (a boilerplate nav component from DaisyUI is loaded for testing, and is called from ```/src/includes/base.html``` using nunjucks templating).

## Development
Both eleventy and tailwind are watching for changes to your files (with the *--serve* and *--watch* flags in ther respective commands), so you should be able to 'hotload' edits in the browser (i.e. see changes as you make them) automatically. Some changes will require you to end your terminal sessions and rerun the ```npm``` build commands inside new terminal sessions.

## Deployment
To deploy a static site to a public server, run fresh ```npm``` commands and then simply copy the contents of ```/_site``` to your publicly shared directory. You may need to adjust files paths in your template files, depending on your deployment environment.

## NB
It should go without saying, but further additions, such as other pages, a different folder structure, etc., will likely neccessitate changes to the paths in the various config files to tell 11ty and Tailwind where to be looking for templates and CSS classes. The compile command in particular needs to specify the correct input and output files.