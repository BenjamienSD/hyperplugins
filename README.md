configuration for the hyper command line application. In particular the 'retro' setup to mimic 'cool-retro-term'.

https://github.com/slammayjammay/hyper-postprocessing/issues/27#issuecomment-554684042


    make a directory under home, .hyper-plugins
    in that folder run npm install postprocessing three
    download the repo as a zip, and extract the contents of the examples folder to .hyperplugins. When you are done the folder structure should look like

effects
glsl
images
node_modules

    Add 'hyper-postprocessing' to the .hyper.js plugins array as specified in the docs
    In .hyper.js under exports add

hyperPostprocessing: {
     entry: '<ABSOLUTE PATH TO YOUR HOME DIRECTORY>\\.hyper-plugins\\.hyper-postprocessing.js'
}

    Create a file .hyper-postprocessing.js inside of the .hyper-plugins directory.

    To enable retro I put the following in .hyper-postprocessing.js:

const { readFileSync } = require('fs');
const { resolve } = require('path');
const pp = require('postprocessing');
const retro = require('./effects/retro');

module.exports = ({ hyperTerm, xTerm }) => { return retro({hyperTerm, xTerm}); };

I was then able to modify effects/retro/index.js to customize the retro plugin, as well as modifying the shaders, to suit my preferences.
