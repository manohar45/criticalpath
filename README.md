CriticalPath
============

Calculates the [critical path](http://en.wikipedia.org/wiki/Critical_path_method) through a network of tasks.

Assumes the given graph is acyclic (has no loops).

Installation
------------

    pip install criticalpath

Usage
-----

    >>> from criticalpath import Node
    >>> p = Node('project')
    >>> a = p.add(Node('A', duration=3))
    >>> b = p.add(Node('B', duration=3, lag=0))
    >>> c = p.add(Node('C', duration=4, lag=0))
    >>> d = p.add(Node('D', duration=6, lag=0))
    >>> e = p.add(Node('E', duration=5, lag=0))
    >>> p.link(a, b).link(a, c).link(a, d).link(b, e).link(c, e).link(d, e)
    project
    >>> p.update_all()
    >>> p.get_critical_path()
    [A, D, E]
    >>> p.duration
    14
