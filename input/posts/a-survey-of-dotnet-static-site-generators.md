Title: A Survey of .NET Static Site Generators
Published: 10/6/2014
Edited: 6/22/2015
Tags:
  - programming
  - static site generator
  - open source
---
<div role="alert" class="alert alert-info">    <div><strong>Update June, 2015:</strong> Since writing this post, I've finally decided to act on my long-standing interest in static site generators and write the kind of one I want to use. If you're interested, <a href="http://wyam.io" class="alert-link">check out Wyam</a>! It has most of the features of the generators listed below and is configured via a flexible module-based approach.</div>
</div>

There is a lot of demand and a lot of active development around static site generators. If you're not familiar with them, these tools take markup or other simplified content and turn those resources into a full static website (HTML, CSS, etc.). There are a number of great static site generators out there, and it seems like a new one is released nearly every week. However, for this survey I am going to focus on the state of static site generation in the .NET ecosystem.

Why should we care about .NET static site generators as opposed to just using one of the non-.NET static site generators? For one, there are a number .NET-specific technologies that a .NET developer might already be familiar with and want to exploit (for example, the Razor templating engine). For another, while many of the most popular static site generators work just fine on Windows systems, it's not the primary deployment target and can feel a little bit hackish to set up, especially if you have to install frameworks or technologies you wouldn't otherwise use. While a .NET static site generator wouldn't necessarily be the only way to find one that works well on Windows with pre-installed libraries, it's a fair assumption that they would at least have a friendlier user experience for Windows and .NET developers. Finally, there are potential opportunities for a .NET developer to extend or integrate with a .NET static site generator that just wouldn't exist with those built on other platforms.

# Why Are Static Site Generators Becoming So Popular?

Before we get to the survey, let's back up a step and consider static site generators in general. Specifically, why are they becoming *so* popular right now? I think it's a combination of a few factors:

* **An emphasis on site speed.** As web sites get more and more complex, there has been a backlash against the increased delivery times needed by more dynamic site technologies. The modern web user expects content almost instantly and anything that can help meet those performance goals is something worth investigating and implementing. Delivering static content instead of dynamic content certainly helps here, and it moves the burden of generating content away from the user and web server and towards the developer and build environment.

* **A shift to the client for dynamic content.** It used to be that if you wanted dynamic content on your site, you had to rely on the server to generate and deliver it to the user as HTML. However, in the last couple years there has been an explosion of front-end frameworks designed to provide very powerful dynamic capabilities from the client. To this end, it's now possible (and becoming more popular) to shift this burden onto the client and rely on Ajax and DOM changes to retrieve dynamic content through web services and inject it into the page after it's been delivered. This helps with the site speed problem described above, but also helps remove load from the content delivery servers and moves it onto back-end servers that may be more equipped to deal with it.
        
* **A backlash against traditional Content Management Systems (CMS).** With the explosion of new frameworks for managing and delivering content, designers and developers are getting tired of business as usual from the crop of traditional CMS tools. Many are bloated, slow, and out of touch with more modern development tools, techniques, and methodologies. Most have also been designed from the beginning to serve a niche of allowing non-developers to create blogs or web sites. When there weren't many other options, many developers accepted that using a CMS was the most efficient way to get their ideas on the web. Now that a huge variety of tools exist to help even a more entry-level developer craft their vision, many are re-evaluating how much hand-holding they need and how much control they want to retain over their technology stack.

# What I Looked For

Many static site generators tend to share similar traits, after all there are only so many ways to accomplish a particular task. For this survey I tried to focus on the following capabilities. Note that I relied heavily on browsing documentation, examples, and source code. This was a survey and not a test, so I didn't have time to install and run each tool.

* **Ease of use.** What installation steps are required? Can the tool be run from the command line? Are the commands easy to learn and use? What kind of configuration file is needed (if any)? Does it work out of the box? Does the tool enforce a strict folder hierarchy or can it be configured? What kind of control is provided over inputs and outputs (include/exclude, file names, etc.)?

* **Metadata.** Is there a way to use additional metadata and make it available to the templates (I.e., list Jekyll YAML front matter)?

* **Templating engine(s).** How many and what kind of templates does the tool support? I'm primarily interested in Razor and/or Markdown, but additional template support is welcomed. Does the tool support other types of content such as the compilation of Less or SASS files to CSS? Can common layouts be used?

* **Testing support.** What kind of testing support does the tool have? Can a preview be generated? Can it launch a web server to check the results?


