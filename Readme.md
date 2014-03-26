Heroku buildpack: Python
========================

This is a fork of https://github.com/heroku/heroku-buildpack-python.
We needed libffi (for pylibmc/memcachier and djangosaml2).
One of the other buildpacks on github was broken, and another one had an old version of the heroku build pack. So this buildpack is synchronized with the latest copy of heroku's official python buildpack. The only additional files are bin/steps/libffi, and linking to bin/steps/libffi in bin/compile.

To add this buildpack to upcoming builds of an existing application:

    $ heroku config:add BUILDPACK_URL=git://github.com/heroku/heroku-buildpack-python.git
