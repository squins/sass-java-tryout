# Sass-java-tryout

[![Build Status](https://travis-ci.org/squins/sass-java-tryout.png)](https://travis-ci.org/squins/sass-java-tryout)


## Changelog


14 oct 2017:

* Removed Compass framework (seems dead, support to be removed)
* Updated Jetty, Maven plugin to recent versions.

Tryout to combine Sass and Java in a standard java web (WAR) project.

This project can be used as template for new war projects.

We assume that IntelliJ IDEA is used as IDE. Some hands-on experience with Java and Maven will be helpful.

## Goals of tryout

One of our customers is about to use Sass in one of their projects. Their current stack is made up with Java. Goals of this tryout is to find out how Java and Sass (SCSS) function together.

Questions to answer during my journey:

 * Why Sass and not just plain CSS?
 * How are Sass, SCSS and CSS related to each other?
 * How to integrate the Sass compiler in a java webapp?
 * Is it possible to change Sass file without restarting the container?
 * Is it needed to have Ruby or Sass locally installed to compile the Maven project?
 * How to make the Maven build fail if Sass compilation fails?

During this tryout I created some exercises to get familiar with basic Sass syntax.

## Why Sass and not just plain CSS?

Writing CSS needs a lot of copy paste which makes it hard to maintain CSS files, especially in large projects.

Limitations of CSS include:

* no support for variables
* no inheritance
* no composition.

One way to take away these problems is to make use of a CSS preprocessor. Most known preprocessors are [LESS](http://lesscss.org/) and [Sass](http://sass-lang.com/).

I decided to go for Sass in my tryout.

## Why Sass?
It seems that Sass [is getting most attention](http://www.google.nl/trends/explore#q=%2Fm%2F054k6n_%2C%20%2Fm%2F03qlp8&cmpt=q), so I decided to give it a try.

## How are CSS, SCSS and Sass related to each other?
CSS stand for Cascading Style Sheets. It is a way to define design for an HTML document. Browsers can work with CSS files.

SCSS stands for Sassy CSS. It is a superset of CSS. It adds support for variables, inheritance and composition.

Sass stands for Syntactically Awesome Stylesheets. Sass is the language and compiler. Its compiler compiles SCSS files to CSS.

## How to integrate the Sass compiler in a java webapp?

Sass is made in the Ruby language. Ruby can run on the JVM using JRuby. There are a few integrations available that use JRuby to integrate Sass in Java via a Maven Plugin. The plugins I started with are:

* [Sass Java component provided by Darrin Holst](https://github.com/darrinholst/sass-java)
* [Jasig sass maven plugin](https://github.com/Jasig/sass-maven-plugin)

I started with the first. The plugin uses a servlet Filter to monitor Sass files that recompile modified scss files on the fly when files are modified.

This works well but there is is a nasty problem that kills this approach: adding JRuby to the classpath of `mvn jetty:run` increases startup time with about half a minute.

Next was to try the other plugin: the [Jasig sass maven plugin](https://github.com/Jasig/sass-maven-plugin). With that plugin, automatic recompile on change can be achieved with a separate maven goal that needs to run in its own console with `mvn sass:watch`.

It works well on Ubuntu locally, but after pushing this to Github Travis cannot build it. It fails with the following error:

   org.jruby.embed.EvalFailedException: (TypeError) can't convert String into Array
   at org.jruby.embed.internal.EmbedEvalUnitImpl.run(EmbedEvalUnitImpl.java:136)

Searching for a a solution turned me to [this pull request](https://github.com/Jasig/sass-maven-plugin/issues/47). The issue is open for more than a year, so the project seems to have lost interest of maintainer(s). Starting a new project with an unmaintained plugin is a no-go, so this plugin is no longer an option.

Search for a solution continued. I found [this fork](https://github.com/GeoDienstenCentrum/sass-maven-plugin/) which is maintained, builds on Travis CI and works well locally.

So I stick with this plugin.

## How to run the example project
The sass-java-tryout project has the sass-maven-plugin configured, and some Sass examples included that could be used as a tutorial for developers new to Sass.

To run the application use following steps on a console:

* git clone https://github.com/keesvandieren/sass-java-tryout.git
* cd sass-java-tryout
* mvn jetty:run

Go to [http://localhost:8080](http://localhost:8080) to see Sass in action with several examples.

The .scss sources are in src/main/webapp/WEB-INF/sass.

The CSS files are compiled to src/main/webapp/stylesheets.

## Effective development without container restarts
It is possible to change scss files, and see the changes reflected in the browser without container restart.

Open a new console, and execute commands:

* cd sass-java-tryout
* mvn sass:watch

Changes in .scss files will be compiled instant and available in the webapp by refreshing the page.
## Conclusions
* Sass integration in Java is available with JRuby
* Hot deployment for SASS is available
* All dependencies are managed by Maven; no Ruby or Sass installation needed.

## Next steps
* Read and understand the examples. Review scss files in `src/main/webapp/WEB-INF/sass/`
* Read the sass guide [Sass guide](http://Sass-lang.com/guide)

## Feedback and suggestions
Please [Tweet us](https://twitter.com/squinscom) or contact us via [our contact form](http://www.squins.com/contact).
