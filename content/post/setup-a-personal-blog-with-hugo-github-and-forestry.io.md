+++
categories = ["github", "hugo", "blog"]
date = 2020-12-28T23:00:00Z
description = "Finally finding a proper setup for a free blog-setup"
image = ""
title = "Setup a personal blog with Hugo, Github and Forestry.io"
type = "post"

+++
I wanted to setup a personal blog and migrate my posts from Medium.

It turned out, that there is a plethora of possibilities to host your own blog today. Having different static-site generators like [Gatsby](https://www.gatsbyjs.com/), [Jekyll](https://jekyllrb.com/) and [Hugo](https://gohugo.io). They can also be combined with Headless CMS systems as "data source" and then using services like [Netlify](https://www.netlify.com/) or Vercel to host/publish your changes immediately.

So a setup can potentially look like this:

* (Headless) CMS: for generating/managing content
* Static site generator: for generating the blog from the content
* Deployment service: for (automatically) building the website and deploying it to a server

### Ghost

Next to that you also can host your blog with more advanced and all-in-one systems like  [Ghost](https://ghost.org/), which are more focussed on building blog audiences and also include billing systems and more.  
Ghost is generally open-source but hosting a ghost instance is usually done by paid services. You can host it on your own, but if you're only having a simple webspace (without SSH) as I do, it's not possible to set it up there.  
You can run a ghost instance locally on your development machine and wire it up with a static site generator but when it comes to publishing this static site in an automated manner things get complicated again. You would need to have a tunnel to your local machine in our to let a deployment service like Netlify access the data from your local ghost instance. Also you'd only be able to write/adapt content on your local machine.  
As this was too combersome and I was looking for a zero-cost solution, Ghost was not suitable for me.

### Static site generator

For the use case of a personal blog you should find any of the major static site generators as a suitable tool.  
Those site generators basically build the blog from markdown content and generate a _public_ directory that can be hosted anywhere.

In order to have a convenient blog experience I wanted to have something like an editor for the posts and then automatically updating all the content on the blog. Like a wordpress site.

### Editing

You can accomplish that by hosting your hugo code on any git repository (like Bitbucket, Github) and using [Forestry.io](https://forestry.io) as a "frond-end" editor of your blog.

> To put it simply, Forestry is an editor-friendly interface over Git. This means that developers and editors can now use the same workflow and tool set.

It basically just reads and writes the blog source code from the repository.  
With that you get a better editing experience of the blog instance.

### Publishing

There are really convenient ways of having automated deployments of those static site generators with services like Netlify or Vercel.  
Those are basically watching your blog repository and then compiling it with the preferred static site generator framework and then hosting it on their servers.  
You can also hook up custom domains to that servers.

The problem in my case was that I use a small webspace package that does not support custom DNS entries for my domains, so I could not add DNS-Servers from those hosting services and therefore not use my custom domain.

### Back to basics

I could find a workaround for that problem with [Github Actions](https://github.com/features/actions)

As I was already hosting the blog code on Github it was easy to add an action for building my blog with an action. There are quite a lot of actions available for the different site generators.  
After buidling the site I now had to find a way of deploying the compiled site to my webspace. For that I'm now using a simple FTP action to transfer the complied _public_ folder to my webspace.  
Turns out the setup is also pretty easy. Here's how my action looks like

    on:
    push:
        branches: [ master ]
    jobs:
      deploy:
        runs-on: ubuntu-18.04
        steps:
          - uses: actions/checkout@v2
            with:
              submodules: true  # Fetch Hugo themes (true OR recursive)
              fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod
          - name: Setup Hugo
            uses: peaceiris/actions-hugo@v2
            with:
              hugo-version: '0.79.1'
              extended: true
          - name: Build
            run: hugo --minify
          - name: 📂 Sync files
            uses: SamKirkland/FTP-Deploy-Action@4.0.0
            with:
              local-dir: public/
              server: <my-server>
              username: <my-user>
              password: ${{ secrets.ftp_password }}

With that I could finally find a way of having an easy editor experience to my blog. Build and deploy it automatically, use my existing webspace and domain and all that without additional costs.

![](/images/flow.png)

Feel free to reach out if you have any questions!