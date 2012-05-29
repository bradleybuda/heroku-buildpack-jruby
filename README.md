# Heroku buildpack for JRuby + JDK7 + Rails

*NOTE*: This doesn't really work right now. Try [the JRuby official buildpack](https://github.com/jruby/heroku-buildpack-jruby/) instead.

A buildpack to fast and easy use JRuby on Heroku. Just create a Heroku app like this:

    heroku create -s cedar --buildpack https://github.com/bradleybuda/heroku-buildpack-jruby.git 

It will download and unpack JRuby from [jruby.org](http://jruby.org/), install [Bundler](http://gembundler.com/) and run ```bundle install``` and then use your ```Procfile```.

Example ```Procfile```:

    web: bin/mizuno -p $PORT -E $RACK_ENV

Note: You do normally not want to use ```bundle exec``` with JRuby. Use the binstubs (in ```bin/```) instead, and put ```require 'bundler/setup'``` before any other ```require```.

Current JRuby version: 1.7.0.preview1

The samples, docs, and native libraries were removed from JRuby to reduce slug size.

For now only supports 1.9 mode, open an issue if you need 1.8 mode.

Example application: [github.com/carlhoerberg/heroku-jruby-example](https://github.com/carlhoerberg/heroku-jruby-example)

## JDK 7

This buildpack comes with the Oracle JDK7u4 release. To keep the slug size down, the JDK distribution has been modified to remove several files:

* db/ - The Derby DB
* src.zip
* lib/visualvm
* man/
* include/
* jre/lib/fonts/

## Servers

The only successfully-tested web server is [Mizuno](https://github.com/matadon/mizuno).

Other possible JRuby servers are:

* [Trinidad](https://github.com/trinidad/trinidad) - A wrapper around [Tomcat](http://tomcat.apache.org/)
* [Puma](http://puma.io) - A server written in Ruby, wraps the Ragel parser (from Mongrel)

A comparison can be found here: [carlhoerberg.github.com/blog/2012/03/31/jruby-application-server-benchmarks/](http://carlhoerberg.github.com/blog/2012/03/31/jruby-application-server-benchmarks/)

## License terms

Copyright (C) 2012 by Carl Hörberg

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
