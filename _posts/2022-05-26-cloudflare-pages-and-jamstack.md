---
title: Cloudflare Pages and Jamstack - How I got here
published: true
---

# A little backstory

Now, I was a bit late to the train with Jamstack. I got comfortable where I was at and ultimately didn't give much thought to the domains that I've owned. For the past 8 years or so, I've been running a number of very basic one-off websites. The better part of those years was spent with me managing DigitalOcean droplets. They did their job exceedingly well for the low price of $5/month. I was able to run 6 separate, _mostly_ static websites on a single droplet. Even having one of these websites blow up on Reddit, my droplet handled it without so much as a drop of sweat. In fact, I didn't even notice the large influx of traffic until I looked at my analytics.

These websites are mostly just static websites. They run PHP and nginx and just have a landing page more or less. Extremely simple sites, but they served
their purpose.

Recently, while navigating through my Cloudflare dashboard I decided to investigate further a tab I've seen countless times before. Cloudflare Pages.

# The Jamstack Revelation

While I keep up to date in my specific field of modern software development, primarily with PHP 7-8 and Laravel, I haven't really done much research into static sites. I knew they were popular. Cloudflare's own documentation is a static site built with [Hugo](https://gohugo.io/). What I didn't realize was just **how** popular they are. While navigating through the Cloudflare Pages dashboard for the first time, there was something that really caught my eye.

**Deploy front-end applications in record time.**

Now, that's a pretty compelling tagline if you ask me. I tapped the button labeled _Create a project_, connected my GitHub account and began scrolling through the list of available presets. Jekyll was the first one in that list. I started doing some more search. Checking out the Jekyll [website](https://jekyllrb.com/) I scrolled through the [showcase](https://jekyllrb.com/showcase/). Wow. There was a lot of gorgeous, lightning fast sites. That led me down the rabbit hole of ending up on websites like [jamstack.org](https://jamstack.org/) and [jamstack.wtf](https://jamstack.wtf/). Consider my interest piqued. It sounded like a dream come true. These websites are selling me the dream. It may sound like I just crawled out from under a rock but my entire world has been primarily backend development with PHP and Laravel. You're telling me that I can host an entirely static site by creating some files in Git _and_ it's deployed automatically with new subdomains for branches and automatic builds for _main_? With effectively zero configuration and nearly instant? Oh, and it's free. Turns out GitHub Pages, Netlify, Cloudflare Pages, and a number of other static website providers have generous free plans. If I could get away from paying DigitalOcean $5/mo for a droplet I touch once a year for tiny projects that don't even have a git respository.. that sounds perfect.

# Cloudflare Pages

If you know me in any technical fashion, it's no secret I _love_ Cloudflare. At work, we have an enterprise plan to protect and accelerate our customer's websites. For personal use, all my sites have always had Cloudflare in front of it. I think I've been using Cloudflare for nearly 7 years now. It has too many benefits to ignore and the free plan basically covers everything I could actually need. Sure, there's other paid features that would be a nice bonus but honestly, I just don't need it.

I navigated over to the Jekyll website and started the installation. Pretty simple, just grab the latest version of Ruby from homebrew and get going. I created some new GitHub repos for some of my various domains I have: darin.sh, darinrandal.com, cudi.zone and erppy.co. I ran the scaffolding for my first Jekyll installation for darin.sh and committed it straight to main.

Swapping back over to my Cloudflare Pages tab, I launched a new Pages project and selected the new repo for darin.sh. The process was shockingly simple. I chose the repo and set the preset to Jekyll, pressed continue and it was done. My boilerplate Jekyll install for darin.sh was live on [darin-sh.pages.dev](darin-sh.pages.dev). Yeah, it was that simple. I was absolutely shocked. How have I never really heard more about this? I knew static sites existed but I could've never imagined how simple it was to use. I just launched a brand new website on a subdomain in less than five minutes. I was sold.

# Moving over all my existing static sites

I logged into my DigitalOcean VPS and took a backup of my `/var/www` folder that contained all the sites I've hosted on it over the years. As these were just silly static sites, I never had a repo for it. I just dragged the index.html over to the droplet. Do you really need version control for a single index.html with 40 lines? That was the question I asked myself back then. It was the easiest option, until now. 

Here's a couple ones that you may get a kick out of:

- snoopdo.gg - This used to just be a static site that played Drop It Like It's Hot with Snoop Dogg dancing. I sadly let the domain expire a few years back since it cost something like $70/year. It was immediately picked up and now parked by some madman probably trying to sell it to Snoop Dogg. What a shame.
- cudi.zone - A shoutout to Kid Cudi, one of my favorite artists back then and his song Cudi Zone. I let it expire a few years back and managed to grab it again just a few days ago. Someone owned it for a few years and did something similar to the site that I had on it previously.

The migration process was simple. I created the GitHub repositories for

- darin.sh - This was originally just a extraordinally basic vanilla JS terminal. My plan was to make this site my hacker-style blog. You're probably on it now. The theme would be akin to a terminal thanks to the shell script tld.
- darinrandal.com - Currently just a dead website. I want to turn this into a professional portfolio and resume. I'll have it link out to all my other sites and platforms as well.
- erppy.co - This site I've ran for 8 years now. It just takes a gorgeous visualizer from the old Chromium projects iframed in, and plays Deadmau5 - Strobe from a hidden YouTube player. It's _really_ popular, like, 25-75k visitors a month popular. Why? I'm not sure.
- cudi.zone - Working on updating it. Just displays album artwork and used to play a Kid Cudi - Cudi Zone before autoplaying audio was frowned upon and disabled.

Once I got those repos set up with the static files for those websites I created the Cloudflare Pages projects for each one, connected it to the respective GitHub repo and deployed them. Each project was then tested with the pages.dev URL provided and configured to use my custom domains. Done. My domains now point to Pages instead of my DigitalOcean VPS. It took less than ten minutes to do all of them. It cannot be overstated how in awe I was at this process with how easy and quick it was.

# Deleting my DigitalOcean VPS

In the eight years of running this same $5/mo VPS with its 512MB of RAM and 1 vCPU, it's never had downtime. I think there was part of me that was sad to see it go. It had served me well for so long and here I was, ready to end its life. Its time has come and gone with the ability to serve static websites from the edge. I clicked delete and typed out the name of the VPS. Permanent deletion and scrubbing of 'ol faithful took less than 20 seconds. The future of static sites is here, and it's not with a VPS.