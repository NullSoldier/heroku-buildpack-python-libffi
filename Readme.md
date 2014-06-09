Heroku buildpack: Python
========================

This is a fork of https://github.com/heroku/heroku-buildpack-python.
We needed libffi (for apns-client and djangosaml2).
One of the other buildpacks on github was broken, and another one had an old version of the heroku build pack. So this buildpack is synchronized with the latest copy of heroku's official python buildpack. The only additional files are bin/steps/libffi, and linking to bin/steps/libffi in bin/compile.

To add this buildpack to upcoming builds of an existing application:

    $ heroku config:add BUILDPACK_URL=git://github.com/BetterWorks/heroku-buildpack-python-libffi.git
=======
Usage
-----

Example usage:

    $ ls
    Procfile  requirements.txt  web.py

    $ heroku create --buildpack git://github.com/heroku/heroku-buildpack-python.git

    $ git push heroku master
    ...
    -----> Python app detected
    -----> No runtime.txt provided; assuming python-2.7.6.
    -----> Preparing Python runtime (python-2.7.6)
    -----> Installing Setuptools (3.6)
    -----> Installing Pip (1.5.6)
    -----> Installing dependencies using Pip (1.5.6)
           Downloading/unpacking requests (from -r requirements.txt (line 1))
           Installing collected packages: requests
           Successfully installed requests
           Cleaning up...
    -----> Discovering process types
           Procfile declares types -> (none)

You can also add it to upcoming builds of an existing application:

    $ heroku config:add BUILDPACK_URL=git://github.com/heroku/heroku-buildpack-python.git

The buildpack will detect your app as Python if it has the file `requirements.txt` in the root.

It will use Pip to install your dependencies, vendoring a copy of the Python runtime into your slug.

Specify a Runtime
-----------------

You can also provide arbitrary releases Python with a `runtime.txt` file.

    $ cat runtime.txt
    python-3.4.0

Runtime options include:

- python-2.7.7
- python-3.4.0
- pypy-1.9 (experimental)

Other [unsupported runtimes](https://github.com/kennethreitz/python-versions/tree/master/formula) are available as well.
