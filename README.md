Azkaban Project Main Site
====================

For use with Azkaban site and Azkaban Docs site. It contains information common
to all repos in the project such as the license page.

View the page at [Azkaban Github Page](http://azkaban.github.io/).

View the site Locally
========

One time setup:

It is **highly recommended** to use RVM for creating an isolated Ruby environment before installing packages.
Using RVM will prevent possible conflicts with the default Ruby interpreter that comes with your OS.  
Information for installing RVM can be found [here](https://rvm.io/rvm/install) and basic usage 
is found [here](https://rvm.io/rvm/basics).

The following instructions presume that RVM is installed and will create an isolate environment 
before downloading needed dependencies from the Internet.

    $ rvm gemset create azkaban.gethub.io
    $ rvm gemset use azkaban.gethub.io
    $ gem install bundler
    $ bundle install

To start a local jekyll server, run the following within your RVM environment.

	  $ bundle exec jekyll serve -P 4001

Then visit http://localhost:4001 to view the locally rendered content.

More information about jekyll is [here](https://help.github.com/articles/using-jekyll-with-pages/)