# Here They Are

To try and get a complete list, I checked sites that aggregate static site generators including <a href="http://staticsitegenerators.net/">Static Site Generators</a> and <a href="https://www.staticgen.com/">StaticGen</a> (the simple fact that there are two such sites says a lot about static site generator popularity). I also scoured Stack Overflow, GitHub, and the web to see if I could turn up any additional ones.

<div class="table-responsive">
 <table class="table">
  <thead>
   <tr>
    <th>Generator</th>
    <th>Configuration</th>
    <th>Metadata Support</th>
    <th>Templating Engine(s)</th>
    <th>Testing Support</th>
    <th>Documentation</th>
   </tr>
  </thead>
  <tbody>
   <tr>
    <td><strong>Pretzel</strong></td>
    <td>Command line arguments</td>
    <td>No support</td>
    <td>Razor</td>
    <td>Embedded web server, regeneration on file change</td>
    <td>Sparse</td>
   </tr>
   <tr>
    <td><strong>Graze</strong></td>
    <td>XML config file</td>
    <td>In XML config file</td>
    <td>Razor, Markdown</td>
    <td>None</td>
    <td>Sparse</td>
   </tr>
   <tr>
    <td><strong>Champ</strong></td>
    <td>Command line arguments</td>
    <td>At top of file</td>
    <td>Razor, Markdown, Less</td>
    <td>Regeneration on file change</td>
    <td>Moderate</td>
   </tr>
   <tr>
    <td><strong>StaticSiteGenerator</strong></td>
    <td>Command line arguments</td>
    <td>At top of file, side-by-side files, global files</td>
    <td>Razor, Markdown, Creole, Textile</td>
    <td>Embedded web server, regeneration on file change</td>
    <td>Moderate</td>
   </tr>
   <tr>
    <td><strong>Ocam</strong></td>
    <td>XML config file</td>
    <td>At top of file</td>
    <td>Razor, Markdown</td>
    <td>None</td>
    <td>Moderate</td>
   </tr>
   <tr>
    <td><strong>Mulder</strong></td>
    <td>Command line arguments</td>
    <td>None</td>
    <td>Razor, Markdown</td>
    <td>None</td>
    <td>Sparse</td>
   </tr>
   <tr>
    <td><strong>Sandra.Snow</strong></td>
    <td>Command line arguments, JSON config file</td>
    <td>At top of file, in JSON config file</td>
    <td>Razor, Markdown</td>
    <td>Embedded web server, regeneration on file change</td>
    <td>Sparse</td>
   </tr>
  </tbody>
 </table>
</div>

<h2>Pretzel <small><a href="http://code52.org/pretzel.html">Site</a>, <a href="https://github.com/Code52/pretzel">GitHub</a></small></h2>

<p>The generator that seems to come up most often in searches is Pretzel. Pretzel is one of the projects undertaken by <a href="http://code52.org/">code52</a>, a short-lived experiment in rapid application prototyping and development undertaken by some notable .NET developers. It was originally released in January, 2012 and has had some incremental improvement since then, mostly of the accepting pull request variety.</p>
<p>Pretzel aims to be very similar to <a href="http://jekyllrb.com/">Jekyll</a>, which is a good thing since Jekyll is arguably the most popular of the new breed of static site generators. Pretzel runs on the command line and supports three basic commands: <code>create</code> which bootstraps a folder structure to use, <code>bake</code> which generates the static content, and <code>taste</code> which allows for local testing using <a href="http://loudej.github.io/firefly/">Firefly</a>. There is a minimum of documentation and it's unclear what templating engines it currently supports (for example, the <code>packages.config</code> file lists <code>Microsoft.AspNet.Razor</code> but no Markdown libraries).</p>
<p>Overall, I'd say Pretzel looks like the start to an interesting alternative to Jekyll for the .NET stack, but it doesn't appear ready for production use. That's not to say you couldn't use it for a production site. Hey, if it works it works. However, it lacks the documentation, polish, and community I would normally expect from a stable and robust production-quality tool.</p>

<h2>Graze <small><a href="http://mikaelkoskinen.net/graze-static-site-generator-using-razor/">Blog Post</a>, <a href="https://github.com/mikoskinen/graze">GitHub</a></small></h2>

