sass-java-tryout
================

Tryout to combine Sass, Java in a standard war project

Small tryout to find out how SASS can be used together with Maven and a Java war.

## Goals of tryout
 * How can we integrate SASS in a java war?
 * Is it possible to change sass file without restarting the container?
 * Does a war that needs to compile sass, need Compass executable installed on the OS?
 * Can we make the Maven build fail if SASS compilation fails?
 * Get familiar with basic SASS syntax. 


## Why SASS and not just plain CSS?
CSS has many limitations, such as: no support for variables, inheritance, composition etc. That takes out the fun of 
writing css, as lots of copy-paste is needed to get the Job done.
 
There are a few initiatives to take away this pain: CSS pre-processors. Most known initiatives are 
[LESS](http://lesscss.org/) and [SASS](http://sass-lang.com/).

## Why SASS?
  
It seems that SASS [is getting most 
    attention](http://www.google.nl/trends/explore#q=%2Fm%2F054k6n_%2C%20%2Fm%2F03qlp8&cmpt=q), so we decided to give it 
    a try.

## Getting started

Before we start, we have:

* IntelliJ IDEA as IDE, which supports SASS though Compass. Compass is a CSS authoring framework build on top of SASS.
* An empty Maven project.

## Install Compass
Compass is needed for IntelliJ, in order to find compass component imports. For Java runtime / WAR deployment, it is not needed.

Installation depends on Operating System, check [Compass install guide](http://compass-style.org/install/).

In Ubuntu, you simply could install package ruby-compass with command: `apt get install ruby-compass`

## Review exercises
The exercises are in src/main/webapp.

## Running the examples
Run the project with mvn jety:run. Go to [http://localhost:8080](http://localhost:8080) to see the results.

NOTE: startup may take a while, as during startup JRuby with compass is started, which might take up to 30 seconds.


## Conclusions:
* JRuby slowdowns startup of Jetty too much. This really slows down 'fast feedback' I desire while developing.


## Feedback and suggestions
Please send that to [@keesvandieren](https://twitter.com/keesvandieren)





 
 
 
 
