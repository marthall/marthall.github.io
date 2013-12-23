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
2. Add a `setup.py`-file
3. Upload to [PyPI](https://pypi.python.org)

After this, you and anyone else can install it by typing:

{% highlight bash %}
pip install my_awesome_app
{% endhighlight %}

## Write your script

The script can really simple or big and advanced. We'll cover the most basic example

{% highlight python linenos %}
def hello_world():
    print "Hello World"

if __name__ == '__main__':
    main()
{% endhighlight %}
