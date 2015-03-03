layout:
  - layout
title: Fun with Singleton (Python, JavaScript, Java)
date: 2015-02-26 12:18:42
categories: Python

tags: Python
---

They say that Singletons, like global variables, are evil. They hide dependencies; are harder to test and even harder to extend. Singletons are lies, and it’s best to keep away from them. But, there are scenarios where you need them. For example, when you want a shared resource like printer spooler or file manager or log manager, you want a single object to handle requests from all the various parts of your application.

In this blog, I am going to explore various ways to make Singletons in languages like Python, Java and Javascript so as to keep it simple, elegant and usable. Let’s talk about Python first. I love it, and it’s a really really wonderful language, and in here, there are n different ways to solve a problem. Singletons are no exception. The most natural way to do it is to create a decorator.

``` python
class Singleton(object):
    def __init__(self, klass):
        self.klass = klass # class which is being decorated
        self.instance = None # instance of that class
    def __call__(self, *args, **kwargs):
        if self.instance is None:
            # new instance is created and stored for future use
            self.instance = self.klass(*args, **kwargs)
        return self.instance
```

Now, let’s say you have a Resource class. To make it singleton, you just need to decorate it with ‘@Singleton‘, and you are done.