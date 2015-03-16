Date: 2014-05-23 11:00
Title: Connecting To Oracle In Python
Category: Oracle, Python
Tags: Oracle, Python

# Metadata

This document is formatted using MarkDown

This work was done by Anthony Beck, [OrcID: 0000-0002-2991-811X](http://orcid.org/0000-0002-2991-811X).

Part of the series about working in Oracle and not enjoying it

# Background

Like all things in Oracle doing something simple is very complicated. At work we keep things in Oracle databases. I want to start connecting to these databases so I can start to develop dynamic reports on the underlying data using tools like [dexy](http://dexy.it/). For me this means connecting in Python. This should mean I don't spend all my life re-formatting tables for publication in different environments but I can also expose my data processing workflows. To connect to other databases one invokes a simple command in pip to install the connection library:

> pip install psycopg2 #postgres

But not in the wacky world of Oracle! Heaven forfend that the user should be empowered to do something so simple when you can charge consultancy to do it for them or force them to use an Oracle only software stack!

I used the [following guide](http://iambusychangingtheworld.blogspot.co.uk/2013/06/python-oracle-sqlalchemy-on-ubuntu-1304.html). It worked. It was painful. It should be unnescessary.