<p>Graze was actually released around the same time as Pretzel in early 2012. It runs on the command line and relies on a configuration file to set things up. There is a NuGet package available, but it looks like it's out of date.</p>
<p>Graze relies on XML files for configuration and data. It allows you to define simple site properties such as a title as well as define metadata which will be made available to the templates during generation.</p>
<p>Both the <a href="http://mikaelkoskinen.net/graze-static-site-generator-using-razor/">introductory blog post</a> and the GitHub readme refer to using Razor for templating. The documentation also mentions Markdown support and the source appears to embed <a href="https://code.google.com/p/markdownsharp/">MarkdownSharp</a>, so it's a safe bet Markdown templates are supported as well. Graze perscribes a very strict folder structure, which is how it knows what kind of processing to do to which files. There doesn't appear to be a way to customize this.</p>
<p>I would say Graze is at about the same level of maturity as Pretzel. It could potentially be used for production work, but I wouldn't consider it a complete tool at this time due to the lack of documentation, examples, community, etc.</p>

<h2>Champ <small><a href="https://github.com/lukevenediger/champ">GitHub</a></small></h2>

<p>Champ appears to be under somewhat regular development. It's billed as "A sensible static site generator that uses Razor templates with Markdown files and runs on Windows" which address one of the main reasons why I think a .NET static site generator is worth considering.</p>
<p>Champ can be run either on the command line or as a library (though no NuGet package is available). Like many other static site generators, Champ relies on a specific folder structure to indicate what to do with certain types of files. It can process Razor templates as well as Markdown files and Less CSS stylesheets. It also has support for adding metadata at the top of files and for specifying templates for each page.</p>
<p>Development in Champ appears to be ongoing, and while it already has a few more features than either Pretzel or Graze (such as specifying templates), I wouldn't necessarily say it's any more mature than the other two. That said, Champ does have slightly better documentation and comes with a number of helpful example projects.</p>

<h2>StaticSiteGenerator <small><a href="http://www.hilbert.dk/thomas/pub/dev/StaticSiteGenerator/">Blog Post</a>, <a href="https://bitbucket.org/hilbert/staticsitegenerator/">BitBucket</a></small></h2>

<p>StaticSiteGenerator appears to have been under heavy development in the fall of 2013 (but nothing since then) and is written in F#. It handles the generation process a little bit differently than typical generators. Given a source directory, it scans for any markup files, transforms them, and then runs the result through a Razor parser. It also supports metadata via a Yaml file header similar to Jekyll front matter, a separate file side-by-side with a given markup file, or global Yaml files at the root of the site.</p>
<p>Based on the documentation (of which there is a decent amount), StaticSiteGenerator looks like it was primarily a hobby project to learn F# and provide some static site generation capabilities for the author. That said, it has a large feature base and is probably the most complex of the reviewed generators.</p>

<h2>Ocam <small><a href="http://toddlucas.github.io/ocam/">Site</a>, <a href="https://github.com/toddlucas/ocam">GitHub</a></small></h2>

<p>Ocam looks like another one that was built during a small time window in early 2012 (there have been no commits since). Like Pretzel, it takes make queues from Jekyll but attempts to put a .NET spin on things by processing Razor templates (in addition to Markdown).</p>
<p>Ocam uses an XML configuration file, though it's unclear exactly what this can or should contain. Front matter can also be added to Markdown files, though it's worth noting it accepts a simple key/value syntax limited to specific properties and is not full Yaml. Ocam also has limited support for layouts, which can be specified in the front matter or in a special <code>_PageStart.cshtml</code> file. Like most of the other generators, Ocam requires a specific directory structure.</p>
<p>Generally, Ocam looks similar in maturity to all the other static site generators reviewed so far. That is, it's reasonably complete for what it does, but it has limited functionality, support, and documentation.</p>

<h2>Mulder <small><a href="https://github.com/dragan/mulder">GitHub</a></small></h2>

<p>Mulder appears to have been developed gradually over several years (though the last commit was early 2013). Unlike the other generators, many of which appear to be based on concepts in Jekyll, Mulder is based on <a href="http://nanoc.ws/">nanoc</a>. The documentation is very sparse, so it's unclear exactly what functionality Mulder offers (the GitHub readme says "Mulder is currently in pre-Alpha state and doesn't have a public release yet"). By looking at the source, it does appear to at least support Razor and Markdown and also contains some code for dealing with Yaml (though it's unclear for what). The code does look well structured and contains many tests. It's unclear what the intent for Mulder was in early 2013 when development stalled. It looks promising, but without a little more information it's tough to tell how far along it currently is.</p>

