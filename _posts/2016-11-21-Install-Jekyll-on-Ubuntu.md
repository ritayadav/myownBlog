---
title: "Install Jekyll on Ubuntu (Linux)"
modified: 2016-11-22T09:55:10-04:00
permalink: /posts/2016/11/Install Jekyll on Ubuntu/
categories: 
  - Linux
tags:
  - Jekyll
  - Ruby
---

Jekyll is a static site generator with a templating system that can be adapted for many types of websites, including blogs. It can be run on a server, or run locally and the generated files uploaded to a server. It is the default software used by Github Pages.

_Tested with Jekyll 3.3.1 on Ubuntu 16.04 and 14.10_

Install Prerequisites
======
Install ruby, the ruby development libraries, and the make command.

sudo apt-get install ruby ruby-dev make gcc nodejs
{: .notice}

## Javascript Workaround
Installation of  `nodejs` is required because of an issue where Jekyll requires a JavaScript runtime even if it will not be used

Install Jekyll
======
Install the Jekyll gem system wide. For speed, we are excluding the extended documentation. To include all documentation, omit the `--no-rdoc --no-ri` switches.

sudo gem install jekyll --no-rdoc --no-ri
{: .notice}

Start Jekyll
======
Check that Jekyll has been successfully installed.

jekyll -v
{: .notice}

The current version is `jekyll 3.3.1`.

Recommended
======

Additional gems can add features to Jekyll, such the github-pages gem which bundles together several gems supported by Github Pages.

sudo gem install github-pages --no-rdoc --no-ri
{: .notice}

Although not required, `git` is often used to manage the files of a Jekyll website.

sudo apt-get install git
{: .notice}

## Get Website Content

Now that Jekyll is installed, we need content for it to serve. We can either use a current website, or set up a new site from scratch.

### Use Existing Site

Use `git` to clone an existing Jekyll website, such as this one!

git clone https://github.com/mchelen/michaelchelen.net.git <br>
cd michaelchelen.net
{: .notice}
Please note: the `--config` option must be specified to run `michaelchelen.net` locally. See Extra Options section below.

### Create New Site

For a new Jekyll site, use the `new` command to create a directory structure and config files.

jekyll new my-awesome-site <br>
cd my-awesome-site 
{: .notice}

## Start Jekyll

Now that the basic config and layout are available, start Jekyll to generate the website HTML and start a local server.

jekyll serve
{: .notice}

Then visit http://localhost:4000 in a web browser.

_Jekyll is now successfully runnning!_

## Extra Options

Jekyll can watch the directory for changes and regenerate the website when files are modified.

jekyll serve -w
{: .notice}

The default port `8000` can be changed, for example when running multiple Jekyll instances.

jekyll serve --port 4001
{: .notice}

Then visit http://localhost:4001 in a web browser.

The `_config.yml` can also be specified. This is useful if you need different configs for a public site or when running locally. For example, when running `michaelchelen.net` locally use:

jekyll serve --config _config-local.yml
{: .notice}

The website can also be generated without starting a local server. The files are placed into the `_site` directory and can be uploaded to a web server.

jekyll build
{: .notice}

## Updating Jekyll

Jekyll can be updated similar to installation, by using the `gem update` command.

sudo gem update jekyll --no-rdoc --no-ri
{: .notice}

The same command can be used to update additional gems.

sudo gem update github-pages --no-rdoc --no-ri
{: .notice}
