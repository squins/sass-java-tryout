Sass-java-tryout
================

Tryout to combine Sass, Java in a standard war project.

We assume that you are using IntelliJ IDEA as IDE, and has hands-on experience with Java and Maven.

## Goals of tryout
Goals of this tryout are to answer the following questions:

 * Why Sass and not just plain CSS?
 * How are Sass, SCSS, CSS, and Compass related to each other? 
 * How to integrate Sass in a war project?
 * Is it possible to change Sass file without restarting the container?
 * Does a Maven project that wants to compile Sass, need Compass executable installed on the machine?
 * Can we make the Maven build fail if Sass compilation fails?
 
 Additionally, I'd like to get familiar with basic Sass syntax with some exercises. 

## Why Sass and not just plain CSS?
CSS has many limitations, such as: no support for variables, inheritance, composition etc. That takes out the fun of 
writing css, as lots of copy-paste is needed to get the job done.
 
One way to take away this pain is to make use of a CSS preprocessor. Most known preprocessors are 
[LESS](http://lesscss.org/) and [Sass](http://Sass-lang.com/).

I decided to go for Sass in my tryout.

## Why Sass?
It seems that Sass 
[is getting most attention](http://www.google.nl/trends/explore#q=%2Fm%2F054k6n_%2C%20%2Fm%2F03qlp8&cmpt=q), so we 
decided to give it a try.

## How are Sass, SCSS, CSS, and Compass related to each other?
CSS stand for Cascading Style Sheets is a way to define design for an HTML document. There are 3 majors versions: CSS 1, 
CSS 2 and CSS 3.

All major browsers support CSS 1 and CSS 2. Most browsers support CSS 3 partially.
 
Sass stands for Syntactically Awesome Stylesheets. It is a CSS preprocessor that adds features 
currently missing in CSS. It compiles Sass files to CSS 3. It helps producing better CSS. Main advantages over plain CSS 
are:
                                                                   
* No more code duplication as needed in CSS
* Makes it a lot easier to get CSS that works well across all current browsers
* SCSS readability is better than CSS readability.
  
SCSS is one of the two syntaxes available in Sass. It is a superset of CSS 3, making it easy to embed existing CSS 
stylesheets. For sake of simplicity, other syntax won't be handled here.

Compass is a CSS authoring framework build on top of Sass. It adds many standard Mixins (reusable functions) for CSS3
and other features. Most CSS3 features are supported though vendor-specific prefixes. Compass mixins helps to support
them all in an easy-to-read manner.

## How can we integrate Sass in a java war?
                                                                                                             
This project integrates Sass in a Java war. Compass is started using a Servlet Filter, as defined in web.xml. Servlet 
filter is created by Darrin Holst and is [available on GitHub](https://github.com/darrinholst/Sass-java). This GitHub
project also provides a Maven plugin.   

### Run the war
Run the project with mvn jetty:run. Go to [http://localhost:8080](http://localhost:8080) to see the results.

NOTE: startup may take a while, as during startup JRuby with Compass is started, which might take up to 30 seconds.

The Sass sources are in src/main/webapp/WEB-INF/sass

## Making changes

To make changes, perform following steps:

* Learn Sass language concepts. Read the [Sass guide](http://Sass-lang.com/guide).
* Install Compass, read the [Compass install guide](http://compass-style.org/install/).
* Checkout [this GitHub project](https://github.com/keesvandieren/Sass-java-tryout) and import it in IntelliJ IDEA
* Run application with mvn `jetty:run`
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





 
 
 
 
