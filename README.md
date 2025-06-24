# FOCAL Lab website
This repository contains the source code and media for the [FOCAL website](https://focal-website-2.netlify.app/). Building these source files into an actual HTML website relies on [Hugo](https://gohugo.io/), using the [Hugo Blox](https://hugoblox.com/) theme (specifically the [Boostrap version](https://bootstrap.hugoblox.com/)) and is based on the [Research Group](https://github.com/HugoBlox/theme-research-group) starter template. The build is performed at [Netlify](https://www.netlify.com/) upon push or mege to main. Netlify also serves the site. A preview version of the site is also built and served upon submission of a PR.

<br/>

### Editing Tips

Edit the home landing page at `/content/_index.md`. All other pages can be edited in folders within `/content/`. e.g., the tools page is at `/content/tools/_index.md`
  



## Previewing edits before publishing

There are two ways to preview edits before they become public. **1.** The Netlify option does not require any local software or compute, but it requires pushing changes to Github, submitting a pull request, and waiting about a minute for the website to build. **2.** The local option does not require pushing changes, builds almost immediately, but requires having hugo installed locally.

### Using Netlify's deploy-preview feature

If you commit your changes to a branch, push the branch to GitHub, and then submit a pull request, it will trigger Netlify to build a "deploy preview". Within a few seconds of creating the PR, Netlify will add a comment to the PR that a preview is building, and within a minute or two, it will update with a link to the preview. It is accessible to anyone on the internet but they would need to have the URL (which they could get by visiting our GitHub repo and viewing the PR).

After creating the PR, any additional commits pushed to the branch will trigger an update to the deploy preview. During the build, the Netlify comment will say "building" and when done it will return with the link to the site preview.

### Locally

To edit the website locally, clone this repo to your machine `git clone https://github.com/focal-lab/focal-website-2.git`

Install the required `hugo extended` dependencies following the `hugo blox` instructions [here](https://docs.hugoblox.com/getting-started/install-hugo/).

Then, in a terminal with the root of the website repo as your working directory, run `hugo server`. The website will build in a few seconds, and then the terminal will tell you it is being served at localhost:1313. Go to this URL to see the site.
