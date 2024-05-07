# eg_11tail
A scaffolded starter repo for the [11ty](https://www.11ty.dev/) static site generator (SSG), with [TailwindCSS](https://tailwindcss.com/installation) and [DaisyUI](https://daisyui.com/) for interface styles and components. 

## Usage
  1. Download/clone the repo
  2. In your terminal, change your working directory to the repo's and run ```npm install``` (to download the package dependencies and create an up-to-date ```package-lock.json``` file).
  3. Run ```npm run compile``` to issue the tailwindcss build command. 
  4. Open a second terminal session and run ```npm run start``` to run the eleventy build and start the development server
  5. Visit the URL shown in the terminal (probably localhost:8080)
  6. The contents of ```_site``` can be deployed

## Summary and Notes
Files in the ```/src``` directory are processed by 11ty and Tailwindcss and output to ```/_site```, which is the build directory. These are specified in the following config files: ```tailwind.config.js```, ```.eleventy.js```, and in the "compile" script in ```package.json```.

The theme is controlled by DaisyUI and is set inside ```tailwind.config.js```; see [https://daisyui.com/docs/themes/](https://daisyui.com/docs/themes/) for instructions. 

The eleventy config, ```.eleventy.js``` specifies html, markdown, and nunjucks as templating files, and adds ```/src/assets``` and ```/src/css``` as pass throughs; see [https://www.11ty.dev/docs/copy/](https://www.11ty.dev/docs/copy/) for more information on this important function.

The ```/src/includes``` directory contains the layouts (just a base layout so far), as well as components (a boilerplate nav component from DaisyUI is loaded for testing, and is called from ```/src/includes/base.html```).

If you want to deploy this to a public server, simply copy the contents of ```_site``` to the top level of your publically shared directory. 

Both eleventy and tailwind are watching for changes to your files (with the --serve and --watch flags in ther respective commands), so you should be able to 'hotload' edits in the browser (i.e. see them as you make them) out of the box. your terminal sessions and rerun the ```npm``` commands in new sessions.

It should go without saying, but further additions, such as other pages, a different folder structure, etc., may neccessitate changes to the paths in the various config files to tell 11ty and Tailwind where to be looking for templates and CSS classes. The compile command in particular needs to specify the correct input and output files.