Sass-java-tryout
================

[![Build Status](https://travis-ci.org/keesvandieren/sass-java-tryout.png)](https://travis-ci.org/keesvandieren/sass-java-tryout)


Tryout to combine Sass and Java in a standard war project.

I assume that you are using IntelliJ IDEA as IDE. Some hands-on experience with Java and Maven will be helpful.

## Goals of tryout

One of my companies customers is about to use SCSS in one of their projects. Their current stack is made up with Java.  Goals of this tryout is to find out how Java and SCSS suite together.

Questions answered during my journey:

 * Why Sass and not just plain CSS?
 * How are Sass, SCSS, CSS, and Compass related to each other? 
 * How to integrate Sass in a war project?
 * Is it possible to change Sass file without restarting the container?
 * Does a Maven project that wants to compile Sass, need Compass executable installed on the machine?
 * Can we make the Maven build fail if Sass compilation fails?
 
 During this tryout we also created some exercises to get familiar with basic Sass syntax with some exercises.

## Why Sass and not just plain CSS?
CSS has many limitations, such as: no support for variables, no inheritance, no composition etc. Writing CSS needs a lot of copy paste, which makes it hard to maintain CSS  files.

One way to take away maintenance pain is to make use of a CSS preprocessor. Most known preprocessors are [LESS](http://lesscss.org/) and [Sass](http://sass-lang.com/).

I decided to go for Sass in my tryout.

## Why Sass?
It seems that Sass [is getting most attention](http://www.google.nl/trends/explore#q=%2Fm%2F054k6n_%2C%20%2Fm%2F03qlp8&cmpt=q), so we decided to give it a try.

## How are Sass, SCSS, CSS, and Compass related to each other?
CSS stand for Cascading Style Sheets. It is a way to define design for an HTML document, and browsers understand it.
 
SCSS stands for Sassy CSS. It is a superset of CSS, and adds support for variables, inheritance and composition.

SASS stands for Syntactically Awesome Stylesheets. Sass is the language, which compiles SCSS files into CSS files that can be understand by browsers.

You may also have heard of Compass. Compass is a CSS authoring framework. Main features include:

* Predefined reusable sass extensions
* Generate sprite image from list of images
* Generate grid background image.

## How can we integrate Sass in a java war?

Sass is made in the Ruby language. Ruby can run on the JVM using JRuby. There are a few integrations available that
use JRuby. The ones we tested out are:

* [Sass Java component provided by Darrin Holst](https://github.com/darrinholst/sass-java)
* [Jasig sass maven plugin](https://github.com/Jasig/sass-maven-plugin)

I started the tryout using the Sass java component provided by Darrin Holst. It uses servlet Filter to monitor scss files that
recompiles on the fly if necessary. This works great for development.

However there is a nasty problem that kills this approach: adding JRuby to the classpath of `mvn jetty:run` increases startup time
with 20 seconds.

Next was to try the other plugin: the [Jasig sass maven plugin](https://github.com/Jasig/sass-maven-plugin). With that plugin, automatic recompile on change can be achieved with a separate maven goal that needs to run in its own console with `mvn sass:watch`.

## Run the sample war project

To run the war use following steps:

* Clone the project with git clone https://github.com/keesvandieren/sass-java-tryout.git
* cd sass-java-tryout
* mvn jetty:run
* Go to [http://localhost:8080](http://localhost:8080) to see Sass in action.

The Sass sources are in src/main/webapp/WEB-INF/sass.

The CSS files are compiled to src/main/webapp/stylesheets.

## Making changes to scss files without restarting the container
It is possible to change scss files, and see the changes reflected in the browser without container restart.

Steps to achieve this:
* open a seperate console
* cd sass-java-tryout
* mvn sass:watch.

## Other references

* Learn Sass language concepts. Read the [Sass guide](http://Sass-lang.com/guide).
* Install Compass, read the [Compass install guide](http://compass-style.org/install/).
* Checkout [this GitHub project](https://github.com/keesvandieren/Sass-java-tryout) and import it in IntelliJ IDEA
* Run application with `mvn jetty:run`
* Visit [http://localhost:8080/](http://localhost:8080/) to see the examples
* Make changes in src/main/webapp/WEB-INF/sass
* Refresh [http://localhost:8080/](http://localhost:8080/) in the browser to see the changes applied. 

## Conclusions:
* Embedded Sass in the war takes long time to start. Starting Compass should be optional, only when developer needs
  to update Sass files.
* Sass integration in Java web applications is easy.
* Compass needs to be installed on the developers work station in order to edit .scss files in IntelliJ IDEA with IDE support.

## Feedback and suggestions
Please send that to [@keesvandieren](https://twitter.com/keesvandieren) or contact us at 
[www.squins.com/contact](http://www.squins.com/contact)





 
 
 
 