<h2>Sandra.Snow <small><a href="https://github.com/Sandra/Sandra.Snow">GitHub</a></small></h2>

<p>Sandra.Snow is a newer tool relative to many of the other ones in this round-up, having started development in early 2013. It also appears to be under heavier development with a large number of commits and other activity. It's described as "a Jekyll inspired static site generation tool that can be run locally, as a CAAS(Compiler as a Service) or setup with Azure to build your site when your repository changes." It's built on <a href="http://nancyfx.org/">Nancy</a> and the two primary contributors are notable members of that community (though Sandra.Snow also seems to have a growing community of it's own). On paper at least, it appears to have many of the traits of a healthy Open Source project that the other generators in this list are lacking.</p>
<p>Unfortunately, there isn't much by way of documentation. By looking through the source and NuGet packages, I can infer that both Razor and Markdown are supported. It also looks like there is support for an embedded web server for testing (by using the <code>-server</code> command line argument). There are also a number of source files dedicated to other aspects of a complete blogging platform such as RSS, tags, etc. and in general the primary focus of Sandra.Snow appears to be blog sites. It also looks like there is support for Yaml-style or plain key/value front matter within page files, though it is unclear whether the particular keys are pre-defined or can be user specified. There also appears to be some interesting markup possibilities using XML-style comments (for example, <code>&lt;!--excerpt--&gt;</code> looks like it helps find excerpts for posts). All in all, the features I can gather from a quick stroll through the code look promising.</p>
<p>Sandra.Snow can be run in multiple ways, including from within Visual Studio to create the static content on build (which I think is a very nice feature). The project shows a lot of promise and I'm looking forward to seeing where it goes. However, the lack of any real documentation will make it hard for someone to just pick up and use. I assume that's primarily due to the maturity of the tool and an ongoing development effort. Once things get a little more stable and it makes sense to generate some actual documentation, this could be a viable generator for production use.</p>

<h1>Non-.NET Static Site Generators</h1>

<p>For context it's probably worth looking at a couple non-.NET static site generators if you're not already familiar with some. I won't take up space (or time) reviewing them, but the following generators are currently very popular:</p>

* <a href="http://jekyllrb.com/">Jekyll</a> (and <a href="http://octopress.org/">OctoPress</a>)
* <a href="http://middlemanapp.com/">Middleman</a>
* <a href="http://hexo.io/">Hexo</a>
* <a href="http://www.metalsmith.io/">Metalsmith</a>
* <a href="http://assemble.io/">Assemble</a>
* <a href="http://gohugo.io/">Hugo</a>

<h1>Conclusions</h1>

<p>It's interesting to me that the two most popular .NET static site generators, Pretzel and Graze, appear to be somewhat less polished than some of the alternatives. I suspect that may be due to a combination of how long ago they were released (relatively speaking) and the general popularity of their creators (both were written by prominent members of the .NET community). That said, <em>polished</em> is relative in this case and I wouldn't call any of the currently available .NET static site generators particularly good in this regard. Why is that? I suspect that writing a static site generator is one of those things that's very easy to start developing and get some baseline functionality in place, but getting beyond that point requires significantly more effort.</p>
<p>Could or should you use any of these tools for your own site? I suspect that most will work as advertised, but I don't see a particularly good value proposition right now. The only thing that this crop of generators provides that you wouldn't get from one of the more established non-.NET generators is support for Razor parsing. Is that worth the effort to try and use a tool with minimal documentation, stalled development, and basically no community? I don't know, the answer probably depends on the requirements and your situation.</p>
<p>Regardless, I am disappointed there aren't any better options in the .NET ecosystem. As many .NET developers have lamented before, we're often left with half-built clones that succeed in aspiration and intent if not in implementation. What can be done about it? Not much unless you're interested in developing yet another static site generator. Or perhaps one of these may catch on and begin forming a community (as Sandra.Snow appears to be doing).</p>
<p>There is also cause for optimism. I am encouraged that there is still innovation going on, and Sandra.Snow is a good example of this. While it appears to be in the early stages, it's obvious that the developers have a solid vision and the momentum to follow-through as long as things don't stall out. As static site generation continues to gain in popularity, I wouldn't be surprised to see one or two more reputable projects take on the challenge. If nothing else, each of the tools I've looked at serves as a good incremental building block and a source of ideas for the next developer.</p>
