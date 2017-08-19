# Data Science Decal Website

This repo hosts Machine Learning at Berkeley's Data Science Decal website. The Jekyll theme is from [here](https://github.com/old-jekyll-templates/Strata-Jekyll-Theme/tree/master/images).

## Instructions for MLAB editors

- This site is run of Jekyll, a ruby Gem that generates static sites.
- To use this repo make sure you have Jekyll [installed](https://jekyllrb.com/docs/installation/)
- To debug this site, run `jekyll serve` to create a local server. Go to the specified url (probably http://127.0.0.1:4000/decals/DSD/) to see the site.
- To generate the static site, run `jekyll build`. This generates the stie and puts it in the `_site` directory. (Only really need to do this on the OCF machine (see below))

Writing a post
- Go to the `_posts` directory and make a new markdown file in the same format as the other files
- Edit it using markdown syntax
- To debug, use `jekyll serve` (see above)

Deploying the website
- Push your changes to github
- Log on to the ocf server and go to `~/dgeng/` and find the appropriate directory/repo
- Git pull in the repo on the remote
- Start the rvm (see the README.md in `~/dgeng/`
- Run `jekyll build --destination ../../mlabweb/src/public/decals/DLD/` or `DSD` depending on which
