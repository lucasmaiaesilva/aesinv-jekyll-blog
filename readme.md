# The Blog of Matt Bengston
This is the source for my blog, located at [aesinv.com](http://aesinv.com). It runs on [Jekyll][], a static-site generator, with added development functionality via [Gulp][]. You can read up on the implementation of Gulp on this [blog post](http://aesinv.com/development/2015/08/19/building-a-gulp-workflow-around-jekyll.html).

## Dependencies
- [Bower][]: Front end dependency manager (full integration still WIP)
- [Gulp][]: Workflow automation and task management
- [Node.js][] / [NPM][]: JS Runtime for Gulp and Gulp dependency management

## Project Setup
- Make sure [Node.js][] and [NPM][] is installed locally
- Make sure you've gone through and followed the [Jekyll Installation Guide](http://jekyllrb.com/docs/installation/ "Jekyll Installation Guide"), and have [Ruby][] and [RubyGems][] installed on your machine
- Clone/fork project locally
    + `git clone <repo url> .`
- Ensure [Gulp][] is installed
    + `npm install -g gulp`
- Ensure [Bower][] is installed
    + `npm install -g bower`
- Install [NPM][] package and dependencies
    + `npm install`

## Project Workflow
#### `gulp build:assets`
Concatenates, minifies, and optimizes all site JavaScript, runs the [Jekyll][]-built stylesheet through an auto-prefixer and minifier, then optimizes all published images within the `/project/img/` directory.

#### `gulp serve`
Creates a local server via [Browsersync][], runs the [Jekyll][] build, runs the `build-assets` task, then watches for any changes within the `/project/` directory. Rebuilds necessary files and refreshes the [Browsersync][] server on changes.

#### `gulp deploy`
Runs the [Jekyll][] build with the production config file, then runs the `build-assets` task to build and optimize all site assets.

## Project Structure
```
_dist: Auto-generated built website
bower_components: Front end dependencies
gulp-tasks: Gulp task module files
project: Main project source
    - _assets: Excluded asset files
    - _data: Well formatted site data to be loaded into the site.data global
    - _drafts: Unfinished and unpublished posts
    - _includes: Partials that can be used by other partials as well as layouts
        + components: Components that make up other components and partials
        + custom: Feeds and other self-contained partials
        + svg: SVG's that can be embedded directly into layouts and components
    - _layouts: Usable site layouts made of partials
    - _plugins: Jekyll plugins to include/run when building the site
    - _posts: Published posts
    - _sass: Main styles source
        + components: Styles corresponding to /project/_includes/components items
        + fonts: Custom font declarations
        + partials: Styles corresponding to /project/_includes partials
        + vendor: 3rd party dependencies to be included within the built stylesheet
    - css: Includes main stylesheet
    - fonts: Custom font files
    - img: Published/included image files
        + icons: Site icons (favicons, twitter/og/ms icons)
        + seasonal: Images relating to seasonal settings/components
        + videos: HTML5 Videos and their fallbacks
    - js: Site scripts
        + lib: Vendor libraries/polyfills included in the project
```

## Feature Images
Each post with a featured image requires two images:
- Main feature image: `1920x575`
- Icon: `200x200`

Featured icons can be specified within the [YAML][] front matter block at the top of the post.

```yaml
---
feature: post-feature.png # Relative to /project/img
featureico: post-feature-icon.png # Relative to /project/img
featurealt: The alt message for the featured image.
---
```

## HTML5 Videos
Videos and a single fall-back image should go within the `project/img/videos` directory, with the following specs:
- Size: 750px wide (for full-screen captures @ 1920x1080 or 2880x1800, 750px x 450px)
- Formats: `.mp4`, `.webm`, `.ogv`
- Fallback: A single image file with the same dimensions and same file name.

## Hat Tips
- [Benoît Boucart](http://blog.webbb.be/): Wrote an awesome article on using Jekyll with Gulp, which opened me up to the `child_process.spawn` method.
- Icons from the [Noun Project][]:
    + Category icon on post pages: Shai Rilov
    + Tags icon on post pages: factor[e] design initiative

## TODO
- Sticky chapter guide
- Add "pinned post" functionality (mostly for cars category, for my post engine resource guide)
- Add tag cloud of sorts to expandable sidebar
- Add social share function

[bower]: http://bower.io/
[browsersync]: http://www.browsersync.io/
[gulp]: http://gulpjs.com/
[jekyll]: http://jekyllrb.com/
[node.js]: http://nodejs.org/
[npm]: http://npmjs.org/
[noun project]: https://thenounproject.com/
[ruby]: https://www.ruby-lang.org/en/downloads/
[rubygems]: https://rubygems.org/pages/download/
[yaml]: http://yaml.org/
