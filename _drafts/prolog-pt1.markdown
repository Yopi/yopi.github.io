---
layout: post
title:  "Prolog Pt. 1"
date:   2013-12-06 17:02:54
categories: blog
tags:
  - prolog
  - code
---

Prolog - Programmation en Logique
======

This is the first post on a series about Prolog the language, I'll get more in 
depth about what I like about Prolog and what it's good for in the later posts,
see this as an little introduction.

Before starting this semester I had never heard of Prolog, which I do feel a bit
bad about. It seems like most people have heard some things about it, but never
really tried it out. It's a shame because it is a really interesting language 
after all.

Describing Prolog[^1] is much easier if you've got a grasp of (first order) Predicate
logic, though I don't think it is overly hard to learn even if you don't.
Most things in Prolog are written as logical predicates, and the goal is to write
as much code as possible in logic style. However, there are a few things that have
been added to Prolog to make it easier to program in, but makes it less pure as
a logic language. Examples of such are the "write" predicate that prints text to
the output, and the cut ("!") predicate, which prevents backtracking from that point.

Now that I've brought up backtracking, I want to expand a bit further on that point
because it is one of the main points of Prolog, as I see it. What Prolog does is
that everytime it fails a predicate, it tries the next one (if there is one to try),
and then it continues like that until it either succeeds, or has exhausted all 
possibilities.

To give a very trivial example:

```prolog
is_parent(Person) :- Person == john.
is_parent(Person) :- Person == joe.
is_parent(Person) :- Person == jack.
```

Now calling is_parent(jack). will be true. However, Prolog will try the predicates
in order, so it'll try is_parent(jack) :- jack == john, which will fail. It will 
then do the ame for joe, and finally with jack which will then succeed.

Giving a simple example like this does not do much good, but it shows in a little
bit how Prolog works. If each of those predicates in turn tried predicates that
had multiple ways of being true, then the proof tree would increase in size, but
Prolog would try each combination still.

The second big point about Prolog are non-set variables

[^1]: http://en.wikipedia.org/wiki/Prolog