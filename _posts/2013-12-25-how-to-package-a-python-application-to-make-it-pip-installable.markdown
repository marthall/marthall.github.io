---
layout: post
title: "How to package a python application to make it pip-installable"
date: 2013-12-23 18:00:00
categories: python pip package
permalink: blog/how-to-package-a-python-app
---

# {{ page.title }}

Python scripts are usable for a lot of stuff, i.e. fetching tha latest posts from /r/python or counting the total number of lines in your project folder. However, remembering where a script is placed and having to type `python dest/to/script/myscript.py` every time can be a lot of pain. Of course, you can make an alias so you only have to type `myscript` to run it, but it would be much nicer to make the script available from any computer, any place, and in addition possibly helping others with the same problem.

It only takes three simple steps to make you python app pip-installable.

1. Write your script or application
2. Add a setup script
3. Upload to [PyPI](https://pypi.python.org)

After this, you and anyone else can install it by typing:

{% highlight bash %}
pip install my_awesome_script
{% endhighlight %}

## Write your script

The script can really simple or big and advanced. We'll cover the most basic example

{% highlight python linenos %}
#!/usr/bin/env python
print "Hello World"
{% endhighlight %}

You can name the script anything, but this name will be the name you'll be typing every time, so make sure it's not to difficult. We'll name our script `helloworld`.

## Add a setup script

The `setup.py` file is is the centre of building, distributing and installing modules using the Distutils.

{% highlight python linenos %}
from setuptools import setup

setup(
    name='my-awesome-helloworld-script',    # This is the name of your PyPI-package.
    version='0.1',                          # Update the version number for new releases
    scripts=['helloworld']                  # The name of your scipt, and also the command you'll be using for calling it
)
{% endhighlight %}

**Optional**: We can now package the script using `python setup.py sdist`. This will create a `dist` folder containing all your distributions. After unpacking the distribution file, you can simply install it using `sudo python setup.py install`.

## Upload to PyPI

First, you need to register the package on PyPi. This is simply done by typing `python setup.py register`. If you haven't registered a package from this computer before, you'll be prompted with this message:

{% highlight sh %}
$ python setup.py register
running register
We need to know who you are, so please choose either:
1. use your existing login,
2. register as a new user,
3. have the server generate a new password for you (and email it to you), or
4. quit
Your selection [default 1]:
...
{% endhighlight %}

Once this is done, register will ask you if you want to save your login information in the `.pypirc` file. By default, this will store the login name and the password. The next step is to upload your package. Just type `python setup.py sdist upload`, and the package is now available on PyPI! You can save a few keystrokes by doing it all in one command: `python setup.py register sdist upload`.

## Install using pip

Finally, you can now install you package with `pip install my-awesome-helloworld-script`. You probably want to `sudo` that line. You can now run the script with:

{% highlight sh %}
$ helloworld
Hello world!
{% endhighlight %}

## What's next?

All code from this guide can be found [here](https://gist.github.com/marthall/8122805). For more advanced programs and packages, I recommend [this guide](http://www.scotttorborg.com/python-packaging/) by Scott Torborg.


