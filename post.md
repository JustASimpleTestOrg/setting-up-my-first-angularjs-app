## 1 AirPair Development Philosophy

Pure best-practices AngularJS challenges some of my combined developer-entrepreneur value set. At AirPair, we code with the following priority order.

1. Revenue generating code
2. User experience
3. Best practices & maintainability

We have some application architecture decisions to make where (1), (2) & (3) can be at odds. Templating architecture is one area where where our prioritization probably conflicts with other developer cultures that may value scalability and reduced complexity higher than revenue.

## 2 Server and client-side templates
 The main issues with server-side vs client-side template architectures are SEO (important for revenue), social sharing of pages (again revenue) and flickering loading experiences of dynamic vs static pages (user experience). I'm very interested to explore the following options with some top notch experts:

### 2.1 Pure client-side templates
Matias Niemila is an AngularJS core team member. He is championing an application architecture with no server-side templates. There are compelling reasons for this architecture. You can build an extremely efficient data API and then deploy all your client side JavaScript and templates to a CDN which propagates your assets all over the world. You app is effectively as scalable and fast as your data API.

### 2.2 Mixing server and client
Another approach is to leverage the best of both worlds by doubling the work. In this architecture part of your app could be deployed on a CDN and the pages that need to be search-indexed or social shared could be served with server-side template by your own servers. The drawbacks of mixed templates are increased complexity. You have to define both server-side and client-side routes that might conflict with each other and you need to know and maintain multiple templates and template languages.

### 2.3 Shared templates
A cool optimization that gets rid of multiple template languages, and that I had with the previous version of airpair.com was using `handlesbars` as the client-side template language for `Backbone.js` on the client AND with `expressJS` on the server. Thus I was able to thus reuse the exact same templates on both serve and client. I'm not sure if this is possible with AngularJS, but it's something I'd like to look into.

## 3 Setting up AngularJS

Turns out you can get setup in 30 seconds.

### 3.1 Install AngularJS with Bower

Package managers have become omnipresent in server-side coding. Ruby Gems, nuget, pip, npm - you've heard of them and they're all awesome. Turns out the font-end kids have come up with their own font-end package manager called `bower`. Bower users a `bower.json` file for managing libraries, similar to a `package.json` file for npm / node_modules.

The `.borwerrc` file tells bower where to install packages. In our case the `public` dir.

Installing AngularJS took 4 steps:

 1. `npm install bower -g`
 2. Create `.bowerrc` file
 3. `bower install angular --save`
 4. reference angular like `<script src="/bower_components/angular/angular.js />`
	

### 3.2 Testing AngularJS with karma
We didn't get to the point of testing anything during our AirPair session, but I did learn about [`karma`](//karma-runner.github.io/). In airpair.com v0, I used `phantomjs`, a headless web browser to invoke `mocha` to execute integration style tests. Karma replaces that solution with a slightly different approach. Rather than being a headless web browser, karama is a process that launches real browsers like chrome and firefox, runs your tests it, displays the results in you terminal.

### 4 Summary

Matias and I also wrote out my first ever AngularJS feature. We covered some high level concepts pretty quickly that I'll talk about in one of my next posts. I'm really looking forward to being mentored by him daily setting and picking things up much quicker than I would on my own.